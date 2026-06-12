---
title: "Problem installing Adobe Reader"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-15
I've been trying to install Adobe Reader in Ubuntu 7.10 using the terminal. Keep getting the following error:

jacatone@eMax:~$ sudo aptitude install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  acroread 
The following NEW packages will be automatically installed:
  gcc-3.3-base libstdc++5 
The following packages have been kept back:
  gdebi gdebi-core 
The following NEW packages will be installed:
  gcc-3.3-base libstdc++5 
0 packages upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 30.0MB of archives. After unpacking 75.0MB will be used.
The following packages have unmet dependencies:
  acroread: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
acroread [Not Installed]

Score is -9879

Accept this solution? [Y/n/q/?] y
The following packages have been kept back:
  gdebi gdebi-core 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
jacatone@eMax:~$ 

I guess it's hung up on another program I tried to install called gdebi. Anyone know how to fix this? Thanks.

---

### Post by Xiong Chiamiov on 2008-05-15
I think that you've marked gdebi and gdebi-core for holding at their current version, though I can't tell for sure.  Have you tried
```

sudo apt-get update; sudo apt-get -f; sudo aptitude install acroread

```

---

### Post by ZabiGG on 2008-05-15
Well, from what I read in your post, the package is "broken" (too full of bugs) and your system plainly refused to install it. Asked if you wanted to put your request on hold for a while until the package is no longer broken.

You answered yes, so it should install at some point...

If it's just a PDF reader you need, there are many great alternatives.

Tell me what you need, I can probably help. I've tried a lot ;)

---

### Post by ubunu on 2008-05-15
..."I've tried a lot"

In that case is [http://www.foxitsoftware.com/pdf/desklinux/](http://www.foxitsoftware.com/pdf/desklinux/) any good?

I have it running fine on windows so just wondered if it would break anything?

---

### Post by ZabiGG on 2008-05-15
if you want something light and uncomplicated, might be a good option ;) I can't give you an expert opinion on stability, but it has worked nicely on my computer. No problem so far.

Cheers,

---

### Post by jacatone on 2008-05-15
Used Update Manager and it downloaded and installed gdebi, although I can't seem to find it in the Appz menu or using Alt/F2. Anyone know how I would launch this thing?

---

### Post by ZabiGG on 2008-05-15
I've never launched it via the menu. It appears automatically when I try to download deb packages from Firefox or Opera...

Sorry I can't be of more help on this.

---

### Post by drs305 on 2008-05-15
> **jacatone said:**
> Used Update Manager and it downloaded and installed gdebi, although I can't seem to find it in the Appz menu or using Alt/F2. Anyone know how I would launch this thing?

You should just be able to type gdebi or gdeb-gtk. You can find the location of most programs by typing:
```
whereis program_name
```
This is a good command to find the program for creating shortcuts or terminal launches (obviously).

By the way, you aren't on a 64 bit machine with acrobat, are you?

---

### Post by ZabiGG on 2008-05-15
Cool tip ;) Thanks!


Z.

---

