---
title: "Remote desktop support for family members"
date: 2007-04-24
forum: Pennsylvania Team - US
---

### Post by zacinator on 2007-04-24
From the Hello thread
> **kejava said:**
> 
one suggestion. make sure you get sshd running and port forward to port 22 on your dad's PC. also, use dyndns.org to give yourself a pseudo-static IP. this is very handy if you want troubleshoot problems or install software remotely for them.

start a new thread if you want more detailed support on this topic. i'll be glad to help 

Is there a tutorial on this?  Or a how to... this would save me from having to drive to there house all the time!

Thanks for all your help!

p.s. this might be a good way to spread ubuntu around PA and beyond!

---

### Post by jsma on 2007-04-24
On the machine you'd like to be able to administer remotely, you'll need to install the openssh server:
```
sudo apt-get install openssh-server
```When the poster said to 'port forward to port 22', this step applies only if the machine is behind a firewall. For instance, I have a belkin wireless router with a firewall. I can use the router's web-based configuration editor (usually located at http://192.168.2.1 or similar from within the firewalled network) to tell it that port 22 should be open and to forward all external requests on port 22 to my machine on the same port. To do this, I've given my machine a static IP address and then enter this IP address in the router's management interface, so it knows which computer it should talk to (assuming there is more than one machine on the network). 

Then to make it easy to get to from the outside, go to dyndns.org and sign up for a free host name for your dynamic address (something like 'easytoremember.dyndns.org'). When you set up your account with dyndns.org, you tell it the external IP address of the router (the IP address the ISP assigns to you, not the internal 192.168.x.x number assigned to the machine). This allows you to type in your easy to remember host name to connect to the remote machine. Then to log in remotely, you'd need to install openssh-client on your machine:
```
sudo apt-get install openssh-client
```Then you should be able to just open up a terminal and do:
```
ssh -C username@easytoremember.dyndns.org

```I think it asks you a couple of straightforward questions the first time you try to connect and then give it your password and you're in. Note that the username/password combo must be a username and password of a user on the system you're trying to administer, not your local machine username. Although if it's a machine belonging to your parents, you might as well create your own user account on their machine.

Another thing you should note, you have to refresh the IP address with dyndns.org once a month or they delete your account (which isn't a big deal, just get another one). There is a utility you can install on the remote machine called 'ddclient' (available through apt) that will refresh the address automatically, although I couldn't get it to work behind a firewall. It kept telling dyndns.org my internal IP address of the machine ddclient was running on, and not the external IP address assigned to the router.

Anyway, hope this helps or at least points you in the right direction.

---

### Post by kejava on 2007-04-24
jsma,

nice work!  i was just about to reply to him when i saw your post.  basically it's everything i was about to say but i think your description is better ;-)  the only thing you may want to mention is that the remote router may already have native support for dyndns.  my old netgear rp114 fully supports dyndns but my newer us robotics does not.  ddclient works just as well.

oh yeah, here's a link to **[ddclient config]("http://ddclient.sourceforge.net/?page=0#install")** on it's homepage.

-kevin

---

### Post by jsma on 2007-04-24
Yeah, my router actually has built in support too, but for some dumb reason it truncates or otherwise limits the number of characters to 15, which chops off the last two characters of my name. I guess I should have opted for a shorter name anyway, what was I thinking?

---

### Post by zacinator on 2007-04-25
Thanks so much!  I will let you know how it goes when I do it later on this week!

---

### Post by kejava on 2007-04-25
> **jsma said:**
> Yeah, my router actually has built in support too, but for some dumb reason it truncates or otherwise limits the number of characters to 15, which chops off the last two characters of my name. I guess I should have opted for a shorter name anyway, what was I thinking? wow.  i haven't seen that yet.  good to know though as I'm sure many of them do this.  i'll keep it in mind.

---

### Post by zacinator on 2007-04-27
I just wanted to let you guys know that this worked like a charm!  Thanks for all of your advice!  

My brother was excited about Beryl and couldn't wait to show it off to his friends.  Not sure why I didn't do this earlier!

---

### Post by wilsonkins on 2007-08-06
While I can do the above to remotely administer my Mom's computer, I would like to show her how to do things. I need to see her screen on my display, move her mouse, and have her see what I am doing on her machine.  Where should I look for help?

---

### Post by lamalex on 2007-08-07
install x11vnc on her computer and then you can do just this. there are 1000s of tutorials on how to set up vnc. i think ubuntu-tutorials.com has a good one

---

