---
title: "Firefox warning of untrusted connection on server certificate issued by local CA"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by dvks on 2014-05-13
I am running Ubuntu server 12.04 with desktop installed on top of the server installation. I am using Firefox to test access to the local apache2 server with HTTPS connection.
The problem is that HTTPS access from Firefox returns warning that the connection is untrusted.

1. I installed OpenSSL with proper settings for local CA
2. I created CA certificate for the local domain
3. I issued certificate/key pair for the local server by the local CA
4. I enabled the apache2 default-ssl and updated the default-ssl file 
    a. SSLEngine   on
    b. SSLCertificateFile    <path to the server's certificate  crt file>
    c. SSLCertificateKeyFile   <path to the server's   key  file>
    d. SSLCertificateChainFile   <path to the  CA  certificate file>
    e. Tried also to set   SSLCACertificatePath  <path to the CA   ca_certificates.crt >  but when I set it the apache2 fails to restart, is this indication to the problem?
5. I checked the server certificate and it is referencing the  proper local CA certificate
6. I set the local CA certificate on the Firefox

And ..... after all these settings when I try to access the apache2 server using Firefox/HTTPS I get the warning message: 
"This Connection I Untrusted  ...... 
Technical details:
192.168.1.5 uses an invalid security certificate.
The certificate is only valid for ksnas83.keyscan.com
(Error code: ssl_error_bad_cert_domain)

How do I debug such problem?
Any idea how to resolve it?
Why I can't set   SSLCACertificatePath   on   default-ssl   file

---

