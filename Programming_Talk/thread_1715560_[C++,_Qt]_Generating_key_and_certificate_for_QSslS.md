---
title: "[C++, Qt] Generating key and certificate for QSslSocket"
date: 2011-03-27
forum: Programming Talk
---

### Post by dawwin on 2011-03-27
I am writing simple network communicator which uses SSL, and I want to  be sure how to create certificate and private key correctly. I use  following commands to create keys:
```

./CA.pl -newca #creates new CA certificate
./CA.pl -newreq-nodes #creates a new certificate request
./CA.pl -signreq #calls the ca program to sign a certificate request

```(CA.pl script is available in /usr/lib/ssl/misc directory. It's part of OpenSSL)

CA certificate is generated in demoCA/cacert.pem
Private key is newkey.pem
Signed certificate is newcert.pem

On the server I use
demoCA/cacert.pem as argument for addCaCertificate() 
newcert.pem as argument for setLocalCertificate()
newkey.pem as argument for setPrivateKey()
On the client I use
demoCA/cacert.pem as argument for addCaCertificate()
demoCA/cacert.pem is public and I share this for users

I want to know if this, what I described is correct and secure

---

