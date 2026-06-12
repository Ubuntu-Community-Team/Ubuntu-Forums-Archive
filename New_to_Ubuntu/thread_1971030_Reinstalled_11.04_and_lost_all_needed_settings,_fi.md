---
title: "Reinstalled 11.04 and lost all needed settings, files, etc."
date: 2012-05-02
forum: New to Ubuntu
---

### Post by crazybear on 2012-05-02
Only a newbee [as I] could make such a horrible mistake. I thought it would only put in the OS files - and not remove all the: history, configuration files etc. [they were done by an expert over many weeks - and he is now not alive]....so, I have a system that won't configure my 3 screens; won't configure the ATI ccc driver, won't print and several other long-fought configurations are gone - as is history, which would allow me to re-create his fixes. However, I think all is not lost....I made a copy of the system and it is on another disk [now seen as /dev/sdb1]. On it there is a file /boot/initrd.img-2.6.38-13-generic [and all the other versions I had had installed] that I THINK I need to copy/move/unpack? to my main system and all will [?] be OK?!?!?!?!? BUT - I: 1] don't know how and 2] if I should...though it seems I should. What else might I have to move [and how to do so]?

Please help and PLEASE do NOT assume I know anything..I'm really a beginner at this...or I'd not have made the mistake! Please tell me step by step and ask anything / tell anything that could make the above more of a problem than a solution. Many thanks! The only difference between the 'old' copied system and the new is the addition of Ubuntu studio [which I think will not make a difference -but don't know].

NB - I think trying to configure the ccc again [it took an expert DAYS] would take me months, so not up for that if it can be avoided. Ditto making printer [Cannon MP  540] and several other devices. It seems now only the configurations for these devices are gone....]

NBB - and while I'm at it...during some update 2.6.38-14 was installed, but it says 'virtual' after it and it doesn't boot...what is that?! I move down to the 13 and it boots..or did...now it only boots in low video mode [or seomething like that - I'm in Windoz now]
-------------------------------
Looking further, in the copied [about a month old] Grub files are: 
abi-kernal#
config-kernal#
initrd.img-kernal#
System.map-kernal#
vmcoreinfo-kernal#
vmlimuz-kernal#
files.....
Question, How and which [all?] of these do I move back to my main device/OS - and what dangers precautions need be taken into account? Thanks much!

--------------------
With more hunting I found the copyied [month old, but all needed changes were before then!] history file!....but am not very confident about how to move it into my system in sda1 or if it will cause problems with what is there...nor how to execute the commands where they are - if possible. I have printed it out [30 pages]. There is also a .bashrc file that from its size seems important. Now what do I do?! This is my trial by fire.....I'll be intermediate after this!

Even more hunting [have edited this many times over several hours!] I find that when I was asked for my user name I made a slight punctuation/spacing difference and some [not all] of the old files that used to be in my old account are still there...now it is even more confusing [to me] how to reconstruct things...but maybe not....don't know. Would REALLY appreciate the help. I'm really missing using Ubuntu...!!!!!!

---

### Post by crazybear on 2012-05-04
Well, I've made a little progress in getting the driver for my ATI video partly working [got the three screens as one, but ccc won't change color except on one - minor compared to my other problems!.....but still don't know how to move things back from my copy [and what would and what could cause problems]. The printer still doesn't work. Strangely, the system now won't let me in with the correct [sic] password.....I did NOT change it and there is only one account. I see a fix for getting in without one and resetting it, which I'll try. **_I sure could  use some help here!_**

---

### Post by SuaSwe on 2012-05-04
Hi crazybear,

That's quite a situation you've got going there! To begin with, I wish to query this quote:

> 
Even more hunting [have edited this many times over several hours!] I find that when I was asked for my user name I made a slight punctuation/spacing difference and **some [not all] of the old files that used to be in my old account are still there**...


Do you mean that some files belonging to the user with the spelling you had before the install still exist? This would suggest to me that you never actually formatted the /home partition, or else there should be no files belonging to that user in there.

Could you do the following in Terminal as root:

```

df -h
ls -l /home

```

.. and post the output here? Cheers!

---

### Post by SuaSwe on 2012-05-04
Just edited my message above - "ls -lR" will give a huge output if you still have lots of files under your previous user; might be worth you pasting "ls -l /home" to us (just to see what users are present) and running "ls -lR /home" as root yourself, which should show you what directories and files sit under each user.

---

### Post by crazybear on 2012-05-04
WOW Cowboy! I can't get to a terminal screen! I tried using something I found on the internet, but it didn't work for me. I hit Escape at Grub prompt - nothing happened. I hit e and got miniscule letters just at my ability to read white on gray and I can't read them. I was told to enter rw init=/bin/bash and I'd be able to log on without a password [my system has somehow changed the password - I did NOT!]; but that gave a response of rw invalid [or unknown] command...so I never could get to your request. One step at a time...how do I get on to the system. I have Hierins and other such...but am stumped and exhausted...there were a tiny list of commands [in 2 pt type [white on light grey] and I tried a few I could read...but they all said 'arguments expected' and I don't know what they want..IT wants. I need a beer or ten....

Thanks for the help...hope I can get that far.....I'm now locked out. I remember seeing something on the HUGE Heiren's disk about getting into Ubuntu without a password...but where?!...and why is it changed. It is the same as I had before and have gotten on THIS time [until now] without trouble. I've tried perhaps 40 times today...no way!:(:(:(:(

---

### Post by SuaSwe on 2012-05-04
Maybe start by using a LiveCD or USB (like one you'd use to install Ubuntu), select "Try Ubuntu" and check what your drives are doing from there, before doing anything else? By entering a live environment this way you will have visibility of what users have home directories (Places > Home, from memory, will bring up a Windows-like file explorer) and generally which files are and are not there. 

Also, could you take us through exactly what happens when you boot the machine, step by step? In addition, where exactly did you enter "rw init=/bin/bash"?

---

### Post by crazybear on 2012-05-04
> **SuaSwe said:**
> Maybe start by using a LiveCD or USB (like one you'd use to install Ubuntu), select "Try Ubuntu" and check what your drives are doing from there, before doing anything else? By entering a live environment this way you will have visibility of what users have home directories (Places > Home, from memory, will bring up a Windows-like file explorer) and generally which files are and are not there. 

Also, could you take us through exactly what happens when you boot the machine, step by step? In addition, where exactly did you enter "rw init=/bin/bash"?

......I'm somewhat without words to express my inability to express....
I do NOT yet understand how to 'navigate' in Ubuntu....nor how to do most things...let alone know where I am. I try and I consider my self intelligent [PhD, if that means anything - and though I hate Windows I DO know how to navigate it...but Linux/Ubuntu....I have not yet come to the 'aha' moment. Sometimes I feel I know less the more I use it. With that caveat.... OK, the install disk allowed me to look at the drive with the 'real' Ubuntu on it and the backup disk. I got into terminal, but was hopelessly lost in it. I seemed to always be in the CD - never in the disk. Anyway, it seems that most [?] of the old information is there...but:
1] I can't get into the system - it has changed the password without me doing so.
2] When I was in it [before yesterday for a few days after my dumb move] it looked totally different and the drivers for all the devices my expert installed were [it seemed] gone.
3] your suggested commands did nothing, but list /home/ubuntu/Documents, Downloads, Music, Pictures, Templates and two others [can't read my own writing when I'm upset]...but I think [don't know...I was NOT looking in the disk, but the CD and don't know [oh how embarassing] how to do so in terminal. Yes, I could look in the /dev/sd_1 and see my old files [at least many I couldn't see when I was allowed to log in].
4] what now?! How could the password have changed. I didn't know the command to change it and I never tried to....but it rejects the password now. There are also other [important?] changes in the boot screen - the latest kernel is only labeled as [virtual] - whatever that means. And I can get to a log in screen ONLY in the next to last version. All others lead to a frozen screen.

In summary, it seems most or all of my old stuff [drivers and configuration I do NOT know] are in there...but now A] how to get in and B] how to move them [the old files] to replace the new mess I created?!

If the above is not clear, I understand. [that I don't understand] ):P

NB - I had tried "rw init=/bin/bash" on the login screen after hitting 'e' and getting the all too high resolution and low contrast screen...but clearly saw it rejected the command. I also tried it just now, but fear I was not giving that command to my real drive, but to the CD....I'm just a one beaner...sorry.

NBB - **_many_** of the folders in my drive [device] I wanted to look at were locked...such as users [to see if there were more than one] I do not know how to get past that lock-out.

---

### Post by crazybear on 2012-05-05
So, any help would be most appreciated. It seems [though it is far from clear] that most of my folders are in two [possibly three] locations....1] I had made a copy of the main files on another disk 2] there was an on-disk copy of the main files and perhaps there are two [?] sets of files in the main folder system now. All I know is that when I could log in it looked different; my desktop was empty and the drivers to all devices I had long ago struggled to install were gone. Most [but not all] of the programs I had installed were there in the drop-down menus. Now, for no apparent reason, I'm not allowed to log on...though I never changed the password and only learned that command AFTER being locked out. I'm left with only the dread Windoz - please help me get back in and how to move the old files back into place and 'restore' my computer to what it was. Many thanks. I'll not make this/these mistakes again. The person who helped me [a VERY advanced Linux guy] and who has gone, set up a system he understood, but I did not, fully. I also don't know what caused the 'no OS present' statement that caused my mistake of re-installing 11.04. Thanks for any advice.

