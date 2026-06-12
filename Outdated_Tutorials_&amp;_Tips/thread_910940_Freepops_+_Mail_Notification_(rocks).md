---
title: "Freepops + Mail Notification (rocks)"
date: 2008-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by npnutn7 on 2008-09-05
First, i wanna thank you for this place, it was a reason to choose Ubuntu. I am an expert windows user since the first version 3.1 and newbie when it comes to linux. This is my first week ever using linux "Ubuntu" and i LOVE IT already:). i don`t find it that hard to learn, it reminds me of the old DOS commands. it`s gonna be my default OS after i find out some alternatives to my favorite windows apps.

tried to get an alternative to yahoo messenger mail notification pop up but nothings works as i need ,even pidgin gets the mail and hide it:confused:. so here`s what i did.


very simple
1) install "freepops" using synaptic manager.
2) open session and add "freepopsd" as a startup program
3) install "Mail Notification" from synaptic manager
4) open Mail Notification and add your emails and config as follow
    mailbox type: POP3
    server: 127.0.0.1
    username: your complete email address
    password: *********   "replace with your stars"
   on the connection tab, change port to "2000"
5) ALT+F2  and run "freepopsd"
6) that`s it , enjoy mail notification from all your emails.

---

