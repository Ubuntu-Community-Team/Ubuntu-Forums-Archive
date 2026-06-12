---
title: "Noob question"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Pendragoon99 on 2008-07-25
i figured i would post this here

[http://ubuntuforums.org/showthread.php?p=5454801#post5454801](http://ubuntuforums.org/showthread.php?p=5454801#post5454801)




Quote:
Originally Posted by iaston View Post
Thanks for the response Aenima. I think you're right about full 64bit support but the main problem I had was installing from the repos. I was able to download the svn and make an install no problem but I like it when things "just work" so I had a dig around on the XBMC repos site and found this:

[http://ppa.launchpad.net/team-xbmc-s...n/binary-amd64](http://ppa.launchpad.net/team-xbmc-s...n/binary-amd64)

It looks like there is a specific XBMC distribution for AMD64 from yesterday at least... Nice

Run 'sudo gedit /etc/apt/sources.list' in a terminal window;
Add 'deb [http://ppa.launchpad.net/team-xbmc-svn/ubuntu](http://ppa.launchpad.net/team-xbmc-svn/ubuntu) hardy main' then save and close the file;
Run 'sudo apt-get update'
Run 'sudo apt-get install xbmc'

I hope this helps people that have had the same issue as me...


I was getting the "E: Couldn't find package xbmc" thing as well , did the above step and i got running. Unfortunately It keeps freezing on me and is not stable at all..........Stupid noob question , i have an Amd64 bit system but am running the 32bit hardy 8.04 , would this be the reason its running like crap?
Pendragoon99 is offline   	Reply With Quote

---

### Post by chuckyp on 2008-07-25
No you should be able to run 32bit operating systems with your cpu with out a problem.

---

### Post by Pendragoon99 on 2008-07-25
so was the above fix for 64bit hardy or ppl with 64bit processors?

---