---

### Post by Daveth on 2012-05-05
I think we need to slow down here and take stock, as this is getting very confusing. If I may summarise:

You installed Ubuntu over an older version, did not have a separate /home partition, and so formatted over all your config files (and everything else). You were wise enough to make a system copy, and that resides on another hard drive, so there is potentially some hope of copying key config files from 1 drive into the new Ubuntu version. You are no longer the owner of those copies (which is why you are locked out).
 
But can you get into the new Ubuntu version or not?

---

### Post by crazybear on 2012-05-06
> **Daveth said:**
> I think we need to slow down here and take stock, as this is getting very confusing. If I may summarise:

You installed Ubuntu over an older version, did not have a separate /home partition, and so formatted over all your config files (and everything else). You were wise enough to make a system copy, and that resides on another hard drive, so there is potentially some hope of copying key config files from 1 drive into the new Ubuntu version. You are no longer the owner of those copies (which is why you are locked out).
 
But can you get into the new Ubuntu version or not?
Thanks for the reply. I spent all morning [many hours] fighting with this on  my own....made a little progress. It is [sadly] more complicated [I think] than it sounds....but think if someone with good understanding would be able to find a VERY simple solution. I discovered there are two accounts in home [the old and the new]....BUT I can NOT log on [except when I log in under repair mode using failsafe graphic mode. All other ways in I can't. Once in a tried to made some changes...I tried to reset the password [and did...]...but when I'm not in failsafe graphic mode it endlessly says 'login failure' or some such. [remember I can't see my Ubuntu and write you at the same time]. What I don't know is which folders and files contain all the configuration files, nor how to move them 'back'...but first I must be able to log in. I made myself the Administrator. I tried endlessly to change the boot/splash screen, but never did it change to something good or usable, and Never what I had set it to..it has a mind of its own. Sadly, the two [old and new] user ID accounts have confusingly similar names [not to me, but maybe to the system]. Yes, it seems there are TWO or THREE sets of my old files 'in there', but can't get in there except in a very limited mode and can't log on in normal mode, plus can't set the log in screen so I can. The display of kernels to boot into is strange, at best and NOT what I ever requested it be. Sorry I sound frustrated...just am. So, what do you think? Is the ATI driver preventing log in [sounds odd to me]? Why would it not let me log in [EXCEPT on failsafe graphics mode]? Once in, how do I configure the log in and splash screen [not the image - which needs to be changed, having almost NO contrast with the letters and the letters too small to see without microscope [but that is not priority]. Listed are two virtual kernels, I never knowingly installed and NONE listed will go anywhere - even to a log on screen. I discovered by accident that only hitting 'old linux kernels - or something like that] could i find the latest kernel in a non-virtual mode and hit 'repair mode' and then hit 'failsafe graphics' and then I CAN log in...but only then.....

Thanks again....the panic grows the longer I'm kept out; and I fear small changes I make when in could make things worse, not better. I don't have another computer and I'm having other problems with Windoz [I think unrelated]....so really can't do any work but fight with the two systems. Sanity at breaking point. I prefer Ubuntu....but only Windoz is allowing me to do anything at the moment....even if with its own problems. 

Any more info you need. I'll try to write down more exactly what is going on....sad one can't take screenshots when one is having problems like this.

Re-reading your post, I'm not sure what you mean. I reinstalled 11.04 over 11.04 [not an older version]. If that matters]. I used the same exact install disk I did when I originally installed. The 'repair' option on the install disk let to choice I didn't understand the consequences of...so backed out.

---

### Post by Daveth on 2012-05-07
OK, so you installed 11 over 11 (the what over what is less relevant than the how!). So, when you first installed 11, did you just do a plain install without setting up any partitions, i.e. the system files and the home directory were all on the same partition? This is the standard "press the buttons" approach, and you would remember if you had set up separate partitions. I ask, as your config files would have been completely over-written, leaving only your separate back-up drive.

Are the 2 hard drives you have different sizes in Gbs? This would easily allow you to id what is where. Alternatively, as suggested earlier, use the Ubuntu 11 cd as a Live disk (stick it into your PC, enable boot from cd in the BIOS, and let it run ***only*** in memory,i.e. do not "install" and see what drives and contents are present. It should allow you to navigate around the disks it finds in the file manager. It will have itself (largely empty of course), your Ubuntu 11 install with its multiple personalities, and the other hard drive, hopefully with the config files. This would at least confirm what is where.

Making more new user accounts is a bit pointless. 

If you can definitively see what is where, then it might be worth starting again, putting a new clean 11 install in, get that up to speed, and then try raiding your other drive. 

Your low graphics situation is because you would need to load up the graphics drivers I imagine,so all you are getting is the basic output.

---

### Post by crazybear on 2012-05-08
> **Daveth said:**
> OK, so you installed 11 over 11 (the what over what is less relevant than the how!). So, when you first installed 11, did you just do a plain install without setting up any partitions, i.e. the system files and the home directory were all on the same partition? This is the standard "press the buttons" approach, and you would remember if you had set up separate partitions. I ask, as your config files would have been completely over-written, leaving only your separate back-up drive.

Are the 2 hard drives you have different sizes in Gbs? This would easily allow you to id what is where. Alternatively, as suggested earlier, use the Ubuntu 11 cd as a Live disk (stick it into your PC, enable boot from cd in the BIOS, and let it run ***only*** in memory,i.e. do not "install" and see what drives and contents are present. It should allow you to navigate around the disks it finds in the file manager. It will have itself (largely empty of course), your Ubuntu 11 install with its multiple personalities, and the other hard drive, hopefully with the config files. This would at least confirm what is where.

Making more new user accounts is a bit pointless. 

If you can definitively see what is where, then it might be worth starting again, putting a new clean 11 install in, get that up to speed, and then try raiding your other drive. 

Your low graphics situation is because you would need to load up the graphics drivers I imagine,so all you are getting is the basic output.

Thanks for the reply. Some things you suggest I cannot/will not do. Such as RAID...can't and wouldn't if I could. Yes I remember how I originally installed. A standard install...but this expert added two modifications [later] He added a folder called Ubuntucopy, which contains and contains still the old config and other files....and these are also in the copy on the other drive [which he strangely set up for the primary drive to always look for [and when it is not in the computer I must tell it to skip mounting it or it won't boot. However, you have not told me [yet] - nor has anyone else:
1] How do I get in...I can NOT - the password is ONLY recognized and I can only enter [sic] in failsafe graphic mode [is the ATI ccc driver causing this?!]....
2] how after I get 'in' again fully can I and do I and which should I move over from Ubuntucopy or the other drive to set up the system as before
3] I need my configuration files, those [if not configuration] that have the driver and hardware configurations and history - most importantly.

- As for going in on a live CD, I have and I can see the old files in two or possibly three places.....but unless and until I can get in, I'm not sure I can move things [or at least don't know how - now which to move and which could cause more problems then they'd solve. It is not needed, as I can get in on a very limited basis in failsafe graphics mode...but in both some folders I don't have permission to view or enter [though I'm the Administrator]. 

Again thanks and please someone let me know how to proceed. It seems I DO have the old files that I need, but  not sure how to move them; which to move and how to get past the password problem that now exists.

I think extraneous now is to explain why I when re-installing used a variant of my original user name. I did so to try to preserve the old one and files. I believe that worked [that is why I say there might be THREE copies of the good old files]. I had ALWAYS had a problem logging in from command line - NEVER was able to...only on the Grub sign in was I able to before...now not. That needs to be addressed, but is NOT a priority, I think.

---

### Post by crazybear on 2012-05-17
These are moved from another thread [which I was told was an inappropriate thread for my situation and posts]:

 1 Week Ago 	   #1356 
kiwimenace 
Spilled the Beans

  
Join Date: Jul 2009
Location: new zealand, south island
 Beans: 14 
 Ubuntu 9.10 Karmic Koala 	Re: Howto: Backup and restore your system! 
Is it possible for me to just manually copy all the files(incl hidden file) from "file system" partition to a safe place and then just copy them back again later under a live disk to restore my system?

 I have a separate /home partition.

 Cheers
 Last edited by kiwimenace; 1 Week Ago at 10:03 AM.. 
    	   
 1 Week Ago 	   #1357 
crazybear 
Just Give Me the Beans!

  
 
  
Join Date: Jun 2010
 Beans: 74 	Re: Howto: Backup and restore your system! 
Quote: Originally Posted by kiwimenace  
Is it possible for me to just manually copy all the files(incl hidden file) from "file system" partition to a safe place and then just copy them back again later under a live disk to restore my system?

 I have a separate /home partition.

 Cheers

What I don't know [and fear] is that a wholesale movement/overwriting of ALL files might [I'd think LIKELY will] cause problems - NO? My system looked quite different before/after. Wouldn't it be better to move only the configuration files to start with - those with the old setups. I don't really know what is stored where. I also don't understand the new entry for a virtual kernel; nor not being able to log in with password except in failsafe graphics mode [but if the old configuration files were there, that would likely go away. Will older files overwrite newer ones? Many thanks.
    	    
 1 Week Ago 	   #1358 
newb85 
A Carafe of Ubuntu

  
Join Date: May 2009
Location: Indiana
 Beans: 130 
 Ubuntu 11.10 Oneiric Ocelot 	Re: Howto: Backup and restore your system! 
@ crazybear & kiwimenace,

 Simply copying all files back to the partition using a live disc should only be a problem if you've created/deleted, moved, resized, etc. a partition or partitions (i.e., if any of the UUIDs have changed). In that case, it would still work, but you would have to edit your fstab file to reflect the changes.

 The default for tar -x is not to remove files from the destination that are not in the backup, so if you're taking the wholesale approach, delete all contents of the destination partition first (start with a blank partition).

 @ crazybear

 The trouble with only moving the old configuration files is exactly that you don't know where they all are. With a little research, though, you could probably find most of them. What exactly did you mean when you said this:

Quote: My system looked quite different before/after. 

How did it look different?
    	   
 6 Days Ago 	   #1359 
crazybear 
Just Give Me the Beans!

  
 
  
Join Date: Jun 2010
 Beans: 74 	Re: Howto: Backup and restore your system! 
Quote: Originally Posted by newb85  
@ crazybear & kiwimenace,

Quote: Simply copying all files back to the partition using a live disc should only be a problem if you've created/deleted, moved, resized, etc. a partition or partitions (i.e., if any of the UUIDs have changed). In that case, it would still work, but you would have to edit your fstab file to reflect the changes. 

No, I have not moved, resized the partition. I re-installed over and it said it would save my files.....it apparently did, but all the drivers and general set-up is different! The drivers for the Printer, Video Card and several other things were GONE...these my Guru had worked long and hard on.

Quote: The default for tar -x is not to remove files from the destination that are not in the backup, so if you're taking the wholesale approach, delete all contents of the destination partition first (start with a blank partition). 

I didn't use tar to backup. I simply made a copy using dd, I believe. The Linux Guru who used to help me [and is now apparently dead] also made a file within the main device called 'Ubuntucopy' which also has a copy of the originals, it seems. Lastly, as when I re-installed I used a slight variation of the original user name, there seem to be the old and new users.
Quote: @ crazybear

 The trouble with only moving the old configuration files is exactly that you don't know where they all are. With a little research, though, you could probably find most of them. What exactly did you mean when you said this:



 How did it look different? 


I especially don't know which are important and what they contain.....which are the old [I guess I can try looking at dates on them] and which might have been modified with the new install. More importantly: 1] I don't know what problems could be caused if there were two sets of a file; or mixed and matched files that need to coordinate with one another, and 2] Using Live CD some [quite a few] are locked to me and I can't open [and likely can't copy and overwrite without permission - though I'm the 'Adminstrator' - except by terminal, I would think.

 As to looking different, this is hard to fully explain. Remember too [all seem to ignore this], that NOW I can NOT log in except [I discovered] in default graphics mode under the repair scenario...for reasons unknown [I could log in for a while after the change the 'normal' way]. Additionally, there are two new entries in the list of kernels. [14, I believe] and they say (virtual)...I don't know why nor what they are and I never set up knowingly anything like a VM scenario. Also, worth mentioning 13, 12 and earlier kernels can NOT be booted into. ONLY 14 and ONLY in failsafe graphics mode...although this was not the case until I started to [?!] set up the ATI ccc driver....which [I thought] was working with one small exception of one LCD screen of three being the wrong color and it would allow me to only change that one - none of the others...seemed minor...maybe unrelated. 

 I do NOT have another OS on this disk. Lastly, just before the system went 'weird' I suddenly had the new look of the Ubuntu Studio - unexpected, but not bad...but strange as i had NOT just installed it...I believe I had months and months ago and it suddenly took over the look of the desktop. That was BEFORE I got the screen that there was 'NO OS on this disk', which caused me to mistakenly panic and re-install...I should have tried other things first...as there WAS an OS.

 So, I have copies of the old configurations and files...if I can determine which I need and which they are....please tell me someone how in terminal I can move them back and not be blocked with permissions. I think the system doesn't know who the Administrator is anymore.

 Hope that answers your questions and asks mine in a manner that is comprehensible. My old Guru would have fixed this in a flash....alas....I'm on my own now. 

 Thanks so much for the help....I'm VERY hesitant to attempt moving the files back until I
 1] can open and see all the files
 2] know which ones would be different and should be moved [and which might cause a problem if moved - if any]
 3] how to move them in the terminal, so I can have the proper permissions
 4] if the old settings for the video card, printer et al. should all be returned or if some hybrid will be made in the process [a Frankenstein]?
 5] any other warnings a novice like me should know about BEFORE attempting this.
