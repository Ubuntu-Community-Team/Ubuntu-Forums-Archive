---
title: "Help: Messed Up My System"
date: 2011-12-10
forum: New to Ubuntu
---

### Post by danmartin555 on 2011-12-10
Hello,

Hope you can help me. Yesterday I was trying to create a partition but the tutorials I was finding online weren't exactly matching up to what was happening on-screen. So I quit what I was doing but on exiting it said changes will update when the system is restored.

Now this morning, I turn it on and I get this error message:

GRUB loading stage 1.5

GRUB loading, please wait.......
Error 22.

I can't find out what this means. Drawing blanks. I know I should have remembered how to create a partition but last time I did it was 2 years ago. 


Any help would be much appreciated.

Dan

---

### Post by danmartin555 on 2011-12-10
[http://ubuntuforums.org/showthread.php?t=1842330](http://ubuntuforums.org/showthread.php?t=1842330) ok found this but it still doesn't really help me. I need to reboot from a CD? Might as well change to Lubuntu then, as I was planning on doing that. 

Last silly question: will I lose all of my files from before?

---

### Post by bluexrider on 2011-12-10
> **danmartin555 said:**
> Hello,

Hope you can help me. Yesterday I was trying to create a partition but the tutorials I was finding online weren't exactly matching up to what was happening on-screen. So I quit what I was doing but on exiting it said changes will update when the system is restored.

Now this morning, I turn it on and I get this error message:

GRUB loading stage 1.5

GRUB loading, please wait.......
Error 22.

I can't find out what this means. Drawing blanks. I know I should have remembered how to create a partition but last time I did it was 2 years ago. 


Any help would be much appreciated.

Dan
Dan,

What you didn't mention is what kind of computer you were running as in Dell, HP or whatever and the model would be nice too. Along with some sort of info as to the distro that you want to repair.

Please only post references that help, otherwise can be confusing.

This could be helpful.

Thanks

---

### Post by lolpenguin on 2011-12-10
Maybe the partitioning tore apart GRUB into different sectors.

---

### Post by danmartin555 on 2011-12-11
emachines (crappy)
1.6GHz
160GB
1GB DDR
Intel 230

9.04 Jaunty - I know it's old but that's why I want Lubuntu (and because the system is low spec)


It's just a cheapy but I need to work today and can't. I'm downloading Lubuntu on a neighbours computer, but it's the work I did yesterday I'm worried about. I use Dropbox but hadn't backed it up from Friday onwards.

Thinking about it now, I think I created a new partition and then deleted it as I didn't do it properly, but this must have affected the whole system. 

Apologies for my lack of knowledge but I just prefer Ubuntu (hate Windows) but when it comes to all of the techy stuff (or simple stuff) I fail miserably. Thanks in advance.

---

### Post by danmartin555 on 2011-12-11
Any help would be really appreciated. I've tried burning Lubuntu onto a disc and I just get the same error message as above. Can't really do anything with the computer other that go into the system menu but I can't see what I can do to fix the problem.

Can I not just start all over again? Or have I completely broken something?

---

### Post by cryptotheslow on 2011-12-11
No, nothing is completely broken.

Provided you haven't done anything more than create and then delete a partition - then TestDisk should be able to recover things back to how they were.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)


When you try to boot from you Lubuntu disc (I presume you mean CD) - does it even attempt to boot from the CD? i.e. can you hear the CD spin up? If not you may need to make a change in your computer BIOS (probably what you are calling the system menu) to boot from the CD drive first rather than the harddrive.

Also - how did you burn the Lubuntu image file to the CD? e.g. depending how you do it - it is possible to just end up with a copy of the .iso file on the CD rather than the image being extracted and burnt to the disc.

---

### Post by danmartin555 on 2011-12-11
> **cryptotheslow said:**
> No, nothing is completely broken.

Provided you haven't done anything more than create and then delete a partition - then TestDisk should be able to recover things back to how they were.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)


When you try to boot from you Lubuntu disc (I presume you mean CD) - does it even attempt to boot from the CD? i.e. can you hear the CD spin up? If not you may need to make a change in your computer BIOS (probably what you are calling the system menu) to boot from the CD drive first rather than the harddrive.

Also - how did you burn the Lubuntu image file to the CD? e.g. depending how you do it - it is possible to just end up with a copy of the .iso file on the CD rather than the image being extracted and burnt to the disc.

Yes, you're correct disc + BIOS menu :) I'm reburning onto a new CD now as just noticed that I have to do it a certain way. I get no response from then computer other than the error message or the option to go into BIOS before the error message pops up.

So, once this CD has the image on it then Lubuntu will start up? Fingers crossed.

---

### Post by cryptotheslow on 2011-12-11
Yes - it very much sounds like the problem you have right now is that the image was burnt incorrectly to the CD. Once done the correct way, the PC should bootup fine from it.

That will get you to a working desktop at least.

Once at that point it would be useful if you could attach a screenshot from GParted here so we can see what partitions are currently on your harddrive. That will help us guide you to a (hopefully) successful recovery - or at least recover the files you need before you go on to actually install Lubuntu.

n.b. Don't proceed to installing Lubuntu before you have recovered your files - that will most likely make recovery of them impossible.

---

### Post by danmartin555 on 2011-12-11
> **cryptotheslow said:**
> Yes - it very much sounds like the problem you have right now is that the image was burnt incorrectly to the CD. Once done the correct way, the PC should bootup fine from it.

That will get you to a working desktop at least.

Once at that point it would be useful if you could attach a screenshot from GParted here so we can see what partitions are currently on your harddrive. That will help us guide you to a (hopefully) successful recovery - or at least recover the files you need before you go on to actually install Lubuntu.

n.b. Don't proceed to installing Lubuntu before you have recovered your files - that will most likely make recovery of them impossible.

Thanks, I really appreciate you helping here....however, even now I still get the Error 22 message...no different to before. I take it I just run the CD straight from starting up? If so, that doesn't work. If there's something different, then I don't know...

---

### Post by cryptotheslow on 2011-12-11
Yes - put the CD in the drive and restart the PC e.g. power it off then on.

The GRUB error 22 popping up still, means it is still trying to boot from the harddrive.

Have a look in your BIOS settings for something called Boot Order or Boot Priority - something of that sort that determines what drive the PC boots from first and make sure the CD drive is before the harddrive.

Other than that - are you sure the CD burnt correctly this time? Will it boot up on any other PC? (You can test it on any other PC, it won't install or change anything on that PC unless you select the Install option - which would be unwise if trying it on a friend's PC :D )

---

### Post by danmartin555 on 2011-12-11
> **cryptotheslow said:**
> Yes - put the CD in the drive and restart the PC e.g. power it off then on.

The GRUB error 22 popping up still, means it is still trying to boot from the harddrive.

Have a look in your BIOS settings for something called Boot Order or Boot Priority - something of that sort that determines what drive the PC boots from first and make sure the CD drive is before the harddrive.

Other than that - are you sure the CD burnt correctly this time? Will it boot up on any other PC? (You can test it on any other PC, it won't install or change anything on that PC unless you select the Install option - which would be unwise if trying it on a friend's PC :D )

Hi, yes, I had to disable it from booting from the HD and it loads up the Lubuntu screen :guitar: - next question so I don't wreck it even more...I just "try" Lubuntu first then I'll add a screenshot for you. I have backed up my files apart from Friday and Saturday's work on Dropbox so I'm not *too* bothered if I can't recover it. I just need a working computer....and I'll be running into the early hours by the looks of it.

EDIT: the Lubuntu screen comes up but no matter what I press nothing happens. I can scroll up and down the screen but as soon as I choose anything I can't scroll, the CD doesn't spin and nothing happens...

---

### Post by cryptotheslow on 2011-12-11
So you actually get to the Lubuntu desktop? Then it stops responding?

What are you "pressing"?

When in this state do the Caps and Num Lock lights toggle on and off when you use their respective buttons on the keyboard? (If not the PC is hard locked up).

Bear in mind it can take a fair amount of time to fully boot up when booting from a LiveCD.

I have to go out and do some work on the car now before it gets dark (car's always seem to choose the coldest shortest days to malfunction when you have no garage to work in! :( ).

I'll be back in a couple of hours max. Might be worth downloading a different LiveCD image - maybe the Ubuntu 10.04LTS one as your PC was previously working OK on 9.04 and trying that.

Back soon to pick up on this - unless someone else steps in in the meantime :)

---

### Post by danmartin555 on 2011-12-11
Sorry - I'm pressing [enter] to start the [try lubuntu] option. I've tried installing it too but after about 10 minutes I get an error code in green scrawly writing across the top the screen saying error in sector [then some unreadable numbers I think]. The keys don't move anything after I've selected an option. Just locks up. I'm guessing there is either something wrong with the CD or Lubuntu just doesn't want to work on my PC.

I'm downloading 10.4 Ubuntu now but it's taking forever as I live in a stupid country where the Internet switches on and off like a light switch.


Oh and as an ex-mini and mk2 escort owner, I know alllll about cars + winter = freezing, swearing, bloody hands, anger etc :)

