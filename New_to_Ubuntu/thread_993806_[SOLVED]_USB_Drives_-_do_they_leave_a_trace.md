---
title: "[SOLVED] USB Drives - do they leave a trace?"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by cristo-father on 2008-11-26
Hi,

do usb drives leave a trace on computers they are plugged into? If so, is there any way to retrieve/delete that information?

cheers

---

### Post by MockY on 2008-11-26
Your intentions sound malicious  :)

---

### Post by cristo-father on 2008-11-26
> **MockY said:**
> Your intentions sound malicious  :)

why?

---

### Post by lisati on 2008-11-26
> **cristo-father said:**
> Hi,

do usb drives leave a trace on computers they are plugged into? If so, is there any way to retrieve/delete that information?

cheers
I don't know about Linux, but I'm pretty sure they leave a trace on Windows machines.

> **MockY said:**
> Your intentions sound malicious  :)

There's also privacy to consider but I don't thinks it's a big issue unless there's something nasty on the machine they're plugged in to.

---

### Post by cristo-father on 2008-11-26
oh btw, i am admin of that computer and only user.

---

### Post by halovivek on 2008-11-26
In windows you can find the trace in log files. but i have not done experiment in Linux. I will to do that one also.:guitar:

---

### Post by cristo-father on 2008-11-26
> **halovivek said:**
> In windows you can find the trace in log files. but i have not done experiment in Linux. I will to do that one also.:guitar:

Thanks. I will wait.:)

---

### Post by AnRa on 2008-11-26
Yes, in '/var/log/syslog'.

---

### Post by mjwhitfield on 2008-11-26
dmesg will show that a drive has been plugged in for sure.

---

### Post by loell on 2008-11-26
i think,
when you use nautilus to view files in your usb, it will generate a thumbnail  from any of these (picture / pdf / movie) and it will be stored in **.thumbnails** in your home directory, thus enough to hint some of the contents of the usb drive.

any corrections about this, is aprreciated. :)

---

### Post by Dedoimedo on 2008-11-26
Hello,

First, leave trace for how long?

There are many files that contain info on mounts, including /proc/mounts and /etc/mtab. Depending on your permissions, you may find your mounts there. And they might not be cleared until next reboot.

Furthermore, system log files will keep info on mounted hardware.

Are you asking about file access on mounted usb devices?

Dedoimedo

---

### Post by cristo-father on 2008-11-26
Thanks for all your answers.
Is there an app that can manage usb to avoid trace or any existance of info about files in usb and modifications to those same files. Or delete any info about files in usb and connections of the usb to the computer(this can be with usb unpluged).
Thanks once more.

---

### Post by cristo-father on 2008-11-26
bump

---

### Post by Olivier2371 on 2008-11-26
To answer your question if you have illegal files on your usb, there is nothing you can do to stop anyone to recover them, apart if your usb stick is encrypted with at least 1024 kb encryption cypher.

Using forensic tools you can easily recover files from HDD or USB stick.

---

### Post by cristo-father on 2008-11-26
Why are you talking about illegal files?....

---

### Post by keithweddell on 2008-11-26
Perhaps if you explained why you want to do this, no-one would jump to the wrong conclusion.

Keith

---

### Post by Olivier2371 on 2008-11-26
If we are not talking about Illegal files then the question is irrelevant.

PS: Don't worry I do not work for any government agency.

---

### Post by opscure on 2008-11-26
If you are looking for better security when it comes to things you do on your pc, then I would keep your current install (HD) for your normal activities and install a version of Linux on a thumb drive and boot to that when you want to keep things quiet.  This will load the OS and all logs/files/traces of your activities (including your thumb drive mounts) to the system memory.  Now, this isn't completely secure since someone could essentially use a cooling agent to keep this data stored on your memory chips long enough to do a data dump and find out all your dirty secrets, but you can hinder that by purchasing a lock for your computer chassis.  Then again some people can pick locks, so you may want to get a sold steel encasement for your computer chassis and weld it shut, you see where I'm going with this?  How secure do you want to be.  You may just want to stick with the thumb drive boot idea.

