---
title: "Ubuntu install issue (Toshiba)"
date: 2017-05-15
forum: New to Ubuntu
---

### Post by MNKK on 2017-05-15
Hello all,

First and foremost, I'm completely new at this, and only trying it to see what else I can learn about computers. I'm ok when it comes to windows, but talking with a friend of mine this past weekend, he mentioned that I should try Linux (Ubuntu specifically). 

I tried to install Ubuntu (latest version) this past weekend on my Toshiba Satellite (will updated model after work). 

I did well as far as getting it onto a liveUSB, and was able to run through the Trial version well. However when I tried to select the Install version and ran through the whole process, it won't let me. When it gets to the end of the install process, and says to restart computer, I've tried completely powering down the laptop, removing the USB, turning power back on. I get to the copyright page, then it goes to an error. From that page, it will let me into the BIOS section, where I can insert the USB and back out, it will then load into Ubuntu.

Also, and since I'm on the subject... I feel this is a lost cause, but before I did all of this, I had some pics and documents on that usb. I moved them over to the desktop when it was on Win 10... I'm an idiot... I'm pretty sure, but wanted to ask, is everything gone now? I'm pretty sure in afterthought that some of my wedding photos were saved on that specific flash drive and the desktop in windows before I tried to do this install of Ubuntu...

again, please don't judge me if I'm using the wrong terminology on anything... not really into this yet. trying to learn.

---

### Post by TheFu on 2017-05-15
Welcome to the forums.

Hard to say if your photos are gone or not. Cannot tell what/how you did anything with the flash drive. Normally, the creating of a Linux boot flash drive wipes everything from the disk, so anyone on it is gone.  There are clear warnings about this, so I'm confident you were warned.  When you are new, read **everything** and don't continue if it sounds like something you might not want.  The language used is usually very clear.

Next, as a new user, you probably do NOT want to run the latest Ubuntu release. The latest release has less than 1 yr of support/patches.  Most people are better off staying with LTS releases - 16.04 is the current one. Start with that. It is more stable, like an old friend, and will get patches until early in 2021.  LTS releases happen every even year 8, 10, 12, 14, 16, .... 18 in April.  That's the 16.04.  Prior LTS releases were 14.04, 12.04, 10.04.  '.04' is April.  You'll see '.10' releases too. NONE of those are LTS. NONE.

You aren't an idiot. You are just ignorant about Linux methods and techniques. At some point we all were.  Nobody is born knowing these things and while it is reasonable to expect stuff you've learned from Windows to hold true, that is a mistake.  Linux is not Windows.  Linux is not OSX. Linux is not Android and Linux is not some proprietary Unix either, though many things do work the same on Linux and Unix and some OSX things work the same way too.  Windows is vastly different from all the other OSes.  All the others come from a Unix base - OSX and iOS are based on BSD.  Android is based on Linux, but with highly different configurations.

Ok - back to your install issues.  The best way to get help is to clearly specify your exact model of computer and use google "toshiba xxx42344 Ubuntu install" to see what others did. Most of the time, there is an easy answer.

In the meantime, you might want to do about 45 min of reading about the ways Linux is different with reasons for why that is true.  [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) - check out the first 2 links. Those are good beginnings for someone switching or even if they are just curious.

One of the most important ideas with Linux is having **backups of anything you don't want to lose**.  This is most important when you are new, since in the Linux world, you can completely trash your system by accident if you run commands without understanding each option.  
That isn't to say that Linux is easily broken, but as the installer, if you use 'sudo', then you can wipe anything. It is unusual for the system to question a command.  One of the core ideas in Unix/Linux is that the user is king. If you ask the computer to do something, even something foolish, it should do it anyway.  After all, the computer can't tell whether it is foolish OR genius.  There is a fine line between those to ideas. Sometimes I've crossed over the line, in each direction. ;)

"*I am only an egg.*"

---

### Post by Bucky Ball on 2017-05-15
Welcome. Firstly, no, you're not an idiot. We all started somewhere. ;)

Just a tip; one support request a thread is the protocol around here. Suggest you remove the stuff about trying to retrieve your pics from this thread and start a new one. Just gets confusing otherwise, cross-posting and what not. Just slows down the process of you getting help with your original issue.

As far as that goes here, put that USB aside, don't use it until you are ready to explore retrieving those files, and start with a new USB using 16.04 LTS, as suggested. That is supported until 2021 as opposed to for nine months (17.04 dies in Feb 2018 from memory). If this is not possible, forget about this thread for now and focus on a new thread about retrieving those files. Main thing: don't use that USB until you have done more research and are ready to retrieve files. Testdisk and/or photorec is probably what you want, but as I say, new thread for more help. Post a link to it here if you like.

