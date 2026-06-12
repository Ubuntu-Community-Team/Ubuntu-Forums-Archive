---
title: "Acer laptop nightmares (very long post, I apologize in advance)"
date: 2008-12-21
forum: Other OS Talk
---

### Post by LashSilence83 on 2008-12-21
I recently purchased an Acer Aspire 4530 Athlon X2 laptop. It came with vista on it but I wasn't even the slightest bit interested in using that so I figured I could probably use Ubuntu or some other linux distro on it. I've been having issues and have even discussed some of them in the forums here but nobody seems to know much about this particular laptop or nobody bought them. I'm basically looking for some insight into why I'm having so many strange issues with almost all distros that I've never had on any other system. Either way, here is a list of the distros I've tried on it and the results. 

Ubuntu Intrepid 64 bit live cd: Boots to menu and whether "try ubuntu without changing your computer" or "install ubuntu" is chosen, it brings up the boot splash and the orange and black progress indicator makes it to about 10% and the system freezes. The caps lock light flashes when this happens and I'm forced to do a hard shutdown. 

Ubuntu Intrepid 32 bit live cd: boots fine, live environment works. Strange thing is that for installation, only the "install ubuntu" option will work  from the boot menu of the cd. If I try to install from the live environment, the system will freeze and once again I must do a hard shutdown. I did get this installed fine though, but with issues. The main ones being that programs would crash randomly and with no discernible pattern, and I would get an insanely loud beeping when booting up sometimes. This is totally unacceptable as I use this computer at school and while working and neither of those places are acceptable environments for this behavior. So back to the drawing board...

OpenSuse 10-11.1 32 and 64 bit live cd's: None of these will boot. They either get one of two things after the main boot menu: a 'kernel panic not syncing vfs', or during the boot splash the system would simply freeze and require a hard shutdown.

CentOS 5.1 and 5.2 32 and 64 bit live dvds and install dvd's: kernel panic - not syncing: fatal exception

Knoppix 5.1 and 5.3 live cd's and dvd's: Tells me that the knoppix file system cannot be found and that I'm being dropped to a (very limited) shell

Fedora 8, 9, and 10 32 bit live cd's: freeze right after a message about checking udev except for 8 which gives the kernel panic: not syncing error

Mandriva One 2009: Installs fine, runs fine. I'm just holding out at the moment for something else as this will be my absolute final choice and last resort. I just flat out wasn't too pleased with all the features of this os.

BlueWhite64 12.1 :Installs and runs fine, except it takes 3 minutes to boot up, and everything is totally unfamiliar on how package management and basic system administration works. Plus this os doesn't have any 32 bit libraries and I'm not sure if and how I can implement them. :confused: I have no problem with learning how, It's just hard to learn something entirely new to me when I'm a bit pressed for spare time while in school. 

Slackware 12.2 install dvd: Everything goes fine through about half of the install but then I begin to get "fatal error attempting to install..." errors all along the rest of the way and of course the system won't boot after it's all said and done. 

Slax live cd: begins booting after menu, then system locks up and caps lock light flashes after "Triggering udev events: /sbin/udevtrigger

I have also tried Debian 4 64 bit dvd, gentoo 2008 live cd(the one that boots into gui), and a few others but so far it seems that I will have to settle for mandriva or bluewhite64 unless there are ways to fix the issues with ubuntu. Other problems I'm having with ubuntu would be no working headphone jack or web cam. Alright, sorry once again for my verbosity. I'm just trying to find a solution to make this laptop at least somewhat usable.

---

### Post by pytheas22 on 2008-12-21
I think it's fair to conclude that some part of your hardware--probably the motherboard--doesn't agree very well with something in the Linux kernel.

One method of getting these distributions installed is to use [unetbootin]("http://unetbootin.sourceforge.net/") from within Windows.  That would allow you to install all of the distributions that currently crash during the installers (which sounds like everything besides 32-bit Ubuntu and Mandriva).  However, unetbootin wouldn't guarantee that these systems would run any better once you actually boot into them...but it's worth a try.

