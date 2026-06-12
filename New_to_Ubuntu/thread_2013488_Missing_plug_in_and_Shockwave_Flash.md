---
title: "Missing plug in and Shockwave Flash"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by ericstrom on 2012-06-30
Seeing missing plug in where videos should be. I also see a message just below my bookmarks bar that says  ...the following plug in has crashed: Shockwave Flash.

Running Lucid Lynx and Chromium. 

I was running Chrome but ran into a problem with the latest upgrade so I installed Chromium and removed Google Chrome. To fix the problem with the missing plug in and Shockwave Flash, I've already removed Chromium and completely reinstalled. 

What should I try next ?

---

### Post by mikewhatever on 2012-07-01
Since you haven't mentioned installing the flash plugin, perhaps you could try that.

---

### Post by ericstrom on 2012-07-01
Sorry I didn't mention that in my post. The latest version of Flash Plugin Installer is installed and was re-installed. I did this through Synaptic. It shows version 11.2.202.236ubuntu0.10.04.1 if Flash Plugin installer.

What can I try next ?

---

### Post by sandyd on 2012-07-01
> **ericstrom said:**
> Sorry I didn't mention that in my post. The latest version of Flash Plugin Installer is installed and was re-installed. I did this through Synaptic. It shows version 11.2.202.236ubuntu0.10.04.1 if Flash Plugin installer.

What can I try next ?
There is no Shockwave for Ubuntu.

---

### Post by ericstrom on 2012-07-01
> **sandyd said:**
> There is no Shockwave for Ubuntu.

OK, well what does that tell me since I continue to get the message about Shockwave crashing ?

I also noticed some of the graphical elements are not coming up. Just getting black background with white figure where the element should be.

What do I try to get this resolved ?

---

### Post by lovinglinux on 2012-07-01
Shockwave is not the same as Shockwave Flash. To avoid confusion, keep in mind your problem is with Flash.

Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by ericstrom on 2012-07-01
> **lovinglinux said:**
> Shockwave is not the same as Shockwave Flash. To avoid confusion, keep in mind your problem is with Flash.

Try [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Is Flash Aid an add on for Firefox or does it work with Chromium ?

---

### Post by NikTh on 2012-07-01
> **ericstrom said:**
> Seeing missing plug in where videos should be. I also see a message just below my bookmarks bar that says  ...the following plug in has crashed: Shockwave Flash.

Running Lucid Lynx and Chromium. 

_**I was running Chrome**_ but ran into a problem with the latest upgrade so I installed Chromium and removed Google Chrome. To fix the problem with the missing plug in and Shockwave Flash, I've already removed Chromium and completely reinstalled
Same problem all the way.. 
[http://ubuntuforums.org/showthread.php?t=2013260](http://ubuntuforums.org/showthread.php?t=2013260)
[http://ubuntuforums.org/showthread.php?p=12065445#post12065445](http://ubuntuforums.org/showthread.php?p=12065445#post12065445)
[http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)
Google Chrome did the "trick"

---

### Post by lovinglinux on 2012-07-01
> **ericstrom said:**
> Is Flash Aid an add on for Firefox or does it work with Chromium ?

It only works on Firefox, but any changes made by it will affect Chromium as well.

---

### Post by ericstrom on 2012-07-02
Flash Aid didn't solve the problem. If anything, it made it worse. Getting the missing plug in and Shockwave flash crash messages all over the place now. 

Someone said that downgrading to an older version of Chrome worked.
 
"Downgrading to Google Chrome v91.0.1084.56 fixes the problem" 

I removed Chrome when I installed Chromium. So how could I go to Chrome v91.0.1084.56 ? Where do I get an old version ? What's the command to do it or could I do it through Synaptic ?

---

### Post by lovinglinux on 2012-07-03
> **ericstrom said:**
> Flash Aid didn't solve the problem. If anything, it made it worse. Getting the missing plug in and Shockwave flash crash messages all over the place now. 

Someone said that downgrading to an older version of Chrome worked.
 
"Downgrading to Google Chrome v91.0.1084.56 fixes the problem" 

I removed Chrome when I installed Chromium. So how could I go to Chrome v91.0.1084.56 ? Where do I get an old version ? What's the command to do it or could I do it through Synaptic ?

It won't make a difference going from Chromium to an older version of Chrome. Downgrading Chrome will only help if you are already using Chrome, to avoid the new PepperFlash. Chromium doesn't have PepperFlash.

Please click FLash-Aid menu, select Help, then Generate Report and paste the result here.

---

### Post by ericstrom on 2012-07-03
I couldn't just copy it because I kept getting an error message about too many tags or smiley faces. I tried to remove the tags and such but I still couldn't copy.

Hopefully the upload works

---

### Post by ericstrom on 2012-07-05
> **lovinglinux said:**
> It won't make a difference going from Chromium to an older version of Chrome. Downgrading Chrome will only help if you are already using Chrome, to avoid the new PepperFlash. Chromium doesn't have PepperFlash.

Please click FLash-Aid menu, select Help, then Generate Report and paste the result here.

Hello, I posted the report as requested. But I put it in a separate post. I am also attaching it here. Any suggestions on how to resolve this issue ?

---

### Post by dansang on 2012-07-09
Hi had the same problem on a friends pc! installed flash aid and ran the wizard! flash didn't work in either chrome,chromium or Firefox 13. download google-chrome-stable which never launched! 

Also downloaded the latest  tar.gz file from the the adobe website! extracted and copied the libflashplayer.so file to ~home/username/.mozilla/plugins...rebooted opened Firefox no change.

I thought the flash aid in Firefox would correct the problem for chromium/chrome!

Is the problem arising because adobe won't support flash for linux, although they are supposed to be maintaining it for older versions for 4 years.

Hopefully we'll discover the problem soon!

---

### Post by pyutaros on 2012-11-19
I didn't read the entire thread, so I apologize if someone already posted something like this.  I got tired of manually downgrading flash on every computer I use, so i wrote this script.  Save it to a your computer and remove the ".txt".  Make sure it's sent to run as an executable and then you can run it from a terminal by typing ./Adobe_fix.  Here is the code below:

```
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip
unzip fp_11.1.102.63_archive.zip
tar -xzvf fp_11.1.102.63_archive/11_1r102_63_32bit/flashplayer11_1r102_63_linux.i386.tar.gz -C fp_11.1.102.63_archive/
sudo cp -f fp_11.1.102.63_archive/libflashplayer.so /usr/lib/flashplugin-installer
```

---

### Post by mastergunner on 2013-01-29
Sorry to drag up an olf thread but does this work with non-sse2 cpu's?

---

### Post by tiggsy on 2013-01-30
I've run all the stuff in this post and still no flash in chromium.

I've also run the instructions linked to by Adobe because "flash is built in", but when you do about:plugins what you see is that in fact flash is NOT one of them

This is the Ubuntu standard issue so why has it been delivered incomplete?

---

### Post by mastergunner on 2013-01-30
I finally got flash to work last night in Chromium using the old version of Flash. Now the problem is choppy and slow play in flash.

---