Thanks for your help and hopefully I can make this work...

---

### Post by critin on 2011-12-11
> I have backed up my files apart from Friday and Saturday's work on Dropbox so I'm not *too* bothered if I can't recover it.Did you do this with a live CD?

---

### Post by winh8r on 2011-12-11
Make sure that you burn the .iso image to the disc at the slowest possible speed to prevent errors, then run an integrity check on the disc on your neighbours PC. If you eliminate the potential errors one at a time you will get it sorted much faster.

Also, if you want to recover anything from your HDD, avoid using it , that way you will have a higher chance of a successful recovery process.

Be nice to your neighbours, and remember to drop them in a couple of bottles at Christmas!!!

---

### Post by cryptotheslow on 2011-12-11
Hmm.. trying to install is not a very wise option unless you have given up hope of recovering Friday and Saturday's work.

That "error in sector" message could be relating to a bad sector on the hard drive but more likely to be referring to an errored sector on the CD itself. When you finally get that 10.4 image - burn it using the very slowest speed possible (1x speed). When you then boot from it - I think one of the options offered is Verify CD or Check CD - something along those lines - use it to allow the CD to self check.

Anyways - once you get to a functional LiveCD desktop - post back with that GParted screen grab and we can take it from there.



Mk3 VW Golf here that's playing up - so nice and easy to get at things thankfully (been there done it with the swearing etc. in the past on minis and a Nissan Pulsar GTiR - need tiny multi-jointed arms and hands for both those things :twisted: ). Not managed to fix the thing yet - just ruled out a few things it could have been lol. Get there in the end.

