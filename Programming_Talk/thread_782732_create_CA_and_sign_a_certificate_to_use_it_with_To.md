---
title: "create CA and sign a certificate to use it with Tomcat"
date: 2008-05-05
forum: Programming Talk
---

### Post by lulon on 2008-05-05
Hi, I need help with this, please, I'm doing my final project degree.

I want to create a CA to sign my certificate. This is what I do:

1. I've created my certificate with keytool.

2. With this certificate I've created my CSR

3. I've created a new CA with Openssl:

    ./CA.pl -newca

        * a name
        * secret passphrase for the private key
        * more information

4. I've rename the CSR with the name "newreq.pem" and then I've signed it.

    ./CA.pl -sign

5. Now, I have the new certificate signed, "newcert.pem"

6. What do I have to do for use them with Tomcat??
I think I have to install the CA certificate and the signed certificate, but how??

Thanks.

---

