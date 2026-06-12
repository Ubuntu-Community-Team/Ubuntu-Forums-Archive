---
title: "How do I install Open office 3 beta in Ubuntu 7.10/ 8.04"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by quinnten83 on 2008-05-08
I downloaded a package on the website especially for Ubuntu. Turns out that it is not a .deb but a a folder compressed in tar.gz. There is a script called update in the uncompressed folder, When I use sudo sh ./update the script runs, but I see no new icons for OO.o in my menu. OO.o2.4 is still installed....
So can anybody point me in the right direction here? I allready tried googling but all info I got so far was unrelated to OO.o3 beta.

---

### Post by forestpixie on 2008-05-08
To install it, download the tar, extract and then cd into DEBS, then run

```
sudo dpkg -i *.deb
```

It installs to /opt/openoffice.org3

I have a launcher for it that runs
/opt/openoffice.org3/program/soffice

---

### Post by talsemgeest on 2008-05-08
And if you ever have to compile from the source, the application is usually located in /usr/share so you can add it to the menu.

---

### Post by robert114 on 2008-05-08
> **forestpixie said:**
> To install it, download the tar, extract and then cd into DEBS, then run

```
sudo dpkg -i *.deb
```

It installs to /opt/openoffice.org3

I have a launcher for it that runs
/opt/openoffice.org3/program/soffice

Ahh thanx! i tried apt-get install *.deb but it didn't work... now it's installing!

---

### Post by quinnten83 on 2008-05-08
thanks, guys and gals..
that did the trick.

---

### Post by in_rainbow on 2008-05-08
that did the trick, thanks

---

### Post by AaronMT on 2008-05-08
Yes. Installing this seemed to have lost all file type associations with office. How can I restore these?

As well, where are the icons located for OpenOffice 3 so I can associate with one my launcher?

---

### Post by Splower on 2008-05-08
I think something is wrong.  I can't cd into DEBS.  I am a rookie, so, can someone let me know hoe to do this.

thanks

---

### Post by celticbhoy on 2008-05-08
Can OO3 work alongside OO2.4 ???

---

### Post by Splower on 2008-05-08
I downloaded the tar file and extracted it on my desktop.  I can go to terminal but can't cd into DEBS.  I even tried putting the DEBS file right on my desktop and try to run it.  No luck..

---

### Post by talsemgeest on 2008-05-08
You can't cd into DEBS? At each level, type ```
ls
``` to tell you everything there is to cd into.

---

### Post by Splower on 2008-05-08
WOW....  You just opened up a wide range of answers I had about the file system in Ubuntu.  I am all good now.

Thanks.

---

### Post by talsemgeest on 2008-05-09
Cool, glad I could help.

---

### Post by boomdiddly on 2008-05-10
> **Splower said:**
> I think something is wrong.  I can't cd into DEBS.  I am a rookie, so, can someone let me know hoe to do this.

thanks

I don't want to teach you to suck eggs here but you are putting DEBS in all uppercase arn't you as it is case sensitive.

i.e

cd debs = doesn't work
cd DEBS = should work

Cheers

Paul

---

### Post by shifty_powers on 2008-05-10
.

---

### Post by MarnixV on 2008-06-28
Hi. I installed without a problem, on ubuntu 8.04, alongside OOo 2.4. But now, when I run /opt/OpenOffice.org3/program/soffice, I see the splash screen for a split second, then it's gone and the program doesn't run at all.

The README file mentions start up problems while using gnome, and proposed to add "unset SESSION_MANAGER" at the start of the soffice script. I tried this without result.

Does anyone have this problem too? And more importantly, does anyone have a solution?

Thanks

---

### Post by MrClearPore on 2008-07-03
The file **soffice** is not actually an executable file as such.  It's more like a script.  You have to run it like this:

```
/opt/OpenOffice.org3/program/./soffice
```

Note the "./" before the word **soffice**

Good luck.

---

### Post by 5735guy on 2008-07-19
To launch OpenOffice 3 (BETA) submit this command in the Terminal

 /opt/openoffice.org3/program/soffice

Hope this is useful.

---

### Post by thestig_992 on 2008-08-18
> **boomdiddly said:**
> I don't want to teach you to suck eggs here but you are putting DEBS in all uppercase arn't you as it is case sensitive.

i.e

cd debs = doesn't work
cd DEBS = should work

Cheers

Paul

also make sure that there are no spaces in the directory path...to fix this, put a \ before every space in the cd

---

### Post by BlasterXL on 2008-10-07
Finally registered to this community! (Hi!).

I started using Ubuntu (for like 2 months now), had some problems, but solved everything using the great community! Im really happy using it! I 

Also had troubles installing OpenOffice3, but thanks to you guys its a peace of cake.

Im also new to this OS and had lots of problems @ the start:
- Compiz running, like I want it.
- Sound problems, with my subwoofer (build in laptop Inspirion 9400).
- Bluetooth problems connecting my mouse.

All these problems are solved, thanks everyone. [-o<

---

### Post by sefs on 2008-10-14
In addition to running 

```

