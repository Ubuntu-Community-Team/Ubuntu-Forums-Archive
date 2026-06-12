---
title: "upgrading to 12.04"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Niemand000 on 2012-04-26
To begin with, I'm an ABSOLUTE beginner to Ubuntu, I downloaded it to a used Dell I just got. A friend of mine gave me a 10.04 CD; now I see there's a 12.04 version and I really want to cut my teeth on that instead of an older version. 
 
I started the upgraded as was suggested at ubuntu.com. (press Alt+F2 enter such and such and follow the onscreen commands) after doing so everything started downloading fine. I came back a couple of hours later and the screen is completely black. When I rebooted and check on everything it said I had broken files? 
 
I'm kinda confused at this point and REALLY need help.
1. I don't know how to take care of broken files (but I intend to learn as soon as I get home from work)
2. How am I going to install 12.04
3. I heard today 12.04 Beta 2 isn't suppose to come out LTS until a couple of days from now? If that's true then why would they let me download it yesterday?
4. What's the difference between 12.04, 12.04 Beta 2, and 12.04 Beta 2 LTS
 
Thanks for the help in advance. I know it'll be a long hard road, but I'm excited about one day answering questions like this for other beginners, and tackling some more advanced stuff. 
 
God speed,
Niemand000

---

### Post by ptn107 on 2012-04-26
Open update manager, check for updates, and install any that appear.  If after you are not prompted for an Upgrade to 12.04 LTS then you already have it and the upgrade was [partially] successful.  You can check your version by typing:
```
lsb_release -a
```
in a terminal window.

