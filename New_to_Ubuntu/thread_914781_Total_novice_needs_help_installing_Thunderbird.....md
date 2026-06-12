---
title: "Total novice needs help installing Thunderbird....."
date: 2008-09-09
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-09
I have always wanted to try Ubuntu, but being a novice, I was too afraid to try the partition. Last night I found a program that did the whole thing for me, right down to getting me connected to the internet. So far, everything seems to be working fine. Not sure if I'm allowed to post the program here, so I'll leave it for now. 

I'm using Ubuntu now,to access the forums, the version I'm using is Ubuntu 8.04 - the Hardy Heron - released in April 2008. 

Firefox was already installed, which I was pleased about. So is a e-mailclient, which I have managed to get working.

What I wanted was to install Thunderbird, as I use it for the Newsgroups.

Can somebody help me please?

As mentioned, I am a pc novice, and a total novice for Ubuntu, and am using the ubuntu interface to get my way around.

I need step by step instructions if that is possible.

I really appreciate the help.

John Matthews.

---

### Post by lswest on 2008-09-09
you've got a couple of possiblities.  You can open a terminal (applications-->accessories-->terminal) then type ```
sudo apt-get install thunderbird
``` and enter your password (the cursor will not move or display any characters, just type your password and hit enter).  Or you can go to Add/Remove programs (found under Accessories) and to search for thunderbird.  And lastly, you can go to System-->administration-->Synaptic package manager and search for thunderbird, then click the checkbox next to the entry and choose "install".

I believe that it's in the default enabled repos, but anyone who knows better, feel free to correct me :P

---

### Post by Elfy on 2008-09-09
There are a few ways to install thunderbird - easiest is the command line (terminal, Accessories - it will nedd your normal password, which will not be visible) Add/Remove in one of the menus and synaptic in System >Admin - both Add/Remove and synaptic are front ends for apt-get (which will become useful to you :)

Run this command from the terminal

```
sudo apt-get install thunderbird
```

There's nothing to stop you using tbird for e-mail - I do.

---

### Post by Idefix82 on 2008-09-09
You may also want to have a look in this forum for alternative software:
[http://ubuntuforums.org/showthread.php?t=351118]("http://ubuntuforums.org/showthread.php?t=351118")

P.S. In fact I think that evolution, the standard email client has support for reading newsgroups. So you don't need to install any extra software.

---

### Post by sloggerkhan on 2008-09-09
If you used wubi that's not abnormal... if it was something else, there's no harm in mentioning it. Just hope you didn't get some sort of weird insecure script or something.

---

### Post by jakewc2 on 2008-09-09
Hi everybody, thank yoiu so much for all your replies, I really apprecioate it. I used the Add/Remove way of doing things, and it worked a treat, plus I found a load of other things that were usefull as well. I just installed TB, and am going to set it up now.

Thank you again.

John

---

### Post by jakewc2 on 2008-09-09
Hi, I did use wubi, and during the installation, everything went really went well, and I didnt get any insecure scripts at all. It installed then opened, and so far, cross my fingers, I havent had any odd scripts at all. :)

---

### Post by lswest on 2008-09-09
Glad we could help, and if you would be so kind as to mark the thread as solved (using the thread tools at the top of your thread) it would help others who are looking for the same answer.  Wubi is officially supported by Canonical and Ubuntu (was it also developed by them?), so there's really no harm in mentioning it.

Enjoy Ubuntu,
Lswest

---

### Post by Elfy on 2008-09-09
> so there's really no harm in mentioning it.Indeed quite the opposite, if you do come here needing support it makes it easier as sometimes it can make a difference.

---

### Post by jakewc2 on 2008-09-09
Thank you again, I will add Solved now.

I shall probably be back quite a bit asking for help, as this is totally new, but quite exciting. :)

Thank you again. :)

---

### Post by chronographer on 2008-09-09
Welcome and congratulations on making the move! You will be using the gparted live Cd to create a new partition for your next intrepid ibex install in no time! (not to mention getting mpd working with sonata and setting up mySQL for mythtv and all that)

I hope you have fun, are productive and learn much.

---

### Post by jakewc2 on 2008-09-09
Hi chronographer, now you have me interested, I found out what ibex is, but have now idea what mpb or sonata is, though I know what mysql is, but what also is mythtv? Now you have me interested?

Thank you. :)

---

