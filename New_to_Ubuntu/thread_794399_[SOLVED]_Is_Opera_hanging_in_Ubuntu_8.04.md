---
title: "[SOLVED] Is Opera hanging in Ubuntu 8.04"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by a.v.l on 2008-05-14
I've been a happy Opera user for five years but since installing Ubuntu 7.10 and 8.04 I find that it hangs or works very slowly at times and  usually at the wrong time. 

I've just missed winning an Ebay auction after placing a last minute bid close to the  auction end. By the time Opera had done its thing the auction had ended and I lost the auction when my bid exceeded the winning bid. A quick check using Firefox and Ebay showed me that Firefox worked much faster than Opera does 

Anyone else notice this as a problem?  Can this be resolved somehow?

---

### Post by tjwoosta on 2008-05-14
i have heard of others here on the forums who have had the same problem with opera (it seems to be only the 32bit version)

i use opera9.50b2 on 64bit and it is by far the fastest browser available for ubuntu right now (scores highest on acid 3)

---

### Post by KenBW2 on 2008-05-14
I recently (about a week ago) switched to Opera. No problems here!
- Opera 9.5b2 32bit

---

### Post by a.v.l on 2008-05-14
> **KenBW2 said:**
> I recently (about a week ago) switched to Opera. No problems here!
- Opera 9.5b2 32bit

Its an odd thing, after downloading version 9.5b2 and trying to install it I get a message from the packet installer that I already have a later version of Opera installed. I know for a fact that the version I have is not the latest being version 9.2. How do I resolve this issue please?

---

### Post by tjwoosta on 2008-05-14
uninstall your old opera first

---

### Post by a.v.l on 2008-05-14
> **tjwoosta said:**
> uninstall your old opera first

Thanks for that, uninstalling the old version of Opera first, allowed me to install the latest version without getting the same warning. By the way, Opera automatically saved all of my emails, bookmarks and history in a folder which I was able to reinstall to the new installation later.....that was clever.

---

### Post by robalcorn on 2008-05-14
> **tjwoosta said:**
> i have heard of others here on the forums who have had the same problem with opera (it seems to be only the 32bit version)

i use opera9.50b2 on 64bit and it is by far the fastest browser available for ubuntu right now (scores highest on acid 3)

I can confirm 32bit has problems I just tried the acid3 test (kinda neat never heard of it before) and my mark with opera 9.2 was 34 and ff3 b5 scored 71

---

### Post by KenBW2 on 2008-05-14
@a.v.l.:

Go to your Home folder, go to View > Hidden Files and look in any folder starting with ".", eg ".opera". That's where all the applications' preferences are - since any folder outside your home folder isn't writable by anything but root. This works well, for example, if you want to move to a new PC. Just copy your .opera/.pidgin/.whatever to the new install and all your preferences instantly appear :) Also works for different distributions. This is why it's best to keep your home folder on its own partition so that a move to another install is absolutely painless :)

---