If you want to check to see if you have to fix broken packages, open a terminal and type:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get -f install
```
press enter and supply your password when prompted.

If your looking to completely reinstall Ubuntu we can cross that bridge when you get to it.  For now we'll try to fix the install you have.

Beta 2 for 12.04 LTS has long passed.  It was 3/29/12 [1].  The beta 2 milestone was the second public pre-release used to help fix bugs before the final release.  Don't get the nomenclature mixed around.  Beta 2 was just a milestone, a snapshot of the precise pangolin archive at a given instant.  The tag 'LTS' means long term support.  Regular releases are supported with updates and fixes for 18 months.  LTS releases are supported for longer periods [2].  These releases are targeted towards businesses, schools, or other institutions that aren't interested in upgrading to the next release 6 months down the road.  This 12.04 LTS is supported for 5 years.  Keep in mind that not all releases of 12.04 carry the LTS tag [3].  For example: Lubuntu, Mythbuntu, and Ubuntu Studio will only get the standard 18 months of support, while Ubuntu, Ubuntu Server, Ubuntu Core, Edubuntu, Kubuntu, and Xubuntu LTS will get 5 years.

[1] [https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)
[2] [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
[3] [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes)

---

### Post by jerrrys on 2012-04-26
Burn a CD and do a fresh install of 12o4.  Thats the best way in my book.

[http://fridge.ubuntu.com/2012/04/26/ubuntu-12-04-development-update-22/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29](http://fridge.ubuntu.com/2012/04/26/ubuntu-12-04-development-update-22/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ubuntu-news+%28Ubuntu+News%29)

---

### Post by wildmanne39 on 2012-04-26
+1 on a fresh install there are many changes from 10.04 to 12.04 and the upgrade process to unity does not always go well.

The first recommendation is worth a try but there will probably be other issues from the upgrade.
[http://ubuntuforums.org/showthread.php?t=1946145](http://ubuntuforums.org/showthread.php?t=1946145)
Thanks

---

### Post by FulciLives on 2012-04-26
I have 12.04 Beta 2 and today it had me download an update (it was around 50MB or so I think) and then asked me to reboot.

In terminal I see this:

```
~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
```
Does this mean it upgraded to 12.04 LTS "final" or am I still Beta 2?

---

### Post by grahammechanical on 2012-04-26
12.04 Precise Pangolin is officially released sometime during 26th April (today). The exact time varies.

From the 27th April development will begin on the next release, 12.10 Quantal Quetzal. So, to put it another way, 12.04 has been under development since last October and it has been possible to download and install it for testing purposes.

Here is the release schedule:

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule]("https://wiki.ubuntu.com/QuantalQuetzal/ReleaseSchedule")

You can see the relationship between Alpha 1, 2, Beta 1, 2, Release Candidate and the final release of 12.10.

If you like you can join in testing 12.10 as it is developed.

There are two basic ways of doing this.

1) Install a second version of 12.04 into another partition, dual boot into it and in a couple of weeks convert it to 12.10 development branch. It will still be very much like 12.04 but changes will be brought over time.

2) Test the ISO images at each milestone point. Test them as a live CD or test them as an install into another partition.

I will be using both these methods over the next six months.

go to here and click on Testers Wiki.

[https://wiki.ubuntu.com/U+1]("https://wiki.ubuntu.com/U+1")

The main thing you need to watch out for is your data and documents. Keeping them backed up and on a separate /home partition. Then if you need to re-install you just install Ubuntu again into the / partition and your data is not only safe but available.

Regards.

---

### Post by TBABill on 2012-04-26
If you have installed all the updates, your beta is now the final version.

---

### Post by Niemand000 on 2012-04-26
UPDATE
 
Alright, so I downloaded 12.04 to a CD and booted it from there but now I'm running the test off the CD to see how it's working out.  I love the lay out and all it has to offer but it's running preeeeetty slow....
Is that just a result of it being run in "test mode" off a CD, or is that how fast it's actually gonna run when I install it? 
 
And if I go ahead and install it, and it runs slowly, can I just reinstall 10.04, or will the change in OS over the past day be too much for the CPU (from WIN XP to Ubuntu 10.04, to Ubuntu 12.04)

---

### Post by Niemand000 on 2012-04-26
Aaaaand I managed to F it up. While installing 12.04 I got a black screen that says a bunch of stuff but starts with 
[ 1877.235193] BUG: unable to handle kernel NULL pointer dereference at 00000140
[ 1877.235264] IP: blah blah blah
[ 1877.235400] *pdpt = blah blah blah, so on and so forth on down the page with many more 
[ 1877.235numbersnumbersnumbers] Modules linked in: xfs reiserfs jfs ext2 blah blah blah
[ 1877.235numbersnumbersnumbers] More computer stuff
[ 1877.235numbersnumbersnumbers] More letters and numbers
etc
etc
etc
 
 
Wtf? What do I do now?

---

### Post by oboedad55 on 2012-04-26
> **Niemand000 said:**
> UPDATE
 
Alright, so I downloaded 12.04 to a CD and booted it from there but now I'm running the test off the CD to see how it's working out.  I love the lay out and all it has to offer but it's running preeeeetty slow....
Is that just a result of it being run in "test mode" off a CD, or is that how fast it's actually gonna run when I install it? 
 
And if I go ahead and install it, and it runs slowly, can I just reinstall 10.04, or will the change in OS over the past day be too much for the CPU (from WIN XP to Ubuntu 10.04, to Ubuntu 12.04)

It will fun much faster installed than off the CD. And no, it won't hurt your computer. I'd suggest you install 12.04 and give it a good try before going back. 10.04 is still supported, but only for one more year.

---

### Post by ptn107 on 2012-04-26
> **Niemand000 said:**
> Aaaaand I managed to F it up. While installing 12.04 I got a black screen that says a bunch of stuff but starts with 
[ 1877.235193] BUG: unable to handle kernel NULL pointer dereference at 00000140
[ 1877.235264] IP: blah blah blah
[ 1877.235400] *pdpt = blah blah blah, so on and so forth on down the page with many more 
[ 1877.235numbersnumbersnumbers] Modules linked in: xfs reiserfs jfs ext2 blah blah blah
[ 1877.235numbersnumbersnumbers] More computer stuff
[ 1877.235numbersnumbersnumbers] More letters and numbers
etc
etc
etc
 
 
Wtf? What do I do now?

You should now do a clean install.  Download the 12.04 LTS 32-bit image _[here]("http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-i386.iso")_ or the 64-bit image _[here]("http://releases.ubuntu.com/precise/ubuntu-12.04-desktop-amd64.iso")_.  Burn it to a CD, put it in, reboot, and 'Install Ubuntu'.

---

### Post by Niemand000 on 2012-04-27
I got that message after doing a clean install : / I'm checking my system now to make sure I have the minimum requirements.  It occurred to me today that that may be the issue.

---

### Post by Niemand000 on 2012-04-27
No Worries!! After clean installing (without trying it first) I've successfully installed and am now currently running Ubuntu 12.04! Thanks for all your help!

---

### Post by wildmanne39 on 2012-04-27
Hi, good to hear.

---

### Post by Johnny3 on 2012-04-27
One of my first installs from software center would be Synaptic Package Manager.
Have Fun and God Bless Johnny3 65+++
Youtube has a lot of how to for Ubuntu too.

---

### Post by duceduc on 2012-04-27
Hi all. I have a question that is not so related to upgrading to 12.04. I do not want to upgrade to 12.4 from 11.10 on my ubuntu server edition. However, whenever I ssh using putty, I get this message that an upgrade is available. How can I get rid of that message?

---

### Post by Niemand000 on 2012-04-28
> **Johnny3 said:**
> One of my first installs from software center would be Synaptic Package Manager.
Have Fun and God Bless Johnny3 65+++
Youtube has a lot of how to for Ubuntu too.

No doubt, I'm checkin it out now

---

### Post by Johnny3 on 2012-04-28
> **Niemand000 said:**
> No doubt, I'm checkin it out now

I like this young man a lot [http://www.youtube.com/watch?v=BRIgT8YffDY&feature=g-all-u](http://www.youtube.com/watch?v=BRIgT8YffDY&feature=g-all-u) don't always known what he is talking about. But To me he explains thing good. He kowns more that I will every known.
Good Luck and God Bless Johnny3 65+++

---

