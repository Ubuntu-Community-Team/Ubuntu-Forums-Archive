---
title: "Openssl self signed certificates gets the “valid from date” with timezone UTC offset"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by buddingspacer on 2013-04-02
I created a self signed certificate with openssl command

 openssl req -x509 -days 365 -in xxx.csr -key xxx.key -out xxx.crt 
 - with the option to be valid for 365 days. The time of execution of this command at say 10:04 am (Timezone is GMT+5.30) 
Now when i use this certificate as the webserver SSL certificate, But I get the error as 'The security certificate presented by this website has expired or is not yet valid."
In the certificate details,  it says the certificate "valid from date" is 3:34 pm . It seems to add the timezone UTC interval is getting added to the current time.
Any clues?

---

### Post by KnownSyntax on 2013-04-02
Have you made sure that your system clock is in sync with time servers by chance? That might be your problem, or that your system is somehow using the wrong time due to it not updating.

---

