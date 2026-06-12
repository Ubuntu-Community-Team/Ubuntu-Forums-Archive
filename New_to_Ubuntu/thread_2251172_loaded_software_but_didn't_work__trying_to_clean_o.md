---
title: "loaded software but didn't work / trying to clean out"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by ccbmailroom on 2014-11-02
I've been using Ubuntu since release 9.04 with the docky app keeping my personal quick links easily accessible.  I've upgraded through the years and now am using Ubuntu 14.04 LTS and will be keeping this release for some time.  It's installed as the main OS for my HP AMD A8 laptop.

At this time in my life, I don't have the time to learn command line programming without the help of web help showing what to type to install various software.  My goal is by summer of 2014 to move to an Apple computer...I just can't afford one right now.  Ubuntu does a wonderful job of keeping things organized in a sleek OS.  I use GIMP, Google Chrome, Thunderbird, Firefox, etc.

* * * To my point.  I've tried installing other software that does not work  I've added a few lib files to get Google Earth to work (both 32 bit and 64 bit) to no avail.  For a situation like this where I am so frustrated trying to install Google Earth, all of the help things I've done so far have advised to run sudo apt get and wget stuff but I've given up.  Now, I have a Google Earth icon in the Unity section but when I click on it, it gives me the splash screen and then goes away.

How do I just get rid of all of the Google Earth stuff I've just spent two days trying to get to work?

I'm keeping this laptop as it's secure and does photo editing very well, it also has a nice secure OS.  Any help is appreciated, thank you.

Botch

---

### Post by bapoumba on 2014-11-02
How did you install Google Earth ? From the Software Center ? Just remove it from there. Would you remember which other packages you installed ?

---

### Post by ccbmailroom on 2014-11-02
> **bapoumba said:**
> How did you install Google Earth ? From the Software Center ? Just remove it from there. Would you remember which other packages you installed ?

Oh if it were only so easy.  I used terminal and ran a few commands:
sudo apt-get install libc6:i386 lsb-core
wget -O google-earth64.deb [http://drive.noobslab.com/apps/google-earth-stable_current_amd64.deb](http://drive.noobslab.com/apps/google-earth-stable_current_amd64.deb)
sudo dpkg -i google-earth64.deb

I've given up.  Now there is a Google Earth icon when I search in Unity for Google and no access to it in Software Center at all.   That's why this post.  Google Earth splash page, then disappears.  I just want it gone.

---

### Post by ccbmailroom on 2014-11-02
> **bapoumba said:**
> How did you install Google Earth ? From the Software Center ? Just remove it from there. Would you remember which other packages you installed ?

Oh if it were only so easy.  I used terminal and ran a few commands:
sudo apt-get install libc6:i386 lsb-core
wget -O google-earth64.deb [http://drive.noobslab.com/apps/google-earth-stable_current_amd64.deb](http://drive.noobslab.com/apps/google-earth-stable_current_amd64.deb)
sudo dpkg -i google-earth64.deb

I've given up.  Now there is a Google Earth icon when I search in Unity for Google and no access to it in Software Center at all.   That's why this post.  Google Earth splash page, then disappears.  I just want it gone.

Oh, I also had downloaded both the 32 bit as well as the 64 bit from the website as well.  Something is there, I just want it cleaned out.  

**I've heard through other Linux users that Fedora is a good OS that doesn't change much with each of the new releases.  There isn't any opinion on that is there?  I know, this is an Ubuntu forum....**

---

### Post by ccbmailroom on 2014-11-02
Real quick, I forgot to add I don't know much command line programming at all, I use Windows at work and work with my wife's Macbook Air for simple video editing.  The last time someone suggested I needed to do something via terminal, my OS crashed and I had to re-image my laptop so I am sceptical of suggested this and that.  Just sayin.

---

### Post by bapoumba on 2014-11-03
As you have installed it from dpkg and not from apt-get (package manager) or one of its front ends (synaptic, Software Center), you could check if there is any trace of it by doing :
```
dpkg -l google-earth* 
```
as it seems this string is in the package name. How did you remove it ?

---

### Post by whitesmith on 2014-11-03
> **ccbmailroom said:**
> ...My goal is by summer of 2014 to move to an Apple computer...I just can't afford one right now.  Ubuntu does a wonderful job of keeping things organized in a sleek OS.  I use GIMP, Google Chrome, Thunderbird, Firefox, etc...
Purely out of curiosity, why move to Apple? We all have personal views of our tools, especially those favored by others. Mine is that Apple is a voluntarily worn straitjacket. I am not condemning your goal, simply trying to understand it. Less for more was Jobs' intention stated in a boardroom, I believe, but almost certainly not verbatim). I'm not asking you to hand-deliver 10,000 words to a thesis defense committee, but could you explain your choice in a little detail? Your words will help me, and just might help others in the forum.Thank you.

---

### Post by QIII on 2014-11-03
Why someone wants to use this or that OS is really not our business.

---

### Post by Penguin360 on 2014-11-03
Just guessing here: Launch Software Center, then click Installed, then expand each category, do you see Google Earth there?

---

### Post by whitesmith on 2014-11-03
> **QIII said:**
> Why someone wants to use this or that OS is really not our business.

I apologize to all who were offended by an undignified display of intellectual curiosity.

---

### Post by ccbmailroom on 2014-11-04
The this or that issue of another Linux OS was purely rhetorical.  As to the choice of OS, I have not found a usable video editor for Ubuntu.  My wife having worked for Apple computers through to about 2 to 3 years ago has a very intuitive video editor interface.  BUT...(there's always a BUT isnt there), I'm looking to do video editing to the extent of professional developement, hence why the goal for a Mac.  Not being a regular linux user for more than outside of documentation / audio / 'web surfing' and research / etc, If there was something that might work for video on a professional level, I could very well be swayed to stay with Linux solely.

As to the command:
dpkg -l google-earth*

I got the result of:



chuck@A117PizzaTruck:~$ dpkg -l google-earth*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  google-earth-s 7.1.2.2041-r i386         Explore, search and discover the 
chuck@A117PizzaTruck:~$

...but the Google Earth icon is still there.  :(

Also, still relating to this thread, if there is other junk software I've downloaded to my computer, is there a way to check to see what it is and remove it?  I'm not familiar with the dkpg -l command, (as a reminder, I don't know  much at all about terminal)

---

### Post by deadflowr on 2014-11-04
Try this
```
sudo dpkg --purge google-earth-stable
```
Then if it works and uninstalls that, try
```
sudo apt-get update && sudo apt-get upgrade
```
and if all is well there, try
```
sudo apt-get autoremove
```
In order the first command should remove the google earth package.
The second should make sure the system is fully updated.
And the last should remove any packages that the newly updated system deems no longer needed, hopefully it'll list those 32-bit libs.
Post back if any problems arise, with the output as well.

Hope it helps.

---

### Post by ccbmailroom on 2014-12-01
The 3 magic beans above worked!  I made it to the top of the bean stalk!  Thank you and thank you again!

I think that cleaned out of a bunch of stuff that was obsolete, even the stuff that I had downloaded through the software center then removed.  

Thank you again!

Signed
Happy Ubuntu user!  :)

---

