---
title: "After all these years the inability to install 12.04"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by packrat on 2012-05-25
in-spite of all the instruction on burning an iso is very disappointing. Something is not right. Have tried on two different system with the same result. The program goes the gyration of displaying the rotating white and purple balls and the seizes. At this point in time, an attempt to transition to the new LTS is thwarted by its own existence.

---

### Post by ajgreeny on 2012-05-25
I don't understand what you are seeing; your description is not very clear.

What are the "rotating white and purple balls"?

---

### Post by mlentink on 2012-05-25
"Not clear" seems to me to be the understatement of the week. 

Would you care to clarify? What steps have you taken, where dor things seem to go wrong, what error messages, if any, did you get?

---

### Post by packrat on 2012-05-25
The boot up process...Ubuntu with the little balls underneath...they sequence back and forth and then seize, system locks up and does not continue, does not install.

---

### Post by BlinkinCat on 2012-05-25
I assume you did your md5sum ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oldfred on 2012-05-25
Is this after install or boot of liveCD to test system?

Either way often a video issue. What video card?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by packrat on 2012-05-25
> **BlinkinCat said:**
> I assume you did your md5sum ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You assume correctly.

---

### Post by packrat on 2012-05-25
> **oldfred said:**
> Is this after install or boot of liveCD to test system?

Either way often a video issue. What video card?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Can neither install nor boot live.

---

### Post by Enigmapond on 2012-05-25
If you can't run LiveCD and the data is correct, this may be a hardware issue. Have you attempted with a USB stick? I find this works better anyway...

---

### Post by jmore9 on 2012-05-25
did you google to see if your video card is supported in Ubuntu 12.04.  I had an older one which worked just fine in 11.10 but 12.04 did not like it so would not install.

Used my newer machine and it installed .  I just put linuxmint on the other one so only use ubuntu 1 time this time.

---

### Post by packrat on 2012-06-11
will install on my HP Special Edition L2000 laptop...even paid Compusa tech to give it a go...it would not get past Ubuntu Screen and seized before the cursor arrow launched. Returned to 11.04 64x and as before, it works great. 