Last edited by crazybear; 6 Days Ago at 12:59 PM.. 
    	    
 6 Days Ago 	   #1360 
newb85 
A Carafe of Ubuntu

  
Join Date: May 2009
Location: Indiana
 Beans: 130 
 Ubuntu 11.10 Oneiric Ocelot 	Re: Howto: Backup and restore your system! 
First, some general forum etiquette: You're posting your questions in the wrong thread. Despite its vague name, this thread is about backing up and restoring using the tar command and the method prescribed by Heliode. If you choose instead to use DejaDup, more power to you, but your questions should be posted in a thread about DejaDup. If no appropriate thread exists, create your own. In addition to adding off-topic posts to an already unwieldy thread, your questions have confused those who have tried to help you. (E.g., I assumed you had backed up your system according to the howto at the beginning of the thread, so some of the answers I gave you were not appropriate for your situation.)

 Second, some general backup basics: There are a plethora of backup and restore options, and part of the freedom of Ubuntu is your ability to choose which one you want to use. However, you need to be consistent: if you created your backup with DejaDup, you need to restore your system using the recommended DejaDup method. (I am not at all familiar with DejaDup, so I can't be any help here.) Some backup methods copy everything in your system, while others track changes you've made and still others use different paradigms. Mixing and matching can have undesirable results, as you've found.

 Third, a point on administrator and superuser: In Linux, being an administrator does not automatically give you access to all files. It enables you to gain access to all files, that is, to act as superuser. If you try, from a terminal, to open a file that your user doesn't have permission to open, the system won't let you. However, if you precede the command with "sudo" and enter your password when prompted, the system will allow you to open it as superuser. The default file browser in Ubuntu is Nautilus. If, in the terminal, you enter 
Quote: sudo nautilus 

, it will open a browser window where you will have access to all files. There are also commands you can execute as superuser to change ownership or permissions of particular files.

 Lastly, you probably shouldn't post something like 
Quote: I'm on my own now. 

 on a forum like this one. You're not on your own. You have access to a community through this forum. You just have to learn a few things along the way.

Re: Howto: Backup and restore your system! 
Thanks. Sorry, if this is on an inappropriate thread. I had started my own...waited several days...but had NO responses and NO access to Ubuntu [now it is several weeks]...so looked around for another thread I though was on the same topic. Sorry, if that was not true. Are there not moderators to move things around. I'll not post here further...but go back to my own thread and wait. I'll try out what you suggest. I hope it works. Hard to believe that with an install CD one can get in and change any Ubuntu system. in this case, however, it is most welcome. Again sorry and again thanks. 

 - NB, yes, I know there is a community here and I have used it a few times before. Sometimes with success and sometimes without. As I said, I had a local older man who had spent his entire life programming Linux who had often walked the few blocks over to assist me. Sadly, he has died, and sadly he was SO far advanced and so quick at the terminal [he did everything in the terminal] he often did things that I couldn't understand or even keep apace with. Now I'll cut and past some of this back to my thread and hope it works out.

---

### Post by crazybear on 2012-05-17
So, I've waited for responses to my remaining questions, but they have not been forthcoming....so soon I'll attempt with great trepidation the move. 

I still do NOT know WHICH files to move - nor if any could cause problems if moved. I don't feel confident I'll be able to move those that show as hidden when I look at them with a live CD. And lastly, I hope they all overwrite and not 'combine'.

So, if anyone has any last minute suggestions - or dos and donts - speak now! [soon!!!]...

I'm NOT sure the above analysis of why I can only log in in failsafe video mode is correct - for I did get the driver to install and for several days all was fine and I could log in normally - it was just not my old computer and other devices and programs that needed lots of hard set-up were missing. Then suddenly it started to shut me out [I'm not aware of any changes made that should have caused that!]. No one has told me what it means or why I have the latest kernel listed in virtual mode, nor why I can ONLY log in EVER [before in normal mode - now only in failsafe video mode] with ONE kernel - the others fail]. Before, I could log in with any of the kernels. All very strange to me and more than I can research. Thanks for any last minute pointers. I do NOT feel confident about this. :confused:

