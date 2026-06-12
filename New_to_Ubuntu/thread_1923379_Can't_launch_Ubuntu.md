---
title: "Can't launch Ubuntu"
date: 2012-02-10
forum: New to Ubuntu
---

### Post by bedpotato on 2012-02-10
Help! I am an average semi-clueless newbie and suddenly have a problem. When I start my laptop it won't open Ubuntu but says "error: could not read file. Press any key to continue." And then pressing any key doesn't do anything. 

I have tried re-booting several times, tried removing the battery and putting it back in, and tried starting in recovery mode (although to be honest I don't even know what recovery mode really does but I just thought it sounded helpful)! but that just gives a longer, more specific error message in gobbledegook. I can't take a screenshot of the recovery mode error message because I can't access my computer, but I took a photo of it on my phone. Do I need to type the error message here so you can advise me, or is it not relevant?

Please can somebody tell me what to do? Why has this happened? Did something break?

Do I need to re-install Ubuntu?

Thank you.

---

### Post by jamesisin on 2012-02-10
Yes, please do post the longer error message.

Are you able to boot your system using the Live CD still?

---

### Post by bedpotato on 2012-02-10
USB 1-1: new high speed USB device number 2 usi g ehci_hcd
Autodetecting RAID arrays. 
Scanned 0 and adding 0 devices. 
Autorun...
...autorun DONE. 
Cannot open root device "UUID= 1708....(lots more digits) or unknown block (0.0)

Please append a correct "root" boot option: here are the available partitions:
Kernel panic - not syncing: VFS: unable to mount root fs on unknown block (0.0)

I haven't tried using a CD, no. I thought the CD was only for installation. 

Thank you for replying. :)

---

### Post by jamesisin on 2012-02-10
Nope.  The installation disc is a fully functioning version of the operating system and it can be very useful in diagnostics and recovery issues.

---

### Post by bedpotato on 2012-02-10
Oh I see! Is there any special procedure I need to follow or do I just put the CD in? Thank you for helping. Does my error message make any sense to anybody?