---

### Post by danmartin555 on 2011-12-11
Critin - no I didn't use LiveCD for the backup I used Dropbox to backup the files I have. My version of Ubuntu was out ofdate and couldn't backup that way so that was my logical next choice.

winh8r - I'll run it at the slowest speed when I burn it. The Internet here (Thailand) sucks massively so it's 120am now and all the kids are offline now and it's downloading faster. I'm gonna to try 10.04 LTS as recommended earlier so hopefully it will work.

cryptotheslow - thanks again dude, you've been a great help. I will report back if this 10.04 doesn't work....and most likely will smash something tonight :) I've been messing about with this since 10am this morning so something has to give. (my email is the same as my username @gmail.com if you need another set of ideas about the mk3)

EDIT: (2AM...)I'm gertting the Ubuntu screen up now but it's asking me for myu username and password. I have entered it correctly (even though I set it up 3 years ago) I'm definite it's correct yet it says authentication error. So close, yet so far. I've looked online and it says to boot up in recovery mode...tried that...and it spits the CD out. So close to headbutting the screen now it's unreal.

Double Edit: It gave me the install screen so I've hit *try* ubuntu so I can get hold of my files (hopefully)...I doubt it's going to be that easy though.

---

### Post by danmartin555 on 2011-12-11
OK, got Ubuntu on now and can't seem to log onto the forum on my PC so I'm still using the borrowed laptop. The GParted screen looks like this :-

unallocated: 146.21GB
dev.sda2 extended 2.84GB
/dev/sda5 linux swap 2.84GB

 I haven't installed Ubuntu 10.04 yet, just trying it first. How can I get my old files and pass them over? And, then when I install it properly will they definitely stay there or does anything change going from the trial/try it OS to the fully installed one?

Thanks again everyone :)

---

### Post by cryptotheslow on 2011-12-11
Yes that looks a little promising.