sudo dpkg -i *.deb

```

in the DEBS folder 

Within the DEBS folder in the final release there is a folder called "desktop-integration" with a single .deb in it, and when you run this deb it places the individual launch items into the office menu of the ububutu menus system.

---

### Post by corrrnbread on 2008-10-14
> **forestpixie said:**
> To install it, download the tar, extract and then cd into DEBS, then run

```
sudo dpkg -i *.deb
```

It installs to /opt/openoffice.org3

I have a launcher for it that runs
/opt/openoffice.org3/program/soffice


For some reason that command did not work for me, but ```
sudo dpkg *.deb --install
``` worked... arent they basically the same? anywho mine finally works =]

looks pretty good so far  :KS

---

### Post by pickarooney on 2008-10-14
Anyone got a link to the improvements in v3.0 Openofffice.org's site is inaccessible, presumably due to high traffic - is the official 3.0 version out?

Is it still as ugly? :)

---

### Post by Tanker Bob on 2008-10-14
deb install worked like a charm with dpkg. Thanks!

I uninstalled 2.4 before installing 3.0, but still had to correct some Writer file associations. The old version didn't remove itself from the file association list. The new version put itself in the association list, but under the old version so that the non-existent 2.4.1 would be called first. It only took a few minutes to clean up. So far, it looks like the other programs associated just fine.

---

### Post by 73ckn797 on 2008-10-14
> **pickarooney said:**
> Anyone got a link to the improvements in v3.0 Openofffice.org's site is inaccessible, presumably due to high traffic - is the official 3.0 version out?

Is it still as ugly? :)

The new 3.0 is why the site is busy.

Here is how I installed it:
* [http://ubuntuforums.org/showthread.php?p=5966220#post5966220](http://ubuntuforums.org/showthread.php?p=5966220#post5966220) 			*

---

### Post by WBL on 2008-10-14
Won't Ubuntu eventually release 3.0 via update manager anyways?

-WBL

---

### Post by Tanker Bob on 2008-10-14
> **WBL said:**
> Won't Ubuntu eventually release 3.0 via update manager anyways?

-WBL
Not for 8.04. I may be in the 8.10 repositories if we're lucky. Canonical's philosophy goes against major-version software upgrades within a given distribution. It hit the fan over the disconnect with Firefox a few updates ago, but no budge from Canonical. It's why I dropped down from 64-bit to 32-bit. Most everything is available in 32-bit, so I can upgrade anything when I so desire.

---

### Post by soho2014 on 2008-10-15
> **Splower said:**
> I downloaded the tar file and extracted it on my desktop.  I can go to terminal but can't cd into DEBS.  I even tried putting the DEBS file right on my desktop and try to run it.  No luck..

Make sure that you type the case exactly as it is, because cd DEBS is important, not cd debs  and similarly, to cd into desktop, type:

cd Desktop  not cd desktop.

---

### Post by tronador on 2008-10-22
Hi all!

I had a lot of trouble installing it, and it was just that the version was not automatically recognised by Openoffice. In  this case is Ubuntu 8.04 64 bits, so the link provided by a user here did the trick. Thanks a lot!.

for the case sensitivity problem, try using the TAB key, it saves a lot of time and there, you can see if you are spelling the commands right.

Keep feeding up, it is what makes Ubuntu great!

---

### Post by shk76 on 2009-01-09
Following the steps in "http://sayeed-linux.blogspot.com/" should do.:o

---