Update: I put the CD in and it's reached the part where it asks me if I want to TRY or INSTALL. I don't think either of those is what you meant.

 What should I do next? :(

---

### Post by jamesisin on 2012-02-10
Try.  That just runs the OS from RAM and the disc.

---

### Post by bedpotato on 2012-02-10
Ok thank you. I clicked TRY and have a desktop now. How do I diagnose the problem? Do I have to type something into a terminal? Please can somebody tell me what to type? Thank you.

---

### Post by jamesisin on 2012-02-10
One thing you might try is mounting the HDD and see if you can run any diagnostics on that drive in case there is a physical problem.  You should see the internal drive listed under Places.

If you click on it Ubuntu will attempt to mount that drive.  (With the drive mounted you can make changes to it so do be cautious.)

Some diagnostics may require that the drive be in an unmounted state, but try mounting it first to see if that's even possible.

I found a mention of this error here:

[http://ubuntuforums.org/showthread.php?t=1582485](http://ubuntuforums.org/showthread.php?t=1582485)

I don't know how closely that matches your situation though.

---

### Post by collisionystm on 2012-02-10
> **bedpotato said:**
> Help! I am an average semi-clueless newbie and suddenly have a problem. When I start my laptop it won't open Ubuntu but says "error: could not read file. Press any key to continue." And then pressing any key doesn't do anything. 

I have tried re-booting several times, tried removing the battery and putting it back in, and tried starting in recovery mode (although to be honest I don't even know what recovery mode really does but I just thought it sounded helpful)! but that just gives a longer, more specific error message in gobbledegook. I can't take a screenshot of the recovery mode error message because I can't access my computer, but I took a photo of it on my phone. Do I need to type the error message here so you can advise me, or is it not relevant?

Please can somebody tell me what to do? Why has this happened? Did something break?

Do I need to re-install Ubuntu?

Thank you.


you need to boot into recovery mode and choose FSCK check file system.

You may need to first choose the option to Mount existing file system before it appears

---

### Post by bedpotato on 2012-02-10
Thank you very much to the people who've tried to help me but you are assuming in your answers  that I know what you are talking about, and I don't. I am not very knowledgable about computers so your answers leave me none the wiser. Please can someone help me in simple terms and tell me HOW to do the things they recommend, as well as just recommending I do them? I would be very grateful. Thank you. e.g. I don't know what "mounting a HDD" means and I don't know how to "run diagnostics" which is why I'm asking for help/instructions doing so.

 I already explained what happened when I tried using recovery mode. I got a funny error message. 

I already did a Google search for the error message and it brought up some threads like the one you link to, but they all seem to be about people who were in the process of installing Ubuntu, whereas mine was already installed and running smoothly up to now and I don't know why it's suddenly gone wrong. 

Thank you for trying to help me and please be patient with me for not knowing all the terminology.

---

### Post by jamesisin on 2012-02-10
HDD simply means HarD Drive.  It's a common shortened form; you'll see it often.

In order to mount the drive (attach the drive to your running system) you will want to click on Places and locate it by name.  I don't know what it's called but it should be the only drive listed there.  You should find it below Computer and above Network.  Just click it.  Then it should appear as an icon on your Desktop and a window should open revealing its contents.

Above collisionystm has recommended one such diagnostic (fschk).  There are others but that's a good place to begin.  This is one you run from a command line (fear not!).  You can open a terminal to run this command by going to Applications --> Accessories --> Terminal.  Just type it in and hit Enter.  I'll leave it to collisionystm to recommend how to make fschk function.

Do let us know if Ubuntu is not able to mount the drive in question (or if no drive appears under Places).

---

### Post by LinuxFan999 on 2012-02-10
You can also open the disk utility (System-->Administration-->Disk Utility) select the hard drive, and click "SMART Data", and View information collected by the Hard Drive, which can tell you if it is about to fail. I would also recommend that you run n extended self-test on the Hard Drive (it will take a while).

---

### Post by bedpotato on 2012-02-11
Thankyou for the replies!

I thought the abbreviation for hard drive was HD. I didn't know it was HDD as well!

I will try some of those suggestions later - thank you - but right now I have given up and am having a break from the whole issue! It's all far beyond my capabilities. 

I have a feeling I am going to have to re-install it. Would that fix the problem?

---

### Post by bedpotato on 2012-02-11
> **jamesisin said:**
> 

Above collisionystm has recommended one such diagnostic (fschk).  There are others but that's a good place to begin.  This is one you run from a command line (fear not!).  You can open a terminal to run this command by going to Applications --> Accessories --> Terminal.  Just type it in and hit Enter.  I'll leave it to collisionystm to recommend how to make fschk function.

Do let us know if Ubuntu is not able to mount the drive in question (or if no drive appears under Places).

I typed Fschk into a terminal and it said it didn't recognise it. Then I checked your post against collisionystm's post and realised you had added in an extra letter so I typed FSCK instead like collisionystm said, and it didn't work either. Then I tried typing it in lower case like this: fsck. It didn't tell me it didn't recognise it, but it didn't DO anything either. All it says is this:

ubuntu@ubuntu:~$ fsck
fsck from util-linux 2.19.1
ubuntu@ubuntu:~$ 

What is that supposed to tell me? I don't understand.

Also I will keep looking but so far I have not found anywhere that says Places, neither is there a folder called Administration when I go to System, so I can't click on the elusive hard drive the way you're all telling me to do. :(

In this similar thread here, the person was advised to type* lspci -nnk* and *sudo fdisc -l *into terminals and also *Boot up off Live CD, run **garted** and check that the Ubuntu partition has the "Boot" flag set*

[http://ubuntuforums.org/showthread.php?t=1909802](http://ubuntuforums.org/showthread.php?t=1909802)

but although that thread was from someone who got the same error message as me, their circumstances were different because they were in the process of installing whereas mine is already installed.

Are those things relevant to me as well? Should I do them? 

>  In order to mount the drive (attach the drive to your running system)  you will want to click on Places and locate it by name.  I don't know  what it's called but it should be the only drive listed there.  You  should find it below Computer and above Network.  Just click it.  Then  it should appear as an icon on your Desktop and a window should open  revealing its contents.
Edit: 

Below Computer and above Network, I have:

Home
Desktop
Documents
Downloads
Music
Pictures
Videos
File System
Trash

and File System sounds like the most related to Hard Drives, right?  but when I click on File System there are just loads of folders with names like bin, boot, cdrom, dev. Is it in one of those folders?

Oh dear. I wish someone was here to do it for me in person! When I click on System there is NOT anything that says Administration. :(

Just to be clear: can someone please help me understand the error message that I got? If my computer has a "file error" does that mean there is something wrong with the Ubuntu software, or does it mean there is something wrong with my hard disc - i.e. hardware? 

If the problem is with Ubuntu then I reason that I could just re-install Ubuntu and start afresh, but if it's a problem with my hard disc then that won't do any good and I might need to take my computer back to the computer shop.

Thank you

---

### Post by jamesisin on 2012-02-11
This is sounding more like a hard drive problem.  Your drive should appear under places when the live CD is running.  If it doesn't that means that the live CD isn't recognizing it.

You can try gparted and Disk Utility to see what they can see.  They are both located under **System --> Administration**.  You can try the test LinuxFan999 suggests above (using Disk Utility).

I don't think Linux cares about the boot flag; I think that's a Windows thing.  Someone can correct me if I'm wrong, but that's my impression.

If you can get gparted to recognize the drive you will see there are at least three entries (partitions) on that drive.  Make sure the one showing as ext4 (or ext3) is the one with the boot flag.  (Right-click on ext4 and choose Manage Flags I believe.)  No other flags should be selected and the other two partitions should not be flagged at all.

As to fsck, you will run it with specific arguments (such as fsck -a).  I'm not that familiar with the use of fsck so I'll again leave it to someone else to give you detailed advice.

Incidentally, there is one command you will want to memorize and that's man.  If you type man [anycommand] it will give you the manual page for that command.  Try *man fsck* and you can peruse the manual for fsck.

---

### Post by bedpotato on 2012-02-11
Thank you for replying but I don't have a clue what gparted or bootflags actually are. I was only quoting from another post to ask if it was relevant to me but please don't let that make you think I know what those people were talking about, because I don't! Also I've already explained I can't see anything called Administration when I go to System. I am looking in the System that is one of the things that shows up when I click on the thing that says Home. Is that the same System you are all talking about, or is there another System that you are all accessing in a different way? If you don't tell me where or what "System" is and how to get there, then I might be doing it wrong. 

I am grateful to those who are trying to help but PLEASE IS THERE ANYONE who is capable of talking in language of a non-expert and can tell me what to do? This is all Greek to me. I need step-by-step instructions that do NOT assume I will know everything, because I know nothing! e.g. screenshots showing me where all these things are, or specific directions of what buttons to click on and where they are, rather than just saying the name of the button, would be helpful to me. I am sorry if that sounds demanding or pathetic but I am a hopeless female all alone and have a mental disability too, and don't know much about computers and I'm really upset about this problem and this forum is my only place to turn for help! Please help, somebody! :( Thank you. 

I find the "man" command to be most relevant and humorous! A man is what I need right now, indeed! A nice man to come and fix my computer for me! Right, I'll try typing that. 

Man

Man

Man!!!!!!!!!

It didn't work. LOL Sorry I will be serious again now.

---

### Post by jamesisin on 2012-02-11
Which version of Ubuntu did you download?  (ie: 10.04, 11.10, &c)

---

### Post by bedpotato on 2012-02-12
It was 11.10.

---

### Post by jamesisin on 2012-02-12
Sorry, I've been giving you directions according to the desktop environment Ubuntu used to use (Gnome 2) and I believe even the live CD of 11.10 is running the new one (Unity).

You can run GParted by typing this command from a terminal:

```
gksudo gparted
```

Not sure how to get a Terminal since I don't use Unity.  It's icon usually looks like a little monitor with a black screen in case you see that.  If you can search for applications then search for terminal and run that.

One you have GParted open you can make changes to the partitions by right-clicking on the one you want to alter and my instructions for doing so above should be useful.

The boot flag selection is (of course) under Manage Flags but it should also be listed under the Flags column in the main GParted window.  As I said above the File System shown as ext4 (or perhaps ext3) is the one you want marked as boot under Flags.

Disk Utility is actually called palimpsest:

```
gksudo palimpsest
```

It's layout is more user-friendly than that of GParted.  Select the drive in question on the left, and information and useful buttons appear on the right.  The diagnostic instructions above (concerning Disk Utility) will become apparent once you have it open and your drive selected.

The only thing that remains is fsck.  Here is some (hopefully) useful information about running that utility:

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

### Post by bedpotato on 2012-02-12
Thank you very much for persisting in your efforts to help me! I am very grateful to you. 

One of the few things I do know how to do is open a terminal, so as soon as I can I will try out your suggestions! (I am not at my computer right now).

Thank you!

---

### Post by bedpotato on 2012-02-13
I tried Gparted and it opened successfully but I have NO idea what all the things mean or what on EARTH I am supposed to be doing. It's like giving a page of advanced algebra to someone who hasn't even learned to count up to 10. I couldn't do anything with it because I didn't know what I was meant to do. I tried taking a screenshot of what it looked like, so as to come on here and ask what things I was meant to be clicking on, but even the screenshots weren't working properly! :(

I really know nothing about any of this and am getting more and more frustrated that nobody here can help (or, rather, that I am not able to carry out the advice being given). I know you are all trying your best but it's too complex for me and I am still stuck with a broken computer. 

As I see it, here are my options:

1. Try re-installing Ubuntu (but no one has answered my question about whether the error message was related to my hardware or my software, so I don't know if this would even do any good).

2. Take my computer to the computer shop and pay loads of money for them to fix it.

3. Try and find a Linux expert in my local vicinity and ask if they will fix it for me free of charge.

4. Buy a new computer (Not AGAIN)!

My preferred option was to try fixing the computer myself with instructions from the Internet, but this option has totally failed. I do not have enough technical knowledge to interpret and carry out the instructions. :(

What can I do, what can I do? I want Ubuntu back! I don't want to have to go back to Windows.

---

### Post by s.fox on 2012-02-13
Moved to [Absolute Beginner Talk]("http://ubuntuforums.org/forumdisplay.php?f=326") at the request of OP.

The OP was having trouble understanding the instructions given in the general help section.

---

### Post by verymadpip on 2012-02-13
Hello bedpotato.
If your keyboard has a windows key on it press that & it will bring up the Unity "dash" (dashboard I think...& no I don't really know why it's called that :)).

In the upper leftish there should be a text entering box with "search applications" in it.  In that box type "disk" (without quotes) & from the options presented click on "Disk Utility".

That should open a window with a panel down the left hand side containing stuff to choose from, & the bigger pane on the right will contain the information about whichever device you've selected from the left pane (one click will select it).

I'd click on all the entries one at a time until you can find your HDD (**H**ard **D**isk **D**rive I think) which you should be able to identify from its size & file system type which is displayed in the right pane of the Disk Utility window in the form of a rectangular box with some text in it.  *Probably* something like 250Gb  ext 4, of course the exact text may be different for you.

Once you've found your HDD you can check its health by using the smart data facility which is above to the right of the rectangular box representing your HDD.

It's a pretty blunt tool, so to speak, but it will tell you if you've a problem with the HDD.

---

### Post by bedpotato on 2012-02-13
Oh thank you very much verymadpip!

I managed to follow your instructions and it said: 

Overall Assessment: Disk has a few bad sectors.

For all the individual bits everything said "OK" or "N/A" apart from the Current Pending Section Count, which came up with a red message saying Warning. :(

Normalised: 100. 
Worst: 100. 
Threshold: 0.
Value: 16 sectors.

Does this make any sense to anyone? 

Does it mean 16 things have broken?

Please can you tell me what I have to do now?

Thank you very much indeed! :)

---

### Post by verymadpip on 2012-02-13
I suspect that 16 bad sectors means there's a problem with the HDD, which will probably get worse over time.  It could last for a long time yet, then again, it may not.  If you've any valuable data on the HDD I'd suggest backing it up to an external medium (USB drive, CDs, DVDs etc) as soon as possible.

Is the machine a desktop box or a laptop?  Replacing a HDD in a desktop rig is pretty straightforward, with a laptop I'm not so sure though.  

As a slight aside; I had an old laptop with bad sectors on the HDD which I used for quite some time before it gave up.  Actually I don't think  it wasn't even the bad sectors that finished it off in the end. It was more to do with the stupidly heavy blow it took which broke the screen & some other internal stuff :) * I must stress there was no data of any value on that box.*
I recovered some sectors at one point by zero writing the HDD, but I think a new drive is probably in order.  (I'm told zero writing a drive can be risky if you want to use it again - clearly the computer gods were with me that day).

Sorry I can't give you any better news bedpotato, maybe someone else can think of something.

---

### Post by bedpotato on 2012-02-13
Oh dear. Thank you for telling me. Well, it's quite a new laptop. I've only had it for a few months. I suppose I will have to take it back to the shop and get them to fix it for me. 

I have got all my stuff stored externally already so that's not a problem. There is only one document I hadn't backed up. It is stored on my "Home" folder within Ubuntu but I can't access any of that at the moment because Ubuntu won't open. I can only access the trial version via the CD but I cannot access the version I had installed. I guess that document is lost. Never mind. It wasn't very important. 

Thanks for your help. :)

---

### Post by verymadpip on 2012-02-13
It being new is good news :) & yeah, they should fix it for you

Can you not get into the Home folder from the Live CD?  If you open the file browser (Nautilus) in the Live CD it may show you a "xxxGb File System" in the left hand pane.  It may still be possible to recover that one document too.

I'm out for a few hours now, but I'll check back when I get home later to see how things are going.

---

### Post by bedpotato on 2012-02-13
Thank you but there doesn't seem to be anything there. I can't see anything that says xxxGb File System, but when I click on Home, I can open folders like pictures, documents etc. There is nothing there at all.

---

### Post by winh8r on 2012-02-13
Hi, I am hoping i might be able to help you a little here.

You have got the Live CD running and have a desktop in front of you, if you remember yesterday or the day before when you opened the Menu where you found "FILE SYSTEM" and it had all the folders like boot and etc and usr?

Well try to get back to there and look for a folder called home, if you open it you will see you user name and if you open that folder you will see all your original desktop folders where your document is stored (I hope)

I am not sure what version of Ubuntu you are running but if there is a menu bar at the top left of the screen, you need to go into 

Places> 
And look for the Hard drive icon ( a silve/white thing) which will be labelled <number>Gb Filesystem.

Give it a try and let me know hwo it goes.

---

### Post by bedpotato on 2012-02-13
Thank you Winh8r (I like your username by the way; I didn't understand it until I said it out loud)!

I tried following your first set of instructions, but when I go to File System and click on the folder called home, there is no folder with my username. It just opens up the same folders as before, with pictures, documents, etc, and they're all empty.

As for your second set of instructions, I still can't see anywhere called Places... :confused:

---

### Post by winh8r on 2012-02-13
okay, no problem.

i have booted into 11.10 now so that i can see what you see, sort of!

On the icon panel down the left side of the screen, move your mouse down over the icons towards the bottom.

Before you get to the trash/wastebin there should be an squarish looking white icon. when you hover over it , you will see a number followed by the GB symbol and the word Filesystem.

This is where you need to click.

it will open a window with a folder in it which should be the same name as you used when you installed Ubuntu on your computer.

Open this folder and look for the one named home

this should be the one where all your files are, and you can get anything that you need , and copy or move it to an external drive or a cd/dvd.



If you still cannot find it with the instructions above then try going to the top of the icon stack again, click on the orange folder with the house on it (this is the home folder of the system running from the cd) click on it and open it.
At the top left of the window, you should see the word "Devices@ at the top of the menu list.

The device listed in there should be your Hard Disk Drive . open it and look for the home folder as above .

Thanks for being patient while we try to help you.

---

### Post by bedpotato on 2012-02-13
Thank you! I was able to do it by the second method you described. I've got my file saved externally now. Now I can take my laptop back to the shop and see if they will fix it for me. 

Thank you to all the kind people who've spent time helping me in this thread! 

Should I mark it "solved" now, or do I not do that until my computer is mended again?

 :confused:

---

### Post by winh8r on 2012-02-13
Well, it might be better to mark it as solved since we have done all we can do for now.

You can always start a new thread once you get your computer up and running again.

Glad we could help you this far.

Good Luck and thank you for staying with it to the end!!!

---

### Post by bedpotato on 2012-02-13
It is you who should be thanked, for *you* were the patient one in kindly helping me! :)

Thanks again. :D

---

### Post by verymadpip on 2012-02-13
Sorry I got back so late.

Good to see winh8r was able to help & that all is as well as it can be for now ;)

Good luck with Ubuntu :)

---

### Post by winh8r on 2012-02-14
> **verymadpip said:**
> Sorry I got back so late.

Good to see winh8r was able to help & that all is as well as it can be for now ;)

Good luck with Ubuntu :)

I am glad that we got somewhere in the end! Although I did say to bedpotato that I cannot claim credit for the solution, I just stepped in at the last minute and carried on the good work that had been done by you and the other members before you.

I suggested marking the thread as solved as we had gone as far as we could regarding the laptop as it is going to the repair shop.

Well done all!!

---

### Post by bedpotato on 2012-02-14
Thank you for checking back on me, verymadpip! :) You were most helpful, too! What kind people.

---

### Post by jamesisin on 2012-02-15
Glad you sorted it out.  Cheers.

---

### Post by bedpotato on 2012-02-21
I hope I'm not breaking forum etiquette by bumping a solved thread to update it...

The computer shop have just told me over the phone that the hard drive has indeed broken and they're sending away for a new one for me under warranty. I only bought this laptop in December!! I'm really shocked it broke so fast! 

So I am definitely going to have to reintall Ubuntu then. Everything will start from scratch. Oh dear...

Edit: thank you, jamesisin, too! I just noticed your wee message at the end there. :)

---

### Post by verymadpip on 2012-02-21
Hey bedpotato.  I don't know about the etiquette, but I'm pleased you let us know what's happening.

I know this has cost you some time & inconvenience, but at least not any money.  Sometimes stuff like this happens - the trials of life ;)

If you need any help with the new install don't hesitate to start a thread.

---