Good luck.

---

### Post by cristo-father on 2008-11-26
> **opscure said:**
> dirty secrets

Dirty secrets? wtf...
Ok, you wanna know why I want to do this?
If yes read below.

















Because they contain confidential info such as bank transfers,credit card info,personal info, etc...
Guess what? I might be ling, that is why imho this is absurd.
Why would you trust what i am saying?
Another question might seem to have very innocent applications, but might have a few that are extremely cruel ,malefic and not have passed the mind of those who answered that question.
Hope you learned your lesson(this is not directed to you opscure).

---

### Post by Olivier2371 on 2008-11-26
so if it is just for bank transfers,credit card info,personal info.

Just get an SD Card encrypt it and then put all these data on it.

Like that you can Keep it on you all the time.

---

### Post by NewJack on 2008-11-26
> **Olivier2371 said:**
> so if it is just for bank transfers,credit card info,personal info.

Just get an SD Card encrypt it and then put all these data on it.

Like that you can Keep it on you all the time.

Yes, then it wouldn't matter if your USB/SD Card leaves "breadcrumbs".

---

### Post by Olivier2371 on 2008-11-26
NewJack,

No it wouldn't.

But I try not to be to sarcastic.

---

### Post by NewJack on 2008-11-26
> **Olivier2371 said:**
> NewJack,

No it wouldn't.

But I try not to be to sarcastic.

Neither was I.

---

### Post by cristo-father on 2008-11-26
> **NewJack said:**
> Yes, then it wouldn't matter if your USB/SD Card leaves "breadcrumbs".

Care to explain why it would not matter? 
I am really curious...

---

### Post by cristo-father on 2008-11-27
> **opscure said:**
> This will load the OS and all logs/files/traces of your activities (including your thumb drive mounts) to the system memory.  

If i have a large(4 gb) usb can i store that data in the usb instead of the ram?

---

### Post by mbsullivan on 2008-11-27
Hi cristo-father,

> If i have a large(4 gb) usb can i store that data in the usb instead of the ram?

When he was talking about things being stored in the RAM, he was referring to (largely) temporary products, such as log files, the contents of files while you are editing them, etc. For things like these, you want them to be stored in memory, because it's very fast (and volatile, besides, which means it will wipe its contents after being powered off). You could still absolutely manipulate any files you had on the thumb drive, just like you would under a regular installation.

I think that you might be putting too much importance on the "breadcrumbs" that are left behind when you mount/unmount an external drive. The information that is left behind probably includes things like the log of times when the drive was attached and detached, and perhaps the manufacturer of your drive. It will NOT (in general) contain any portion of the data in your files, so long as you close all programs that were accessing that data.

For your credit card information, etc, I would simply store it in an encrypted folder on the drive, or encrypt the whole drive with filesystem level encryption. The information that will be left on your computer after unmounting the drive should be of no use to anyone who is interested in your personal information.

Mike

---

### Post by C.S.Cameron on 2008-11-27
If you are booting Ubuntu off a live thumbdrive I don't think they can leave a trace

---

### Post by NewJack on 2008-11-27
> **C.S.Cameron said:**
> If you are booting Ubuntu off a live thumbdrive I don't think they can leave a trace

Correct!

---

### Post by Mud.Knee.Havoc on 2008-11-29
> **cristo-father said:**
> 
Because they contain confidential info such as bank transfers,credit card info,personal info, etc...
Guess what? I might be ling, that is why imho this is absurd.
Why would you trust what i am saying?
Another question might seem to have very innocent applications, but might have a few that are extremely cruel ,malefic and not have passed the mind of those who answered that question.
Hope you learned your lesson(this is not directed to you opscure).

It doesn't matter if it leaves a trace on your system.  Somebody would need either physical or remote access (you could set up your firewall to reduce this possibility) and, even then, would only know that at some point you had used a usb thumbdrive.