Question about original issue: are you dual-booting (Win and Ubuntu) or intending this machine to run Ubuntu only?

---

### Post by MNKK on 2017-05-15
Thank you for the reply. 
 
I’m not sure what it was that I was thinking when I tried to back up the photos, docs, etc from the USB to the hard drive of the same computer that I was about to screw up… that was dumb… I suppose my best bet is to hope my wife doesn’t ask for the wedding photos… This is why I need to start using the cloud. Haha..
 
I’ll get the info about which model I’m using. I would guess, but it would be a miracle if that was right. Would there be any additional info that would assist you all in helping, that I could get before I post again? I’ll check here before I gather anything tonight or tomorrow morning.
 
When you say that I shouldn’t use the latest Ubuntu release. I did the download from their website, and I’m not sure that I saw an option to get the download for the LTS release. This should be easy to find through firefox, right? Is it something that I’ll be able to find the directions of how to get it onto the flash drive, and load up like this one?

Bucky, 

I intended to set this up as a dual-boot... however... That idea failed me at some point. When I went through the install process, it did not give me the option (may have the first time and I missed it?)

If I have the time tonight, i'll find another one of my USB drives and save those files to my new-ish external hard drive. THEN find the install info for 16.04 LTS release. I'll try that.

---

### Post by Bucky Ball on 2017-05-15
All good. To install a dual-boot, the safest way is to choose 'Something Else' at the partitioning section, NOT install alongside Windows. You have MUCH more control over what goes where and how big partitions are.

In your next post, perhaps give us an idea of what is already on the drive you want to use. How much disk space does Win take up? Preinstalled, Windows usually uses the whole drive so it will need to be shrunk to make free space for the Ubuntu install. This should be done with the Win disk management tool in Windows, NEVER with Linux tools like Gparted which is on the live session (Try Ubuntu). 

Always defragment the Win partition several times with the Win defragging tool prior to shrinkage. There are more powerful third-party tools which are more thorough than the Win one. Power ISO is one from memory (although it has been a decade or so since I used it!). ;)

Maybe you could also boot to a live session, launch Gparted and see what state your hard drive is now in. Win still there? You can post a screenshot of Gparted here (Go Advanced or Adv Reply and use the paperclip icon). That will give us a better idea of how to help you with the install.

(PS: Just noticed TheFu's link. [Here's another old chestnut]("http://linux.oneandoneis2.org/LNW.htm") along similar lines if you're interested.)

---

### Post by LastDino on 2017-05-15
During install, did you see something like "Something else" for installation type?

That is what you usually choose when you want to maintain your windows partitions/installs and make new ones for Linux according to requirement. 

Like Bucky already suggested, there is still hope, slightly thin but you never know.

Also, here is link for the mentioned LTS

