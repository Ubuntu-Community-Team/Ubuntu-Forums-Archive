---
title: "Running Asp."
date: 2007-09-25
forum: Programming Talk
---

### Post by Kadrus on 2007-09-25
Alright i recently switched to Ubuntu and it's pretty awesome and all
but i can't figure out how to run ASP

Each time i type those commands in terminal:

apt-get install mono mono-gmcs mono-gac mono-utils monodevelop monodoc-browser monodevelop-nunit monodevelop-versioncontrol

apt-get install mono-xsp2 mono-xsp2-base asp.net2-examples

apt-get install mono-xsp mono-xsp-base asp.net-examples

sudo apt-get install mono-xsp2 mono-xsp2-base asp.net2-examples

sudo apt-get install mono-xsp mono-xsp-base asp.net-examples

I get the following error:
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

And that is really pissing me off

Any useful help would be really appreciated 

I hope you guys won't give me the stickies.....

---

### Post by LaRoza on 2007-09-25
Read the stickies :D

OK, really, use the sudo command before each apt-get:
```

sudo aptitude install build-essential

```

Then type your password, and no, you won't see what you are typing, just type and press enter.

Instead of saying "I hope you guys won't give me the stickies.....", say which ones you already read. There are stickies around I think that explain "running as root" and sudo.

---

### Post by Kadrus on 2007-09-25
> **LaRoza said:**
> Read the stickies :D

OK, really, use the sudo command before each apt-get:
```

sudo aptitude install build-essential

```

Then type your password, and no, you won't see what you are typing, just type and press enter.

Instead of saying "I hope you guys won't give me the stickies.....", say which ones you already read. There are stickies around I think that explain "running as root" and sudo.
I know that I don't see my password.
Thanks anyway

---

### Post by LaRoza on 2007-09-25
> **Kadrus said:**
> 
Thanks anyway

It didn't work?

---

### Post by Kadrus on 2007-09-25
> **LaRoza said:**
> It didn't work?
 I got this :@
...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 :@

---

### Post by LaRoza on 2007-09-25
> **Kadrus said:**
> I got this :@
...


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
 :@

Then run it...

---

### Post by Kadrus on 2007-09-25
> **LaRoza said:**
> Then run it...

:@:@

I am switching back to Windows tomorrow...kidding...alright it gave me something like this....bulls*i*
dpkg: requested operation requires superuser privilege

---

### Post by LaRoza on 2007-09-25
Use sudo, like before...

---

### Post by LaRoza on 2007-09-25
The Windows programmer sticky has Asp related topics.

If you are developing in Asp, I recommend using Windows. If you want alternatives, use PHP, or Python.

PHP is what I use.

Apache can be used on Windows also, my wiki has Windows software including Apache.

---

### Post by Kadrus on 2007-09-25
> **LaRoza said:**
> The Windows programmer sticky has Asp related topics.

If you are developing in Asp, I recommend using Windows. If you want alternatives, use PHP, or Python.

PHP is what I use.

Apache can be used on Windows also, my wiki has Windows software including Apache.

I prefer php from ASP......And I do know Python...started learning 2 months ago...I just recently started learning asp when i was still on windows....but anyway i am not going back on Windows...i hate...don't know why...

Anyway thanks for all your time and help..
I know I was a pain in the ***.

---

### Post by LaRoza on 2007-09-25
> **Kadrus said:**
> 
I know I was a pain in the ***.

You are a three star programmer? :D


[http://c2.com/cgi/wiki?ThreeStarProgrammer](http://c2.com/cgi/wiki?ThreeStarProgrammer)

-EDIT Thanks for visiting my wiki!

---

