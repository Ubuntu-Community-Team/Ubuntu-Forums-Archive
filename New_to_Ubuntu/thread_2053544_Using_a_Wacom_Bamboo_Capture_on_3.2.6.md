---
title: "Using a Wacom Bamboo Capture on 3.2.6"
date: 2012-09-05
forum: New to Ubuntu
---

### Post by Shepherd of Wolves on 2012-09-05
I'm running Backtrack 5r3 on my laptop and, correct me if I'm wrong, I believe that pretty much means I'm running Ubuntu 12.04. The command "uname -r" produces just 3.2.6. 
 I bought a Bamboo tablet for an art class I'm taking and I'm having a rough time following Favux's HOW TO on the subject. Would someone help walk me through this?

---

### Post by Favux on 2012-09-05
Hi Shepherd of Wolves,

You're having trouble with compiling input-wacom?  Where are you getting stuck?  By the way input-wacom-0.16.0 has been released.  See the BambooPT HOW TO update on [post #1034]("http://ubuntuforums.org/showpost.php?p=12146782&postcount=1034").

---

### Post by DogMatix on 2012-09-05
> **Shepherd of Wolves said:**
> I'm running Backtrack 5r3 on my laptop and, correct me if I'm wrong, I believe that pretty much means I'm running Ubuntu 12.04. The command "uname -r" produces just 3.2.6. 
 I bought a Bamboo tablet for an art class I'm taking and I'm having a rough time following Favux's HOW TO on the subject. Would someone help walk me through this?

I have a Bamboo Pen & Touch that I use with Ubuntu 12.04 (3.2.0-29-generic-pae) and it worked out of the box. Although, I mainly only use it as a touchpad for my desktop rather than tackling any serious artwork. But as far as I have found it has most of it's functionality.

Is there a reason you need Backtrack? It just seems like a rather specialist distro.

---

### Post by Shepherd of Wolves on 2012-09-06
Oh hey Favux :)
Can I have a link to somewhere where I can download input-wacom-0.16.0? That sounds helpful and I can't find it. Post #1034 only had a link to 0.14.0.
Also, when it asks me to install the headers I don't know which one to get. Since my kernel is just 3.2.6, does that mean it's generic or do I have something different? 
I've followed those instructions (I guessed and installed the generic headers) and then rebooted. I've never gotten lsmod | grep wacom to produce any output whatsoever.

DogMatix, I'm glad to hear that you got is running on Precise. It helps give me faith that I didn't just waste $80 on this thing.
Backtrack's creators and a lot of it's users feel the same way, but Backtrack is kind of like a bare-bones version of Ubuntu. I've been running it on my laptop & my desktop for awhile now and have been happy with it. Granted it's not for everyone, I'm just hopelessly addicted to the command line. I tinkered with it and added some of Ubuntu's repositories so it's more of a hybrid now though.

---

### Post by Favux on 2012-09-06
Oops a typo.  I meant xf86-input-wacom-0.16.0 in case you wanted to update that too although it shouldn't be necessary.  And 0.17.0 was released yesterday.

You should be able to determine the needed kernel header by running **uname -r**.  Likely generic is correct.

On some systems the wacom.ko won't autoload which I'm guessing is your problem.  So you add **wacom** to the end of the list in the modules file in /etc:
```
gksudo gedit /etc/modules
```
and then restart.  You should see **wacom** in **lsmod** then.

You didn't install a Wacom driver dkms at some point did you?

---

### Post by Shepherd of Wolves on 2012-09-07
Okay, I added wacom to that list. I deleted everything else &  decided to start fresh so lsmod still doesn't show anything at the  moment. I didn't realize before (because I wasn't paying attention) that  when I entered "sudo apt-get install linux-headers-generic" I got the output: 
Package linux-headers-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-generic has no installation candidate

How do I go about getting this?

And yes, I did download a dkms earlier on but it didn't work and it made all kinds of things go wrong, so I got rid of it with an autoremove command. Is there anything else I need to do about that?

---

### Post by Favux on 2012-09-07
Well hopefully it is gone.  We may need to make sure of that.  As long as a dkms for a wacom.ko is active its wacom.ko will install blocking any wacom.ko you compile.

What is the output you get with **uname -r**?

---

### Post by Shepherd of Wolves on 2012-09-07
shepherd@bt:~# uname -r
3.2.6

---

### Post by Favux on 2012-09-07
It is looking like Backtrack 5r3 uses a non-Ubuntu naming convention for its kernel-headers.  So without the headers to build against the wacom.ko wouldn't compile.  But it sounds like you did end up with a compiled wacom.ko that you were able to copy into place.  Hmmm.  Could you check the directory the copy command should have put it in and see if there is a wacom.ko there?  And is the date the same date as when you compiled?

It is hard to imagine Backtrack 5r3 doesn't have provision for compiling kernel modules.  Some where there must be an example of someone doing that.  That should tell us what the naming convention is.   Or it should be in the documentation somewhere.  Or perhaps you can look at a list of kernel packages and see if a headers is in there?

---

### Post by Shepherd of Wolves on 2012-09-07
That makes sense. Backtrack's kernel has apparently been tweaked to further its purpose.
Does this have any relevance:   [http://www.backtrack-linux.org/wiki/index.php/Preparing_Kernel_Headers](http://www.backtrack-linux.org/wiki/index.php/Preparing_Kernel_Headers)

I installed input-wacom-0.14.0's wacom.ko again ignoring the bit about the headers. I checked the wacom.ko directory and it had just been modified. I rebooted and lsmod still gave me no output.

How do I find out if the dkms is still having an effect?[SIZE=3]
[/SIZE]

---

### Post by Shepherd of Wolves on 2012-09-07
Also when I run "./configure --prefix=/usr", 

WARNING: Symbol version dump /usr/src/linux-source-3.2.6/Module.symvers
           is missing; modules will have no dependencies and modversions.

ends up in with all the other output. I'm assuming this isn't normal, am I right?

---

### Post by Favux on 2012-09-07
Right, that isn't normal.

If I follow your link to the backtrack-linux.org's wiki page on "BT5 kernel sources" correctly then you need to follow its instructions to get their version of headers.

Apparently prepare-kernel-sources is a script or some such.  And it looks like you are suppose to run eveything as root.  So if you have sudo first run the script:
```
sudo prepare-kernel-sources
```
Then change directory to /usr/src/linux:
```
sudo cd /usr/src/linux
```
Now copy recursively whatever the script generated in include/generated/ into include/linux/:
```
sudo cp -rf include/generated/* include/linux/
```
And I guess you now have their equivalent of kernel headers.

---

### Post by Shepherd of Wolves on 2012-09-08
Well...I was about to say "Okay now I have the headers, what about this Module.symvers thing?" and then the power cord fell out of my battery-less laptop and when I restarted my tablet worked! :D
Now I just have to enable it in Gimp and get used to the feel of it!
Thank you Favux, you've been truly awesome.

---