[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

I would recommend going through torrent way as it keeps your ISO file intact and download is also fast enough.

Edit: Bucky beat me to it it seems. Damn refresh button >.>

---

### Post by MNKK on 2017-05-15
in response to the info on how much space win is taking up, and that info... When I take the USB out and boot the PC up, it goes to some sort of copyright page, then errors to a blue screen asking me to select one of three options; cd/dvd drive (I think theres a disk in there still i'll take it out), then two other options but their names escape me right now. Could this mean that windows is entirely gone? The PC used to have windows 7 but was upgraded to Win 10 when they released that (that was another headache and several windows forums posts)...

---

### Post by LastDino on 2017-05-15
If during your first installation attempt, you went with option "Erase disk and install Ubuntu"

Sorry to say but It is probably gone.

It will help if you could provide some images to see what is actually you're facing.

---

### Post by MNKK on 2017-05-15
I'll see what I can get for images later on. Will also collect the laptop info. 

Thank you all.

---

### Post by TheFu on 2017-05-15
The information we need is part of the 'boot repair' tool.  Running that will show everything we need and generate a URL with the data we need.  My signature has links to the Ubuntu pages about boot repair.

---

### Post by MNKK on 2017-05-15
Just thinking on this while I'm at work, and trying to ensure I have things correctly. Forgetting the USB data loss, and addressing the Ubuntu not installing permanently issue.

If I load the PC up and log in to the "Try Ubuntu" option, then establish an internet connection, could I then install the LTS release of Ubuntu on that same USB? Will doing so cause any issues? 
Or should I install and run boot repair before anything else?

---

### Post by LastDino on 2017-05-15
No, you can't install on same USB as you've booted Live. However, what you're referring to is called "persistence booting" where one can install OS on USB itself but I think you're not talking about that intentionally.

What you're probably referring to is getting new ISO from this Live USB through "Try Ubuntu" option and then turning the same USB bootable with new ISO. I don't think you can do that, at least not as far as I know.

Best option probably is to download the ISO on working PC with OS and then making the Bootable USB with this new ISO from scratch, things wont be complicated then, but then again you also have data loss issues with USB (to be sort out), so probably try different stick for that.

Or, use this USB to boot into from Try ubuntu and use to make different USB stick bootable with new ISO. Mind you, the more you use this USB it is more unlikely that you will recover your lost data

---

### Post by RobGoss on 2017-05-15
Are you asking can you install 16.04 on the same USB drive you are testing Ubuntu? if so the answer is no. When ever you burn the Ubuntu ISO file it uses the whole drive and will not allow you to install any other data until you format it again and start fresh

---

### Post by Bucky Ball on 2017-05-15
For now, just give us the bootinfo output link from boot repair or a pic from Gparted in a live session even.

Yes, Win might be gone, depending on how far you went, but my suspicion is that you've just messed up the Win boot and that can be repaired so focus might go there. Without more info much is hypothetical. ;)

---

### Post by MNKK on 2017-05-15
[http://paste2.org/](http://paste2.org/)

This is the link they gave me.

Computer info is:
Toshiba Satellite L675 

FWIW: the version of ubuntu that's running on the USB is 16.04.2 LTS. 

not sure what else you'd need.

---

### Post by bak&#305;r on 2017-05-15
The pastebin link that was posted is to nowhere but the home page. Also, when he/she says you can start the system by putting the back, it is  probably booting from the USB from scratch rather than the new installation.

An unequivocal description of the problem is missing, but the OPs situation is as if the boot priority is not set properly or related to secure boot. Does the error say "no bootable device?" What does it say?

Could you have a look into your BIOS settings and see if Ubuntu bootloader is recognised and at a reasonable level on boot devices list? "Two other options that escape you" probably were your hard drive partitions. Any signs of Ubuntu there? If no, you need to fix this.

Else, please check whether secure boot enabled. It sometimes blocks it.

---

### Post by TheFu on 2017-05-16
We need the link to be correct for YOUR system. "Boot repair" will create a custom link that is just for your setup. Without this, we cannot help.

---

### Post by MNKK on 2017-05-16
I ran the boot repair tool completely. That's what it gave me at the end. 
I'll try it again tonight and see if something else happens. 

I have to run to work now, but I took pics of the BIOS pages. Hopefully what you are asking about will be in there. I didn't see anything about ubuntu on any of them. 

When I looked at gparted yesterday, it was a large section that took probably 96% of the drive that was white, then two smaller sections that made up the rest of the drive. I can get specific on that if needed.

---

### Post by LastDino on 2017-05-16
> **MNKK said:**
> 
When I looked at gparted yesterday, it was a large section that took probably 96% of the drive that was white, then two smaller sections that made up the rest of the drive. I can get specific on that if needed.

Doesn't sound too good here, please be more specific as it is indeed needed and if possible after live booting run gparted and take image of what u see exactly.

---

### Post by MNKK on 2017-05-16
To post an image, it seems is different than other forums I'm on. Does the image need to be hosted online somewhere? Not able to just post it from my phone?

---

### Post by LastDino on 2017-05-16
Yes, posting as attachment should be possible through. Or better yet, use hosting sites, keeps image quality.

(That is how I do it usually)

---

### Post by Bucky Ball on 2017-05-16
Ok, the information we need to help you will be shown in the boot repair link. You DON'T run the 'Recommended Repair', you run the report. That will give you a link at the end of the process which we need posted here. Forget about providing us with any other info, BIOS shots and what not. Nothing to do with the info we are asking for.

I also mentioned this earlier from memory, but to post a pic use 'Go Advanced' or 'Adv Reply' and the paperclip icon in the taskbar there. You attach the pic there, don't insert it in the body of the post or link to some other site.

Good luck.

---

### Post by MNKK on 2017-05-16
I've installed and run boot repair twice now, with the same link both times. 

Installed - selected "Create a bootinfo summary", and that link was the outcome both times... It's not working for me.

---

### Post by Bucky Ball on 2017-05-16
Extremely odd is about all I can add. How about a screenshot of Gparted from a live session, as suggested very early on? How to attach it explained in my last post.

---

### Post by MNKK on 2017-05-16
[ATTACH=CONFIG]275141[/ATTACH][ATTACH=CONFIG]275142[/ATTACH]

Hope this works... it's the best I can do without a wifi connection at work.

The directions in boot repair link on your sig lines are easy enough to follow. I did this both times with the same outcome... Just that link is all that appears.

---

### Post by LastDino on 2017-05-16
> **MNKK said:**
> [ATTACH=CONFIG]275141[/ATTACH][ATTACH=CONFIG]275142[/ATTACH]

Hope this works... it's the best I can do without a wifi connection at work.

The directions in boot repair link on your sig lines are easy enough to follow. I did this both times with the same outcome... Just that link is all that appears.

You have wiped clean your native/windows os during your installation attempts along with any data on it, there is however, Ubuntu present on HD and has a signal partition as root and one swap partition. 

Now, what do you want to do? Install fresh one with right partitioning?

---

### Post by MNKK on 2017-05-16
I would like to be able to use the laptop without the USB attached to it. 

When I attempt this the following things happen. 

black page displays "Intel UNDI. PXE-2.1 (build 083) Copyright (C) 1997-2000 Intel Corp
This product is covered by ... copyrights...
Realtek PCIi FE Family Controller series v1.20 (01/26/10 PXE-M0F: Exiting PXE ROM.

then it goes to the blue screen displaying "Boot Menu" with options of 
CD/DVD  HL-DT-STDVDRAM GT30F
FDD
LAN

<ENTER BIOS SETUP>

I'd just like to know how i can get the install of this Ubuntu to stick so I can use the computer now.
I've tried the install twice (the first time apparently wiping any remnants of windows files). Neither one worked.


side note: is this why boot repair isn't displaying a real link? also,,, is there any possibility that there are any files left on there from windows? and recoverable?

---

### Post by MNKK on 2017-05-16
HEY! Just an update on this... 
I was texting with a friend of mine trying to see if he had any ideas..
while i was waiting for his response on something, I was poking around in the BIOS menus, and saw that there was an "!" next to HDD, but nothing next to the CD/DVD, FDD, or LAN options. I removed the "!" and hit F10... according to that screen, i removed the priority from the HDD from the boot up process (?)... It worked... I am now on the ubuntu sign in screen. 

I'm going to change the thread as [solved] for the time being. Thank you all. I'm sure i'll be back on here soon though. :)

---

### Post by Bucky Ball on 2017-05-16
Excellent news and thanks for marking as solved. If you need help with anything else be sure to post a new thread in the appropriate area for best results.

Good luck and enjoy. ;)

---

### Post by LastDino on 2017-05-16
> **MNKK said:**
> HEY! Just an update on this... 
I was texting with a friend of mine trying to see if he had any ideas..
while i was waiting for his response on something, I was poking around in the BIOS menus, and saw that there was an "!" next to HDD, but nothing next to the CD/DVD, FDD, or LAN options. I removed the "!" and hit F10... according to that screen, i removed the priority from the HDD from the boot up process (?)... It worked... I am now on the ubuntu sign in screen. 

I'm going to change the thread as [solved] for the time being. Thank you all. I'm sure i'll be back on here soon though. :)

Glad  to hear it, sometimes solutions are right in front of us and very easy. This is why I was asking for Image of BIOS. 

Welcome to Ubuntu family.

---

### Post by MNKK on 2017-05-17
I'm not sure you'll make it back on this thread, but thank you. The information you all linked me to was great, i enjoyed some of the articles, and actually learned some things. One of the articles uses a toy car vs. lego analogy. That was a good way to understand what i'm doing here. I want my toy car and my legos; I want to know what each block does and why. It'll take time, I know, but I'm really doing all of this to get away from Windows. I don't like it when someone does everything for me. Maybe I tend to question too much sometimes, and it irritates people. That's what I feel with Windows. 

Does anyone want to explain what was happening with this error, and why it was doing this?

---

### Post by LastDino on 2017-05-17
> **MNKK said:**
> I'm not sure you'll make it back on this thread, but thank you. The information you all linked me to was great, i enjoyed some of the articles, and actually learned some things. One of the articles uses a toy car vs. lego analogy. That was a good way to understand what i'm doing here. I want my toy car and my legos; I want to know what each block does and why. It'll take time, I know, but I'm really doing all of this to get away from Windows. I don't like it when someone does everything for me. Maybe I tend to question too much sometimes, and it irritates people. That's what I feel with Windows. 

Does anyone want to explain what was happening with this error, and why it was doing this?

Really simple, you had disabled HDD booting all together.  That exclamation mark indicates that, whichever device is marked with it, is disabled out of boot option.

;)

---

### Post by Bucky Ball on 2017-05-17
> **MNKK said:**
> Maybe I tend to question too much sometimes, and it irritates people.

Doubt that's going to be a problem around here! Unlike Windows, members of the Linux community rely on each other, not some faceless corporate. ;)

So ask away! (On a new thread, of course. :))

BTW, have you[ seen this]("https://ubuntuforums.org/showthread.php?t=1422475")? If not, have a read, taking particular note of point 1.

---

