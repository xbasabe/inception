FROM alpine:3.17

RUN apk -U upgrade && apk add nginx openssl
RUN openssl req -x509 -newkey rsa:2048 -days 365 -nodes \
	-keyout /etc/ssl/private/xbasabe.42.fr_key.pem \
	-out /etc/ssl/certs/xbasabe.42.fr_cert.pem -sha256 \
	-subj "/C=MO/L=KH/OU=student/CN=xbasabe-.42.fr"
	
RUN chmod 600 /etc/ssl/private/xbasabe.42.fr_key.pem \
	/etc/ssl/certs/xbasabe.42.fr_cert.pem 

COPY conf/default.conf /etc/nginx/http.d/default.conf

#EXPOSE 80/tcp
EXPOSE 443/tcp

#ENTRYPOINT ["nginx", "-g", "'daemon off;'"]
CMD ["nginx", "-g", "daemon off;"]