I think that the best thing you could do would be to install 32-bit Ubuntu from the live CD, then try to use the system logs to figure out what's going on.  After you experience weird behavior, type 'dmesg' to get messages from the kernel.  Hopefully this will turn up some clues about what's going wrong, which is most likely some strange low-level kernel problem.  From there, you will hopefully be able to figure out how to work around the issue.

Also, just to check: did you use Vista on this laptop at all for any substantial length of time, just to confirm that the hardware itself is not bad?

---

### Post by Roberticus on 2008-12-21
First thing to come to mind is faulty images. Did you make sure the images are not corrupted? Did you burn the discs at low speed? since the images pack alot of information...

---

### Post by LashSilence83 on 2008-12-21
One thing I didn't do is checksums on all of these images. I really dropped the ball on that one... :( The thing is that I reburned all of them at the slowest speed possible and a few of them were burned a third time but on a different burner. Also, all of the discs worked fine on a couple other systems I have and in virtualbox as well. At any rate, this long, arduous process has taught me a valuable lesson to just spend a bit more and only buy laptops from linux friendly distributors like system76 and the like. On a side note, do you think that perhaps in future kernel patches the compatibility will get better or should I most likely just make do with whatever distro until I can get a new laptop and get rid of this one?

---

### Post by LashSilence83 on 2008-12-21
@ pytheas22

I did try dmesg and also the boot log in /var but I believe this issue is happening before the log has started. It's basically right after the grub menu that it is happening. The weird thing is it never happens with any pattern that I can tell of. I would at least figure that it would happen every time or every other time or something of that sort. About using vista on this system: I only booted it one time and didn't even go past the first screen asking for the key. I did, however, install xp pro on it a few days ago just to see if anything weird happened and everything worked fine including wireless, web cam, headphone jack, etc. Of course I know some of these peripheral issues are because of lack of linux drivers and what not, but I'm thinking this system was built to be an MS only system. Pretty lame. :( 
I actually ran into a somewhat similar issue the other day when I was installing some acer desktops in an office and they came with vista but the clients wanted xp pro. Long story short, some of the device drivers such as the on board ethernet had no existing xp drivers out there and basically the entire system was seeming specifically designed for vista and vista only. What a total pain in the *** that was. With that situation and the one with this laptop, I'm beginning to have some pretty negative feelings toward Acer.

---

### Post by pytheas22 on 2008-12-21
You might want to take a look at [this thread]("http://forumubuntusoftware.info/viewtopic.php?f=42&t=1578&st=0&sk=t&sd=a&sid=1bb3a1996561b7bab1db3d287049c51f&start=10") and this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275159").  Each has some suggestions regarding kernel options that you can pass at boot time to try to make things work; these seem to have helped other users with the same model of Acer laptop.  Do they help you?

---

### Post by LashSilence83 on 2008-12-22
Ok, I did give those a try and none of them worked any differently than usual except for with some live cd's the entire system would lock up with a blank screen before any booting processes began. I'm noticing that sometimes (as with knoppix and debian 4) the cd rom isn't detected. It's just kinda weird since it will boot the cd to it's menu, then tell me that there is no cd rom when I try to go any further. Is it because the cd doesn't have the drivers available to deal with the cd-rom? Am I right in thinking that I probably shouldn't bother with this too much more?

---

### Post by pytheas22 on 2008-12-22
It's possible (though not likely) that your CD drive is faulty.  In that case, you might want to try [installing from USB]("https://help.ubuntu.com/community/Installation/FromUSBStick").

But I think that the likelier source of the problem is just that there's something about your hardware that doesn't agree with Linux.  If you've tried so many distributions (each with a different build of the kernel) and have tried using different acpi settings as per those threads that I linked to in my previous post, it's probably something that you're not going to be able to solve easily, unfortunately.

