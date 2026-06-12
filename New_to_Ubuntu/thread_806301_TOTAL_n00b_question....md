---
title: "TOTAL n00b question..."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by rpwdh on 2008-05-24
I'm embarrassed to ask but after a trip to Shields Up, how to I get my system to refuse ping requests?

Other than that, my laptop does not exist on the internet. I'm VERY impressed! :cool:

---

### Post by rbc on 2008-05-24
I googled and got this. I have not tried it, though I may
[http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/](http://www.cyberciti.biz/faq/howto-drop-block-all-ping-packets/)

---

### Post by daimaru on 2008-05-24
on gnome install firestarter

```
sudo apt-get install firestarter
```
go to system -> administration -> firetarter
go to edit -> preferences 
select ICMP Filtering enable it and don't select any of the ping options. This also makes it impossible for you to ping a server. If you want to ping a server you have to enable "Echo request (ping)" and "Echo request (pong)".

---

### Post by hyper_ch on 2008-05-25
you don't need firestarter

it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by MaindotC on 2008-05-25
[This thread]("http://ubuntuforums.org/showthread.php?t=427527") answers your question.  Here's the excerpt that I think you need:
> 
 Re: "Shields Up!" Fails Because of Ping
Do this:


echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all


This will stop the machine from replying to all ICMP packets, not just pings!

This change will drop once the machine is rebooted however. To apply it permenantly, either make yourself a nice boot script, OR (better solution), append this line in /etc/sysctl.conf:


net.ipv4.icmp_echo_ignore_all=1


However, it looks like later in the thread they just do Firestarter and disable it that way.  Give it a try!

---

### Post by rpwdh on 2008-05-25
> **hyper_ch said:**
> you don't need firestarter

it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)


You're right, I can see where the question is too vague. 8)

Thank you to all who answered. I appreciate the help!

Edit: I tried enabling ICMP in Firestarter but to no avail. I still fail at Shields Up for Ping requests.

---

