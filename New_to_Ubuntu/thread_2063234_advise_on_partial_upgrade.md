---
title: "advise on partial upgrade"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-09-26
usually i upgrade from the command line using
sudo apt-get update && sudo apt-get upgrade
for over a week have been getting a bunch of upgrades held back
if i run the update manager i get the notice that only a partial upgrade is avail and if i check there is the notice that the gnome  desktop will be removed. i have ubuntu, xfce, xubuntu all installed. so couldnt i just do the update and then reinstall gnome. currently running 12.04. tks

---

### Post by Bashing-om on 2012-09-26
rburkartjo;

Hello; Thinking about it.  i would think old fred's method should get you back in shape.
```

oldfred's methology for restoring:
Then try ( all the # are comments do not type anything after a #)
#if not chroot use: /chroot not to be used by new users/
sudo -i
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
All that does is update it again.
#log-out from super user
exit 

```Wiser heads may prevail <==BDQ

---

### Post by Frogs Hair on 2012-09-26
I have used proposed updates for a number of releases  and found it is best to wait until all packages are available when it comes to partial upgrades.
 
By all means look into the method above if it is an ongoing problem. I am currently using the XFCE session along with Unity and the Gnome shell but that is quite a bit different than the Xubuntu desktop.

---

### Post by williejones on 2012-09-26
You have had this for over a week.  That is more than enough time to clear up a partial update to keep things being held back.

Try another approach using Synaptic Package Manager, check to see if broken packages by looking at the bottom of the screen, and fix broken packages if applicable by selecting edit fix broken packages.  Then using Synaptic Package Manager reload , mark all upgrades, apply, apply.  You can see the status at the bottom of the screen to see if everything is successful.

---

### Post by Sef on 2012-09-26
Do not install partial upgrades, unless you have backed up your system and are prepared to do a clean install. For more info on partial upgrades, click [here]("https://wiki.ubuntu.com/U%2B1/partial_upgrade").

---

### Post by rburkartjo on 2012-09-27
first tks for all your help and no i didnt want to do a partial upgrade. here is how i fixed opened spm checked for broken packages and none were found. then searches for all updates and applied. that seem to fix the problem. doesnt make sense but it worked.

---

### Post by Bashing-om on 2012-09-27
All I am going to surmise is Synaptic is very smart ..particularly so when "smart up-date" is enabled ....huh ? 

 Glad Ya got it resolved. -> Happy ubuntu'n

---

### Post by BlinkinCat on 2012-09-29
Hi all,

Unfortunately I did a new install about a day ago as a result of doing a partial upgrade.
I did the install of 12.04 and not 12.04.1, did I make a basic mistake here? Now Update Manager is requesting I do a partial upgrade which I am ignoring because of the wiki and comments on this thread. Update Manager states 63 updates have been selected consisting of 53.1 Mb.
I struggle to understand how I can check when there are seemingly so many packages involved. As an alternative, could I run the commands as outlined by oldfred on this thread? Other than occasional crashes which I expect at this stage, the installation is running well. The amount to be downloaded hasn't changed in about 24 hours - should it eventually?

I am really kicking myself that I installed 12.04 and not 12.04.1 or does that really matter?

Thank you for any assistance you can offer  - :P

---

### Post by Bashing-om on 2012-09-29
BlinkinCat;

 As I understand it...12.04 is what the d/l .iso is (about 2 weeks back is my last d/l) the updates will upgrade to 12.04.1. With 3 recent installs->install updates, 3rd party checked in the installer- change my mirror site to closest/fastest, install synaptic (usage preference) and in synaptic do the remainder of the updates... has always been successful on my part.

In your particular case: I have advised old fred's method many times ..always to good results. I perceive nothing in the code that can have an adverse impact; expect it to bring you up-to-date and all clean .

I am fortunate that I have broadband access ...lot of data to bring in to affect the upgrade to 12.04.1 I have no idea as to how long before the 12.04.1 version will be available for d/l. And, in my experience even when the updated version is available, there remains additional updates to be performed.

[INDENT]my intent is all relations good <==BDQ
  
[/INDENT]

---

### Post by BlinkinCat on 2012-09-29
Hi Bashing-om,

It is probably me, but I was unsuccessful following oldfred's method. I was left with a system that had no access to terminal, how I don't know. Software Center was also graphically distorted - it was probably something I did. I had all sorts of trouble trying to download 12.04.1 - on 4 occasions downloads failed to complete after about 70%. Eventually one download worked, but I was unable to check MD5Sum because of no access to terminal - fortunately I was able to burn disk with good ole brasero - it has its knockers but it works for me - Anyway at this stage after doing a completely fresh install of 12.04.1 I am having no further problems. Sorry to ramble on but I thought I had really had it when those 4 downloads failed - there may be a lesson here for others - there certainly is for me.

Anyway thanks Bashing-om - :p

---

### Post by Bashing-om on 2012-09-30
@ BlinkinCat;

Hey it is great you got installed....Reasons for the faulty installs are numerous; one may never know exactly ..we sometimes must just carry on !

 I look forward to a long continued association.

[INDENT]Best wishes <==BDQ
 
[/INDENT]

---

