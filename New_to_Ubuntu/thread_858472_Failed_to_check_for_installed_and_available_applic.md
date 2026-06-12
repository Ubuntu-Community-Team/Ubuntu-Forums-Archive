---
title: "Failed to check for installed and available applications"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by faim2600 on 2008-07-13
First of all, I do not have internet working on my laptop right now, which is using Ubuntu, but I'm currently on a windows xp desktop.  Point is, I cant copy and paste.

I'm running gutsy (I believe thats relevant)

I get this message in Add/Remove applications.

This is a major failure of your software management system ... 'sudo apt-get install -f'.

I checked for broken packages in synaptic, as instructed, I fixed them.  

When I tried -get update, it said "Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-...Could](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-...Could) not resolve 'us.archive.ubuntu.com' Reading package lists... Done
E: Some index files failed to download, the have been ignored, or old ones used instead.


When i tried -get install -f', it just says to install sun-java6-bin sun-java6-jre.... when i say to continue it says the package cannot be authenticated, E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


All help is appreciated.  Thanks in advance :)

---

### Post by annda on 2008-07-13
it looks like you are trying to install software from the internet repositories without net access. you need a working connection first.

---

### Post by faim2600 on 2008-07-13
oh wowwwwwwww i feel incredibly stupid...

thank you so much...

i'll see what happens

---

### Post by OttifantSir on 2008-07-13
I cannot tell whether you were being sarcastic or not in your last post, but no network connection usually mean you have altered SOME, but not all, of the settings for network

Run this command in the terminal: 'ifconfig' and post the output here

How are you connecting to the net? Dial-up, DSL, satelite, cable, LAN, wireless, etc...
Do you have a router? Is it configured properly? Which is it?
Do these commands in a terminal:
'gedit /etc/hosts'
'gedit /etc/hosts.deny'
'gedit /etc/hosts.allow'
'gedit /etc/network/interfaces'
and post the contents here (if you feel comfortable sharing that info)

---

