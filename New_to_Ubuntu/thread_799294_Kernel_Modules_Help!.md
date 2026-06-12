---
title: "Kernel Modules Help!"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by indiecast on 2008-05-18
would someone please explain to me how to install kernel modules (specificall webcam) on ubuntu 8.04!?!?!?!?!?!

ive looked all over and nothing makes sense and nothing works.


im running a fairly clean install and i dont see any reason why this shouldn't work

i had this same sort of problem  when trying to downgrade ati drivers in a previous ubuntu version

---

### Post by HotShotDJ on 2008-05-18
> **indiecast said:**
> ive looked all over and nothing makes sense and nothing works.

im running a fairly clean install and i dont see any reason why this shouldn't workThere's not much here for me to go on.  What have you tried that didn't work?  What is the make/model of the web cam you are trying to use.  I'd love to help, but I need more info.

---

### Post by indiecast on 2008-05-18
its a quick cam,  but im trying to install the gspca, qc-usb, and ov511 drivers and the module-assistant doesn't work and neither does trying make, make install manually

what exactly is a kernel module anyway?

why arent these drivers installed by default?

why isn't there an easy way to install these drivers?

---

### Post by axor1337 on 2008-05-18
Ditto we need more info if we are to try and help  
distro version
web cam model and brand 
what app are you going to be using it for
what have you tried so far

---

### Post by indiecast on 2008-05-18
i said 8.04 ubuntu

its a quick cam either a quick cam messenger or express idk for sure, doesn't really matter tho cause i can even install the drivers to see if it works!

i wanna use it with cheese or camorama or skype, mostly cheese cause i LOVEEE photobooth.

i tried it in cheese and i get no picture

ive tried using module-assistant to install drivers...nothing
ive tried make, make install...nothing
ive tried make all...nothing
everything i try...nothing

---

### Post by HotShotDJ on 2008-05-18
> **indiecast said:**
> its a quick cam,  but im trying to install the gspca, qc-usb, and ov511 drivers and the module-assistant doesn't work and neither does trying make, make install manuallyOk.  1st take a deep breath.  You haven't told us where you got these drivers that you are trying to install.  If you've just been downloading things off the internet, then there is a big problem with what you've been doing.  So lets back up a bit and see where we are.

1) Have you installed module-assistant using System --> Administration --> Synaptic Package Manager

2) Is build-essential installed (again, check through Synaptic)

3) For ov511, is ov511-source installed (again, check through Synaptic)

4) For qc-usb, is qc-usb-source and qc-usb-utils installed?

5) For gspca, is gspca-source installed?

Again, everything you need is in Synaptic Package Manager.  You should NOT be downloading kernel patches and module from the internet.

After you've checked these things, come back and we'll get things running for you.

---

### Post by indiecast on 2008-05-18
all of that is checked



nothing is downloaded off the internet, only through synaptic


seriously, ive folowed instructions, but it doesn't work

---

### Post by HotShotDJ on 2008-05-18
> **indiecast said:**
> all of that is checked

nothing is downloaded off the internet, only through synaptic

seriously, ive folowed instructions, but it doesn't workOk.  I was hoping that was the case.  But I felt it best to make sure we were both working from the same set of assumptions. :)

Lets start with ov511.  What happens when you run```
sudo module-assistant auto-install ov511
```Please post the complete output after you've run the command.

---

### Post by indiecast on 2008-05-19
from looking at error messages i have gotten in the past when trying to compile things, i have had a feeling ubuntu has a different kernel header than other linux distros.  im not sure tho, cause i have no clue what kernel headers are. all i know is i see that in errors alot


i had not tried auto-install before

output:
```

&#9474; Bad luck, the kernel headers for the target kernel version could   &#9618; 
     &#9474; not be found                                                       &#9618; 
     &#9474; and you did not specify other valid kernel headers to use.  

```

what are kernel headers?

where are my ubuntu 8.04 kernel headers?

and how do i specify to m-a where they are?

---

### Post by Shazaam on 2008-05-19
Do this in terminal...
```
sudo apt-get update
```
then run this....
```
sudo apt-get install linux-headers-$(uname -r)
```
The first code will update the package list. The second code will install the headers for you.

---

