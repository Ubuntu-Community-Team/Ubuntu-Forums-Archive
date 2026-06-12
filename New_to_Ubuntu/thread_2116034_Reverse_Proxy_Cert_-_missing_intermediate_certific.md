---
title: "Reverse Proxy Cert - missing intermediate certificate"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by SIlvio24 on 2013-02-14
I need some help.  I’m trying to setup an ubuntu reverse proxy for exchange webmail OMA using a Network Solution generated certificate.   Now considering I don’t know what I’m doing I started out trying to configure mail2 pointing  at a backup network address.  Now, I’m just trying to get Mail2.VVVDOMAINVVV.com working.   I point this out because this approach may have caused some confusion (between mail and mail2) getting back to the exchange server.   Note: How Virtual Host is set in the httpd.conf file..   When set to mail2.VVVDOMAINVVV.com if does not work (400 errors in the browser).   
   
  In any case, this is the error I trying to get past: “missing intermediate certificate”.
   
   
  The proxy works (I do see lots of 70007 timeout messages in the log). I can open webmail and phone syncing is working.
   
  From Microsoft Remote Connectivity Analyzer:
  [COLOR=black][FONT=Tahoma]There's a missing intermediate certificate in the certificate chain. Subject = CN=Network Solutions DV Server CA, O=Network Solutions L.L.C., C=US. For more information, see Knowledge Base Article 927465.[/FONT][/COLOR]
  
  Openssl verify
  openssl verify MAIL2.VVVDOMAINVVV.COM.crt 
  MAIL2.VVVDOMAINVVV.COM.crt: OU = Domain Control Validated, OU = nsProtect Secure Xpress, CN = mail2.VVVDOMAINVVV.com
  error 20 at 0 depth lookup:unable to get local issuer certificate
   
  From the apache2 error log after 
  Thu Feb 14 15:02:30 2013] [warn] RSA server certificate CommonName (CN) `mail2.VVVDOMAINVVV.com' does NOT match server name!?
  [Thu Feb 14 15:02:30 2013] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
  [Thu Feb 14 15:02:30 2013] [notice] Apache/2.2.22 (Ubuntu) proxy_html/3.0.1 mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
  cgs@mail2:/etc/apache2$
   
   
  Cert Directory:
  -rw-r--r-- 1 root root 1520 Feb  7 12:07 AddTrustExternalCARoot.crt
  -rw-r--r-- 1 root root 3464 Feb 14 10:33 Apache2_Plesk_Install.txt
  -rw-r--r-- 1 root root 1731 Feb 14 09:35 Apache2_Plesk_Install.txt~
  -rw-r--r-- 1 root root 4985 Feb 14 10:09 chain.txt
  -rw-r--r-- 1 root root 3253 Feb 14 10:07 chain.txt~
  -rw-r--r-- 1 root root 4204 Feb  7 12:13 VVVDOMAINVVV.com.zip
  -rw-r--r-- 1 root root 1886 Feb  7 12:07 MAIL2.VVVDOMAINVVV.COM.crt
  -rw-r--r-- 1 root root 1155 Feb  6 16:23 mail2.VVVDOMAINVVV.com.csr
  -rw-r--r-- 1 root root 1704 Feb  6 16:23 mail2.VVVDOMAINVVV.com.key
  -rw-r--r-- 1 root root 1731 Feb 14 09:53 NetworkSolutionsDVServerCA.crt
   
   
   
   
  Httpd.conf
  #LoadModule  proxy_http_module    /usr/lib/apache2/modules/mod_proxy_http.so
  #LoadModule proxy_connect_module /usr/lib/apache2/modules/mod_proxy_connect.so
   
  LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
  LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
  LoadModule ssl_module /usr/lib/apache2/modules/mod_ssl.so
  LoadModule proxy_connect_module /usr/lib/apache2/modules/mod_proxy_connect.so
  LoadModule headers_module /usr/lib/apache2/modules/mod_headers.so
  LoadModule cache_module /usr/lib/apache2/modules/mod_cache.so
  LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
  #listen 443
   
  Servername mail2.VVVDOMAINVVV.com
  ServerAdmin [EMAIL="administrator@VVVDOMAINVVV.com"]administrator@VVVDOMAINVVV.com[/EMAIL]
   
  NameVirtualHost mail2.VVVDOMAINVVV.com:443
  <VirtualHost VVVDOMAINVVV.com:443>
   
  RewriteEngine On
  RequestHeader set Front-End-Https "On"
  ProxyPreserveHost On
  SSLEngine On
  SSLCertificateFile /etc/apache2/ssl1/MAIL2.VVVDOMAINVVV.COM.crt
  SSLCertificateKeyFile /etc/apache2/ssl1/mail2.VVVDOMAINVVV.com.key
  SSLCertificateChainFile /etc/apache2/ssl1/chain.txt
  #SSLCertificateChainFile /etc/apache2/ssl1/Apache2_Plesk_Install.txt
  ProxyPass /exchange [http://exchsvr/exchange](http://exchsvr/exchange)
  ProxyPassReverse /exchange [http://exchsvr/exchange](http://exchsvr/exchange)
   
  ProxyPass /exchweb [http://exchsvr/exchweb](http://exchsvr/exchweb)
  ProxyPassReverse /exchweb [http://exchsvr/exchweb](http://exchsvr/exchweb)
   
  ProxyPass /public [http://exchsvr/public](http://exchsvr/public)
  ProxyPassReverse /public [http://exchsvr/public](http://exchsvr/public)
   
  ProxyPass / [http://localhost/](http://localhost/)
  ProxyPassReverse / [http://localhost/](http://localhost/)
   
  CacheDisable *
  </VirtualHost>


Any help will be greatly appreciated.  Silvio

---

### Post by SIlvio24 on 2013-02-20
[LEFT][SIZE=1][SIZE=1]Tried again using the file provide by Networ Solutions as the Chain file... Same results[/SIZE][/SIZE][/LEFT]
 
[LEFT][SIZE=1][SIZE=1]Below is the output for the Microsoft remote access analyzer tool.[/SIZE][/SIZE][/LEFT]
 
[SIZE=1]The Exchange ActiveSync test failed.[/SIZE]

[SIZE=1]Test Steps[/SIZE][SIZE=1]Attempting to resolve the host name mail2.VVVDomainVVVVV in DNS.[/SIZE][SIZE=1]The host name resolved successfully.[/SIZE]
 
[SIZE=1]Additional Details[/SIZE][SIZE=1]IP addresses returned: 184.74.191.22[/SIZE][SIZE=1]Testing TCP port 443 on host mail2.VVVDomainVVVVV.com to ensure it's listening and open.[/SIZE][SIZE=1]The port was opened successfully.[/SIZE]
 
[SIZE=1][IMG]https://www.testexchangeconnectivity.com/Images/Error.png[/IMG][/SIZE][SIZE=1]Testing the SSL certificate to make sure it's valid.[/SIZE][SIZE=1]The SSL certificate failed one or more certificate validation checks.[/SIZE]
 
[SIZE=1]Test Steps[/SIZE][SIZE=1]ExRCA is attempting to obtain the SSL certificate from remote server mail2.VVVDomainVVVVV.com on port 443.[/SIZE][SIZE=1]ExRCA successfully obtained the remote SSL certificate.[/SIZE]
 
[SIZE=1]Additional Details[/SIZE][SIZE=1]Remote Certificate Subject: CN=mail2.VVVDomainVVVVV.com, OU=nsProtect Secure Xpress, OU=Domain Control Validated, Issuer: CN=Network Solutions DV Server CA, O=Network Solutions L.L.C., C=US.[/SIZE][SIZE=1]Validating the certificate name.[/SIZE][SIZE=1]The certificate name was validated successfully.[/SIZE]
 
[SIZE=1]Additional Details[/SIZE][SIZE=1]Host name mail2.VVVDomainVVVVV.com was found in the Certificate Subject Common name.[/SIZE]
 
[SIZE=1][IMG]https://www.testexchangeconnectivity.com/Images/Error.png[/IMG][/SIZE][SIZE=1]Validating certificate trust for Windows Mobile devices.[/SIZE][SIZE=1]Certificate trust validation failed.[/SIZE]
 
[SIZE=1]Test Steps[/SIZE][SIZE=1]ExRCA is attempting to build certificate chains for certificate CN=mail2.VVVDomainVVVVV.com, OU=nsProtect Secure Xpress, OU=Domain Control Validated.[/SIZE][SIZE=1]One or more certificate chains were constructed successfully.[/SIZE]
 
[SIZE=1]Additional Details[/SIZE][SIZE=1]A total of 1 chains were built. The highest quality chain ends in root certificate CN=AddTrust External CA Root, OU=AddTrust External TTP Network, O=AddTrust AB, C=SE.[/SIZE]
 
[SIZE=1]Analyzing the certificate chains for compatibility problems with Windows Phone devices.[/SIZE][SIZE=1]Potential compatibility problems were identified with some versions of Windows Phone.[/SIZE]
 
[SIZE=1]Additional Details[/SIZE][SIZE=1]The certificate is only trusted on Windows Mobile 6.0 and later versions. Devices running Windows Mobile 5.0 and 5.0 with the Messaging and Security Feature Pack won't be able to sync. Root = CN=AddTrust External CA Root, OU=AddTrust External TTP Network, O=AddTrust AB, C=SE.[/SIZE]
 
[SIZE=1][IMG]https://www.testexchangeconnectivity.com/Images/Error.png[/IMG][/SIZE][SIZE=1]ExRCA is analyzing intermediate certificates that were sent down by the remote server.[/SIZE][SIZE=1]One or more intermediate certificates were missing or invalid.[/SIZE][SIZE=1][IMG]https://www.testexchangeconnectivity.com/Images/Minus.gif[/IMG][/SIZE][SIZE=1]Additional Details[/SIZE][SIZE=1]There's a missing intermediate certificate in the certificate chain. Subject = CN=Network Solutions DV Server CA, O=Network Solutions L.L.C., C=US. For more information, see Knowledge Base Article 927465.[/SIZE]
 
This was done with httpd.conf as follows:
#listen 443
Servername mail2.[SIZE=1]VVVDomainVVVVV[/SIZE].com
ServerAdmin [EMAIL="administrator@continentalguestservices.com"]administrator@[SIZE=1][COLOR=#000000]VVVDomainVVVVV[/COLOR][/SIZE].com[/EMAIL]
NameVirtualHost mail2.[SIZE=1]VVVDomainVVVVV[/SIZE].com:443
<VirtualHost [SIZE=1]VVVDomainVVVVV[/SIZE].com:443>
RewriteEngine On
RequestHeader set Front-End-Https "On"
ProxyPreserveHost On
SSLEngine On
SSLCertificateFile /etc/apache2/ssl1/MAIL2.[SIZE=1]VVVDomainVVVVV[/SIZE].COM.crt
SSLCertificateChainFile /etc/apache2/ssl1/Apache2_Plesk_Install.txt
SSLCertificateKeyFile /etc/apache2/ssl1/mail2.[SIZE=1]VVVDomainVVVVV[/SIZE].com.key
#SSLCertificateChainFile /etc/apache2/ssl1/MAIL2.[SIZE=1]VVVDomainVVVVV[/SIZE].COM.crt
#
ProxyPass /exchange [http://exchsvr/exchange](http://exchsvr/exchange)
ProxyPassReverse /exchange [http://exchsvr/exchange](http://exchsvr/exchange)
ProxyPass /exchweb [http://exchsvr/exchweb](http://exchsvr/exchweb)
ProxyPassReverse /exchweb [http://exchsvr/exchweb](http://exchsvr/exchweb)
ProxyPass /public [http://exchsvr/public](http://exchsvr/public)
ProxyPassReverse /public [http://exchsvr/public](http://exchsvr/public)
ProxyPass / [http://localhost/](http://localhost/)
ProxyPassReverse / [http://localhost/](http://localhost/)
CacheDisable *
</VirtualHost>
 
 
More info:

sudo openssl s_client -connect mail2.VVVVVDomainVVVVV.com:443 -showcerts -CApath /etc/apache2/ssl1 >/home/cgs/Desktop/out.txt
depth=0 OU = Domain Control Validated, OU = nsProtect Secure Xpress, CN = mail2.VVVVVDomainVVVVV.com
verify error:num=20:unable to get local issuer certificate
verify return:1
depth=0 OU = Domain Control Validated, OU = nsProtect Secure Xpress, CN = mail2.VVVVVDomainVVVVV.com
verify error:num=27:certificate not trusted
verify return:1
depth=0 OU = Domain Control Validated, OU = nsProtect Secure Xpress, CN = mail2.VVVVVDomainVVVVV.com
verify error:num=21:unable to verify the first certificate
verify return:1
output directed to Out.txt
CONNECTED(00000003)
---
Certificate chain
 0 s:/OU=Domain Control Validated/OU=nsProtect Secure Xpress/CN=mail2.VVVVVDomainVVVVV.com
   i:/C=US/O=Network Solutions L.L.C./CN=Network Solutions DV Server CA
-----BEGIN CERTIFICATE-----
MIIFRTCCBC2gAwIBAgIRAJJGb6PCULD+5v2dmHmyO04wDQYJKoZIhvcNAQEFBQAw
WTELMAkGA1UEBhMCVVMxITAfBgNVBAoTGE5ldHdvcmsgU29sdXRpb25zIEwuTC5D
LjEnMCUGA1UEAxMeTmV0d29yayBTb2x1dGlvbnMgRFYgU2VydmVyIENBMB4XDTEx
MDYyODAwMDAwMFoXDTE1MDYyODIzNTk1OVowcjEhMB8GA1UECxMYRG9tYWluIENv
bnRyb2wgVmFsaWRhdGVkMSAwHgYDVQQLExduc1Byb3RlY3QgU2VjdXJlIFhwcmVz
czErMCkGA1UEAxMibWFpbDIuY29udGluZW50YWxndWVzdHNlcnZpY2VzLmNvbTCC
ASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAMrIFuLJNr71cLQx1AHjp8mo
XyuYC2k5Ne8HkNSoWVrICTRB1FPRgFPFjKebQP80jxiMLvV+3a6yZBnk6sVBbCum
mm5AldVn8nfCIlQ+BzCsOFxmwHPnjk6eCBRu3dFKzjAvo07Faq8cH0DS018PUMf7
WRGk1fAIPU07eQe7edeoj997ApRYe/TqRec4SKVQNsAQJ7egWZ/8lvqYKEx7BGNF
4JPApNTjLruQ1fzd9X8PYZW5xUoKDn7ORSjVvoSfq4u9fvkK5sF9Ww10LwW+tL1A
86EKSB2PY0Fz0kmjtepyvwC1J6RaLGiSK8R8yE9wgbkM3Ny/xfXUmLveOlTF/xcC
AwEAAaOCAe0wggHpMB8GA1UdIwQYMBaAFFjYJZKkVVpu2aPRo3wMqgQhcS5gMB0G
---------Two Lines Removed ------------------------------------
BG4wbDBgBgwrBgEEAYYOAQIBCQEwUDBOBggrBgEFBQcCARZCaHR0cDovL3d3dy5u
ZXR3b3Jrc29sdXRpb25zLmNvbS9sZWdhbC9TU0wtbGVnYWwtcmVwb3NpdG9yeS1j
cHMuanNwMAgGBmeBDAECATBIBgNVHR8EQTA/MD2gO6A5hjdodHRwOi8vY3JsLm5l
dHNvbHNzbC5jb20vTmV0d29ya1NvbHV0aW9uc0RWU2VydmVyQ0EuY3JsMHoGCCsG
AQUFBwEBBG4wbDBDBggrBgEFBQcwAoY3aHR0cDovL3d3dy5uZXRzb2xzc2wuY29t
L05ldHdvcmtTb2x1dGlvbnNEVlNlcnZlckNBLmNydDAlBggrBgEFBQcwAYYZaHR0
cDovL29jc3AubmV0c29sc3NsLmNvbTAtBgNVHREEJjAkgiJtYWlsMi5jb250aW5l
bnRhbGd1ZXN0c2VydmljZXMuY29tMA0GCSqGSIb3DQEBBQUAA4IBAQABJLyF/4of
UftNvfBkPLfi4raoLaqE/xXY1g1zdKHUY8kU9TvoK3goJ81I8jYc5+6/AI1VlWjU
Dztu2iLfmoMj2o2X9oEn6G1JIiQrCpHPDMoE28+1VQHr4JVONSkTZiTPJCZj/Rya
h8mBweduLRTMbQLf0dDA8im+XWJVKPUEPiY9gtp6ObZLzHKrMGLLHFMqTCG2iDTB
IWgLrsFSd87nYN5KFzSICC0X+7Mz9hU/PPR/917ceoBM3RIWpexRk0QrXm5J6DFE
pDYlPnpBK6ATTyrMTalxmTZfrdG6q4EwECeEAzIybegQLLIXuShgkUrqW0+OZ1mI
UaUWOks7g+Kq
-----END CERTIFICATE-----
---
Server certificate
subject=/OU=Domain Control Validated/OU=nsProtect Secure Xpress/CN=mail2.VVVVVDomainVVVVV.com
issuer=/C=US/O=Network Solutions L.L.C./CN=Network Solutions DV Server CA
---
No client certificate CA names sent
---
SSL handshake has read 1694 bytes and written 540 bytes
---
New, TLSv1/SSLv3, Cipher is RC4-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
SSL-Session:
    Protocol  : TLSv1.1
    Cipher    : RC4-SHA
    Session-ID: 44F941AAC9E4D87B953C136C30C77298E4F389BA73AE0AA031DB321D6426736A
    Session-ID-ctx: 
    Master-Key: 6CC1871B1ABBD43ADB57A6D5E97B492BC506625F9441DAAD354830BC8D253C002B9F098246680654D6CF75F1925E0C94
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - 5a 26 a0 0c ea e4 5a 24-ca 1f a0 a2 f7 9f 1a 01   Z&....Z$........
    0010 - b2 ab d6 04 c0 34 0a 4b-f8 e9 ab ff 42 d3 19 2f   .....4.K....B../
    0020 - 2c e3 5e ff 07 87 0a cf-63 a6 6b c0 7a 53 20 b2   ,.^.....c.k.zS .
    0030 - 5d 7e dd 79 60 ff 64 47-c4 b6 83 c5 23 18 58 2c   ]~.y`.dG....#.X,
    0040 - 46 be 34 79 d7 38 6d 24-19 a7 7c 15 4f ed 51 e6   F.4y.8m$..|.O.Q.
    0050 - 0b 46 06 1f 29 48 bc ea-78 73 3c c8 80 1f b2 c0   .F..)H..xs<.....
    0060 - 92 af c3 60 aa ed e4 d8-00 f7 c7 3d a6 da 5a f5   ...`.......=..Z.
    0070 - 66 7d fd 26 57 41 f0 ef-c6 3e bf bf f0 ea 49 5f   f}.&WA...>....I_
    0080 - b2 97 4b cb 0c b4 79 0f-0e cf 95 c6 1f af 0a e2   ..K...y.........
    0090 - 24 30 db 16 e6 31 c6 28-b3 01 68 c9 6c 65 d4 19   $0...1.(..h.le..
    00a0 - 15 d3 50 81 dd 2c e0 ea-21 38 82 2c ad 59 4a d4   ..P..,..!8.,.YJ.
    00b0 - 8a ef 26 97 ab ce 9e 31-ca a8 a2 5d b1 d4 5b a1   ..&....1...]..[.
    Start Time: 1361469132
    Timeout   : 300 (sec)
    Verify return code: 21 (unable to verify the first certificate)
---
closed
 
Ports.conf
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz
NameVirtualHost mail.VVVVVDomainVVVVV.com:80
Listen 80
Listen 443
<VirtualHost mail.VVVVVDomainVVVVV.com:80>
 ServerName mail.VVVVVDomainVVVVV.com
 DocumentRoot /var/www
 ErrorLog /var/log/apache2/error.log
 CustomLog /var/log/apache2/access.log combined
</virtualHost>
<VirtualHost mail2.VVVVVDomainVVVVV.com:443>
 ServerName mail.VVVVVDomainVVVVV.com
 DocumentRoot /var/www
 ErrorLog /var/log/apache2/error.log
 CustomLog /var/log/apache2/access.log combined
 SSLEngine On
 SSLCertificateFile /etc/apache2/ssl1/MAIL2.VVVVVDomainVVVVV.COM.crt
 SSLCertificateKeyFile /etc/apache2/ssl1/mail2.VVVVVDomainVVVVV.com.key
</VirtualHost>

default (in /etc/apache2/sites-available)
<VirtualHost mail2.VVVVVDomainVVVVV.com:80>
 ServerAdmin [EMAIL="webmaster@localhost"]webmaster@localhost[/EMAIL]
 DocumentRoot /var/www
 <Directory />
  Options FollowSymLinks
  AllowOverride None
 </Directory>
 <Directory /var/www/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride None
  Order allow,deny
  allow from all
 </Directory>
 ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
 <Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
 </Directory>
 ErrorLog ${APACHE_LOG_DIR}/error.log
 # Possible values include: debug, info, notice, warn, error, crit,
 # alert, emerg.
 LogLevel warn
 CustomLog ${APACHE_LOG_DIR}/access.log combined
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>
 
default-ssl (in /etc/apache2/sites-available)
<IfModule mod_ssl.c>
<VirtualHost mail2.VVVVVDomainVVVVV.com:443>
 ServerAdmin [EMAIL="webmaster@localhost"]webmaster@localhost[/EMAIL]
 DocumentRoot /var/www
 <Directory />
  Options FollowSymLinks
  AllowOverride None
 </Directory>
 <Directory /var/www/>
  Options Indexes FollowSymLinks MultiViews
  AllowOverride None
  Order allow,deny
  allow from all
 </Directory>
 ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
 <Directory "/usr/lib/cgi-bin">
  AllowOverride None
  Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  Order allow,deny
  Allow from all
 </Directory>
 ErrorLog ${APACHE_LOG_DIR}/error.log
 # Possible values include: debug, info, notice, warn, error, crit,
 # alert, emerg.
 LogLevel warn
 CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined
 Alias /doc/ "/usr/share/doc/"
 <Directory "/usr/share/doc/">
  Options Indexes MultiViews FollowSymLinks
  AllowOverride None
  Order deny,allow
  Deny from all
  Allow from 127.0.0.0/255.0.0.0 ::1/128
 </Directory>
 #   SSL Engine Switch:
 #   Enable/Disable SSL for this virtual host.
 SSLEngine on
 #   A self-signed (snakeoil) certificate can be created by installing
 #   the ssl-cert package. See
 #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
 #   If both key and certificate are stored in the same file, only the
 #   SSLCertificateFile directive is needed.
 SSLCertificateFile    /etc/apache2/ssl1/MAIL2.VVVVVDomainVVVVV.COM.crt
 SSLCertificateKeyFile /etc/apache2/ssl1/mail2.VVVVVDomainVVVVV.com.key
      
 #   Server Certificate Chain:
 #   Point SSLCertificateChainFile at a file containing the
 #   concatenation of PEM encoded CA certificates which form the
 #   certificate chain for the server certificate. Alternatively
 #   the referenced file can be the same as SSLCertificateFile
 #   when the CA certificates are directly appended to the server
 #   certificate for convinience.
 #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt
        SSLCertificateChainFile /etc/apache2/ssl1/Apache_Plesk_Install.txt   
 #   Certificate Authority (CA):
 #   Set the CA certificate verification path where to find CA
 #   certificates for client authentication or alternatively one
 #   huge file containing all of them (file must be PEM encoded)
 #   Note: Inside SSLCACertificatePath you need hash symlinks
 #         to point to the certificate files. Use the provided
 #         Makefile to update the hash symlinks after changes.
 #SSLCACertificatePath /etc/ssl/certs/
 #SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt
 #   Certificate Revocation Lists (CRL):
 #   Set the CA revocation path where to find CA CRLs for client
 #   authentication or alternatively one huge file containing all
 #   of them (file must be PEM encoded)
 #   Note: Inside SSLCARevocationPath you need hash symlinks
 #         to point to the certificate files. Use the provided
0 #         Makefile to update the hash symlinks after changes.
 #SSLCARevocationPath /etc/apache2/ssl.crl/
 #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl
 #   Client Authentication (Type):
 #   Client certificate verification type and depth.  Types are
 #   none, optional, require and optional_no_ca.  Depth is a
 #   number which specifies how deeply to verify the certificate
 #   issuer chain before deciding the certificate is not valid.
 #SSLVerifyClient require
 #SSLVerifyDepth  10
 #   Access Control:
 #   With SSLRequire you can do per-directory access control based
 #   on arbitrary complex boolean expressions containing server
 #   variable checks and other lookup directives.  The syntax is a
 #   mixture between C and Perl.  See the mod_ssl documentation
 #   for more details.
 #<Location />
 #SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
 #            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
 #            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
 #            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
 #            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
 #           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
 #</Location>
 #   SSL Engine Options:
 #   Set various options for the SSL engine.
 #   o FakeBasicAuth:
 #     Translate the client X.509 into a Basic Authorisation.  This means that
 #     the standard Auth/DBMAuth methods can be used for access control.  The
 #     user name is the `one line' version of the client's X.509 certificate.
 #     Note that no password is obtained from the user. Every entry in the user
 #     file needs this password: `xxj31ZMTZzkVA'.
 #   o ExportCertData:
 #     This exports two additional environment variables: SSL_CLIENT_CERT and
 #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
 #     server (always existing) and the client (only existing when client
 #     authentication is used). This can be used to import the certificates
 #     into CGI scripts.
 #   o StdEnvVars:
 #     This exports the standard SSL/TLS related `SSL_*' environment variables.
 #     Per default this exportation is switched off for performance reasons,
 #     because the extraction step is an expensive operation and is usually
 #     useless for serving static content. So one usually enables the
 #     exportation for CGI and SSI requests only.
 #   o StrictRequire:
 #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
 #     under a "Satisfy any" situation, i.e. when it applies access is denied
 #     and no other module can change it.
 #   o OptRenegotiate:
 #     This enables optimized SSL connection renegotiation handling when SSL
 #     directives are used in per-directory context.
 #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
 <FilesMatch "\.(cgi|shtml|phtml|php)$">
  #SSLOptions +StdEnvVars
 </FilesMatch>
 <Directory /usr/lib/cgi-bin>
  #SSLOptions +StdEnvVars
 </Directory>
 #   SSL Protocol Adjustments:
 #   The safe and default but still SSL/TLS standard compliant shutdown
 #   approach is that mod_ssl sends the close notify alert but doesn't wait for
 #   the close notify alert from client. When you need a different shutdown
 #   approach you can use one of the following variables:
 #   o ssl-unclean-shutdown:
 #     This forces an unclean shutdown when the connection is closed, i.e. no
 #     SSL close notify alert is send or allowed to received.  This violates
 #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
 #     this when you receive I/O errors because of the standard approach where
 #     mod_ssl sends the close notify alert.
 #   o ssl-accurate-shutdown:
 #     This forces an accurate shutdown when the connection is closed, i.e. a
 #     SSL close notify alert is send and mod_ssl waits for the close notify
 #     alert of the client. This is 100% SSL/TLS standard compliant, but in
 #     practice often causes hanging connections with brain-dead browsers. Use
 #     this only for browsers where you know that their SSL implementation
 #     works correctly.
 #   Notice: Most problems of broken clients are also related to the HTTP
 #   keep-alive facility, so you usually additionally want to disable
 #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
 #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
 #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
 #   "force-response-1.0" for this.
 #BrowserMatch "MSIE [2-6]" \
  #nokeepalive ssl-unclean-shutdown \
  #downgrade-1.0 force-response-1.0
 # MSIE 7 and newer should be able to use keepalive
 #BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown
</VirtualHost>
</IfModule>

---

