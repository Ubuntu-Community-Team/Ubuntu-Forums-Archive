---
title: "Connecting exchange server thunderbird mail client"
date: 2018-08-26
forum: New to Ubuntu
---

### Post by its_bigB on 2018-08-26
With Thunderbird I installed ExQuilla and tried to connect exchange email account. But it failed all the time, even the manual configurations. Is there any easiest email client of connecting to my mail server?

---

### Post by SeijiSensei on 2018-08-26
Add support for the standard SMTP and IMAP protocols on your Exchange server.

[https://docs.microsoft.com/en-us/exchange/clients/pop3-and-imap4/](https://docs.microsoft.com/en-us/exchange/clients/pop3-and-imap4/)

Then you can connect to it directly just like any other RFC-compliant mail server.

Microsoft still thinks it rules the roost:

> To support clients that still rely on these protocols

"Still?"  They make it sound like the Internet standard protocols are somehow out-of-date and should be deprecated.

---

### Post by its_bigB on 2018-08-26
> **SeijiSensei said:**
> Add support for the standard SMTP and IMAP protocols on your Exchange server.

[https://docs.microsoft.com/en-us/exchange/clients/pop3-and-imap4/](https://docs.microsoft.com/en-us/exchange/clients/pop3-and-imap4/)

Then you can connect to it directly just like any other RFC-compliant mail server.

Microsoft still thinks it rules the roost:



"Still?"  They make it sound like the Internet standard protocols are somehow out-of-date and should be deprecated.

Unfortunately I can't access the configurations, but as I know those are already enabled.

---