It seems most likely that your 9.04 is/was installed in a partition in that Unallocated space at the start of the disc.

I would try using Testdisk. It may be present on the LiveCD already or it is an easy install there.

Open a Terminal (from the Accesories menu or just Ctrl+Alt+T) and enter the command:

```
testdisk
```If it complains that it cannot find it or says it is not installed then the command to install it is:

```
sudo apt-get install testdisk
```Then try the testdisk command again.

Then follow the step-by-step here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Log_creation](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Log_creation)

 - as far as doing the Quick Search step. Post back what that reports before proceeding.

Oh - in the drive selection choose sda. If it doesn't seem to find any drive at all in the first step - quit the program and try again with:
```
sudo testdisk
```

 - I think it will most likely need sudo privileges, but try without first.

---

### Post by danmartin555 on 2011-12-11
Unfortunately, that brings up:

e: could not open lock file /var/lib/dpkg/lock - open (13:permission denied)
e: unable to lock the administration directory (/var/lib/dpkg/), are you root?


Almost there I think, but just a few niggles. As I'm so close, I'd like to try and get hold of my old files as it's one headache I don't want on a Monday morning :)

---

### Post by cryptotheslow on 2011-12-11
Did you see my edit including sudo?
```
sudo apt-get install testdisk
```

Otherwise make sure you haven't got another package manager open e.g. Synaptic Package Manager or Software Centre

Just popping out for 20 minutes, then I'll be around for the rest of the evening (here) to help you out.

---

### Post by danmartin555 on 2011-12-11
> **cryptotheslow said:**
> Did you see my edit including sudo?
```
sudo apt-get install testdisk
```Otherwise make sure you haven't got another package manager open e.g. Synaptic Package Manager or Software Centre

Just popping out for 20 minutes, then I'll be around for the rest of the evening (here) to help you out.

Yep, thanks. That almost worked but - I got this:

reading package lists....done
building dependency tree....done
reading state information...done
e: couldn't find package testdisk


-so it's almost there. No other things open at the time. In fact, the Synaptic Package Manager doesn't work....is that because it's running off the CD? Cool man, I'll hang about. It's 3am but if this doesn't work tonight I can't start work in the morning so it's gonna be a long night :)

---

### Post by cryptotheslow on 2011-12-11
Hmm...  OK. Give me a minute to boot up on a 10.04 LiveCD and see what's what.

Back in a min.

---

### Post by cryptotheslow on 2011-12-11
Right - I see - the universe repository needs enabling to be able to install it.

Goto the System menu > Administration > Software Sources

On the first tab select the 2nd checkbox down for "Community-maintained Open Source software (universe)" and hit Close - it will take a few moments to bring itself up to date with the new repository before closing.

Then back to the Terminal:

```
sudo apt-get install testdisk
```.... works just fine :) Testdisk takes a 1,547kB download - so you may take a minute or two on your connection :)


EDIT TO ADD: Once installed you definitely need sudo to run testdisk so:
```
sudo testdisk
```

Then over to the walkthrough :)

---

### Post by danmartin555 on 2011-12-11
Hmm, can't seem to open system/software sources. Just nothing happens, the cursor spins for 2 seconds then doesn't load anything. Weird.

---

### Post by cryptotheslow on 2011-12-11
Nothing like a challenge :D

So we try to do it using commands instead. From Terminal these two first:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

gksu gedit /etc/apt/sources.list
```This will open a text editor with a a load of stuff in it (the list of repositories configured on that Live CD).

Add these lines and save & close the file:

```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates universe
```


Then back in terminal:

```
sudo apt-get update