If they wanted to steal your credit card info from your usb drive, they'd have to:
- get access to your computer
- check your logs
- see that you've used a usb drive
- somehow figure out that you keep your credit card info on it instead of somewhere else
- figure out where you live
- somehow figure out where you hide your usb key
- break into your house when you're not around
- steal your usb key

Wouldn't it be easier for them to just steal your wallet and take your credit card?  Or work at a gas station and copy down your credit card number at the register?

The initial request was indeed suspicious, as most people who are sole users/administrators of a system don't need to hide logs from anybody, since nobody else will have access to them anyway.

Finally, yes, there are definitely ways to see if people have been using usb drives on a system.  I don't want to contribute to potentially malicious activity, however, so you'll have to get help from somebody else.

---

### Post by phantomme on 2008-11-30
sorry to break in in your interesting discussion. I have however a similar question but from a completely different angle : The last few weeks I've been busy, as a complete newbie, trying to set up a linux system (xubuntu, as i have an old system) from which i would like to create a pendrive linux system for my children. Main reason : they're doing all kinds of "dangerous" things (from the point of view of downloading virusses or so thru chitchatting with friends ;-), and I do not want that they corrupt our "operational systems" on windows (configured as multimediacentre respectively banking PC). So I assumed that when they boot from a linux pendrive, my harddisks are not at all involved and do not store anything (actually, I could remove them). If ever my children "corrupt" their system, the only thing i lose is the USB stick. Your posts cast now doubt on my premisse.
Can you confirm I am correct in assuming that a pendrive system doesn't record anything on the harddisks ?
thanks in advance

---

### Post by C.S.Cameron on 2008-11-30
I switched my wife and kid's computers to Ubuntu two years ago and went from doing a weekly malware purge on each computer to none since.
Booting Ubuntu from flash drive is about as safe as you can get, unless you unplug the hard drive while they are using the computer.

---

### Post by mbsullivan on 2008-11-30
> If ever my children "corrupt" their system, the only thing i lose is the USB stick. Your posts cast now doubt on my premisse.
Can you confirm I am correct in assuming that a pendrive system doesn't record anything on the harddisks ?

Hi phantomme,

It's fine... booting from a USB drive won't record anything onto the harddrive. Your idea should work.

The main point of the preceeding discussion was that it is unnecessary to boot to a USB thumbdrive if your only objective is to protect certain files (containing credit card information, for instance). There are better ways to protect such information.

Mike

---

### Post by Mud.Knee.Havoc on 2008-11-30
> **phantomme said:**
> So I assumed that when they boot from a linux pendrive, my harddisks are not at all involved and do not store anything (actually, I could remove them). If ever my children "corrupt" their system, the only thing i lose is the USB stick. Your posts cast now doubt on my premisse.
Can you confirm I am correct in assuming that a pendrive system doesn't record anything on the harddisks ?
thanks in advance

Not exactly, but close enough.  You can mount hard drives while using a USB key.  All it takes it double-clicking the volume on your desktop.  As the OS on the usb key is Linux, though, you're safe.  You can click on bad stuff all you want and don't have to worry (especially if you don't have wine installed). EDIT: And even if you do, it's doubtful that you'd have anything to worry about.

If you're booting with a usb stick, it won't touch the hard drives (unless you mount them once booted).  The original poster was referring, I believe, to sticking a usb key into a running computer.  He was worried that somebody could look at the logs and determine that a usb key was plugged in sometime earlier.  This is different than what you're interested in.

EDIT: What you're talking about is pretty much the safest way to surf the net.  The only other option that I'd suggest is looking into cl33n.  It's a live linux cd that boots up and offers an instance of Firefox (and I believe there is also an instant messager).  So it doesn't even include all of the other things that make up a full "desktop" operating system - no word processing, no games, nothing aside from internet apps.  It just lets you surf the net safely, with no hard drive access, and no worrying about anything bad happening. Check out cl33n.com if you're interested.

---

