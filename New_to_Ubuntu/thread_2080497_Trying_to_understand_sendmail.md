---
title: "Trying to understand sendmail"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by deljones on 2012-11-04
All..

I'm not totally new to computers, linux etc etc so I have a good understanding of how things work.

I used to have a qnap NAS with Piwigo, Zenphoto and a bunch of other apps. It all worked very well but I found that it was a little to slow (qnap TS212) a great little box but a little slow. (small memory, small CPU) So I had a spare laptop, installed Ubuntu, Piwigo, Zenphoto and my other apps from the NAS. The speed difference is amazing. Very happy. Love it.....

With the NAS the above apps used to send email such as registration confirmation, notification of comments etc etc. The only thing I did on the NAS setup was not much if anything. It was that long ago I cant remember what I did. When I installed the apps the email just happened....

On my new setup the apps email functions don't function. I understand I needed sendmail to work? So I installed it, the configuration wasn't much if any thing at all. On my new setup I have webmin and noticed in the sendmail module that all the emails I had sent as a test were in fact all queued up in the sendmail system but they where not getting out of the computer.

So I guess you know where I'm going with this.... How do I get them out.???

My laptop is connected to a router, all port forwarding is working. I have set up my DYNDNS address as the old NAS (conistonmedia.webhop.net) all that is working fine, apps work, FTP works, screen sharing. Inside and out side of my LAN its just this sendmail thing I'd like to get working. 

No where in the sendmail config did I see a set up for an smtp server so how does the mail get out. Ive looked around the internet and all the instructions for testing are clear enough but nothing seems to be getting out of the machine...

I do admit that whilst I understand how email works I'm at a loss with sendmail I guess the lack of GUI is a little intimidating which means getting your hands dirty with editing scripts and stuff like that which I don't mind doing and have done but always with extreme caution...

Can anyone shed any light on my problem. Once Ive sorted this out I will be a happy bunny....

Kind regards to you all

Del

---

### Post by klein de usa on 2012-11-05
i messed with send mail a couple of days and never could figure it out. finally i installed postfix and used a gmail account. with bash you can send any message you wont to any email, you can even text a cell phone, with cron you can have it send message, system logs and reminders any time you like drives my wife crazy lol

---

### Post by smtp on 2012-11-09
Sendmal itself is a MTA, thus it follow standart SMTP logic to send mails out.
I would propose to check if port 25 is open (from your LAN to the Internet).

---

### Post by Linxwiz on 2012-11-09
try telneting to your laptop ip from an external ip and see if you can connect to it.

---