sudo apt-get install testdisk
```

---

### Post by danmartin555 on 2011-12-11
Ok, that all worked until the update, it froze at 99% then failed to fetch [http://gb.archive.ubunty.com/ubuntu/dists/lucid/universe/il8ntranslation-en_us.bz2](http://gb.archive.ubunty.com/ubuntu/dists/lucid/universe/il8ntranslation-en_us.bz2) 

and [http://gb.archive.ubunty.com/ubuntu/dists/lucid/universe/binary-i386/packages.gz](http://gb.archive.ubunty.com/ubuntu/dists/lucid/universe/binary-i386/packages.gz) 404 not found.

I tried it again and got the 2nd error only. Then I tried the testdisk again and it #couldn't find packahe testdisk#

Is it safe to shut down and try this in the morning? It's 415 and need to sleep (weak humanbeing). Thank you so much for your help and I hope it's nearly at the end so I can stop pestering you :) But, seriously thank you so much for this.

---

### Post by cryptotheslow on 2011-12-11
Hmm - could be a connection issue between you and the repository - let me just double check that apt.sources entry again.....

---

### Post by cryptotheslow on 2011-12-11
OK - just to be sure the content of that sources file is right.

```
gksu gedit /etc/apt/sources.list
```

And replace the entire contents with this, save and close:

```
deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release i386 (20110720.1)]/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu lucid main restricted universe
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted universe

deb http://security.ubuntu.com/ubuntu lucid-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu lucid universe
# deb-src http://archive.ubuntu.com/ubuntu lucid universe
# deb http://archive.ubuntu.com/ubuntu lucid-updates universe
# deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe
# deb http://security.ubuntu.com/ubuntu lucid-security universe
# deb-src http://security.ubuntu.com/ubuntu lucid-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://archive.ubuntu.com/ubuntu lucid multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
# deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
# deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse
# deb http://security.ubuntu.com/ubuntu lucid-security multiverse
# deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```


That's a straight copy/paste of the one on my LiveCD environment right now.

Then:

```
sudo apt-get update
sudo apt-get install testdisk
```

---

### Post by danmartin555 on 2011-12-11
OK thanks. I#d try that but since restarting my system it's asking for the username and password (still running off the LiveCD) but I hadn't set one up or been prompted to. I've searched around and the consensus seems to be to let it time out.....it's been 40 minutes now and nothing. I've tried an all manner of passwords and usernames but nothing. Also tried not entering anything and pressing enter = nothing but authentication failed.

It did this yesterday twice but then on the third restart it just went straight to the desktop so I could continue with your instructions. 

Anyone else able to help as I'm sure that this helpful chap will be in bed now as it's 5am where he is.

---

### Post by cryptotheslow on 2011-12-11
Still up - just. 4am not 5am :P

And yes still watching here.

If you have given up hope of recovering your files:

LiveCD - boot from it
GParted
Choose Swapoff (right-click) on that swap partition
Delete the swap and extended partition.

Reboot to the 10.04 LiveCD  and choose the Install option "Use whole disk".

Once up n running grab your stuff from Dropbox and get to work :guitar:

The above is only ** IF YOU GIVE UP ON LOSING YOUR FILES ** - sorry had to put that in caps as some people read these threads and blindly copy/paste stuff.

Good luck. :)

---

### Post by danmartin555 on 2011-12-11
> **cryptotheslow said:**
> Still up - just. 4am not 5am :P

And yes still watching here.

If you have given up hope of recovering your files:

LiveCD - boot from it
GParted
Choose Swapoff (right-click) on that swap partition
Delete the swap and extended partition.

Reboot to the 10.04 LiveCD  and choose the Install option "Use whole disk".

Once up n running grab your stuff from Dropbox and get to work :guitar:

The above is only ** IF YOU GIVE UP ON LOSING YOUR FILES ** - sorry had to put that in caps as some people read these threads and blindly copy/paste stuff.

Good luck. :)

Oh man, that's so cool you're around. I have tried installing it from the purple screen after holding shift down. I still get the username and password screens no matter what I do now so I can't actually get onto the desktop. I have been searching around and everyone is saying to put ubuntu as the username and [blank/nothing] as the password but it fails the authentication.

---

### Post by danmartin555 on 2011-12-11
OK, something magically worked. I did as you said with the partitions and am fully installing it now. Thank you so much for your help. It's a shame I couldn't reclaim the files as I only kept the essentials on DropBox but hey-ho, I haven't been able to work so something had to give. 

My offer still stands if you need any ideas on the Golf - I used to have a mk1 with a mk2 1800 engine :)

---

### Post by cryptotheslow on 2011-12-11
Yes still up for my sins to humanity.

What do you want to do? Install and lose file changes to Thursday?

And what have you done?

The LiveCD doesn't prompt for usernames or passwords.

---

