---
title: "K3B: Blu Ray Speed and 99% I/O Errors"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by mantaray on 2012-08-24
I have been trying to burn blu-rays with k3b (V 2.02) in Ubuntu 12.04, and I always get a 99% completion message before it tells me there is an I/O error.  At this point, the burning halts.  Posts by other people suffering a similar fate have suggested installing the newest version of cdr tools.  I have done this, and k3b now uses, as a default, the most recent mkisofs, cdrecord, and readcd rather than the cdrkit fork.  In addition, it will not burn at BD rates.  Rather, is uses DVD speeds.  Ex/ 6x (27 MB/s) becomes 6x (8.31 MB/s) instead.  Is there any way to fix the 99% and DVD rate problem?

Any help would be appreciated!

---

### Post by ianni67 on 2012-10-27
> **mantaray said:**
> I have been trying to burn blu-rays with k3b (V 2.02) in Ubuntu 12.04, and I always get a 99% completion message before it tells me there is an I/O error.  At this point, the burning halts.  Posts by other people suffering a similar fate have suggested installing the newest version of cdr tools.  I have done this, and k3b now uses, as a default, the most recent mkisofs, cdrecord, and readcd rather than the cdrkit fork.  In addition, it will not burn at BD rates.  Rather, is uses DVD speeds.  Ex/ 6x (27 MB/s) becomes 6x (8.31 MB/s) instead.  Is there any way to fix the 99% and DVD rate problem?

Any help would be appreciated!

The same here. Two different machines: ubuntu 10.04 and Kubuntu 12.04. The BD burner is a Samsung external (USB) Blu Ray burner model SE-506.

[EDIT]
I'm currently using Nero for Linux. It works perfectly with my burner but after more than 15 years of open source software for burning (k3B and cdrecord) this is frustrating.

---

### Post by erafael on 2012-11-07
> **mantaray said:**
> I have been trying to burn blu-rays with k3b (V 2.02) in Ubuntu 12.04, and I always get a 99% completion message before it tells me there is an I/O error.  At this point, the burning halts.  Posts by other people suffering a similar fate have suggested installing the newest version of cdr tools.  I have done this, and k3b now uses, as a default, the most recent mkisofs, cdrecord, and readcd rather than the cdrkit fork.  In addition, it will not burn at BD rates.  Rather, is uses DVD speeds.  Ex/ 6x (27 MB/s) becomes 6x (8.31 MB/s) instead.  Is there any way to fix the 99% and DVD rate problem?

Any help would be appreciated!



Same issue here.
Spoiled some dual layer disks already on the process. 
I  using 12.04 LTS. Didn't have such problems in previous releases.

Does anyone have an idea what the cause of it might be?

---

### Post by Raphicerus on 2012-11-07
> **mantaray said:**
> I have been trying to burn blu-rays with k3b (V 2.02) in Ubuntu 12.04, and I always get a 99% completion message before it tells me there is an I/O error.  At this point, the burning halts.  Posts by other people suffering a similar fate have suggested installing the newest version of cdr tools.  I have done this, and k3b now uses, as a default, the most recent mkisofs, cdrecord, and readcd rather than the cdrkit fork.  In addition, it will not burn at BD rates.  Rather, is uses DVD speeds.  Ex/ 6x (27 MB/s) becomes 6x (8.31 MB/s) instead.  Is there any way to fix the 99% and DVD rate problem?

Any help would be appreciated!

I had a similar error, and ended up running a thing called k3bsetup which gets installed with k3b.  A dialogue appears; you select what it recommends for the dvd drive and the programs. You are asked to authenticate, and it then tweaks the permissions.

I also had to select "burn at 2.4x" from a dropdown menu, rather than some more ambitious default, and then there were no more duds. (Higher speeds produced DVDs where the burn "succeeded", but then they froze during replay.)

I'm not convinced that all the settings stay between sessions, so I do it every session I want to make DVDs. Maybe someone will give us the real lowdown on this.

(Edit). Sorry, I was just burning plain DVDs, but the permission thing might still be relevant).

---

### Post by erafael on 2012-11-08
Raphicerus - it seems that your hint and installing the latest cdrtools package did the job - I can now burn blu rays 100% and have no errors any more. Thanks!
I first installed cdrtools, applied the permissions and set my burner's speed to 2x.

