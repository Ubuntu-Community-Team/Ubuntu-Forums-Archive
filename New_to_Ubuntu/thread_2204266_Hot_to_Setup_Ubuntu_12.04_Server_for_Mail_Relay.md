---
title: "Hot to Setup Ubuntu 12.04 Server for Mail Relay"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by don_diego2 on 2014-02-07
Hi everyone... I'm new to Linux. I've been tasked with using Ubuntu 12.04 to setup a Mail Relay Server. It's an internal server so security is not an issue. The plan is for our app on another server to use the Mail Relay Server to create & send email messages to our employees. So customers who want to ask questions of our employees will access APPSERVER.INTERNALDOMAIN and create an email message on MAILRELAYSERVER.INTERNALDOMAIN which will then send the email message to Recipient mailboxes in MXSERVER.EXTERNALDOMAIN. Of course EXTERNALDOMAIN is our Public Domain. The "From" address will be that of the customer so the customer should not have to authenticate on MAILRELAYSERVER.INTERNALDOMAIN.

What is the simplest way to set this up? What application should I use. I have heard of Postfix & Sendmail.

Any assistance is appreciated in advance.

---