### Post by danmartin555 on 2011-12-12
Eventually got onto the desktop and hit install ubuntu. It's hanging at 60% but hopefully it's just sorting out all the files. Honestly, I don't really care about the files now - if they've gone they've gone. I need to start working as my clients are already miffed.

---

### Post by cryptotheslow on 2011-12-12
Cross-posted. Seems like you found a solution.

Takeaway is - backup critical files daily at the very least - you never know when hardware will **** itself beneath your feet leaving you stranded. Don't trust it to RAID or local replication - get that vital stuff off site or offline as often as you can. That's not paranoia - that's just ***-biting failures striking at the least opportune times talking over too many years.


As for the car - tomorrow sees me on my merry way with the propane looking for vac leaks - damn thing has vac lines everywhere - vac powered locks I ask you - surely you'd modulise the vac? Hmm.... and this is where we come in to Linux...   wow that was a painful route back to on topic but I managed it from a VW!

yayme... must sleep.

init 6 - no I refuse to reboot...  sleep is required here.

But party on without me :popcorn:

---

### Post by danmartin555 on 2011-12-12
It's working now but in the top right-hand part of the screen there is a big red STOP sign, which says:

"An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was : ' Error: BrokenCount >0' This usually means that your installed packages have unmet dependencies."

Problem is, the Package Manager doesn't load up when you right click. And I don't understand what to write the terminal. From the list it brings up I can't 'check' the files that have unmet dependencies, and it's stopping me downloading certain programs I need, Adobe etc. 

I'm about 1-day away from either smashing the screen or getting Windows as this is just too fiddly for my small mind.

Edit: 

More errors in the terminal when trying to update it:
python-gmenu
python-pyicu
software-center
ubiquity
ubiquity-frontend-gtk
E: sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by cryptotheslow on 2011-12-12
Ugh - sorry stupidly busy busy day here. Surprised no-one else jumped in on this in the meantime :(

So you did a fresh 10.04 install - then what? From the dependency hell you seem to find yourself in I'm guessing you downloaded something(s) from a website to install (?). For general adobe stuff like flash player and pdf there's no need to use anything other than Synaptic Package Manager - although you may need to first fire up Software Sources and tick the repositories for universe, multiverse, restricted etc.

So - what did you do and what adobe thing do you want to achieve?

---

### Post by danmartin555 on 2011-12-13
Well, I needed to start working so I started :) I've noticed that in System there is INSTALL RELEASE, which I've searched around and it seems that 10.04 hasn't installed correctly, or it still thinks I'm just 'trying' it. Either way, once I've finished work I'll install it properly and see what's what. 

I downloaded Ubuntu 10.04 from the ubuntu site. I could only burn it at x4 speed, no slower, maybe that was the problem. 

There's loads of things that don't work, synaptics, software sources, can't install dropbox, adobe (for YT vids/music:) ) , but at least I managed to claw my biggest paying client back :)

I'll report back once I've installed it.

---

### Post by danmartin555 on 2011-12-13
OK it looks like I was just testing Ubuntu.

After hitting INSTALL RELEASE. It's asking whether I want to run the /dev/sda5 alongside /dev/sda1? How much space do I give to each? I don't understand this at all. I want Ubuntu on like 99% of the space, then create partitions as an when I want at a later date. I just don't know which one to choose.

---

### Post by danmartin555 on 2011-12-13
Attached screenshots. I can't get past this bit of the install, it says that there is no root file and keeps on flicking back to page 4 of 7. 

Why isn't it just straightforward? I've tried every option and nothing works.

---

### Post by cryptotheslow on 2011-12-13
OK - that's a little odd. Are you still booting up using the CD or without it now (i.e. from the hard-disk)?

The LiveCD environment doesn't automatically mount any partitions from the hard drive - which is what that error is complaining about.

Also can you post back the output of these two commands:

```
sudo fdisk -l
``````
mount -l
```That's a lowercase L as the option in each case.

That should tell us what partitions are on the harddrive and what they are mounted as currently.

---

### Post by danmartin555 on 2011-12-13
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e57af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153309184   83  Linux
/dev/sda2           19087       19458     2978817    5  Extended
/dev/sda5           19087       19458     2978816   82  Linux swap / Solaris

----

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)


