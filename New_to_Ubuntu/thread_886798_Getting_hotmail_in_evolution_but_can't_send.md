---
title: "Getting hotmail in evolution but can't send"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-11
I was trying to get evolution to pick up my hotmail. I configured it and it did import all my hotmail to my inbox in evolution. The problem is when I try to send emails I get this error after putting my hotmail password in Error while performing operation connection refused. I configured it this way
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

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500		stream	tcp	nowait	nobody	/usr/sbin/tcpd /usr/bin/hotsmtpd

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

Can anyone tell me if they know how to fix this problem.

---

### Post by Living2007 on 2008-08-11
Are you a hotmail free, plus, or premium user. What type of user you are, it will depend if you can use desktop e-mail clients.

I'll tell you one thing; Hotmail Free users cannot accses their e-mail on desktop clients

After a mounth of trying, I found i couldn't accses it at all. I'm now on Gmail now

---

### Post by ibgeorgeb on 2008-08-11
I spent a lot of time (too much time) researching how to get my Hotmail on evolution and I just ended up having Hotmail forward my emails to my gmail account. Evolution reads and writes to gmail -- no problemo. gB-)

---

### Post by tuxxy on 2008-08-11
Setup guide for hotmail in evolution

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

---

### Post by brucegriffin on 2008-08-11
I may end up going to gmail. I am a free msn mail user, but evolution does import my email I am geting, I just can't send email. Thought I might just have my send settings wrong. This is the way I set it up. Hope someone might see something wrong in the send settings. Thanks for your replies.

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

Tuxxy, The how to you suggest is what I used to set it up. Thanks alot for replies.

---

### Post by tuxxy on 2008-08-11
My friend receives his standard hotmail account mail through thunderbird, although I personally use the web service and dont even have a desktop mail client installed :)

---

### Post by Living2007 on 2008-08-12
> **brucegriffin said:**
> I may end up going to gmail. I am a free msn mail user, but evolution does import my email I am geting, I just can't send email. Thought I might just have my send settings wrong. This is the way I set it up. Hope someone might see something wrong in the send settings. Thanks for your replies.

Receive Server type: POP
Server: 127.0.0.1
Username: [EMAIL="xxx@hotmail.com"]xxx@hotmail.com[/EMAIL] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [EMAIL="xxx@hotmail.com"]xxx@hotmail.com[/EMAIL] (same as above)
(Optional Remember password checkbox)

Tuxxy, The how to you suggest is what I used to set it up. Thanks alot for replies.
I changed to Gmail for the exact same reason. You have more flexibily with gmail. But if you want to get your contacts from Hotmail, Do the following.

In Windows Live Hotmail:

Options -> More Options -> Export Contacts. And Download contacts as .CSV file.

In Gmail

Contacts -> Import (Found on the top right hand corner) -> Click Browse -> Than click Import

---

### Post by brucegriffin on 2008-08-12
my problem is not getting my email or contacts from hotmail to evolution. I have all my email that I receive at hotmail coming into evolution that works and my contact list as well. The problem is sending it, when I create a message to send and I click send it looks like it goes but it doesn't. It just goes to the outbox and when I try to send it there it asks for my password for my hotmail account I put it in and another window comes up which says Error while performing operation could not connect to 127.0.0.1 connection refused. I may go to gmail but I am getting mail just figure I must have my sending smtp settings wrong somewhere. thanks for the reply.

---

### Post by brucegriffin on 2008-08-14
Bump

---

### Post by Shrek X on 2008-08-16
It looks like your trying to use the HOTMAIL server as an SMTP server for your send.  That obviously wont work, you need to have a true SMTP server.  If you use comcast or something like that, you may be able to use theirs.  

there is a tutorial around here someplace for Thunderbird which spells this out pretty clear, I suspect that will solve your problem.

---

### Post by Jaqoup on 2009-04-02
that seems to be solved
they have at last enabled the POP3
check this
[OUUUUUF….. At Last !!! (Hotmail & POP3)]("http://jaqoup.wordpress.com/2009/04/02/ouuuuuf-at-last-hotmail-pop3/")

---

### Post by Irvysan on 2009-07-05
> **Jaqoup said:**
> that seems to be solved
they have at last enabled the POP3
check this
[OUUUUUF….. At Last !!! (Hotmail & POP3)]("http://jaqoup.wordpress.com/2009/04/02/ouuuuuf-at-last-hotmail-pop3/")


Ty, works a treat :)

---

