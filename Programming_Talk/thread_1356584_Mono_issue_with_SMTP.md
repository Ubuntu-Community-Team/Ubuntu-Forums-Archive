---
title: "Mono issue with SMTP"
date: 2009-12-16
forum: Programming Talk
---

### Post by mihnea.radulescu on 2009-12-16
Hello everybody!

I developed an application for .NET 2.0 that programatically sends e-mails to targets, using the SMTP protocol. I successfully tested the application on Windows, using my google account smtp configuration, that is SSL enabled, smtp host: smtp.google.com and smtp port: 587.

On Mono is Ubuntu 9.10, it throws an exception pertaining to the SSL (SSL authentication failure and the like). The method code is here:

```
private void SendEmail(string toAddress)
        {
            try
            {
                MailAddress mailAddressFrom = new MailAddress(fromAddress, fromName);
                MailAddress mailAddressTo = new MailAddress(toAddress);

                MailMessage emailMessage = new MailMessage(mailAddressFrom, mailAddressTo);
                emailMessage.BodyEncoding = Encoding.UTF8;
                emailMessage.IsBodyHtml = false;
                emailMessage.Subject = subject;
                emailMessage.Body = content;

                NetworkCredential emailCredential = new NetworkCredential(fromAddress, password);
                SmtpClient mailClient = new SmtpClient(smtpHost, smtpPort);
                mailClient.EnableSsl = enableSSL;
                mailClient.UseDefaultCredentials = false;
                mailClient.Credentials = emailCredential;

                mailClient.Send(emailMessage);

                Console.Out.WriteLine("E-mail to " + toAddress + " successfully sent.");
            }

            catch (Exception)
            {
                Console.Error.WriteLine("Failure sending e-mail to " + toAddress + "!");
            }
        }

```

I want to ask you if this issue is Mono libraries related, or it happens because of the default firewall settings in Ubuntu 9.10.

All the very best,
Mihnea

---

### Post by Zugzwang on 2009-12-16
Can you copy&paste the exception message? Without knowing it, we can only guess.

---

### Post by mihnea.radulescu on 2009-12-18
Sorry for the delay, here is the extended exception message:

```
MESSAGE: Message could not be sent.

SOURCE: System

INNER EXCEPTION: System.IO.IOException: The authentication or decryption has failed. ---> System.InvalidOperationException: SSL authentication error: RemoteCertificateChainErrors
  at System.Net.Mail.SmtpClient.<SmtpClient>m__3 (System.Object sender, System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Security.Cryptography.X509Certificates.X509Chain chain, SslPolicyErrors sslPolicyErrors) [0x00000] 
  at System.Net.Security.SslStream+<BeginAuthenticateAsClient>c__AnonStorey9.<>m__9 (System.Security.Cryptography.X509Certificates.X509Certificate cert, System.Int32[] certErrors) [0x00000] 
  at Mono.Security.Protocol.Tls.SslClientStream.OnRemoteCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] errors) [0x00000] 
  at Mono.Security.Protocol.Tls.SslStreamBase.RaiseRemoteCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] errors) [0x00000] 
  at Mono.Security.Protocol.Tls.SslClientStream.RaiseServerCertificateValidation (System.Security.Cryptography.X509Certificates.X509Certificate certificate, System.Int32[] certificateErrors) [0x00000] 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] 
  at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] 
  --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000]
```

---

### Post by WitchCraft on 2009-12-18
Credentials ?

---

### Post by mihnea.radulescu on 2009-12-18
The credentials are correct! The application works on Windows.

---

### Post by WitchCraft on 2009-12-19
> **mihnea.radulescu said:**
> The credentials are correct! The application works on Windows.

Yes, but NetworkCredential might not return the same values on Linux than on Windows...

---

### Post by cszikszoy on 2009-12-19
You can also ask people in the official mono irc channel, #mono on irc.gimp.org

---

