---
title: "12:04 Ubuntu, Software Center Opens then Closes"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by xRedex on 2012-05-23
Hallo,

 I'm currently having the same issue with my Ubuntu Software Center opening, then closing suddenly. I tried a search on google, and it led me to this post, so I hope it's ok if I post here. =)
I've tried doing this command: 
```
sudo apt-get update
```However, it started up all fine and everything up until one point. It's now stuck at 'kage lists' and has been for the past hour or so. Heres the last portion of my command prompt window right now:

```
 Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 14.6 MB in 30s (480 kB/s)                                              
xps@xps:~$ kage lists... 0% 
```Help would be very appreciated. Thanks. ^_^

---

### Post by cortman on 2012-05-23
> **xRedex said:**
> Hallo,

 I'm currently having the same issue with my Ubuntu Software Center opening, then closing suddenly. I tried a search on google, and it led me to this post, so I hope it's ok if I post here. =)
I've tried doing this command: 
```
sudo apt-get update
```However, it started up all fine and everything up until one point. It's now stuck at 'kage lists' and has been for the past hour or so. Heres the last portion of my command prompt window right now:

```
 Ign http://ca.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en_CA      
Ign http://ca.archive.ubuntu.com natty-updates/universe Translation-en         
Fetched 14.6 MB in 30s (480 kB/s)                                              
xps@xps:~$ kage lists... 0% 
```Help would be very appreciated. Thanks. ^_^

If you have a problem, it's almost always better to just start a new thread rather than append a post to an old one or to someone else's.
It looks as though it updated fine, and now you're back at the prompt. Isn't your user name xps?

---

### Post by sffvba[e0rt on 2012-05-23
*Thread moved to **Absolute Beginner Talk** in its own thread.*


404

---

### Post by xRedex on 2012-05-27
> **cortman said:**
> If you have a problem, it's almost always better to just start a new thread rather than append a post to an old one or to someone else's.
It looks as though it updated fine, and now you're back at the prompt. Isn't your user name xps?

Ah, so kage lists wasn't supposed to do anything? It didn't get past 0% at all ( pressing enter gave me blank spaces without my username infront like it was still running...so I don't think it did finish :\) . Yes, my username is XPS ^^. Sorry to bring back an old topic, just thought it'd be easier because it was directly related. So, what I did next was I closed the command prompt because it wasn't getting past 0%...Checked to see if the software manager was opening now (still was the same, not opening)then I shut down Ubuntu. I booted it up again, and this time the software manager opened. However, as soon as it opened, Ubuntu ( on virtual box ) went to not responding, and then I had to click the option 'close program'. I got the press F to check for error message on boot...and then booted normally. This time, the software manager opened, and stayed open. This time though, when I went to search for software, it wouldn't find anything, and the mouse icon kept spinning...I also got an error from the update manager...As well, nothing would open. Well, things opened, but everything was a white screen. I then sent the shut down signal from virtualbox to Ubuntu, and it didn't do anything...So then I just shut it off. I booted it up again, and this time it only got to the login screen before it went to 'not responding' and it had to be closed. Now, everytime I open Ubuntu, it only goes to not responding, and closes regardless..So virtualbox just says it was 'aborted.' This was from a fresh install Ubuntu on virtualbox as well, so I'm not sure what it was..But, I switched to another distro that I had used in the past that's based off Ubuntu (JuLinux), so I guess everything is fine now. ^_^ Although if I boot Ubuntu now, I still get the same error. ^-^;;

Edit: Oh, and I don't think I put an & at the end of the command either, since I just copied and pasted the command from the original post to fix it. ^^

---

