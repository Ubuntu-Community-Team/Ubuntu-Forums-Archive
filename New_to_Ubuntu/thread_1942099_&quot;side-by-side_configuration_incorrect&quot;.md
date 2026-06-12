---
title: "&quot;side-by-side configuration incorrect&quot;"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by nbcormier on 2012-03-16
First time downloading/installing ubuntu.  Using windows 7.  After downloading from website, an error box comes up and says 'failed to start...side-by-side configuration incorrect' so im stuck there.  i selected to download w/out the 'wubi', what is the difference?  i chose to not download through windows because i want a true dual boot, is that the difference between a straight download and using wubi?

any help or advice would be very appreciated, thanks!

---

### Post by grahammechanical on 2012-03-16
I am sorry but you have confused me.

We speak of downloading a Ubuntu ISO image and then burning it to a CD/DVD or USB Memory stick to create a live CD/DVD/USB memory stick version of Ubuntu that we then boot from. We then get an option to try Ubuntu or Install it to the hard disk.

When we select Try Ubuntu the operating system runs from the CD and in the computer's memory. It does not make any changes to the hard disk. In this way we test to see if Ubuntu works on our machine and is to out liking before we install it to the hard disk.

We only get the install side by side option if we have chosen to install Ubuntu instead of trying it and there is another operating system present on the hard disk.

So, this comment does not match my experience of installing Ubuntu.

>  After downloading from website, an error box comes up and says 'failed to start...side-by-side configuration incorrect'

We do not go from downloading the Ubuntu image from the web site to a side by side install without first burning the Ubuntu image to the CD and then booting from it. If we do not understand your situation correctly we may give inaccurate information. 

Have you run Ubuntu in the Live CD Try Ubuntu Mode. Were there any problems?

Wubi is a method of using Ubuntu inside Microsoft Windows. You install Wubi and with it Ubuntu just as you would any Windows program. There are instructions on the Ubuntu web site on how to do this. It may seem that you are dual booting into Windows and Ubuntu but you are actually loading a Windows program.

The purpose of a Wubi Ubuntu install is to give Windows uses a working taste of Ubuntu without modifying the hard disk in a serious manner. It is not intended that Wubi/Ubuntu be used for any length of time.

A straight hard disk install of Ubuntu actually puts the Ubuntu operating system on to the hard disk. If you want, or to put it another way, if you are not careful, you could install Ubuntu and in the process remove completely any other operating system on the computer.

Regards.

---

### Post by nbcormier on 2012-03-16
Thanks for the response.  To be more clear, I ran into this problem from this stage:

