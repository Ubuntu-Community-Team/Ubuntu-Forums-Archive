---
title: "openssl, python, certificates and all the rest of it..."
date: 2009-10-10
forum: Programming Talk
---

### Post by Choad on 2009-10-10
i am a bit bewildered by the world of encryption and was wondering if anyone could help me. i am making a poker game for my final project at uni and it needs to authenticate the server before anything to stop a fake server stealing passwords.

from what i have gathered, using SSL certificates is the way to go. i have created the private key and certificate file using

```
openssl req -new -x509 -days 365 -nodes -out cert.pem -keyout cert.pem
```

and i have created the public key using

```
openssl rsa -in cert.pem -pubout
writing RSA key
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCzQB/LgWCCoyqk2xTd5i9SxfBI
V0ioN2M+uSIb7gOpi+EnGkLizbwXDZQxY0eihKMe61EgO0SVPymZq3k/csNcXrKU
HzSnGtJJDYL3FZVjEP6YjnmgedjvEyOB5iPazfQii50NEURuPke3h1tHqJ1XRvHm
ndZrmfp+I2G7v9GDzQIDAQAB
-----END PUBLIC KEY-----

```

but now i am a bit lost. could anyone who knows what they're doing tell me if i am on the right track, and where i need to go from here? thanks.

---

### Post by Choad on 2009-10-10
i got 
```

s = socket.socket( socket.AF_INET, socket.SOCK_STREAM )
ssl_sock = ssl.wrap_socket( 
	s, 
	ca_certs=ca_certs_file, 
	cert_reqs=ssl.CERT_REQUIRED )
ssl_sock.connect(( host, port ))
```
in my client which i guess just checks the certificate file sent from the server matches the certificate found in the ca_certs file.... but nowhere does it use the public key.... so this can't be secure *confused*

i thought the whole point of this system was that stuff sent is encrypted with the private key and must be decrypted with the public key so that *only* my server can send stuff

i'll attach everything. hope someone know what they're doing

---

### Post by Choad on 2009-10-12
bump. anyone?

---