I got the tip about cdrtools from: [https://regx.dgswa.com/html/content/kd3-fatal-error-during-recordinginputoutput-fixed](https://regx.dgswa.com/html/content/kd3-fatal-error-during-recordinginputoutput-fixed)

Hope it works for other folks as well. If it does - we can than close this thread, so please confirm.

Thanks again for your help!

---

### Post by Raphicerus on 2012-11-08
> **erafael said:**
> Raphicerus - it seems that your hint and installing the latest cdrtools package did the job - I can now burn blu rays 100% and have no errors any more. Thanks!


Great to see you got a result, erafael! I was getting annoyed enough spoiling blank DVDs, so wasting blu-rays must be worse.

---

### Post by dgray_from_dc on 2012-12-19
I've been having the same problem with Blu-Ray burning and have found an easier way of impletemting the solution here: [https://blog.redhoundsoftware.com/?p=75]("https://blog.redhoundsoftware.com/?p=75")

---

### Post by ariel on 2012-12-21
> **dgray_from_dc said:**
> I've been having the same problem with Blu-Ray burning and have found an easier way of impletemting the solution here: [https://blog.redhoundsoftware.com/?p=75](https://blog.redhoundsoftware.com/?p=75)

Thanks for this! it's a bit amazing that we still have to do all this manual tweaking just to get BDs properly burned... but... whatever works :)

---

### Post by meesterblack on 2013-01-27
Confirm same problem with K3b here.

Issue stems from genisoimage/growisofs issues closing out multi-session BD-R discs.  Seen various bug reports around saying this and that.. bottom line, they don't currently work (and may not in the near future -- allegedly the code behind these packages is based on dated/buggy sources).


Here are the steps I finally took to enable me to successfully and repeatedly get error-free BD-R discs burned:

[LIST=1]
[*]Download K3b, if you haven't already. 

```
sudo apt-get install k3b
```

[*]Download cdrtools source code to a folder (suggest /tmp)

```
wget ftp://ftp.berlios.de/pub/cdrecord/alpha/cdrtools-beta.tar.gz
tar xvf cdrtools*.gz
cd cdrtools*
```

[*]Unpack and compile (make sure package build-essentials are installed) - cdrtools will now be installed at /opt/schily

```
make
sudo make install
```

[*]Once successfully compiled, open K3b and select "Configure K3b" under Settings.  Go to "Programs" and click the "Search" button.  

You should see "cdrecord" as one of the programs listed and below it there should be a green check mark next to "/opt/schily/bin/cdrecord".  DON'T CLOSE OUT THE SETTINGS DIALOG BOX -- one more thing to do...


[*]Click on the "Advanced" icon in the Settings dialog box (might have to scroll icons down to see it).  Check the "Show advanced GUI elements" option.  Click OK to close dialog box now.


[*]When you go to burn  your BD-R disc, you must select two things above all in order for your burn to work.  First, change  "writing app" and select "cdrecord".  Second, under the Misc tab make sure you select "No multisession" (otherwise k3b will go back to using genisoimage/growisofs and you will encounter same problems).
[/LIST]

This worked for me on Ubuntu 12.10... hope it works for you!

---

### Post by jajodo on 2013-03-10
Thanks meesterblack.  Worked for me on 12.10 64 bit.  Was using Nero 4 but could only burn blu ray at 1x.  With K3B I burned at 6x with no issues :)

---

### Post by Azrael Nightwalker on 2013-06-10
> **ianni67 said:**
> The same here. Two different machines: ubuntu 10.04 and Kubuntu 12.04. The BD burner is a Samsung external (USB) Blu Ray burner model SE-506.

[EDIT]
I'm currently using Nero for Linux. It works perfectly with my burner but after more than 15 years of open source software for burning (k3B and cdrecord) this is frustrating.

I have the same burner and same problem.
I'm using Ubuntu 12.10.
I think I'll try NeroLinux...

---

### Post by Azrael Nightwalker on 2013-06-10
BTW: has anyone tried to file a bug about it?
I couldn't find any bug in Launchpad that would describe exactly this problem...

---

### Post by Azrael Nightwalker on 2013-06-10
Found the bug:
[https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/788322](https://bugs.launchpad.net/ubuntu/+source/dvd+rw-tools/+bug/788322)
Same bug in Debian:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661368](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661368)

---

### Post by ariel on 2013-06-10
Try using cdrtools from this ppa:

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

K3b started to work right away with blurays after I switched from ubuntu's cdrkit to cdrtools (before that, it would only burn BR coasters). I was also a frustrated nero linux user for years until I discovered this (nero linux stopped working for me in 12.10 for some reason anyways). I burned a lot of BRs with k3b+cdrtools and it has been rock solid. I use BRs for optical backups so this is important to me.

Unfortunately the guy behind the ppa didn't release the debs for 13.04, but if you are using 1204 or 1210 you should be fine.

p.s.: for 13.04, I tried downloading the CDRTools source and compiling (following the instructions in one of the first posts in this thread) and it just worked

---

### Post by Azrael Nightwalker on 2013-06-15
I did, and it worked (I'm on Ubuntu 12.10).
I was finally able to burn DVD+R DL correctly.

---

### Post by arloth on 2013-06-25
Meesterblack's fix on the first page worked for me..  I'm using Ubuntu 13.04.  I removed wodim initially when I started looking for a solution, but then recompiled and installed k3b per those instructions.  Works a treat now.  No more burning at the incorrect speed or erroring out at 99%.  Thanks much.

---

### Post by alexandre-css on 2014-03-09
After using this procedure, I'm finally able to write BD-R disks on my Ubuntu 12.04 with K3B.
Thanks a lot meesterblack.

---

