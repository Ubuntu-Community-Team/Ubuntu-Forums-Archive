---
title: "Error in sending Email from Google Apps"
date: 2015-05-15
forum: Programming Talk
---

### Post by Zara_Melikov on 2015-05-15
Hello, I want to send EMail from my Website hosted at [Hostforlife.eu]("http://hostforlife.eu"), and we are using Google Apps for Emails. Here is my code in ASP.Net/ C#
    ```
MailMessage mMailMessage = new MailMessage();
    mMailMessage.From = new MailAddress("utility@mydomain.com", "GotFeedback", System.Text.Encoding.UTF8);
    mMailMessage.To.Add(new MailAddress("feedback@mydomain.com"));
    mMailMessage.Subject = "subject";
    mMailMessage.SubjectEncoding = System.Text.Encoding.UTF8;
    mMailMessage.Body = body;
    mMailMessage.BodyEncoding = System.Text.Encoding.UTF8;
    mMailMessage.IsBodyHtml = true;
    mMailMessage.Priority = MailPriority.Normal;

    SmtpClient mSmtpClient = new SmtpClient();
    mSmtpClient.UseDefaultCredentials = false;
    mSmtpClient.Credentials = new System.Net.NetworkCredential("utility@mydomain.com", "mypassword");
    mSmtpClient.Host = "SMTP.GOOGLE.COM";
    mSmtpClient.Port = 587;
    mSmtpClient.EnableSsl = true;
    try
    {
        mSmtpClient.Send(mMailMessage);
    }
    catch(Exception e)
    {
        string edsf = e.ToString();

```
But I am getting Exception that it is unable to connect to remote server :( Please help. Thanks!

---

### Post by spjackson on 2015-05-15
> 
    mSmtpClient.Host = "SMTP.GOOGLE.COM";


Are you sure about that? Isn't it smtp.**gmail.**com? That's what I use.

---