---

### Post by Zill on 2012-05-17
> **crazybear said:**
> So, I've waited for responses to my remaining questions, but they have not been forthcoming...
Firstly, you have my sympathy for the situation you are now in.  Unfortunately, I am concerned that, with your current level of knowledge about the Linux OS, you may find it very difficult to get back to where you want to be.  Your first post stated that you wanted to keep all your settings including history, configuration files etc.  While this *may* be *possible*, I suggest it could be unrealistic for you to actually do this.

Alternatively, I suggest that the most important thing to keep is your data.  i.e. all the documents you produced and kept in your /home/user directory.  Traditionally, whether you are using Linux, Windows or Mac, it is always *essential* to keep backups of any and all data you cannot afford to lose.  These backups *must* be kept on a totally different drive on a totally different system to ensure availability in the event of the hard-disk drive in a PC failing.  These backups can be on a different PC, an external HDD, a USB flash drive, a DVD, or in "the cloud".  If you do have backups of your important data (i.e documents) in such a location then their recovery should be straightforward.

Regarding the "settings" (configuration data), I suggest that your best action is to forget about all your current versions of Ubuntu and to start from scratch.  This means that you need to assess whether you wish to stick with Ubuntu (Linux) or possibly move to a different OS such as Windows or Mac.  I exclusively use Linux here but appreciate that more support tends to be available locally for the other OS's.  In your case, this might be an important factor if you need support in future.