I went to the download page on the ubantu website.  I selected "Download and Install" from the 3 options (including "Run it with Windows").  From there I clicked the orange box to download and ran the default option "corel" (i suppose this is my computers cd-burning application".  Then the usual green bar download was in progress.  Finally, minutes later when it finished downloading, when I click to open the ubuntu file, this error box showed up.

I assumed once/if I could open that file, I could then burn it to my cd, then restart the computer to actually install ubuntu.  However, the downloaded file "fails" to open.

I hope this has clarified the issue a little better.
Thanks.

---

### Post by critin on 2012-03-16
> **nbcormier said:**
> Thanks for the response.  To be more clear, I ran into this problem from this stage:

I went to the download page on the ubantu website.  I selected "Download and Install" from the 3 options (including "Run it with Windows").  From there I clicked the orange box to download and ran the default option "corel" (i suppose this is my computers cd-burning application".  Then the usual green bar download was in progress.  Finally, minutes later when it finished downloading, when I click to open the ubuntu file, this error box showed up.

I assumed once/if I could open that file, I could then burn it to my cd, then restart the computer to actually install ubuntu.  However, the downloaded file "fails" to open.

I hope this has clarified the issue a little better.
Thanks.

Is this the page you downloaded from?

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)



I've never seen instructions say [B]"Download and Install" 
[/B]>  From there I clicked the orange box to download and ran the default option "corel"The iso must be downloaded completely before it can be burned.   Don't open the downloaded files,  open the cd burner and choose to burn the iso from there.  Note where the iso was saved so you can browse to it.

Instead of choosing a program to open with, press SAVE when the download screen pops up.

It usually takes longer than "a few minutes" to download, even with a torrent.

---

### Post by nbcormier on 2012-03-16
critin:

yes, that is the page I'm downloading from.  thanks, i just tried to open "corel" (which ive never used) and the same error box came up as before.  maybe the error is associated with the corel program.  i am currently attempting to download again, but this time using windows media center.  thank you for the tip about going directly to the cd-burner, I hope it works this time.

---

### Post by critin on 2012-03-16
> **nbcormier said:**
> critin:

yes, that is the page I'm downloading from.  thanks, i just tried to open "corel" (which ive never used) and the same error box came up as before.[COLOR=Red]**  maybe the error is associated with the corel program.  i am currently attempting to download again, but this time using windows media center**[/COLOR].  thank you for the tip about going directly to the cd-burner, I hope it works this time.

[COLOR=Red]No.[/COLOR]

As long as you choose Save when choosing to download, you should be fine.  It seems like you're choosing corel/cd burner when downloading and expected it to install--iso's just don't work that way.

---

### Post by nbcormier on 2012-03-16
> **critin said:**
> [COLOR=Red]No.[/COLOR]

As long as you choose Save when choosing to download, you should be fine.  It seems like you're choosing corel/cd burner when downloading and expected it to install--iso's just don't work that way.


I saw your edit and did switch to "save" option before downloading.  Sorry, I may not be explaining everything in the best manner, but I do understand that i must burn the ISO image onto a disk or usb to install.  as of right now i am burning the iso image onto a cd.  so i may have gotten past the original problem (thanks again), but i do have another question:

I was viewing several tutorials prior to this, and most instructed the viewer to go into "disk management" and shrink the c drive (or wherever windows was being stored).  i went ahead and did that several hours ago in preparation for the install.  i shrunk the c drive by about 28 GB.  First, was this completely wrong to do?  if not, what other steps do i need to take with respect to hard drive management (partitioning?).

---

### Post by bodhi.zazen on 2012-03-17
See this link: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Basically you save the ubuntu desktop .iso on your Desktop (or wherever you wish). Then you either burn it to a CD or if you prefer make a bootable flash drive with it.

CD : [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Flash Drive : [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You then back up your data , boot the CD or Flash drive, and follow the guide.

---

### Post by critin on 2012-03-17
Hi, I really hesitate to speak on partitioning Windows, it's too easy to lose the OS.  I've never partitioned a Windows disk.

prepare the free space partition using Gparted in the live cd.  Use the Try option when booting into the cd and find gparted there.

Wait for experts to advise or find some tutorials in the forums.

Be careful.

---

### Post by nbcormier on 2012-03-17
Thanks, so it is not necessary to go into disk management on windows before install?  So when I boot ubuntu and select dual boot, it will basically do the partitioning for me (more safely im sure)?  I just want to be sure that ubuntu is completely separate from windows.

Side note:  i downloaded the 32 bit ubuntu, and i just realized my system is 64 bit...does that matter, or it is more optimal to have downloaded the 64 bit ubuntu?

---

### Post by bodhi.zazen on 2012-03-17
> **nbcormier said:**
> Thanks, so it is not necessary to go into disk management on windows before install?  So when I boot ubuntu and select dual boot, it will basically do the partitioning for me (more safely im sure)?  I just want to be sure that ubuntu is completely separate from windows.

Side note:  i downloaded the 32 bit ubuntu, and i just realized my system is 64 bit...does that matter, or it is more optimal to have downloaded the 64 bit ubuntu?

I would advise you use 64 bit ubuntu. 

IMO it is best to resize your windows partition from within windows.

back up your data before you begin.

---

### Post by Mark Phelps on 2012-03-17
> **nbcormier said:**
> Thanks, so it is not necessary to go into disk management on windows before install? 
YES ... is IS necessary to use Win7 Disk Management to shrink the Win7 OS partition -- unless, you don't care about Win7 getting corrupted and not booting anymore.
> So when I boot ubuntu and select dual boot, it will basically do the partitioning for me (more safely im sure)?
The "more safely" way is to use Win7 Disk Management.  The Linux partition managers will allow to to shrink Win7 as much as you want --even if the result damages the Win7 filesystem.  Win7 will restrict the shrinkage to prevent such problems.

---

