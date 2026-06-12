---
title: "hotmail transfer to evolution"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by c-man01 on 2008-08-05
How do you transfer your hotmail account into the evolution mail client?

---

### Post by st33med on 2008-08-05
It is not exactly a "transfer" of accounts. You still use your hotmail account, but, the email client makes it easier to access and manipulate email. Just start the up Evolution email client and follow the setup for your email.

---

### Post by jmghist on 2008-08-06
Hi,

Had the same problem.  This is a copy of a response that I got which worked perfectly for me.  Couldn't remember where I found it so I just copied it here.

Good luck.
Now if I can get my Novell email working with Evolution I will be happy.



First, make sure your system is up to date. Open up a terminal and type:

Code:
sudo apt-get update
 Now, install the inet daemon

Code:
sudo apt-get install inetutils-inetd
 This takes care of all of our dependencies. Now on to the good stuff...

Code:
sudo apt-get install hotway hotsmtp
 This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:
sudo gedit /etc/inetd.conf
 Look for a line like this:

Code:
pop3streamtcpnowaitnobody/usr/sbin/tcpd /usr/bin/hotwayd
 By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:
pop3streamtcpnowaitnobody/usr/sbin/tcpd /usr/bin/hotwayd -r
 And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:
2500streamtcpnowaitnobody/usr/sbin/tcpd /usr/bin/hotsmtpd
 This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:
sudo /etc/init.d/inetutils-inetd restart
 If everything is working properly, you'll see this pop up on your screen:

Code:
* Restarting internet superserver inetd                            [ ok ]
 Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)


John

---

### Post by Living2007 on 2008-08-12
If you have a Hotmail Free account, you will be unable to accses your e-mails on my desktop because Microsoft has block port accses to free users. Even if you want to upload your mail to a new service, it will still be blocked.

If you are a Plus user; search in Windows Live help for support to accses your mail.

I would recommened to use Gmail

---