When you have decided which OS you wish to use then I suggest reinstalling this on your corrupted PC, making sure that you reformat the hard-disk drive totally.  This will mean that *all* the data on your PC (including all your documents) will disappear but this will not be a problem *if* you have backups already stored elsewhere.

However, if you do not already have backups stored elsewhere then *now* is the time to do this!  I suggest you use the Ubuntu Live CD to access the /home/user directory on your hard-disk drive and then copy this to a suitable external backup location as described above.  Just use the Nautilus file manager from the Live CD to copy this directory.

Once you have done this (and verified you have a good copy!) you can then go ahead and install the OS of your choice.

Configuration of the new OS should be largely automatic but if you need assistance with any particular aspect then (if you have chosen Ubuntu) simply post back to these forums.  It is probably best to start a new thread, with a descriptive title, for each problem.

Note that video, printer, wifi drivers etc are often configured automatically with newer versions of Ubuntu so just try things first - you may well find that most things "just work".

Once you have your new system installed it should then be simply a matter of copying your previously backed-up documents to your new directory.

---

### Post by crazybear on 2012-05-17
Thanks for the above, but I think it is not for me....no personal offense. 

What I need to know is how to move the files using a live CD. I just tried and was told I didn't have permissions. Next I need to know which folders to move and any I should not.

I do NOT see how the above suggestion is anything more than an extra and unnecessary step. It would also remove all of my MANY, MANY programs - which would take weeks to try to redo. Ditto other information that was not overwritten with the re-install...it seems like a step backward. Don't make the mistake of thinking because I'm rather un-saavy with Ubuntu that my system was in any way simple- it was quite complex, in fact and I don't want to do a clean install unless I absolutely have to - weeks to months of work would await me.

Also, for me your statement about most devices installing themselves is just dead wrong. It took an expert of over 5 decades many days to install things...and even he sweated over much...but got it all going. I have the same hardware and programs [some unusual] and that information is all in the saved extra disk.

Now with my fiddling and without information on how to move the files and which to move, I made things a bit worse. Now I can't log in at all - under any situation. First [after re-install] I could; then only in failsafe video mode - now not at all!!! I also now do NOT get a grub spash screen with choices..it goes directly to the login and NOT the way I set up the login - not the way it was....so the only way in seems to be via a live CD?

