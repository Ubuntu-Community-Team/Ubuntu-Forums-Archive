---
title: "Open Office not starting"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by lolwhites on 2008-10-31
When I tried to run Open Office 3, it crashed every time, saying it would recover an imaginary document. I tried following the advice [[COLOR="Red"]here[/COLOR]]("http://www.nabble.com/-Linux--OOo3RC2-Installation-Issues-Workaround-td19695985.html") but that didn't work. Now I get nothing at all when I click on a launcher, and trying to run in a terminal does nothing, so no error message I can go on.

---

### Post by sayems on 2008-10-31
Ho did you installed Openoffice? 

Remove Openoffice from your pc and Copy this repository to your sources list and update, I hope that will fix the problem.

## Openoffice.org
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

---

### Post by drs305 on 2008-10-31
When you try using OpenOffice 3 in terminal, does using this command format work?
```
openoffice.org3 /path.to.file/filename
```

---

### Post by lolwhites on 2008-10-31
I completely removed Openoffice and added the repositories, updating didn't install it. I installed using the instructions [here]("http://www.tectonic.co.za/?p=3363") and now have open office in the menu, but clicking still does absolutely nothing, as does trying to run in a termin as drs305 suggests. It show up in the system monitor though.

---

### Post by thomas228 on 2008-10-31
> **lolwhites said:**
> I completely removed Openoffice and added the repositories, updating didn't install it. I installed using the instructions [here]("http://www.tectonic.co.za/?p=3363") and now have open office in the menu, but clicking still does absolutely nothing, as does trying to run in a termin as drs305 suggests. It show up in the system monitor though.

When you removed 00 did you also remove all of 00o3. If not try this terminal command:
Step 1 clearly requires you to remove ubuntu's 2.4 version.

you may have to remove 00o3 using tombuntu.com's script: 
sudo apt-get remove ooobasis3.0-base ooobasis3.0-binfilter ooobasis3.0-calc ooobasis3.0-core01 ooobasis3.0-core02 ooobasis3.0-core03 ooobasis3.0-core04 ooobasis3.0-core05 ooobasis3.0-core06 ooobasis3.0-core07 ooobasis3.0-draw ooobasis3.0-en-us ooobasis3.0-en-us-base ooobasis3.0-en-us-binfilter ooobasis3.0-en-us-calc ooobasis3.0-en-us-draw ooobasis3.0-en-us-help ooobasis3.0-en-us-impress ooobasis3.0-en-us-math ooobasis3.0-en-us-res ooobasis3.0-en-us-writer ooobasis3.0-gnome-integration ooobasis3.0-graphicfilter ooobasis3.0-images ooobasis3.0-impress ooobasis3.0-javafilter ooobasis3.0-kde-integration ooobasis3.0-math ooobasis3.0-onlineupdate ooobasis3.0-ooofonts ooobasis3.0-ooolinguistic ooobasis3.0-pyuno ooobasis3.0-testtool ooobasis3.0-writer ooobasis3.0-xsltfilter openoffice.org3 openoffice.org3-base openoffice.org3-calc openoffice.org3-dict-en openoffice.org3-dict-es openoffice.org3-dict-fr openoffice.org3-draw openoffice.org3-en-us openoffice.org3-impress openoffice.org3-math openoffice.org3-writer openoffice.org-ure

before removing ubuntu's 2.4 version.
I cut and pasted this from
http://ubuntuforums.org/showthread.php?p=5977796#post5977796
post #2
Dont know if it will help but it worked for jmcgovern.

Good Luck 
Tom

---

### Post by lolwhites on 2008-10-31
Have removed Open Office using this script and reinstalled but the problem persists.

Edit - one reboot later and it's fine. Thanks!

Edit 2 - Spoke too soon! It worked once, then it was back to not starting again!

---

### Post by VoodooLoveDog on 2008-10-31
I noticed when I upgraded to 8.10 from 8.04 all of the desktop integration from OOov3.0 was missing. I didn't try to open the software to see if it was the desktop integration only that was a problem. 

Here's what I did to fix it. 

I opened the Synaptic Package Manager and removed all  instances of OOo from my machine. Then I re-ran:

sudo dpkg -i *.deb 

(from the directories I extracted the package to from the OOo site: OOO300_m9_native_packed-1_en-US.9358)

Then I drilled down the 'desktop-integration' folder and ran the same command as above. 

Fixed my install.

---

### Post by lolwhites on 2008-10-31
It seems to be working now...

---

### Post by thomas228 on 2008-10-31
> **lolwhites said:**
> It seems to be working now...

A little utility for looking at my file system and that showed me a number of 00o2.4 files I thought I had gotten rid of is fslint_2.24-1_all.deb. It was featured on linux.com about a month ago and can be found by googling.
Dont know if this will help you solve your problem or not.
I'm sure that you went back and got a fresh download of the tarball from
http://download.openoffice.org/other.html#en-US
Good luck
Tom

---

### Post by lolwhites on 2008-11-02
OK, it works just after booting up the system. After a while, the launchers don't respond and I have to restart the whole system to get OOo working again, at which point it tells me it has X number of documents to recover (X being the number of times I tried to start OOo). This happens regardless of whether I click on an icon or try to star from the command line.

---

