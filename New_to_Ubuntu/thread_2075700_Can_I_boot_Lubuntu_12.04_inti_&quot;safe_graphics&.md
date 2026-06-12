---
title: "Can I boot Lubuntu 12.04 inti &quot;safe graphics&quot; mode?"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-10-24
Running Lubuntu 12.04 Ppc on Mac G4 “Graphics” model 450 (450 Mhz, 20 GB hard drive, 1256 GB RAM).
  **        NOTE:  **Using a $5.00 used monitor from Salvation Army store
   
  [FONT=&quot][SIZE=3]I continue to struggle with an ongoing graphics problem with this computer. Boot-up to a usable desktop from either the live CD or a permanent installation only happens 50% of the time or less. The rest of the time, I just boot to a dark screen with a moveable cursor. I don’t have any problems with previous versions of Ubuntu; 10.10 Ppc works great on this box. I believe most of my problems stem from the 450 Mhz processor not playing nice with the newer kernel.[/SIZE][/FONT][SIZE=3]

[FONT=&quot]  After Googling around, I’ve surmised that maybe if I was able to boot into a “safe graphics” mode using xvesa at boot-up of the live CD, I might be able to get around this problem. The reason I think this is that in experimenting with an ancient Dell laptop where Lubuntu would not produce a usable desktop (severely distorted screen), I did have success with both Zorin Lite and Watt OS (both cut-down versions of Ubuntu) where a “safe graphics” mode was offered on the initial splash screen (didn’t know about the “F6” option at the time). I’d like to be able to try it in any case. I’ve also found some documentation here: [http://www.linuxquestions.org/questions/linux-newbie-8/xorg-vs-xvesa-653951/#post3314015](http://www.linuxquestions.org/questions/linux-newbie-8/xorg-vs-xvesa-653951/#post3314015)[/FONT][/SIZE]  [SIZE=3]      [FONT=&quot]and here: [http://ubuntuforums.org/showthread.php?t=1081398&highlight=booting+xvesa](http://ubuntuforums.org/showthread.php?t=1081398&highlight=booting+xvesa)[/FONT][FONT=&quot].[/FONT][/SIZE]
   
  [SIZE=2]The problem is, when I boot the powerpc live CD there is no initial splash screen with any boot options; it simply boots (eventually) to the live desktop. So I guess what I need to know is, is there a command I could enter at the initial boot prompt that would take me there? If not, where during the boot process would I press F6 the get to the boot options?[/SIZE]

---

### Post by powerpcliberation on 2012-10-24
This page will help you whether you have ATI or Nvidia graphics.  The ATI solution is much simpler.  
Link: [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)

I just realized you might still have the original Rage 128 card which the above solution won't help with.

From the [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues) page:

**ATI Rage 128**

 Users with a  Rage 128 graphics card will probably find they boot into a low graphics  mode (or a command prompt) with the live CDs ([bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/949288")).   For this reason, some users may prefer to install from the  alternate/mini ISOs.  The mini ISO will download the latest kernel  version which contains the fix. 

For  most users this bug should be fixed when you run the Update Manager.   Some users (e.g. those with a G3 iMac) may also have to create an  xorg.conf file setting HorizSync and VertRefresh values (see [PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F")). AGP users may also have to force PCI mode.   

If you need to install the latest kernel from a command prompt, then type the following: 
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot

If you would like to use the live CDs in full technicolor then there are two solutions to you.  Both require starting the CD in [single user mode]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_into_single_user_mode.3F").  You can configure an xorg.conf file setting "UseFBDev" "False" and "NoInt10" "True".  Instructions to do so are [here]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_configure_an_xorg.conf_file.3F").  Once configured, issue the command  
sudo start lightdmto start the desktop.  

The second solution is to disable the openfirmware framebuffer.  At the yaboot prompt type: 
live video=offb: off single

This  will freeze or give you a blank screen.  You will have to judge blind  when the machine has finished booting which can be longer than you  think.  

Type the command (you won't see what you type): 
modprobe aty128fb

Text should now appear on the screen.  You can now start the desktop with the "sudo start lightdm" command."

---

### Post by Javelin Dan on 2012-10-24
Thanks for the response. I'll try what you suggested as soon as possible (may not be tonight) and report back on my progress. 

I also found this buried in a thread - let me know what you think...

[I]"Yes,

         2 options[/I] [I]

1st [/I] [I]boot from recovery mode . Recovery mode is listed in grub menu . If you haven't grub menu at startup , then hold down the [Shift] key during boot until grub menu loads. 
 When you boot from recovery mode , at the opened window select "FailSafeX" . See if boots correctly in low graphics.

2nd option is from a LiveCd/Usb. [/I]  [I]Boot from there and "Try Ubuntu" . Then we must follow another method to mount your drive and find the affected files."

[/I]

---

### Post by powerpcliberation on 2012-10-25
> **Javelin Dan said:**
> Thanks for the response. I'll try what you suggested as soon as possible (may not be tonight) and report back on my progress. 

I also found this buried in a thread - let me know what you think...

[I]"Yes,

         2 options[/I] [I]

1st [/I] [I]boot from recovery mode . Recovery mode is listed in grub menu . If you haven't grub menu at startup , then hold down the [Shift] key during boot until grub menu loads. 
 When you boot from recovery mode , at the opened window select "FailSafeX" . See if boots correctly in low graphics.

2nd option is from a LiveCd/Usb. [/I]  [I]Boot from there and "Try Ubuntu" . Then we must follow another method to mount your drive and find the affected files."

[/I]

Those must be solutions for older Ubuntu because I have never seen them.  I know the methods I list work in Lubuntu 12.04 and 12.10.

---

### Post by Javelin Dan on 2012-10-25
powerpcliberation  -
   
  I had precious little time last night – a little after supper and a little before I went to bed, but here’s what happened. First, in my typical ADD fashion, I originally overlooked the link at the top of your post and didn’t see that till this morning. Good info there. I’ll probe to see which graphics card I have and report back. But here’s what I did do…
   
  I first tried the suggestion that I found in the thread I posted and holding down the shift key at boot did nothing other than to allow it to go through the boot process normally – no help there. I then tried entering the command *“**live video=offb: off single”* at the boot prompt. It was rejected and I got a message to the effect of “invalid command, no such directory found”.  Just curious, did “*sudo”* need to be precede that command?
   
   I then tried to boot up this cranky old machine. After the fourth attempt, I was rewarded with a visible desktop. I then opened synaptic, reloaded the repository, and did a complete update per the suggestion on your post. I had to leave this for a while as there was much to update, so I left to attend a meeting. Later after I got home, acting on nothing other than a hunch, I went into the monitor settings and changed the refresh rate to “Auto”. I then repeatedly rebooted it and got a desktop five times in a row. I can’t yet say with confidence that this is behind me, but it wouldn’t have booted each and every time before I tried that. At that point, the sand man was beating me to death so I gave up and went to bed.
   
  I will wait and watch and report back. If it did work, do I mark this thread as “solved” even though I didn’t really accomplish what I originally set out to do? Thanks.

---

### Post by Javelin Dan on 2012-10-25
Going back to my original question, after some more research it looks like if I can figure out how to boot into "Recovery Mode" I'll then see a choice to select "FailSafeX". I just need a clear tutorial on how to boot into recovery mode on this system.

---