I see no reason to reformat the disk and start over, unless you can convince me. It seems all I need to do [but don't know how to] is move the home files from the 'ubuntucopy' folder to the main home folder and overwrite them. No? I need to know how and how to have the permissions, as I can't log in.

Thanks much...very very frustrated. Two weeks with no system and every time I go to try to make things a bit better they get a bit worse....

Still no one has told me why the 15 kernel is virtual and if that is normal? or a problem. [Of course now it doesn't show as a possible choice anymore.....but it was strange that shortly after it appeared things started to go wrong.

Many thanks for help.

---

### Post by Zill on 2012-05-17
> **crazybear said:**
> ...I see no reason to reformat the disk and start over, unless you can convince me...
I just considered it the best way forward in view of your comments - but it's your system to fix as you wish.
> **crazybear said:**
> ...It seems all I need to do [but don't know how to] is move the home files from the 'ubuntucopy' folder to the main home folder and overwrite them. No? I need to know how and how to have the permissions, as I can't log in...
Just use the Live CD to copy your 'ubuntucopy' folder to your chosen destination.  To use the graphical file manager Nautilus on files with any permissions, simply open it from a terminal with super-user privileges:
```
gksudo nautilus
```
> **crazybear said:**
> ...Still no one has told me why the 15 kernel is virtual and if that is normal? or a problem. [Of course now it doesn't show as a possible choice anymore.....but it was strange that shortly after it appeared things started to go wrong.
I have no idea what this is all about!  Which is another reason why I still consider a clean install is your best bet!

---

### Post by crazybear on 2012-05-19
> **Zill said:**
> I just considered it the best way forward in view of your comments - but it's your system to fix as you wish.

Just use the Live CD to copy your 'ubuntucopy' folder to your chosen destination.  To use the graphical file manager Nautilus on files with any permissions, simply open it from a terminal with super-user privileges:
```
gksudo nautilus
```

I have no idea what this is all about!  Which is another reason why I still consider a clean install is your best bet!

I'll give the above a try later today [minus the clean install - as I mentioned it would LITERALLY take me MONTHS to set up all again - the number of installed programs was great and some of them needed special and difficult setting up [done by my former Linux guru]]. Ditto the setting up of some of the hardware. That [a clean install] would be a horrible fate and only as a very last resort! My only worry about the above is if the system has somehow lost or changed 'who' is the administrator and what my password is - or if only the video driver is preventing my logging in now. Will know soon. If I have log in problems, someone had suggested a way to get in and change the password and/or check it...but can't locate that now.

---

### Post by crazybear on 2012-05-19
just spent MANY frustrating and confused hours trying to do what everyone posting just says 'DO', without saying how....and I have NOT been able to figure out how. I spent all night last night reading a multi-hundred page Ubuntu manual, read all the posts, tried with a live CD [very confusing for me to know where I am] and opened up nautilus...but was denied permission to move anything...in fact it said there was 'no room' to move anything - which can't be true, unless it though I was trying to move to the CD, which I didn't think I was...but don't know. Now, I'm in Window$ and I have a program in Window$ that can see into Linux...and I can see that on /dev/sdb1 it looks like everything I ever had and wanted is there; but [and I may be making a mistake...I don't fully understand naming and navigation in Ubuntu]; in /home are also all my old things - BUT under users there are two [I only had one before and created a slightly different one when I re-installed [stupidly]. However, with neither can i enter the password [was the same for both]. It no longer shows the splash screen, so I can't use the old method I had to get in.

But the most frustrating is I can't drag and drop any files, nor do I know how to construct a dd if..... of...... for the whole set and move - without making things worse.... of cp -a 'Dir x' 'Dir new' without making a mess o things either. The Guru who set this up for me made it a bit more complex than the normal system...it turns out it has saved my ***, but also makes it very confusing to clearly see what is what and where things should go. Again, if I could show a visual to someone knowledgeable I think it would be a lot clearer than my babbling.

I could open one nautilus that seemed 'active' and couldn't open a second that was. The second one I could open said something like can't access computer; can't access this and that....couldn't access anything. I was hoping to drag and drop that-a-way.

Frustrating. Very. I'm exhausted and wonder if someone would be willing to contact me by email and we can connect by skype - or leave it at email and I can show you screen shots of what this all looks like - I'm sure for an old hand this is a few minutes work. For me it has been weeks and seems like it isn't gonna end soon. :confused::confused::confused:

If someone knows how I can get in and change the password and delete one user, it might make it possible to enter into Ubuntu again. For now, I'm on the outside looking confusedly in...but I see all my old files and a small number of new ones that seem to be causing all the problems. Even my old history is there...though there is another new history since the re-install and a new everything since the re-install - BUT IT SEEMS TO HAVE PRESERVED ALL OF MY OLD SETTINGS, FOLDERS, ETC...now just how to move them and rid the new ones. If I sound confused and exasperated, it is only because I am.

NOTE: email or skype need not be done; any help in how to get permission to move things will be helpful and perhaps I can figure out where to move them...there are three copies of everything old and a fourth single set of the new....which adds to the confusion and chance of a mistake. many thanks in advance. I know it is as frustrating for those advanced Linux persons to try to understand and explain to a newcomer and learner [such as I], as the other way around.

---

### Post by Zill on 2012-05-20
> **crazybear said:**
> ...any help in how to get permission to move things will be helpful and perhaps I can figure out where to move them...
> **Zill said:**
> To use the graphical file manager Nautilus **on files with [COLOR="Red"]any[/COLOR] permissions**, simply **open it from a terminal [COLOR="Red"]with super-user privileges:[/COLOR]**
```
gksudo nautilus
```
Having said that, a clean install first should immediately resolve your login problems (and others!).  A clean install would only take and hour or two and leave you with a fully working system.  As long as you have your documents safely backed up elsewhere, you could then simply restore these back to your new working system.

Regarding your "MANY, MANY programs", assuming they are included in the current Ubuntu repositories (many thousands are there!), installation can be done very quickly.  Either use the Ubuntu Software Centre or Synaptic (my preference) if you want a GUI.  Multiple programs can also be installed with one line using the terminal.  i.e.
```
sudo apt-get install package1 package2 package3 and so on
```

ps.  Don't forget to ensure that your system is fully updated *before* installing any new packages.  i.e.
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by crazybear on 2012-05-21
> **Zill said:**
> Having said that, a clean install first should immediately resolve your login problems (and others!).  A clean install would only take and hour or two and leave you with a fully working system.  As long as you have your documents safely backed up elsewhere, you could then simply restore these back to your new working system.

Regarding your "MANY, MANY programs", assuming they are included in the current Ubuntu repositories (many thousands are there!), installation can be done very quickly.  Either use the Ubuntu Software Centre or Synaptic (my preference) if you want a GUI.  Multiple programs can also be installed with one line using the terminal.  i.e.
```
sudo apt-get install package1 package2 package3 and so on
```

ps.  Don't forget to ensure that your system is fully updated *before* installing any new packages.  i.e.
```
sudo apt-get update
sudo apt-get upgrade
```

Again, thanks but I am so VERY FAR [MONTHS!!!!!!!!!!] from even thinking of a clean install I can't even express it here. I know [and you don't - and see you assume otherwise] how complex my software setup was; how much even an expert fought [though prevailed] to set-up some drivers and devices. Please don't waste your time further trying to convince me in that direction. IT WOULD BE A **_MULTI-MONTH_** PROJECT, NOT THE CAKEWALK YOU ASSUME! This much I know! It would be a greater nightmare solution, IMO. I don't just do common nor simple things and everything was working just fine. 

What I'm asking for it help to overwrite the good old files [extant in three complete sets] over the new single set that was created with the 're-install' over the old installation. I did use the sudo command for nautilus, but had felt i needed to nautilus screens open and the second one would do nothing, though was open...it just gave error messages as I mentioned. I can't drag and drop/overwrite in just one window - or at least I don't know how that would be possible. It seems to me any one of the good sets, if moved to overwrite the new set would set all 'right'. Also no one has address the several times I've mentioned that the system has for reasons uknown locked me out - not honoring either my name of password [either of them]. I also no longer presents the usual screen for log in - but quite a different one. In the NEW file system under user there are my old user name and the new one I created on the re-install. 

Please someone help me figure out how to do this [move the old good set of system files over the new - it should do the trick, but I am told I either don't have permission, there is no space for the move [there is 500GB!] or don't know how to construct the command in terminal or have two working nautilus windows with which to do it graphically. 

I am not the least bit moved toward a clean install...with good reason. I saw a man who devoted his life for over 55 years to Linus and Linux programming struggle setting up some features of my system....that is all intact in the old files - I could never re-create that...and need not if I can move those files. I start to sound like a broken record. I am unmovable on the issue of a clean install, sorry. Just one program Warrick took the guru days. There were other unusual ones, as well.

Help please.

---

### Post by Zill on 2012-05-21
> **crazybear said:**
> ...Please someone help me figure out how to do this [move the old good set of system files over the new - it should do the trick, but I am told I either don't have permission, there is no space for the move [there is 500GB!] or don't know how to construct the command in terminal or have two working nautilus windows with which to do it graphically...
I regret that you have chosen to reject my advice regarding a reinstall. You have repeatedly been advised how to move ***any*** files/directories graphically via the Live CD (Hint: if you only want to use one Nautilus window then hit "F3" within Nautilus!).  If you prefer to move files via the terminal then this is equally possible and usage of the cp (copy) command is available from the man (manual) command.
```
man cp
```
Similarly to the Nautilus GUI file manager, if you are using the Terminal then you must use the prefix sudo (super-user do) to copy files if you are getting ownership/permissions problems.  There is plenty of information available to help you with all this.  Unfortunately, if you are unwilling or unable to take the time to learn *how* to use a Linux OS then I suggest you may not be able to resolve your problem.  If you *need* to have a hands-on "expert" locally to help you out then Linux may not be the best solution, as local help is usually easier to find with other OS's.

I wish you well.

---

### Post by rewyllys on 2012-05-21
Crazybear, you've received good advice in this thread, but are clearly unwilling to experiment on your own.  I think Zill hit the nail on the head by suggesting that you would do well to seek a local Linux expert to help you.

If you're in the USA, I suggest that you make use of your local Craigslist.  Search on "Linux" under "Services -> Computer", and you'll probably find at least one local person who offers Linux consulting services.  

Alternatively, within or outside the USA, you can search on the Web for Linux-enthusiast groups in your local community.  Try posting an email to such groups in which you ask for help with your situation.

Good luck!

---

### Post by steve7777777 on 2012-05-21
> **rewyllys said:**
> Crazybear, you've received good advice in this thread, but are clearly unwilling to experiment on your own.  I think Zill hit the nail on the head by suggesting that you would do well to **seek a local Linux expert to help you**...

I browsed this entire thread and that's the best advice. Good luck!

---

### Post by crazybear on 2012-05-22
I  had what I thought was a good idea.....I had an extra unused HDD and installed 11.04 on it, using my original username and password. I was able to move my folders/files from my username home folder and they are all there....but I'd REALLY like someone to help me make a list of which folders I must move, should move and which not [certainly NOT the newest ones from the over-installation]. Among those I THINK should be moved [from the OLD-ORIGINAL installation] are:
/boot
/stand
/unix
/vmunix
/kernel
/bin
/usr
/sbin
/opt
/etc
/root
/media
/mnt
/var
/dev
/sys
/proc
/lost+found

...but I suspect that some of these are NOT necessary or would cause problems. And certainly if there are ANY OTHERS, let me know. Kindly help. Thanks. I think I'm almost 'there'.....

---

### Post by crazybear on 2012-05-22
> **rewyllys said:**
> Crazybear, you've received good advice in this thread, but are clearly unwilling to experiment on your own.  I think Zill hit the nail on the head by suggesting that you would do well to seek a local Linux expert to help you.

If you're in the USA, I suggest that you make use of your local Craigslist.  Search on "Linux" under "Services -> Computer", and you'll probably find at least one local person who offers Linux consulting services.  

Alternatively, within or outside the USA, you can search on the Web for Linux-enthusiast groups in your local community.  Try posting an email to such groups in which you ask for help with your situation.

Good luck!

I am an American in a non-Western foreign country. There are few locals and a small expat community who would help out - and many of those few wouldn't be able to communicate well or at all. I'm also unusually poor at the moment, and wouldn't be able to hire a professional - who would charge a foreigner much more than a local. Local groups likely exist, but would deal in the local language which I can't handle more than buying groceries and such. But thanks anyway. What I can't figure, is why no one answers my direct questions, but instead seems to just points me to local help or starting all over. I think some of you with the experience had really consider whether you are offering help or resting on your laurels and looking down your noses at those who don't know as much. Just sayin'. Perhaps you mean well and perhaps you think my life is more normative than it is. I left America under death threats for political whistleblowing and all my money and property were taken. I didn't mention that this 'incident' involved a man with a key to my flat, entering, smashing my computer and nearly destroying it completely....and taking many of the disks. Life is sometimes more complex than it seems on the surface. As for help here....I'm still hoping, but feel I'm constantly pointed in another direction - perhaps with the best intentions. I don't feel a sense of 'community' if that is what it is supposed to be. I was chided by someone with many beans for posting in desperation on the backup and restore thread. You with more normal lives and better understanding of Linux can pat yourselves on the back - or try to help out. I could use it. Thanks. Sorry for the rant. I'll probably regret some of above, but it is all true. It will turn many off [especially in the USA]...some it may touch a chord in. In fact I did have a Linux 'guru' who was very helpful. I thought he had died [he was on in years; as am I!], but it turns out he is traveling - but he said when back he'd not help - the smashed computer incident made him want to blame the victim. I am struggling to re-assemble the computer and Windows as I struggle with Ubuntu - although I'm much more familiar with those than I am with Ubuntu and Linux....that was something recent. NB - I also have limited time, as the landlord is about to force me to move due to the break-in and all....and I may be semi-homeless for a while and need to get computer things done NOW [its all destop - no laptop!]..or it may be until Fall...and that could be fatal to near fatal...thus the sense of mild panic one might detect in my posts. Sorry, all truth. Near meldown. Sorry.

---

### Post by Zill on 2012-05-22
> **crazybear said:**
> ...What I can't figure, is why no one answers my direct questions, but instead seems to just take the easy way and point me to paid help [I thought that was against the whole idea of Linux] or starting all over...
The reason "no one answers my direct questions" is that they appear to be illogical.  For example, the list of directories you provided in post #25 above is different to that in a default Ubuntu installation.  As such, you cannot just copy these random directories into a new installation and expect it to work as per your original system.  A Linux system has heavily integrated links and, unless you *really* know what you are doing, you will simply break your new installation again.

A complete Linux system consist of the Linux kernel, programs *and* data (documents etc.).  The kernel and the programs are generally regarded as separate from the data.  The initial installation installs the kernel and sufficient programs to allow a user to get started.  The user/administrator can then install additional programs as desired.

Once this has been done, a user can then create or modify data.  As this is generally kept within the user's home directory, this data is totally separate from the rest of the OS (the kernel and the programs).  Following an upgrade or reinstallation this makes it very easy to retain data (in the home directory) and this can then be used with the upgraded or new installation.

So, to answer your question, you just need to retain/copy your /home/user directory as this should contain all your data.  However, you *will* have to reinstall any programs you added to the default installation to ensure that all the links to the rest of the OS are built correctly.

BTW, to correct a misunderstanding, I did not actually suggest you look for paid help with Linux.  I suggested that, as local Linux support is often not readily available, moving to a more "popular" OS might make a local "expert" easier to find (hopefully free!).

---

### Post by crazybear on 2012-05-22
I understand that I didn't use the normal 'tar' backup and restore, but I did clone the drive from two months ago [good enough for me - all was fine and I have the small differences elsewhere] on a separate disk. Additionally, the original helper [who will help me no more due to the computer attack....go figure how many like to blame the victim - he even knows why [which I'll not put up here] and I'd think with my value system that would make him  more sympathetic, not unsympathetic...but I digress....]
set up a special folder called Ubuntucopy; which kept a copy [updated ever so often] of the rest of the important folders [he would know what is important!]. I realize it would be easier for someone to help by my side, but this is likely not possible. Talking me through it - teaching me what I need to know or having someone do a remote computer set-up. I now HAVE a new install, but it is empty of SO many things I need. I have the old History too....some of it I can relate to what it was about; other parts not - and the responses are not shown, of course. I'm really exhausted - mentally and physically by the whole thing and am running out of time and could be without computer over the entire summer - meaning no income and little communication. He set it up so I could move things back if something went wrong and now I'm sort of told by others I can't. He, I'm sure could...but for his own reasons wants nothing more to do with it. Sigh. I realize the folders are inter-related; but a wholesale return of a set of them [the right set] all copied at the same time should work. No? I admit I do not know which to include and which maybe to exclude - nor exactly how to fail-safe move them. That is why I made the new disk...to try...if I mess up, I can reformat and try again. But helpful suggestions until someone can sit next to me would greatly be appreciated. I have just put an ad in the expat-English-speaking community website..but I'm not holding my breath. I did last time when I got my guru...but it was a one month wait, I believe. I don't have a month now.

---

### Post by crazybear on 2012-05-23
This is what I got [an excerpt minus more negative stuff on my past and 'blame the victim stuff' I removed as not relevant] from my ex Linux-guru.

"I've spent many hours already building our system for you. I'm not used to working with people so prone to disaster, and I don't enjoy it - and if you're losing machines to enemy action, you ought to face the fact that it's your life that needs fixing, not your computer! I'm not good at those things.

You obviously can see the files you've lost, if only by running under the live CD and **_re-mounting your old partitions on a new directory_** (a well-documented procedure.) If you have a new disk with space, or a CD writer, there should be no problem in copying them off. Use tar to collect a whole tree of files into one file and copy that, or learn a simple bit of shell script to identify all the files you want, and copy them serially & individually. Your home directory will be one tree to copy; /etc is useful as it contains most of your system settings, and possibly later files in .../bin & .../lib may contain unusual drivers, etc. Most of the 'special' work I did for you (your printer, 802.11n, etc.) will probably be standard now, as linux tends to catch up with new hardware, after some delay. I wish you luck, but I absolutely do not have time to come & do the work for you."

My question is: what exactly does it mean to re-mount my old partitions on a new directory? Procedure? I think I can tar, but need to know what to tar and then where to put all. Thanks.

---

### Post by Zill on 2012-05-23
Did you actually *read* what your "ex Linux-guru" has told you?  He has precisely answered your questions.

> **crazybear said:**
> "...You obviously can see the files you've lost, if only by running under the live CD and **_re-mounting your old partitions on a new directory_** (a well-documented procedure.) If you have a new disk with space, or a CD writer, there should be no problem in copying them off. Use tar to collect a whole tree of files into one file and copy that, or learn a simple bit of shell script to identify all the files you want, and copy them serially & individually. Your home directory will be one tree to copy; /etc is useful as it contains most of your system settings, and possibly later files in .../bin & .../lib may contain unusual drivers, etc. Most of the 'special' work I did for you (your printer, 802.11n, etc.) will probably be standard now, as linux tends to catch up with new hardware, after some delay. I wish you luck, but I absolutely do not have time to come & do the work for you."

My question is: what exactly does it mean to re-mount my old partitions on a new directory? Procedure? I think I can tar, but need to know what to tar and then where to put all. Thanks.
Clue: when someone refers to "a well-documented procedure" you could do worse than try a quick search on Google!

In addition, the [Ubuntu Community Documentation]("https://help.ubuntu.com/community") is chock full of useful information.  eg.
[URL="https://help.ubuntu.com/community/Mount"]
Mount[/URL]

---

### Post by crazybear on 2012-05-24
> **Zill said:**
> Did you actually *read* what your "ex Linux-guru" has told you?  He has precisely answered your questions.


Clue: when someone refers to "a well-documented procedure" you could do worse than try a quick search on Google!

In addition, the [Ubuntu Community Documentation]("https://help.ubuntu.com/community") is chock full of useful information.  eg.
[URL="https://help.ubuntu.com/community/Mount"]
Mount[/URL]

What is *_perfectly_* clear to you [or to him], is ***not*** to me. To YOU he precisely answered my question; I have a PhD and I do NOT see any clarity in his statement or your hints. Sorry. I don't understand what part/portion of my old system should be [re]mounted - approximately my question[s] above. I just looked at some on-line references [and have printed out others and as e-books yet others] all giving the [COLOR="RoyalBlue"]how[/COLOR]...BUT, I need to know the WHAT/WHICH FOLDERS or TREE. Thanks. Sorry, but I have not yet gotten to the 'aha' moment with Linux. He, when he was at my side [often] worked so quickly and silently, without explanation, I couldn't follow...things happened, but I was left wondering how. I have read much and it seem clear  until I sit in front of the computer and can't navigate, know where I am or think through what needs or should be done often. Little things sometimes. You think the answer is staring me in the face - as does he. The clarity is not there for me....yet.

---

