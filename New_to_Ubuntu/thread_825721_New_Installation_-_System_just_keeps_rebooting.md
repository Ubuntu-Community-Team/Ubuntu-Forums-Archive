---
title: "New Installation - System just keeps rebooting"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by mreyeros on 2008-06-11
Good morning I am totally new to ubuntu/linux and am havinga hard time just starting up my system.  I was able to successfully install the new distribution from the alternat install cd.  My system specs are as follows:

Soyo K8 USA Dragon Ultra MotherBoard
AMD Athlon 64 3400+
2GB RAM
NVidia GEForce FX 5700 LE 256MB (AGP)
Soundblaster Audigy 2 Sound Card (PCI)
2 x 80 GB Seagate Barracuda HD
CD-RW
DVD-RW

I am not sure what could be the cause, this system setup is quite a few years old but the only thing that I can think of is a driver issue.  Either the video card or the sound card.  Sometimes the system will get all the way to the login screen and enter and then a few seconds later it will reboot.  Other times it does not make it to the login screen.  I had the same issue with this box when I orignally had Windows Vista Installed and found out that it was my video card and the NIC.  I swapped those out for new ones and it worked fine.  I also have another video card an ATI Radeon (not sure the model #) off hand.  BUt have tried with this card to no avail.  Any help would be appreciated.

Regards,
Michael Reyeros

---

### Post by wpshooter on 2008-06-11
First option:  Check integrity of Ubuntu CD by running the verification function that is found on the initial Ubunut boot screen menu.

Second option:  Try installation using safe graphics mode.

Third option:  Download, burn and use ALTERNATE CD version (text based) of Ubuntu to perform the O/S installation.

Good luck.

---

### Post by mreyeros on 2008-06-11
> **wpshooter said:**
> 
First option:  Check integrity of Ubuntu CD by running the verification function that is found on the initial Ubunut boot screen menu.
**This was the first thing that I did when I downloaded the cd from the site.**

Second option:  Try installation using safe graphics mode.
**This I have not done.**

Third option:  Download, burn and use ALTERNATE CD version (text based) of Ubuntu to perform the O/S installation.
**This is how I installed the O/S**
Good luck.

Any other help would be appreciated.

---

### Post by mreyeros on 2008-06-11
I know that there are others experienceing random reboots as well.  Do you guys think that it is a hardware issue and that I need to change some parts or should I just try installing the 7.10 version instead of the 8.04 version?

---

### Post by lukelongbeard on 2008-06-11
> **mreyeros said:**
> I know that there are others experienceing random reboots as well.  Do you guys think that it is a hardware issue and that I need to change some parts or should I just try installing the 7.10 version instead of the 8.04 version?

I'm having the same issue WITH 7.10.

---

### Post by mreyeros on 2008-06-11
Can anyone lend a hand on this issue?

---

### Post by wpshooter on 2008-06-11
Mreyeros:

Sounds like to me that you probably did the "SUMCHECK" of the downloaded ISO, BUT did you actually run the CD integrity function that is found on the **INITIAL UBUNTU BOOT SCREEN MENU **?

---

### Post by mreyeros on 2008-06-11
I downloaded the ISO mounted the image to a CD booted my box with the cd and ran the cd check from the ubuntu startup menu.

---

### Post by mreyeros on 2008-06-11
I know that this box is around 4-5 years old but I did not think that I would have this much trouble installing the O/S.  I have seen some other posts that mention that reboots could be caused by a number of hardware related issues, one being the power supply.  I may try swapping the power supply but is there any way that I can try to rule out hardware related issues.  I did mention before that something similar happened when running vista on this same box and that is the only thing that tends to lean me more towards a hardware issue than software.

---

### Post by wpshooter on 2008-06-11
I would boot the machine to the Live Ubuntu CD and choose the option to run memtest.  If it reboots while it is running that then you can pretty much conclude that it is a hardware problem.

You could also make yourself a WIN98SE bootable diskette and boot to it and let the computer run and then if it reboots/turns off, then you pretty much know you have a hardware problem.

Good luck.

---

### Post by mreyeros on 2008-06-11
Yesterday before I left the house for work I left the computer running the memtest when I got home the memtest was still running (at least 8 hours) and had gone through 23 passes with no errors.

---

### Post by wpshooter on 2008-06-11
Then, that being the case, what I would do is get [www.killdisk.com](www.killdisk.com) and WIPE that hard drive completely clean (this is assuming that you don't have anything on it that you need to save) and then I would attempt a fresh installation of Ubuntu from a verified copy of the ALTERNATE version of Ubuntu.

Good luck.

---

### Post by mreyeros on 2008-06-11
Thanks WPShooter I will give that a try when I get home in a bit and will post back again with my findings

---

### Post by mreyeros on 2008-06-11
oooh one question how would I currently run this application against my hard drive(s)????

---

### Post by mreyeros on 2008-06-11
I am running the killdisk app now against my drives and will attempt reinstall after it completes I also ran a checksum on the 64bit alternate cd that I downloaded and the hashes are the  same.  I will make sure to run the cd check utility at the ubuntu menu also when I am able to reinstall

---

### Post by mreyeros on 2008-06-12
ok I finally finished the install late last night after running the killdisk app.  The one thing that I noticed right away was that the installation took alot longer than the last time I ran it.  I was abl to log into the system once and then the crashes started again.  The system does not stay up for more than 5 minutes and it crashes and reboots.  I have also had instances where it just simply hangs on the desktop.  It also seems to be alot slower than the last time that I installed it.  When logging in it takes almost 30 seconds to see the taskbar and the desktop background and even here the tribal drums.  I just about to give up on this and just reformat and reinstall my vista os.  I did not think that it would be this hard to get this os up and running.  Any further assistance would be great.

---

### Post by mreyeros on 2008-06-12
Please Please Please, any further assistance from the community would be great.

---

### Post by mreyeros on 2008-06-12
Good morning everyone I have been trying to get assistance for just a few days now and am totally down.  I tried to install the 8.04 distro and my box just continuously reboots you can check out this thread that I started in the Installation and Upgrade forum but have not had any luck:
[http://ubuntuforums.org/showthread.php?t=825721]("http://ubuntuforums.org/showthread.php?t=825721")

Any help would be appreciated, I would really like to continue learning linux/ubuntu since I have never had the chance to play around with either, coming from a totally microsoft development background.  I thought it would be cool to play around with and learn something new.

Regards,

Michael Reyeros

---

### Post by BDNiner on 2008-06-12
Do you have temperature monitors in your BIOS? The PC could be shutting off because it is overheating. Your hardware specs indicate that you should run ubuntu with little problems. So i would look at the actual hardware to detemine what is causing problems. Do you have a PCI network card installed?

---

### Post by milton1 on 2008-06-12
Can you please list your hard drive partitions and formats?

---

### Post by Linux_Man on 2008-06-12
Have you tried to boot it in failsafe mode? If Ubuntu is the only OS on the computer GRUB defaults to having you press ESC to open up the menu.

---

### Post by forger on 2008-06-12
While grub boots up, try pressing the "Esc" key,
choose Ubuntu 8.04 (**recovery mode**)

This should get you in a safe environment, try executing: **dmesg**
Or you could check out the log files in /var/log/ such as:
> /var/log/messages
/var/log/dmesg
/var/log/kern.log
/var/log/Xorg.0.log


you can check them out with the more command, i.e.: more /var/log/messages
(space jumps page, enter jumps line, q quits)

look for segfault or error or something like that

---

### Post by mreyeros on 2008-06-12
BDNiner, yes I have a Linksys PCI NIC installed in this box.  I also have an onboard integrated LAN but i think that I disabled it when I was running vista on this same box because it was giving me trouble in vista.

---

### Post by mreyeros on 2008-06-12
Milton1, in terms of my hard drive partitions I simply formated both drives that I have and then created the starndard partitions on both drives

---

### Post by BDNiner on 2008-06-12
If the onboard network card functions then i would remove any unnecessary devices and reinstall ubuntu using the alternate cd.

---

### Post by mreyeros on 2008-06-12
so after removing the NIC you would recommend a full reinstall?  Do you think that any other hardware could be causing this reboot issue?  Or is my hardware nothing out of the ordinary that it would not play nice with ubuntu?

---

### Post by BDNiner on 2008-06-12
Yes your hardware should work perfectly with ubuntu. The only two things that i can see being a problem is a hardware issue. or an issue with the cd image you downloaded.

I do recommend a full reinstall with a newly downloaded alternate cd. Verify the md5 checksum before you burn the ISO to make sure there are no problems with the image. In fact if you had k3b burning software installed it does verify the checksums for you.

---

### Post by mreyeros on 2008-06-12
Actually as suggested by another community member yesterday, I did run the mdChecksum for windows against the ISO image that I had downloaded and the hashes matched what was posted on the ubuntu hashes page.  I also checked integrity of the disc from the main ubuntu cd menu and all seemed fine as well.  but if you suggest another download and burn then I will give it a try.  I have never been one to give up easily and am really looking forward to getting my feet wet in the linux world.  What do you make of the slow system performance after I installed yesterday?

---

### Post by jasontu on 2008-06-12
I am very new to Linux myself, but if any system, regardless of OS, were doing this to me, temperature would be the first thing I would look to.  

Particularly if the system crashes at slightly different points...  If it were a software bug I would think it would more likely crash at a consistent point.  Something could be overheating, fans could be getting blocked, who knows.

Alternatively your harddrive may have issues that your tests can't reveal.

---

### Post by BDNiner on 2008-06-12
This is a very unusual case. From the hardware you listed there should be no problems whatsoever. Unless some of the hardware is defective. 

If you already verified the checksums then the cd is fine. are you installing the i386 version or the amd64 version?

---

### Post by mreyeros on 2008-06-12
I installed the AMD64 bit version.  But I guess I could try the i386 version as well.

---

### Post by mreyeros on 2008-06-12
What would be the best way to test to see if any one particular piece of hardware is failing?

---

### Post by BDNiner on 2008-06-12
Check the temperatures that the devices report in the BIOS. the closer things get to 90 degrees C the greater your chances of hardware failure and permanent damage.

---

### Post by mreyeros on 2008-06-12
Ok I just had my sister check my BIOS temps and this is what she saw:
CPU Temp External     43 deg. Celc    109 deg. Fahr
Chassis               36 deg. Celc    98 deg. Fahr
CPU Temp on Dye       59 deg. Celc    138 deg. Fahr

Is this considered high my colleague here at work has a macbook that the CPU temp is at 57 deg. Celc and it is running fine?

---

### Post by BDNiner on 2008-06-12
Yes those are within normal. This one has me. I  don't know what else could be causing you issues? are you able to boot to the terminal with out it restarting?

---

### Post by mreyeros on 2008-06-12
if by the terminal you mean the recovery mode then yes and it does not restart at all.  I even ran the apt-get update to grab the initial 158 updates after installation from the recovery mode root

---

### Post by BDNiner on 2008-06-12
Oh ok, then it is probably an issue with the GDM installation. There are ways to reinstall Gnome Desktop Manager but i don't know how. if it was my computer i would try and reinstall one more time.

---

### Post by mreyeros on 2008-06-12
Should I run the killdisk application again to write 0's to the harddrive or should I go out and get a new hard drive?

---

### Post by fenian on 2008-06-12
It could also be a PSU(power supply) problem.Sometimes when the power supply begins to fail it can be hard to know because the computer will still turn on but as it begins to work harder the failing power supply begins to malfunction resulting in crashes,freezes and reboots.A few telltale signs of a failing PSU are if the fan in the PSU is not spinning (if its not it need to be replaced),a faint electrical smell kind of like burning plastic as well as the crashing,freezing and reboot problems.
If you have access to another power supply you could replace the suspect one with it to test if this is the problem.

---

### Post by mreyeros on 2008-06-12
I have seen that suggestion on other posts as well regarding a failing PSU.  I may give that a try as well and maybe drop a few bucks on a bigger harddrive while I am at it.

---

### Post by mreyeros on 2008-06-12
Any other suggestions out there in the community based on my details of the problem.  I do not have a problem with reinstalling the o/s as many times as is needed :)

---

### Post by mreyeros on 2008-06-12
Now I am really going to freak out I purchased a new PSU and new harddrive and still am getting reboots, did a full installation to no avail.  I am pulling my hair out.  Not sure what else to do, can anyone help me?:confused:

---

### Post by mreyeros on 2008-06-13
I take my last comment back an even more terrible thing has happened I think that I fried my memory.  I was trying to work out this problem till late last night and tried reseating all of my hardware and I guess I was not paying attention and reseated my memory in the wrong direction and of course I try to boot and start to smell burnt plastic and the box just goes crazy.  I powered down reseated the memory correctly and now the box does nothing.  Why Ubuntu Why?????????????????:(

This blows, i just dropped $200 on the harddrive and the PSU and now I need to go get more memory and hopefullly its just that and not the mobo.  This hurts.

---

### Post by BDNiner on 2008-06-13
I am sorry to hear that. You may have damaged the motherboard. Is the physical damage only one the memory or also on the memory slots? Don't worry too much about it. I destroyed a computer also when getting started with linux.

---

### Post by mreyeros on 2008-06-13
So would you say that I have totally hosed this computer and it is probably not worth replacing the memory?

---

### Post by BDNiner on 2008-06-13
I would not reuse that motherboard until you can determine what melted. so yes it could be totally hosed.

---

### Post by mreyeros on 2008-06-13
Thanks alot BDNiner, you have been a great help. I guess my computer parts adventures will now being and will be back with more questions probably next week when I try to reinstall again.

---

### Post by forger on 2008-06-15
> **mreyeros said:**
>  Why Ubuntu Why?????????????????:(
It wasn't Ubuntu's fault you weren't careful...:KS

Sorry for the hardware, I was feeling the same way when one day I shutdown my computer and couldn't turn it back on :(

---