The only other thing I can think of is to [file a bug report on Launchpad]("https://answers.launchpad.net/ubuntu/+addquestion"), where you can get the attention of developers who might be able to look at the kernel source itself to figure out what about it doesn't like your laptop.

However, all that said, I did google for a while yesterday for your laptop model and never found anyone else who had so many problems using it with Linux.  So I'm not 100% comfortable saying that the issue doesn't come down to faulty hardware instead of a general incompatibility.

---

### Post by kazuya on 2008-12-22
It may be a wastwed suggestion, but did you try latest Mepis livecd installer?
I would recommend Mepis as a last option to try and then post back; But like they say, there maybe some incompatibility issues with something in your Acer.
 
On the slackware side, I would recomend like zenwalk or vectorlinux.
 
But if Mepis 32 bit fails., then we may have to really look at the error messages...
 
I thanked you for this post, because you made great efforts here to try and get this PC to work. If your issue is resolved, it would aid many more other users.

---

### Post by pytheas22 on 2008-12-22
An additional thought: according to [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275159"), which seems to describe your issue, you should be able to install 64 or 32-bit Ubuntu using the alternate-install CD.  You might want to try that, then see if you can boot normally after it's installed.

I came upon that report because I remembered that I'd been involved in a [long thread of Acer 4530 users]("http://ubuntuforums.org/showthread.php?t=882003&page=2") who couldn't get their wifi to work.  While the wireless was problematic under 8.04 (it should work out-of-the-box in 8.10), only a couple people mentioned problems installing Ubuntu on the 4530.  So this should confirm that the Acer 4530 should definitely be capable of running Ubuntu, at least if it's installed using the alternate CD (unless, of course, Acer changed the hardware in some way without changing the model number).

---

### Post by LashSilence83 on 2008-12-22
WARNING: YET ANOTHER LONG POST.
@kazuya
First off, Howdy :D. I'm originally form Corpus Christi/Nueces County Area. I do miss the Lone Star State. 
Anywho, I appreciate the thanks. I know there must be a good amount of people out there with this laptop because it sold out at a few of the online retailers when I had bought it. At least a few people may be going through this same struggle and they may not be as vigilant about running GNU/linux on this thing as I am ;) . I sincerely hope this may be of some assistance to those folks. 

@pytheas22
I'm currently downloading those alternate install images and I'll update once they are done and I've tested them both. I just hope that maybe (even thought it's a bit illogical) if it does work, that horrible beeping won't come back. :(

Update and slight correction: After going back over my list of distros I've tried, I realized that I missed one version of OpenSuse that I thought I had covered. This one was only worth mentioning because it did provide slightly better, albeit still not fully functional results. 

The versions of OpenSuse that I mentioned previously were all covered (including betas and RC's) all the way up to 11.1. Apparently I had slipped up and forgotten to try the 64 bit version of the full public release of 11.1. It runs great live and the install went rather smoothly and painlessly. The issues began after the first boot setup. It will finish all configs and setup routines and then tries to start the desktop. In doing so, it will only show a black screen with the mouse cursor (which does respond to the trackpad). I waited about 5 minutes before I did a hard shutdown and restart only to consistently get the same effect. I did a Ctrl+Alt+F1 and started poking around a bit and then decided to try installing 180 nvidia beta driver (I dont know why I thought it would help) after copying it from a usb thumb drive. It tells me that a package called libutils is missing and after trying to find and install said package from the text version of yast and failing at both aspects, I gave in and tried the Mepis cd.

SimplyMepis 7 32 bit live cd: Pretty boot menu comes up and gives lots of options, yet none of them work in the slightest. It will give a couple messages about the kernel and bzimage and then go to a blank screen. If I wait about 3-4 minutes, it starts printing "Looking for cdrom in: /dev/hda1" and then "..../dev/hda2" and eventually "..../dev/hdk21" and so on until finally it stops and says: 

"Can't find MEPIS filesystem, sorry. Dropping you to a (very limited) shell. Press reset button to quit. 

/static/ash: can't access tty; job control turned off


Interesting stuff, huh? The one cool thing was that in printing the incessant messages about looking for a cdrom, it made a really fun diagonal ASCII type pattern down the screen. :P


UPDATE: I have installed 32 bit ubuntu intrepid with the alternate installer and everthing has gone quite well so far. Issues I'm having with this (after installing all updates) are:
-no webcam. It recognizes it as the correct model but neither ekiga or cheese seem to work with this. 
-headphone jack won't work no matter what mixer or sound driver settings I change
-out of the box wifi doesn't work but ndiswrapper does with xp 32 bit driver

---

### Post by 3rag0n on 2008-12-24
> **LashSilence83 said:**
> WARNING: YET ANOTHER LONG POST.
@kazuya
First off, Howdy :D. I'm originally form Corpus Christi/Nueces County Area. I do miss the Lone Star State. 
Anywho, I appreciate the thanks. I know there must be a good amount of people out there with this laptop because it sold out at a few of the online retailers when I had bought it. At least a few people may be going through this same struggle and they may not be as vigilant about running GNU/linux on this thing as I am ;) . I sincerely hope this may be of some assistance to those folks. 

