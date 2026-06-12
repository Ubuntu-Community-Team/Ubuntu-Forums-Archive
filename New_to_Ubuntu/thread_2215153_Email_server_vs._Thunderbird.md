---
title: "Email server vs. Thunderbird"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by tom60 on 2014-04-05
What is the difference between using an email server and Thunderbird?  I have a server set up with a new copy of Ubuntu.  I am now setting it up to sync Firefox bookmarks, etc.  It is also going to be my print/fax server as well as my backup drive and file server for my home.  I am now wondering, is there any benefit in making it an email server?  My emails are all connected to my own domain xyz@my domain.com  I have been using Tbird as my email client on my desktop - my tablet, notebook and work computer all read the emails as webmail. Some of the goals I have in doing these things is to move data and files so that they are stored within my own premises - under my own control.  Once FF sync is set up, and this question is answered, I will pursue the option (I have heard that the option exists) of using my server as a hub and firewall :)

---

### Post by Frogs Hair on 2014-04-05
When using a mail client the mail is passes through a configured maintained sever controlled by the email provider . If you set up your own mail server you will have to learn to configure it and maintain it yourself .   [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch21_:_Configuring_Linux_Mail_Servers)

---

### Post by SeijiSensei on 2014-04-05
If you don't want to go to the trouble of setting up a full-fledged mail server, which can be a pretty complicated task, you might look into using [**fetchmail**]("https://library.linode.com/email/fetchmail") with your current mail provider(s) instead.  Fetchmail will download messages from remote servers and deliver them locally on your box.

---

