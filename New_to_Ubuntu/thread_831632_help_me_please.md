---
title: "help me please"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by snake19 on 2008-06-17
help me please.i'm really a beginner.i already install kubuntu 8.04. and i can't add a program if i use add/remove program. this command always show

**There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. **

is there anyone can help me? please tell me step by step, because i'm really really a beginner. thx

---

### Post by cdtech on 2008-06-17
You might want to run on a command line:
sudo dpkg &#8211;configure -a

And do a:
sudo apt-get autoremove

To clean out your repositories.....

[B]P.S.
Then do your sudo apt-get update, reboot then try again.
Seems you might have had a ton of upgrades or installs at one time.[/B]

Hope this helps......

---

### Post by snake19 on 2008-06-17
i already do what you say. but it still the same problem:(. why this happen? any other solution?thx

---

### Post by hyper_ch on 2008-06-17
It is adviced to use a descriptive thread title that reflects the content of the post/problem/inquriy instead of useing a generic one like "noob here" or "help needed".

---

### Post by bumanie on 2008-06-17
Go to sytem --> administration --> software sources and check the first four boxes, ensure cd-rom is unchecked. The go to third-party software and check any boxes in there. Then in teminal run the command > sudo apt-get update  After that try add and remove again or synaptic package manager.

---

### Post by Pasty-Flawss on 2008-06-17
i've never used kubuntu before but i had this problem on ubuntu.. i went software > administration > software sources or something and clicked on change download server or something then i chose best for me by pinging all or something then it worked fine. sorry if this makes no sense im on a windows computer right now.

---

### Post by snake19 on 2008-06-17
> **manie said:**
> Go to sytem --> administration --> software sources and check the first four boxes, ensure cd-rom is unchecked. The go to third-party software and check any boxes in there. Then in teminal run the command  After that try add and remove again or synaptic package manager.

i do that.but the same problem is show:confused::(:(

what will i do? This OS is really disappoint me.

---

### Post by kalesh7 on 2008-06-17
alright lets take this one step at a time, 
try installing through command line.
sudo apt-get install packagename
and post any errors here.
btw, you are connected to the net when trying to install right?

---