@pytheas22
I'm currently downloading those alternate install images and I'll update once they are done and I've tested them both. I just hope that maybe (even thought it's a bit illogical) if it does work, that horrible beeping won't come back. :(

Update and slight correction: After going back over my list of distros I've tried, I realized that I missed one version of OpenSuse that I thought I had covered. This one was only worth mentioning because it did provide slightly better, albeit still not fully functional results. 

The versions of OpenSuse that I mentioned previously were all covered (including betas and RC's) all the way up to 11.1. Apparently I had slipped up and forgotten to try the 64 bit version of the full public release of 11.1. It runs great live and the install went rather smoothly and painlessly. The issues began after the first boot setup. It will finish all configs and setup routines and then tries to start the desktop. In doing so, it will only show a black screen with the mouse cursor (which does respond to the trackpad). I waited about 5 minutes before I did a hard shutdown and restart only to consistently get the same effect. I did a Ctrl+Alt+F1 and started poking around a bit and then decided to try installing 180 nvidia beta driver (I dont know why I thought it would help) after copying it from a usb thumb drive. It tells me that a package called libutils is missing and after trying to find and install said package from the text version of yast and failing at both aspects, I gave in and tried the Mepis cd.

SimplyMepis 7 32 bit live cd: Pretty boot menu comes up and gives lots of options, yet none of them work in the slightest. It will give a couple messages about the kernel and bzimage and then go to a blank screen. If I wait about 3-4 minutes, it starts printing "Looking for cdrom in: /dev/hda1" and then "..../dev/hda2" and eventually "..../dev/hdk21" and so on until finally it stops and says: 

"Can't find MEPIS filesystem, sorry. Dropping you to a (very limited) shell. Press reset button to quit. 

/static/ash: can't access tty; job control turned off


Interesting stuff, huh? The one cool thing was that in printing the incessant messages about looking for a cdrom, it made a really fun diagonal ASCII type pattern down the screen. :P


UPDATE: I have installed 32 bit ubuntu intrepid with the alternate installer and everthing has gone quite well so far. Issues I'm having with this (after installing all updates) are:
-no webcam. It recognizes it as the correct model but neither ekiga or cheese seem to work with this. 
-headphone jack won't work no matter what mixer or sound driver settings I change
-out of the box wifi doesn't work but ndiswrapper does with xp 32 bit driver


Hi, i have the same model ...
I'm currently using intrepid 32-bit... 
My experiences :guitar::
1.The incessant beeping you mentioned happened only once after installing updates (the kernel was updated to 2.6.27-9 ). After a reboot it was gone. :lolflag:
2. In GNOME, open the volume control and select the device " HDA NVidia (Alsa Mixer) "(It will probably be selected by default anyway.)
 Now in the "Preferences" button below, tick everything.
Do this :
PCM -> Left = Max, Right = 0
Front-> Left = 0, Right = Max
Front Mic -> Both Max
Front Mic Boost -> Both = 0
Microphone = 0
Mic Boost = 0
PC Speaker = 0
Everything Else = Max

Click on the "switches" tab and tick "Headphones".
Your head phone will work now :guitar: and the lappie spkrs will be muted.

To turn on lappie speakers, set PCM Right != 0 and Front  Left !=0.:lolflag:

3. I dont know how to make wireless work coz there is no wireless network in my area to test with.

4. Earlier, on starting cheese, the video area in the window was blank. Then i installed "gqcam" via synaptic and upon starting cheese again there was a change... The video did not appear, but in it's place i could now see a GNOME foot shaking it's toes !!! (it wasnt there before)
Rather insulting, i should say.. i mean, after all that effort, i am shown a damn foot!

5. I also installed "camorama"... upon starting it a dialog appeared saying "could not connect to video device /dev/video0. Please check connection."
I navigated to that directory /dev/ and the file video0 was there, but i couldn't open it
Then i did sudo nautilus and changed the permissions of the file /dev/video0 to allow read-write by everyone.
Then i opened System->Admin->Users & Groups, selected my name, and after clicking properties and the user privileges tab i ticked on "allow user to use webcam and video devices."

Now cheese works!!! (but not camorama)

---

### Post by 3rag0n on 2008-12-24
My post was the longest .. haha:lolflag:

---

### Post by mips on 2008-12-24
> **pytheas22 said:**
> you should be able to install 64 or 32-bit Ubuntu using the alternate-install CD.  You might want to try that, then see if you can boot normally after it's installed.



+1 I suspect the alternate cds will work.

---

### Post by LashSilence83 on 2008-12-27
3rag0n : 

THANK YOU! How in the heck did you come up with that mixer setting to get the headphone jack to work? I tried all manner of settings but I still don't understand how or why that works (though I am glad it does). Also, the cam works now but is there a way to get it to work with the higher resolutions? The best it will work at is 176x144. Is this a limitation of the hardware or a software config issue?

UPDATE: I've found another issue with this... it won't restart properly. Here's what happens: Whether I choose to restart from the terminal "sudo init 6" or I go to System->Shutdown->Restart, It will go through the process of halting all the services and what not and then after a blank screen for a second or two, I get the amd bios splash screen and it stops there. The only thing that will work at that point is to turn it off and back on with the power button. I'm guessing the kernel is in need of some sort of option to be passed when booting but which one? Or should I change the sata mode in bios to ide instead of ahci?

---

### Post by 3rag0n on 2008-12-30
> **LashSilence83 said:**
> 3rag0n : 

THANK YOU! How in the heck did you come up with that mixer setting to get the headphone jack to work? I tried all manner of settings but I still don't understand how or why that works (though I am glad it does). Also, the cam works now but is there a way to get it to work with the higher resolutions? The best it will work at is 176x144. Is this a limitation of the hardware or a software config issue?

UPDATE: I've found another issue with this... it won't restart properly. Here's what happens: Whether I choose to restart from the terminal "sudo init 6" or I go to System->Shutdown->Restart, It will go through the process of halting all the services and what not and then after a blank screen for a second or two, I get the amd bios splash screen and it stops there. The only thing that will work at that point is to turn it off and back on with the power button. I'm guessing the kernel is in need of some sort of option to be passed when booting but which one? Or should I change the sata mode in bios to ide instead of ahci?

Well about the mixer settings... nor do i know how it works... i was just fiddling with the mixer and stumbled upon this setting by chance :popcorn:!

Also..., restart works perfectly in my lappie... i'm not sure how it depends on the SATA mode, but mine is IDE...so try it, maybe it will work for you... lol

---

### Post by billhung on 2009-01-07
thank you 3rag0n, it worked!

btw, the surround was in mute by default, so be sure the surround is max and not muted.

---

### Post by l_synapse_l on 2009-01-09
you need not make such a complicated mixer setting. just unmute surround, turn it up and headphones will work

---

### Post by oOarthurOo on 2009-01-09
This is why I only buy a laptop that has been on the market for a year. I once bought a brand new laptop just released and it was such a pain. So many things wrong / not working. Video, sound, suspend. A year and a half later I could install any distro and everything would just work.

When a company releases a new product they tend to also release the windows / mac drivers needed to make it work right away. Then linux users have to hack away at it until they too can get it to work. It's changing somewhat I guess, with more hardware manu's coming onboard, and Dell testing out the machines they sell before shipping. But I think it's still a good idea to avoid buying brand spanking new models unless you're interested in filing bug reports and testing patches etc.

---

### Post by LashSilence83 on 2009-01-11
> **oOarthurOo said:**
> This is why I only buy a laptop that has been on the market for a year. I once bought a brand new laptop just released and it was such a pain. So many things wrong / not working. Video, sound, suspend. A year and a half later I could install any distro and everything would just work.

When a company releases a new product they tend to also release the windows / mac drivers needed to make it work right away. Then linux users have to hack away at it until they too can get it to work. It's changing somewhat I guess, with more hardware manu's coming onboard, and Dell testing out the machines they sell before shipping. But I think it's still a good idea to avoid buying brand spanking new models unless you're interested in filing bug reports and testing patches etc.



Very true indeed. This whole fiasco has also made me come to the conclusion that in the future, I will only buy laptops from *nix friendly vendors. I mean it makes sense in so many ways and it would mean giving my money to a company that might actually somewhat share my interests. Wouldn't you rather support a company that wouldn't dare pre-install something like vista on their machines?  :rolleyes:

---

### Post by owend on 2009-01-11
I also have an Acer (Travelmate), AMD processor. I also had it freeze about 10% in. 

I'm running Hardy exclusively now! Trick: download the AMD64 version - the vanilla doesn't seem to like AMD (Ubuntu-8.04-desktop-amd64.iso). Watch the updates though - I'm getting freezes with Kernel 2.6.24-23, keep to -22.

For information (slightly treacherous but at least Linux), Mandriva one 2009 also loaded flawlessly.

Good luck!

---

### Post by Fzang on 2009-01-12
I've had an Acer Aspire 5050 before I got this amazing laptop (woohoo, linux now!) and I must say the motherboard is definitely screwed up, because I couldn't boot ANY live CD's either :(

---

### Post by nerd0795 on 2009-01-13
> **LashSilence83 said:**
> I recently purchased an Acer Aspire 4530 Athlon X2 laptop. It came with vista on it but I wasn't even the slightest bit interested in using that so I figured I could probably use Ubuntu or some other linux distro on it. I've been having issues and have even discussed some of them in the forums here but nobody seems to know much about this particular laptop or nobody bought them. I'm basically looking for some insight into why I'm having so many strange issues with almost all distros that I've never had on any other system. Either way, here is a list of the distros I've tried on it and the results. 

Ubuntu Intrepid 64 bit live cd: Boots to menu and whether "try ubuntu without changing your computer" or "install ubuntu" is chosen, it brings up the boot splash and the orange and black progress indicator makes it to about 10% and the system freezes. The caps lock light flashes when this happens and I'm forced to do a hard shutdown. 

Ubuntu Intrepid 32 bit live cd: boots fine, live environment works. Strange thing is that for installation, only the "install ubuntu" option will work  from the boot menu of the cd. If I try to install from the live environment, the system will freeze and once again I must do a hard shutdown. I did get this installed fine though, but with issues. The main ones being that programs would crash randomly and with no discernible pattern, and I would get an insanely loud beeping when booting up sometimes. This is totally unacceptable as I use this computer at school and while working and neither of those places are acceptable environments for this behavior. So back to the drawing board...

OpenSuse 10-11.1 32 and 64 bit live cd's: None of these will boot. They either get one of two things after the main boot menu: a 'kernel panic not syncing vfs', or during the boot splash the system would simply freeze and require a hard shutdown.

CentOS 5.1 and 5.2 32 and 64 bit live dvds and install dvd's: kernel panic - not syncing: fatal exception

Knoppix 5.1 and 5.3 live cd's and dvd's: Tells me that the knoppix file system cannot be found and that I'm being dropped to a (very limited) shell

Fedora 8, 9, and 10 32 bit live cd's: freeze right after a message about checking udev except for 8 which gives the kernel panic: not syncing error

Mandriva One 2009: Installs fine, runs fine. I'm just holding out at the moment for something else as this will be my absolute final choice and last resort. I just flat out wasn't too pleased with all the features of this os.

BlueWhite64 12.1 :Installs and runs fine, except it takes 3 minutes to boot up, and everything is totally unfamiliar on how package management and basic system administration works. Plus this os doesn't have any 32 bit libraries and I'm not sure if and how I can implement them. :confused: I have no problem with learning how, It's just hard to learn something entirely new to me when I'm a bit pressed for spare time while in school. 

Slackware 12.2 install dvd: Everything goes fine through about half of the install but then I begin to get "fatal error attempting to install..." errors all along the rest of the way and of course the system won't boot after it's all said and done. 

Slax live cd: begins booting after menu, then system locks up and caps lock light flashes after "Triggering udev events: /sbin/udevtrigger

I have also tried Debian 4 64 bit dvd, gentoo 2008 live cd(the one that boots into gui), and a few others but so far it seems that I will have to settle for mandriva or bluewhite64 unless there are ways to fix the issues with ubuntu. Other problems I'm having with ubuntu would be no working headphone jack or web cam. Alright, sorry once again for my verbosity. I'm just trying to find a solution to make this laptop at least somewhat usable.

I have the exact same notebook lol.  I was able to install Ubuntu through Wubi.

---

### Post by LashSilence83 on 2009-01-13
So after a couple weeks without any issues, today I booted up my laptop to the familiar screaming (beeping) and it needless to say, it caused quite an awful disturbance in class. :(  I'm beginning to think that perhaps I should just go with another os until (if ever) this gets figured out. My laptop is essentially useless if I can't use it at school or in any other public place where insane beeping isn't too kosher. I have no idea what to do with this thing anymore. I installed mandriva one 2009 again and I'm having various aggravations with that. Hopefully I can get the kinks worked out before I end up smashing this thing with a sledgehammer. :mad:

---

### Post by FAMUgolfer on 2009-01-13
I have a 4530-5889 for about a month now, and yeah 8.10 can be a hassle.  Have you tried installing with the actual Shipit CD? I actually had a rather smooth install. It beeped when I first installed 8.10, but after a restart it went away, maybe i'm just lucky.  

I would really consider ordering a CD from the ubuntu website, but of course, they will ship the 32-bit version, which is really no biggy since there really isn't that much difference between 32 and 64-bit with our Acers.

Anyways, don't give up, and good luck with your laptop!!

---

### Post by zmjjmz on 2009-01-13
> **LashSilence83 said:**
> So after a couple weeks without any issues, today I booted up my laptop to the familiar screaming (beeping) and it needless to say, it caused quite an awful disturbance in class. :(  I'm beginning to think that perhaps I should just go with another os until (if ever) this gets figured out. My laptop is essentially useless if I can't use it at school or in any other public place where insane beeping isn't too kosher. I have no idea what to do with this thing anymore. I installed mandriva one 2009 again and I'm having various aggravations with that. Hopefully I can get the kinks worked out before I end up smashing this thing with a sledgehammer. :mad:
I dunno, you could disconnect the PC speaker.

---

### Post by LashSilence83 on 2009-01-14
> **zmjjmz said:**
> I dunno, you could disconnect the PC speaker.

That idea was already being considered until after further investigation, I found that this laptop uses the same speakers for media as it does for the system. This is why it is so loud. It's like hearing that discordant system beep that we all know very well, only through boom box speakers, and repeated incessantly for about a minute.

---

### Post by LashSilence83 on 2009-01-14
> **FAMUgolfer said:**
> I have a 4530-5889 for about a month now, and yeah 8.10 can be a hassle.  Have you tried installing with the actual Shipit CD? I actually had a rather smooth install. It beeped when I first installed 8.10, but after a restart it went away, maybe i'm just lucky.  

I would really consider ordering a CD from the ubuntu website, but of course, they will ship the 32-bit version, which is really no biggy since there really isn't that much difference between 32 and 64-bit with our Acers.

Anyways, don't give up, and good luck with your laptop!!


I have shipit cds of all the various versions including the 64 bit ones. They are what I originally used for the installations. It's really a shame that I can't figure out what the heck is causing that beeping because otherwise everything else is fine. It just happens right after the grub menu and it says "invalid pblk length". It even goes on to boot normally after that. Strange stuff indeed.

---

### Post by russell5 on 2009-01-16
I have had this laptop for about 4 months now and i do love this laptop. Here is my experience. 

At first i tried to install 8.10 64bit and could not get the live cd to load. So i went with 8.10 32bit. That installed no problem and with little tweaking got everything working. 

I then decided to try opensuse11.1 64bit and everything went off without a hitch. I then found out i didn't like opensuse11.1 that much.  

So just the other day i installed 9.04 daily build 64bit with the text based installer. It installed no problem but on first reboot it did that horrible beeping, but would only happen every couple of boots. So what i did was remove "quiet splash" from menu.lst now it doesnt boot with that beeping so far. I am not sure if using the text based installer for 8.10 and removing that option form menu.lst will work for 81.0 but it might be worth a try if you want to use 64bit.

---

### Post by LashSilence83 on 2009-01-17
> **russell5 said:**
> I have had this laptop for about 4 months now and i do love this laptop. Here is my experience. 

At first i tried to install 8.10 64bit and could not get the live cd to load. So i went with 8.10 32bit. That installed no problem and with little tweaking got everything working. 

I then decided to try opensuse11.1 64bit and everything went off without a hitch. I then found out i didn't like opensuse11.1 that much.  

So just the other day i installed 9.04 daily build 64bit with the text based installer. It installed no problem but on first reboot it did that horrible beeping, but would only happen every couple of boots. So what i did was remove "quiet splash" from menu.lst now it doesnt boot with that beeping so far. I am not sure if using the text based installer for 8.10 and removing that option form menu.lst will work for 81.0 but it might be worth a try if you want to use 64bit.


I'm totally baffled as to how you achieved the opensuse11.1 install and was able to use it at all. When I did the install, everything went totally smooth until the first boot came and I was met with a black screen with only the mouse cursor. I tried to install a different version of the nvidia driver but failed because it was missing libutils and ld, neither of which could be installed by any means that I tried. Also, how in the heck did you manage to even get the 64 bit install cd's to boot at all? No matter what I choose with those, I get to about 10% and it stops. I'm wondering what it is that I'm doing wrong here? How could I be doing something wrong in the first place when the only thing is to choose different boot options until one of them works? I'm really confused as to how something with the exact same laptop could have totally different outcomes from me. It's not like the bios offers any real config options so I seriously doubt it's that. Besides, I've even switched those around as well. What is going on here?

---

### Post by russell5 on 2009-01-22
Well when i installed the 64 bit opensuse 11.1 i had used the network install with the minimal boot disk. 

It is really weird for the different outcomes.

---

### Post by LashSilence83 on 2009-01-24
ah, I see. I never did try to do any network installs with this thing. Perhaps that is the answer. As for now, I've been having no problems at all since I changed the boot option in the grub to not include the quietsplash part. I actually really like seeing the messages going by when I boot up so it's a win-win either way. Despite the fact that intrepid 32 bit is working fine, I think I will try out the opensuse network install just for the heck of it. "It's good to have options".   :)

---