### Post by HotShotDJ on 2008-05-19
[QUOTE=indiecast;4991680```

&#9474; Bad luck, the kernel headers for the target kernel version could   &#9618; 
     &#9474; not be found                                                       &#9618; 
     &#9474; and you did not specify other valid kernel headers to use.  

```[/QUOTE]Kernel headers didn't get installed with build-essential?  That can't be right. Well.. lets check.  First, we need to know what kernel your using (probably generic, but lets be sure...) In a terminal, type uname -a

The first part is what we care about... here is mine: ```
2.6.24-16-generic
```So now, open up Synaptic Package Manager and search for linux-headers.  Mark for installation the one that matches the output of uname -a.

If they headers are already installed, I'll have to do some poking around to find what the problem is.

---

### Post by indiecast on 2008-05-19
synaptic says i have the headers


however, i noticed linux-source-2.6.24  was not installed so im installing it right now

does that have anything to do with it?

---

### Post by indiecast on 2008-05-19
also, build essential was installed when i looked.  i never manually installed it through synaptic or the terminal


also, should i re-install the linux headers?

---

### Post by HotShotDJ on 2008-05-19
> **indiecast said:**
> synaptic says i have the headers


however, i noticed linux-source-2.6.24  was not installed so im installing it right now

does that have anything to do with it?It could.  And there is no harm in installing it.  I've been reading some bug reports regarding the ov511 package.  Before we continue and, possibly, start pulling our hair out, lets verify the exact model of the webcam in question.  I'd hate to spend a lot of time with these things only to find out that the webcam isn't supported.  And if it IS supported, we could focus our attention on the correct package.

---

### Post by indiecast on 2008-05-19
how do i do that?

is it like lsusb -something   or something like that?

---

### Post by indiecast on 2008-05-19
i used it today in windows and its a quickcam messenger.  im not sure of its exact model.

how do i find this out?

---

### Post by HotShotDJ on 2008-05-19
> **indiecast said:**
> i used it today in windows and its a quickcam messenger.YEAH!!!  What good luck... we don't need to mess around with ov511.  The quickcam messenger uses qc-usb. Make sure the qc-usb-source is installed and then```
sudo module-assistant auto-install qc-usb
```With a little luck, that will go smoothly.  If not, post any error messages.

EDIT:  Ok... the above may fail (I did some research after posting).  But I found a solution.  Unfortunately, I don't have a quickcam messenger to test it out on, but I got the module to compile using Module Assistant without any errors.

If the qc-usb-sources from Synaptic Package Manger throws errors when you use module assist, then you will need to completely remove the packages:```
sudo apt-get autoremove --purge qc-usb-sources qc-usb-utils
```
Next go to [http://ftp.ceid.upatras.gr/pub/debian/pool/main/q/qc-usb](http://ftp.ceid.upatras.gr/pub/debian/pool/main/q/qc-usb) and download qc-usb-source_0.6.6-5_all.deb and qc-usb-utils_0.6.6-5_i386.deb.

After you download the files, double-click on qc-usb-source_0.6.6-5_all.deb and install it (You will get a warning about an older version being available in the repositories.  Just dismiss the warning)

Now, run:```
sudo module-assistant auto-install qc-usb
```As I said, this worked with no error on my system.  You should now be able to plug in your camera and have it work.  If so, go ahead and install the qc-usb-utils that you downloaded and have fun.

---

### Post by indiecast on 2008-05-19
alright! thanks!   i also found out today that i get an image from camarama in 7.10 on another computer w/o doing anything.  but not in cheese on 8.04. 


i figured it was qc-usb.  i was just going to install them all just incase.  so...im assuming ubuntu 8.04, or ubuntu in general does something funny with its headers and the defualt source files are edited to account for this.  so these new source packages must have been patched for ubuntu? 

what is the source of these source files i need to download?

how did you find them?

^^^i ask these questions so i remember for the future and to help other people and just to learn a little more about linux


EDIT:  Is is possible that the source in the repository is the wrong version for compiling with 8.04?

---

### Post by HotShotDJ on 2008-05-19
> **indiecast said:**
> what is the source of these source files i need to download?

how did you find them?

EDIT:  Is is possible that the source in the repository is the wrong version for compiling with 8.04?I actually Googled and found a bug report pertaining to the qc-usb package in Hardy.  According to the bug report, the error (changes in the kernel prevent package from compiling) was patched upstream (Debian) but it was too late to get into Hardy for the scheduled release.  So, I went upsteam.  The source of those files is the Debian maintainers.  Of course, when you do that, it sometimes doesn't work... which is why I made sure I tested it before I got your hopes up. :) Of course, I don't have the hardware, but at least I got the software installed.

---

### Post by indiecast on 2008-05-19
hooray!


lol 

thanks a bunch...ill be sure to try it. ive got to reinstall 8.04 though cause i wanted to reinstall winxp cause it was real cluttered. so i did that this morning and got rid of 8.04 just cause it was new and my partitions were all screwey.  now my partitions are great, i have a perfect xp install, and im planning on putting 8.04 on there tonight be4 bed.  i was actually thinking of trying fedora just to branch out, but i can seem to get the dvd to work.

so far ive had the best experience with everything in ubuntu and ive been using it since 6.10, then i stopped for a while and started up again with 7.10. ive been using it constantly on two computers since last december. i love it for the most part. there are a few things i would fix if i was a developer.

over :):):)

and u get thanked

---

### Post by indiecast on 2008-05-21
no luck with cheese : ( and i get a weird looking image from camorama. i tried installing ov511 from the same source site and that didnt work. i tried installing gspca, it installed but cheese still doesnt work.  i tried installing qc-usb-messenger, which is prolly the one i need, but it wouldn't compile either.  WHY DID UBUNTU SCREW WITH THE LINUX HEADERS!!!!!  I've heard Fedora is possibly the best linux os.  I'm going to try that this weekend.  If that doesn't work, I'll play around with Fedora for a while then i might come back to Ubuntu.  If the webcam doesn't work on anything,  I'll just use it in windows like i have been.  The only reason I really want it on linux is to use cheese and play around with other apps.  IM clients dont have video for the AIM protocol so I'd have to use that on windows anyway.  It seems to me that until manufacturers start making propritary linux drivers for specialize stuff like webcams, scanners, etc, these specialized things will just have to be used with windows.

---

### Post by HotShotDJ on 2008-05-21
> **indiecast said:**
>  i tried installing ov511 from the same source site and that didnt work. i tried installing gspca, it installed but cheese still doesnt work.  i tried installing qc-usb-messenger, which is prolly the one i need, but it wouldn't compile either.  WHY DID UBUNTU SCREW WITH THE LINUX HEADERS!!!!!I feel your frustration, indiecast.  Do you have any reason to believe that ov511 or gspca will do anything for you?  Have you made sure that the module is loaded (sudo modprobe quickcam, if I recall correctly)? Have you installed and worked with qc-utils to try to improve things?  Also, Ubuntu didn't screw with the linux headers... this was a change that the kernel-maintainers made.  It often takes time for the downstream packages to catch up with these kinds of changes.

I wish it were easier to get webcams up and running in Linux, but until the manufacturers of these little devils start cooperating with the Linux community either by providing proper drivers or providing the technical specifications to the kernel maintainers, we are kind of stuck.

---

