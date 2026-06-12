---
title: "Crossover Installation Issues"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by dow mathis on 2008-10-29
Hello.

I'm running eeebuntu on an Asus eee pc 1000H.  Everything seems to be working fine, except that I am unable to install crossover.  Below is what I get when I try the install:

> root@dow-laptop:/usr/local/src# su
root@dow-laptop:/usr/local/src# sh install-crossover-pro-7.1.0.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
.............................................................
...................................................

The DISPLAY variable is not set.  You should either login as root or use
the command "su" with no flags, to make sure setup has an X display to use.

The setup program seems to have failed on x86/glibc-2.7
Check the system requirements at:
[http://www.codeweavers.com/products/cxoffice/requirements/](http://www.codeweavers.com/products/cxoffice/requirements/)
root@dow-laptop:/usr/local/src# 


Apparently, I need to upgrade glibc, but I don't know where to look to verify what version I have, or what process to go through to get it updated.  I looked in Add/Remove, and did a search for glibc, but was told that, "There is no matching application available."

Also, since it tells me that the DISPLAY variable isn't set, then I need to figure out what to do about that.

Thoughts?  Suggestions?

Thanks.

---

### Post by dracayr on 2008-10-29
> You should either login as root or use
the command "su" with no flags, to make sure setup has an X display to use.

well, execute the script with sudo

could you please edit your post so that it isn't thrice as wide as the normal page

dracayr

---

### Post by dow mathis on 2008-10-29
> **dracayr said:**
> well, execute the script with sudo

I did that to start with, then I read something that suggested that I install it as root, so I did that with su privileges.  The result is the quoted portion.

> could you please edit your post so that it isn't thrice as wide as the normal page

Done.  it wrapped on my screen, so I assumed that it did for everyone else.  Sorry.

---

### Post by dracayr on 2008-10-29
try this:

```
DISPLAY=:0.0 export DISPLAY
```

if it works, put the command in your .profile file

dracayr

---

### Post by dow mathis on 2008-10-29
> **dracayr said:**
> try this:

```
DISPLAY=:0.0 export DISPLAY
```

if it works, put the command in your .profile file


Okay, I tried that, and this is the result:

> root@dow-laptop:/usr/local/src# DISPLAY=:0.0 export DISPLAY
root@dow-laptop:/usr/local/src# sh install-crossover-pro-7.1.0.sh
Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional

*.......... A Big Gob of Dots..........*

No protocol specified

Setup requires an X display to run.  There is a display variable set, however
you have no permissions to access the X server (:0.0) it points to.
Try running xhost +localhost before su'ing to root.

The setup program seems to have failed on x86/glibc-2.7
Check the system requirements at:
[http://www.codeweavers.com/products/cxoffice/requirements/](http://www.codeweavers.com/products/cxoffice/requirements/)
root@dow-laptop:/usr/local/src#


I then tried entering the "xhost +localhost" command, and got this:
> root@dow-laptop:/usr/local/src#  xhost +localhost 
No protocol specified
xhost:  unable to open display ":0.0"
root@dow-laptop:/usr/local/src# 


Also, by .profie, are you referring to "normal.profile"?

---

### Post by Nepherte on 2008-10-29
Try:
```
sudo -i
sh install-crossover-pro-7.1.0.sh
exit
```

---

### Post by dow mathis on 2008-10-29
> **Nepherte said:**
> Try:
```
sudo -i
sh install-crossover-pro-7.1.0.sh
exit
```

Sorry, that gives the same results: 
> Verifying archive integrity...OK
Uncompressing CrossOver Linux Professional

.......... A Big Gob of Dots..........

No protocol specified

Setup requires an X display to run. There is a display variable set, however
you have no permissions to access the X server (:0.0) it points to.
Try running xhost +localhost before su'ing to root.

The setup program seems to have failed on x86/glibc-2.7
Check the system requirements at:
[http://www.codeweavers.com/products/.../requirements/](http://www.codeweavers.com/products/.../requirements/)

Any other ideas?

---

### Post by gandaran on 2008-10-29
are you trying to install in /usr/local?
I just installed crossover and you have two options, if you run the installer as root it installs to /opt, which I didn't want so I just run the installer as user and I have it installed in my home folder which is quite nice, if I get tired of it I just delete everything related to crossover there.

---

### Post by dow mathis on 2008-10-29
Well, there's nothing like trying something new to make you feel like an idiot, lol.

I went back to the original downloaded file, which is on my desktop...  Right click - Properties - Permissions - Check "Allow executing file as program" - Close.

Double-click on the file, and select "Run in Terminal" in the menu that pops up.  Then the install went fine.

I'm going off now to bang my head against the wall for a while.  It hurts less, lol.

Thanks to everybody who offered help today.  I think that I was just making it too difficult.

---

### Post by drakeman007 on 2008-11-01
> **dow mathis said:**
> Well, there's nothing like trying something new to make you feel like an idiot, lol.

I went back to the original downloaded file, which is on my desktop...  Right click - Properties - Permissions - Check "Allow executing file as program" - Close.

Double-click on the file, and select "Run in Terminal" in the menu that pops up.  Then the install went fine.

I'm going off now to bang my head against the wall for a while.  It hurts less, lol.

Thanks to everybody who offered help today.  I think that I was just making it too difficult.

Thanks because this works for me too!
great!

---

### Post by dow mathis on 2008-11-01
Great!  Glad it worked.

---