Hope that is what you're looking for. I run from the hard drive, not a disk any more. I thought it was fully installed but by the looks of it, it's not. I can't mess about with it too much as I have a lot of work booked in this week.

---

### Post by cryptotheslow on 2011-12-13
OK - then something definitely seems messed up with the installation. If you are booting from the hard drive already and the root filesystem / is mounted from the hard drive as it clearly is - then it is de-facto installed - so why you still have the Install Release option is curious.

Proceeding to try to complete what it is offering via "Install Release" will most likely profoundly break something - or at best install a 2nd instance of 10.04 alongside the already existing one.

I take it you simply took the Install Ubuntu option from the LiveCD originally?

---

### Post by danmartin555 on 2011-12-13
Yeah, straight install from the disc. Problem is I tried for hours and hours to download the iso file on Sunday night, but it kept on failing. It finally did it but as the Internet flicks on and off here, maybe that has caused the problem? I dunno. 

A fresh install do you think? A different OS? A hammer to the screen? I'm all ears.

---

### Post by cryptotheslow on 2011-12-13
While a hammer to the screen may bring a temporary satisfaction - probably not the best course of action :D

I would first verify that the iso file is intact then verify that the CD burnt correctly.

Both these can be done with a fairly simple MD5 check.

Copy the actual iso file onto the machine e.g. to the Desktop. Once it is on the desktop this command in Terminal:

```
md5sum ~/Desktop/ubuntu-10.04.3-desktop-i386.iso
```

If your iso filename is different - substitute that in the above command!

That should return a result like this:
```
f63028da38308d917cd1460e14fb8540  ubuntu-10.04.3-desktop-i386.iso
```

Verify that the MD5 hash (that big long string) and make sure it matches the hash for the file published here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Will post the CD verification bit in a mo.

---

### Post by cryptotheslow on 2011-12-13
Carrying on from the above - once you are happy the MD5 hash is correct for the ISO how to check the CD burnt correctly and is readable throughout.

Put the CD in the drive :D

Then we need to know the actual size of the iso so:

```
wc -c ~/Desktop/ubuntu-11.10-desktop-i386.iso
```

Which gives a result like:
```
729067520 ubuntu-11.10-desktop-i386.iso
```

Divide that number by 512 - in this case 729067520/512 = 145813504

Then using that number:
```
dd if=/dev/cdrom count=145813504 | md5sum
```

You should get an output like this:

```
c@rypto:/media/2ndDrive/isos$ dd if=/dev/cdrom count=145813504 | md5sum
dd: reading `/dev/cdrom': Input/output error
1423960+0 records in
1423960+0 records out
729067520 bytes (729 MB) copied, 4.11509 s, 177 MB/s
c396dd0f97bd122691bdb92d7e68fde5  -
```

That md5 hash on the last line is what we're after - again check it matches the md5 hash you got from the iso file and matches the published hash.

Again - substitute your own iso filenames into the above - I did the above with an 11.10 iso and CD (as that's what happened to be to hand!) - so the hashes and sizes won't be the same as you will get.

---

### Post by cryptotheslow on 2011-12-13
Oh and finally - let's see if we can get an idea what's going on with Synaptic - try to run it from a Terminal should let us see any errors it throws. Just:

```
gksu synaptic
```

Post back what that spits out :)

---

### Post by danmartin555 on 2011-12-13
Cool, that is awesome thanks. I'll try this tonight and report back.

---

### Post by danmartin555 on 2011-12-17
Just wanted to say, I've copped out and have to bow out disgracefully from here.....three years with Ubuntu and I've finally cracked, back to Windows unfortunately. 

I just want to say a HUGE THANK YOU for the help, but with W7 costing so little here and it's working perfectly, I'm afraid I'm no longer a Ubuntu user.

Hope all of ^^^^ this info helps people in the future though :guitar:

---

### Post by cryptotheslow on 2011-12-17
Glad you found a solution :D At least you can now crack on with getting that work done without a continuing headache :)

Keep an eye on your RAM utilisation if the PC becomes sluggish - 1GB is the absolute minimum for Win7 (32bit). Depending what applications you then fire up on it, you may find it swapping out to disk a lot. Easy, cheap fix though - chuck some more RAM in the box. :D

---