Here are the specs...HP Special Edition L2000 laptop:
[http://www.cnet.com/laptops/hp-special-edition-l2000/4507-3121_7-31412742.html](http://www.cnet.com/laptops/hp-special-edition-l2000/4507-3121_7-31412742.html)

Graphics Processor ATI Radeon Xpress 200M - 128.0 MB

Ubuntu, let me know when you get it fixed, please.

---

### Post by Curtis6767 on 2012-06-11
> **packrat said:**
> will install on my HP Special Edition L2000 laptop...even paid Compusa tech to give it a go...it would not get past Ubuntu Screen and seized before the cursor arrow launched. Returned to 11.04 64x and as before, it works great. 

Here are the specs...HP Special Edition L2000 laptop:
[http://www.cnet.com/laptops/hp-special-edition-l2000/4507-3121_7-31412742.html](http://www.cnet.com/laptops/hp-special-edition-l2000/4507-3121_7-31412742.html)

Graphics Processor ATI Radeon Xpress 200M - 128.0 MB

Ubuntu, let me know when you get it fixed, please.


Try the alternate ISO image.[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Just scroll down and look for the alternate image in which ever version you normally use.

Perhaps it's just a shot in the dark.

Edit: The alternate image will do a text-based install rather than the graphic Ubiquity install.

---

### Post by packrat on 2012-06-16
> **Curtis6767 said:**
> Try the alternate ISO image.[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Just scroll down and look for the alternate image in which ever version you normally use.

Perhaps it's just a shot in the dark.

Edit: The alternate image will do a text-based install rather than the graphic Ubiquity install.

OK. Is the text based install a commandline install? What will the interface look like once installed? Thanks.

---

### Post by Curtis6767 on 2012-06-16
> **packrat said:**
> OK. Is the text based install a commandline install? What will the interface look like once installed? Thanks.

No command line. It'll look like a DOS install, is the best way I can describe. You'll be doing a lot of reading and checking this and that. In the end you'll have 12.04LTS with Unity.

---

### Post by CharlesA on 2012-06-16
> **packrat said:**
> OK. Is the text based install a commandline install? What will the interface look like once installed? Thanks.

It's a text-based installer, but it should install everything the regular ubuntu desktop cd does. See here:
[https://help.ubuntu.com/community/Installation#Alternate_Installation](https://help.ubuntu.com/community/Installation#Alternate_Installation)

---

### Post by TheGuyWithTheFace on 2012-06-16
If you already have 11.10, why not just try to upgrade instead of a clean install?

---

### Post by drawkcab on 2012-06-16
Upgrading always tends to produce a bunch of annoying bugs for me, especially with everything since 10.10.  Clean install all the way.

---

### Post by TheGuyWithTheFace on 2012-06-16
> **drawkcab said:**
> Upgrading always tends to produce a bunch of annoying bugs for me, especially with everything since 10.10.  Clean install all the way.

I keep hearing that, but I upgraded to precise from oneric with no problems whatsoever, at least that I could tell.

---

### Post by packrat on 2012-06-16
> **Curtis6767 said:**
> No command line. It'll look like a DOS install, is the best way I can describe. You'll be doing a lot of reading and checking this and that. In the end you'll have 12.04LTS with Unity.

It is a NO-GO, unfortunately. Install screen loaded. Got the select the language. Hit Install after selecting language; and then, it just sat there for 20 minutes doing nothing...the cd drive blinked like an intermittent Caution Light...no other action. So, went back to 11.04. Thanks for your help.

UBUNTU, when you fix 12.04, please let me know.

Best to all of you.

---

### Post by packrat on 2012-06-16
For what it is worth on my homegrown desktop, 12.04 installed without a problem and networked with the 11.04 laptop that will not take a 12.04 install.

---

### Post by cmcanulty on 2012-06-16
I had exact same issue and after much tweaking I had to blacklist the wireless driver at the install I don't remember exact steps but see the post here for April 28th. I have a HP G72t laptop.

[http://ubuntuincident.wordpress.com/2012/04/]("http://ubuntuincident.wordpress.com/2012/04/")

---

### Post by packrat on 2012-06-18
> **cmcanulty said:**
> I had exact same issue and after much tweaking I had to blacklist the wireless driver at the install I don't remember exact steps but see the post here for April 28th. I have a HP G72t laptop.

[http://ubuntuincident.wordpress.com/2012/04/]("http://ubuntuincident.wordpress.com/2012/04/")

Thanks. I'm no good at command line efforts. Will wait for Ubuntu to fix their problem...if they ever do so.

---

### Post by CharlesA on 2012-06-18
> **packrat said:**
> Thanks. I'm no good at command line efforts. Will wait for Ubuntu to fix their problem...if they ever do so.
The instructions are right here:
[http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/](http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/)

---

### Post by packrat on 2012-06-22
> **CharlesA said:**
> The instructions are right here:
[http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/](http://ubuntuincident.wordpress.com/2012/04/28/ubuntu-12-04-stops-booting-b43-wifi-problem/)

Ubuntu needs to fix the problem. These work-arounds leave me up the creek. Thanks.

---

### Post by mlentink on 2012-06-22
> **packrat said:**
> Ubuntu needs to fix the problem.
Ubuntu is you. And me. And all others who want to contribute.

---

### Post by |{urse on 2012-06-22
'Ubuntu' doesn't 'need' to do anything. If you can't be bothered with the workaround you could simply install an older (more stable and developed) version of Ubuntu. What are your system specs?

---

### Post by Zill on 2012-06-22
> **mlentink said:**
> Ubuntu is you. And me. And all others who want to contribute.
+1

Maybe the OP would be happier just "buying" a proprietary OS where at least they can ask for their money back!

---

### Post by cmcanulty on 2012-06-22
No need to be rude. This is a serious problem as it affects the b43 wireless card which is very common. I managed a fix but it took a lot of frustration. I think a patch is definitely in order. We want to keep newbies not alienate them.

---

### Post by CharlesA on 2012-06-22
> **cmcanulty said:**
> No need to be rude. This is a serious problem as it affects the b43 wireless card which is very common. I managed a fix but it took a lot of frustration. I think a patch is definitely in order. We want to keep newbies not alienate them.
Has a bug report been filed already?

---

### Post by packrat on 2012-06-24
> **cmcanulty said:**
> No need to be rude. This is a serious problem as it affects the b43 wireless card which is very common. I managed a fix but it took a lot of frustration. I think a patch is definitely in order. We want to keep newbies not alienate them.

You are quite correct. It does need to be fixed.

Migrate to another OS? The flames are a good reason to do so.

Furthermore, the arrogance and elitism of the flamers is ill considered on their part but not unexpected.

---

### Post by uRock on 2012-06-24
I do not see flaming. I do see that you are unwilling to run one command and edit one configuration file. You only need the command line to run gedit as root to open the conf file. The package the link is recommending for install can be installed via Ubuntu Software Center, though copying and pasting the install command is very simple.

---

### Post by CharlesA on 2012-06-24
> **uRock said:**
> I do not see flaming. I do see that you are unwilling to run one command and edit one configuration file. You only need the command line to run gedit as root to open the conf file. The package the link is recommending for install can be installed via Ubuntu Software Center, though copying and pasting the install command is very simple.
I don't see any flaming either, just people trying to help.

---

### Post by packrat on 2012-06-24
> **CharlesA said:**
> I don't see any flaming either, just people trying to help.

Some thrying to help but not solve the problem on a larger scale...only one right thinking poster saying the problem is on a larger scale.

Otherwise, Myopic. Arrogant. Elitist. Flamers. Deluded.

---

### Post by CharlesA on 2012-06-24
> **packrat said:**
> Some thrying to help but not solve the problem on a larger scale...only one right thinking poster saying the problem is on a larger scale.

Otherwise, Myopic. Arrogant. Elitist. Flamers. Deluded.
With that, this thread is closed.

---

