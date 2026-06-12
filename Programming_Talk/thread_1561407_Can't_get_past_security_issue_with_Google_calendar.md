---
title: "Can't get past security issue with Google calendar"
date: 2010-08-26
forum: Programming Talk
---

### Post by Newbie2910 on 2010-08-26
**Can't get past security issue with Google calendar** 			
 			 			 		   		 		 		An app of mine (in development) on Mono won't read or write to my Gmail calendar... I keep getting "Invalid certificate" errors.

I ran mozroots per the Security FAQ.  I also loaded them into the machine per these instructions:
[http://dotnetopenauth.net:8000/wiki/mono](http://dotnetopenauth.net:8000/wiki/mono)

But I think the problem is either Google actually sending a bad  certificate, or a bug in Mono making it think the certificate is  invalid.

Here's the error:

System.IO.IOException: The authentication or decryption has failed.  ---> Mono.Security.Protocol.Tls.TlsException: Invalid certificate  received from server. Error code: 0xffffffff80092012
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsSer   verCertificate.validateCertificates  (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in  <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsSer   verCertificate.ProcessAsTls1 () [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMess  age.Process () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMess  age:razz:rocess ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.Pr   ocessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg)  [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.RecordProtocol.Internal   ReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in  <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHand  shakeCallback  (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 

Help!

BTW my Mono/.Net code works fine running under Windows.

Using Ubuntu 10.04.

Thanks!

---

### Post by Newbie2910 on 2010-08-31
Anyone have any ideas on this?  I don't have much hair left to pull out.

---

### Post by Zugzwang on 2010-09-01
What about this?: [http://efreedom.com/Question/1-3285489/Mono-Problems-Cert-Mozroots](http://efreedom.com/Question/1-3285489/Mono-Problems-Cert-Mozroots)

---

### Post by Newbie2910 on 2010-09-01
Did mozroots and followed all the guidelines/things to do in the faq.  No luck.

---

