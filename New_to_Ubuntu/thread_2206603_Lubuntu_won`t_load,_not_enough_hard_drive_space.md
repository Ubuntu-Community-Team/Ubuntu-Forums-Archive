---
title: "Lubuntu won`t load, not enough hard drive space"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by Klunker on 2014-02-19
Hi Guys, Have been running Lubuntu on an older Pentium 4 for about the last year...worked great. Yesterday, I tried to update and got a "Not enough hard drive space" message. So, I ran Bleachbit think I might be able to find some space, but while program was running, computer totally locks up. I have to shut off power to get it unfroze. Now, when I try to start up, It gets to a initial  "Lubuntu" screen, then flickers and disappears. That`s it...nothing more.   Any ideas what I might try to get things back up? Any suggestions appreciated...Cheers!

---

### Post by pacman7de on 2014-02-19
> **Klunker said:**
> Hi Guys, Have been running Lubuntu on an older Pentium 4 for about the last year...worked great. Yesterday, I tried to update and got a "Not enough hard drive space" message. So, I ran Bleachbit think I might be able to find some space, but while program was running, computer totally locks up. I have to shut off power to get it unfroze. Now, when I try to start up, It gets to a initial  "Lubuntu" screen, then flickers and disappears. That`s it...nothing more.   Any ideas what I might try to get things back up? Any suggestions appreciated...Cheers!

How to install the Boot-Repair tool in an Ubuntu live disc?

[http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc)

---

### Post by Klunker on 2014-02-19
Hi, Thanks for your help. I tried to access the live USB, but get a "Searching for Boot Record" message and that`s it, nothing more....

---

### Post by pacman7de on 2014-02-19
> **Klunker said:**
> Hi, Thanks for your help. I tried to access the live USB, but get a "Searching for Boot Record" message and that`s it, nothing more....

Try deselecting the boot options, or maybe there is a setting in the BIOS preventing booting from a USB ...

[http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb](http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb)

ps: 64 bit Ubuntu won't boot from a USB, has to be 32 bit .. I think ?

---

### Post by mörgæs on 2014-02-20
The computer boots, so Boot-Repair is irrelevant here. 

Klunker, are you able to get to the Grub menu and select Recovery Mode?

---

### Post by Topsiho on 2014-02-20
You could free some (?: a LOT of !!) space using sudo apt-get clean and sudo apt-get autoremove, and in synaptic removing all kernel images and header files except the last two or so. When you don't do so habitually in the long run a small harddisk may get so full that there is no room left to work in.

Topsiho

---

### Post by Klunker on 2014-02-20
> **mörgæs said:**
> The computer boots, so Boot-Repair is irrelevant here. 

Klunker, are you able to get to the Grub menu and select Recovery Mode?


Hi, Nope, everything disappears at the first Lubuntu screen and there`s no response after that...

---

### Post by Klunker on 2014-02-20
"Try deselecting the boot options, or maybe there is a setting in the BIOS preventing booting from a USB ...

[http://askubuntu.com/questions/15284...12-04-live-usb]("http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb")"


Thanks, tried every Bios setting and nothing else happens.

---

### Post by grahammechanical on 2014-02-20
The Grub boot menu appears before the Lubuntu screen when there is more than one OS on the machine. Otherwise to see the Grub menu when hold down the right shift key.

Depending on the version of Lubuntu that you are using you could see Recovery Mode at the first Grub screen or it could be under the Advanced Options for Ubuntu/Lubuntu sub-menu.

The Recovery menu has an option of Clean. That will run apt-get clean for you. Then try Resume to boot to a desktop. Do you have a separate /boot partition? How large is the hard disk? Have you emptied the Rubbish Bin recently?

Regards.

---

### Post by Klunker on 2014-02-20
> **grahammechanical said:**
> The Grub boot menu appears before the Lubuntu screen when there is more than one OS on the machine. Otherwise to see the Grub menu when hold down the right shift key.

Depending on the version of Lubuntu that you are using you could see Recovery Mode at the first Grub screen or it could be under the Advanced Options for Ubuntu/Lubuntu sub-menu.

The Recovery menu has an option of Clean. That will run apt-get clean for you. Then try Resume to boot to a desktop. Do you have a separate /boot partition? How large is the hard disk? Have you emptied the Rubbish Bin recently?

Regards.

Thanks so much for helping! It`s a 40 gig HD, no partition. There`s only Lubuntu on the system, so I used the right shift and got it to the Grub. I tried the clean option, check files, and repair but it still will not boot to desktop. Just hangs at the Lubuntu screen...flickers...then nothing.  Anything else I can try?

---

### Post by mörgæs on 2014-02-21
> **Klunker said:**
> but it still will not boot to desktop

Does it boot to a command prompt?

---

### Post by mintfan7200 on 2014-02-21
Have you ever tried puppy linux ? It uses a lot less ram and hard drive space than lubuntu . It might be something to try . It is not as easy to use but it is super fast and works great .

---

### Post by Klunker on 2014-02-21
> **mörgæs said:**
> Does it boot to a command prompt?

Yes, I can get to a command prompt...

---

### Post by mörgæs on 2014-02-22
So how does 
```
sudo apt-get clean
sudo apt-get autoremove
```
as mentioned above work?

After that please post (in CODE tags) the output from 
```
df -m
```

---

### Post by Klunker on 2014-02-22
> **mörgæs said:**
> So how does 
```
sudo apt-get clean
sudo apt-get autoremove
```
as mentioned above work?

After that please post (in CODE tags) the output from 
```
df -m
```

Sorry, I think I might have given you some wrong information earlier, It won`t boot to command prompt unless I go to the Grub and select recovery mode.

So I guess that`s actually a root shell prompt. I tried those commands at that prompt and they do nothing. 

I can select Clean that way, and it seems to run okay.  But as soon as I hit resume normal boot, it acts the same way...Lubuntu screen, flicker, gone.

I`m thinking maybe it`s a lost cause...:(

---

### Post by Bashing-om on 2014-02-22
Klunker; Hi !

Let's not give up so easily !
Try this to get to a terminal:
Boot the Lubuntu install, as soon as the bios screen clears depress and hold the right shift key -> grub's boot menu;
With a "non-recovery" kernel highlighted depress the 'e' key for edit mode; -> boot parameters screen;
arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes;
key combo ctl+x to continue the boot process -> to a text login (TTY1).
Enter your user name and then your password - there is no response to the screen when the password is entered (security reasons).

Now perform mörgæs' directive.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-22
> **Bashing-om said:**
> Klunker; Hi !

Let's not give up so easily !
Try this to get to a terminal:
Boot the Lubuntu install, as soon as the bios screen clears depress and hold the right shift key -> grub's boot menu;
With a "non-recovery" kernel highlighted depress the 'e' key for edit mode; -> boot parameters screen;
arrow down and across to the terms "quiet splash" and replace them with the term "text" - with out the quotes;
key combo ctl+x to continue the boot process -> to a text login (TTY1).
Enter your user name and then your password - there is no response to the screen when the password is entered (security reasons).

Now perform mörgæs' directive.
[INDENT][INDENT]my little bit to help
[/INDENT]
[/INDENT]


Thanks so much for trying to help.

I followed your suggestions and this is the resulting screen...

[IMG]http://farm4.staticflickr.com/3719/12707988353_fc7bbd60b4_b.jpg[/IMG]

Anything else I can try?  

Thanks for all the help!

---

### Post by Bashing-om on 2014-02-22
Klunker; Hey, Making progress !

OK, The problem is identified as no disk space in the '/' directory.
So, let's see what is using it all up.
Do this:
```

cd /
sudo du -sx * | sort -n
cd ##returns your Present Working Directory to your /home directory##

```
and post back the output of the "du" command.
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, 
//
df -m says "you are out of space", and du -sx tells you where your space hogs are .
Then we can look at a means to remove files to get that space back.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-22
> **Bashing-om said:**
> Klunker; Hey, Making progress !

OK, The problem is identified as no disk space in the '/' directory.
So, let's see what is using it all up.
Do this:
```

cd /
sudo du -sx * | sort -n
cd ##returns your Present Working Directory to your /home directory##

```
and post back the output of the "du" command.
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, 
//
df -m says "you are out of space", and du -sx tells you where your space hogs are .
Then we can look at a means to remove files to get that space back.
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]



Sorry, but you`ve kind of lost me. Think I messed this up.  I tried to follow your directions but ended up with this...

[IMG]http://farm8.staticflickr.com/7446/12710098134_ff1fcb8f62_c.jpg[/IMG]

Then the computer froze.   Sorry, my fault, I`m sure. Not exactly sure how to get back to where I was... :(

---

### Post by Bashing-om on 2014-02-22
Klunker; Hey,

Rerun the commands as given, and give the 'du' command lots of time to complete. It takes a lot of time to look at every file on the system and sort them out.
As to proc, ignore that output, proc is a virtual file system, constantly changing so can not get a handle on it. That is normal for that command.

[INDENT][INDENT]ain't no big deal
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-23
> **Bashing-om said:**
> Klunker; Hey,

Rerun the commands as given, and give the 'du' command lots of time to complete. It takes a lot of time to look at every file on the system and sort them out.
As to proc, ignore that output, proc is a virtual file system, constantly changing so can not get a handle on it. That is normal for that command.
[INDENT][INDENT]ain't no big deal
[/INDENT]
[/INDENT]


Thanks for hanging in there with me. Went back through and got this as a result...

[IMG]http://farm8.staticflickr.com/7438/12723371105_a46e24de49_b.jpg[/IMG]


Hop you can read that okay,  Thanks again.

---

### Post by mörgæs on 2014-02-23
By the way, which version of Lubuntu are you using?

---

### Post by Klunker on 2014-02-23
I`m sorry, but I`m not sure...

---

### Post by mörgæs on 2014-02-23
What's the third word in the output from
```
uname -a
```

---

### Post by Klunker on 2014-02-23
This is what comes up... 3.11.0-17-generic #31 Ubuntu SMP . But I`m still in the grub menu working from the first generic version.

---

### Post by mörgæs on 2014-02-23
Good, you have the latest Lubuntu. I was just worried that we were trying to salvage an obsolete system.

I shall let Bashing-Om do the talking from now.

---

### Post by Bashing-om on 2014-02-26
Klunker; Hey !

Sorry for dropping out on you, and the rest of the forum.

I had expected to see /boot full, but that is not the case here.
Your /root and /home directories are huge, We need to work on deleting un-needed files from those directories.

I have internet connectivity issues. As soon as I get it figured out and solved, I will be back. I do not have a prognosis thus do not have any idea how long it will take me to resolve my personal issue.

[INDENT][INDENT]we will struggle through
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-26
Thanks for hanging in with me! If anyone has any suggestions, I`d sure appreciate them...

---

### Post by Bashing-om on 2014-02-26
Klunker; Hey,

My little pandamonium is over, I have internet restored!
Back to your situation:
1. /root:
Let's see what is making it so huge:
To Do do so we need to be "root", so be very careful in here, there is no forgiveness of any mistake.
```

sudo -i ##pass word is required##
ls -la
du -sx * | sort -n

```
We are done, so get out now ! least something unfortunate perchances !
```

exit

```

2. /Home
Only you can know what you can delete and only you can know what you can move out to an alternate means of storage (DVDs ??).
But, get rid of all that you can ! You must trim that directory down to size.
Downloads directory ??
 
[INDENT][INDENT]things could be a lot worse
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-28
Hi again, Glad you problems are resolved. Followed your direction,  Here`s what I got...

[IMG]http://farm4.staticflickr.com/3791/12843770834_217fd5b83b_c.jpg[/IMG]


What do I do from here?  Thanks so much

---

### Post by thenh813 on 2014-02-28
EVZg3Kp2UG seems like a wierd folder, not a part of the default OS files.
Can you cd to it and see what is inside? You dont normally store anything to thr Root folder, do you? If anything then, I would delete it if nothing in it is yours. You only gained about a half of a GB then, but it should boot normally. I remember before I replaced my 40GB hdd that died (partially, wasnt detected by BIOS, only Linus or Windows) I was always trying to keep the free space down. I bought a 500GB USB HDD and moved the /home and Documents and Settings folders to it LOL.


Maybe you should consider getting a cheap 32GB flash for $16 or a 64GB  flash drive for a little bit more and move old, and unused stuff to it. Funny how a cheap flash drive can exceed the size of a old HDD so easily.


I know this and what I am about to say probabally is a bad suggestion or out of the question, but have you considered a larger HDD once this is sorted out? If your MB supports SATA of any kind [http://www.amazon.com/Western-Digital-Caviar-Cache-Desktop/dp/B00461G3MS/ref=sr_1_1?ie=UTF8&qid=1393630617&sr=8-1&keywords=500GB+hdd](http://www.amazon.com/Western-Digital-Caviar-Cache-Desktop/dp/B00461G3MS/ref=sr_1_1?ie=UTF8&qid=1393630617&sr=8-1&keywords=500GB+hdd) is 500GB is on sale for only $60! If no SATA then, this thing [http://www.amazon.com/HDE-SATA-Drive-Interface-Adapter/dp/B002Y2NI4M/ref=pd_sim_e_2?ie=UTF8&refRID=0NJNNM7G0GK4W69Z5NZK](http://www.amazon.com/HDE-SATA-Drive-Interface-Adapter/dp/B002Y2NI4M/ref=pd_sim_e_2?ie=UTF8&refRID=0NJNNM7G0GK4W69Z5NZK) allows you to connect a SATA HDD to a older motherboard using the IDE interface. I have a 2001 PC with a P4 also, but it does have sata, so chances are yours would too. HDDs have gotten much cheaper these days, and are pretty easy to get in larger sizes. For example, 3TB (3000GB) can be gotten for $150. That will be my next upgrade besides a P4 HT which is a dual threaded CPU.

---

### Post by Bashing-om on 2014-02-28
Klunker; YUK !

In agreement with thenh813 // But more so ! in that the directory EVZg3Kp2UG is HUGE at 604424 megabytes. You do need to look at what it is and hopefully be able to remove it.

Also, what is .synaptic doing in the root's directory ? .. Might take a look at it and see what it contains - no biggy presently  just wondering.

Then ,as stated, clean up your /home directory.

[INDENT][INDENT]ain't no step for a stepper[/INDENT][/INDENT]

---

### Post by thenh813 on 2014-02-28
@[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508") 	 
I believe it is 604424KB which is 604MB, but that still is WAY to big. I  just thought, if root has a wierd disk waste folder, I wonder if the  user's normal home folder hase some too. Its possible, but with my home  currently sitting at 97GB I know easy it is to accumulate junk. I  deleted over 20GB of junk I didnt need today. I hope they can sort  things out and then maybe have the opportunity to go through old files  and move them elsewhere or get rid of them if the are no longer needed. A  nice cheap stack of 50 CD-Rs is really helpfull at times for quick low capacity data storage (faster than DVDs). I should know, I have more than that many live CDs and multi part backups laying around in a box. I never used to label disks either, so at first it was a mess.


@[**[COLOR=#000000]Klunker[/COLOR]**]("http://ubuntuforums.org/member.php?u=1762511")
If you have blank DVDs or CDs they can also be used to backup or archive old files that are no longer necessary to be on your pc. $10 can get you 100 blank CDs at same places, which is an astounding 70GB of CDs! I am strangely fond of them and prefer them to DVDs for some reason. Usually each month I grab some disks and back up the new or modified stuff to disks and a USB HDD. Backing up is important, because sometimes when this kind of thing happens, you can lost all your data.

---

### Post by Bashing-om on 2014-02-28
@ thenh813; Hey.

Thanks for your input. The size of the output of "du" is as I stated .. in megabytes. Try the command with different options ( say -h, -k, -m ) to see for yourself,
> 
Display  values  are  in  units  of  the  first  available  SIZE   from
       --block-size,  and the DU_BLOCK_SIZE, BLOCK_SIZE and BLOCKSIZE environ&#8208;
       ment variables.  Otherwise, units default to  1024  bytes  (or  512  if
       POSIXLY_CORRECT is set).

       SIZE  is  an  integer and optional unit (example: 10M is 10*1024*1024).
       Units are K, M, G, T, P, E, Z, Y (powers of 1024) or KB, MB, ...  (pow&#8208;
       ers of 1000).


A meeting of minds is
[INDENT][INDENT][INDENT]a good thing
[/INDENT][/INDENT][/INDENT]

---

### Post by daniel121 on 2014-02-28
Im new too but maybe running another linux from usb might allow access to the stuff on your HDD to bacck up then do a re-install to fix it?

---

### Post by Bashing-om on 2014-02-28
daniel121; Hi ! My welcome to the forum .

Granted your suggestion has some merit, and would work, in this case all that is needed to to delete (un)needed files to gain back the disk space.
As we have access to the terminal, we can work this out from the install.

ubuntu
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-02-28
Thanks so much for the help all! I`m happy to remove anything you think I should, but truly have no idea how to do so.  The only thing I really use this computer for is to download and play music, so I`d imagine that`s what the taking up the majority of the space.  If you let me know how to proceed, I`m happy to do so...Cheers!

---

### Post by thenh813 on 2014-02-28
[                                                      @]("http://ubuntuforums.org/member.php?u=1111508")[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")
WOW I guess it really is megabytes, I must have misread earlier. That needs some cleaning, bigtime!

@[**[COLOR=#000000]Klunker[/COLOR]**]("http://ubuntuforums.org/member.php?u=1762511")
Well, anything in /tmp is safe to delete, but in your case its empty so that dosent help.
I suggest you look in  /root/EVZg3Kp2UG for anything you might want (the big folder in /root) and move that elsewhere temporarially, delete that folder, and then put those files in your home folder. Root usually has a empty folder and sometimes a few .<something> folders. Anything else, goes. You might want to check with others before to make sure I am right. Next cd to / and run "find | grep *.tmp". Not sure if anything left temp files, but if it finds any, it pretty much guarenteed that are junk. Same goes for Windows LOL. You could try "find | grep *.bak" if you dont want backup copies of config files and such anymore. I would also try deleting anything in the browser cache manually, if you can find that folder. I think its in you home folder inside .firefox/cache or .mozilla/firefox/cache. I doubt it would equal more than a few hundred MBs, but anything counts, right? Also try running apt-get clean from the terminal just incase it didnt work from recovery mode. Im sure I will figure out more to delete and others like Bashing-om will have ideas too. I will be back tomorrow, its 9:20 and I should go sleep.

---

### Post by Bashing-om on 2014-02-28
Klunker;

Well, We know that  the directory EVZg3Kp2UG is not a standard directory. But rather than blindly removing it and causing a serious situation we need to look at the files in the directory and maybe get some idea of what they are and perhaps how they got there in the first place.
```

sudo -i
ls -la EVZg3Kp2UG 

```
and while we are here, take a look at .synaptic .
```

ls -la .synaptic

```
Done for the time being, revert back to your normal user .
```

exit

```

being careful is
 [INDENT][INDENT]no accident
[/INDENT][/INDENT]

---

### Post by Topsiho on 2014-03-01
First: I have read through this topic, and am quite impressed especially with the tenacity with which Bashing-om is addressing this problem.

I just want to say that I also have the .synaptic folder in my /root, and that it contains a.o. the (system wide) configuration for synaptic, and the lock file.
So I guess the presence of the .synaptic file in /root is normal. I use Ubuntu 12.04, fully updated.

I also think that first of all, the contents of EVZg3Kp2UG should be known before proceeding.

Greetings from

Topsiho

---

### Post by Klunker on 2014-03-01
Thanks for your further comments. I treid the commands last night, but I got a "File not found". Then I realized that the file names were not identical and hoping it was just a typo, tried the other file. This ran, ...and ran, ...and ran, and ...I had to go to bed! ;)  Wow. I left it up all night, as I was afraid to shut anything off.  I woke up to this...

[IMG]http://farm4.staticflickr.com/3807/12855139753_6161037cfc_c.jpg[/IMG]


I don`t know how to scroll the page up (or even if you can) and was afraid to type anythin for fear of screwing something else up... Suggestion?

Thanks so much! Klunker...

---

### Post by Topsiho on 2014-03-01
This output is very much like:
.
.
.
-rw-------  1 jaap jaap       0 feb 14 21:33 .goutputstream-DO1UAX
-rw-------  1 jaap jaap       0 jan 10 17:10 .goutputstream-DZIS9W
-rw-------  1 jaap jaap       0 jan 16 17:13 .goutputstream-E0Z19W
-rw-------  1 jaap jaap       0 jan 26 21:26 .goutputstream-EG3CAX
.
.
.
which I find in my home folder, after some time using my computer. Only difference is the owner and group names, but then, they are in my home folder, and not in /root.
They are the result of a known bug, which for some reason, after years, still is not squashed (Ubuntu 12.04).

These  files are all empty and have random names, and (my files) can be removed, which I usually do once in a while.
Though the files are empty, for each of them some space is used for meta data (file name, creation date and time, and so on), so if there are many of them, much disk space is used, as in your case.

I guess you can remove yours too, but please wait until what the others have to say. You could, before removing them completely, first
rename the folder, in which these files exist, and see whether this affects the operation of your computer (I guess not, what is in an empty file?).
I mean, if the files have become inaccessible (not found), does your computer behave differently? I bet not.

I'll get rid of my goutputstream files :)

Topsiho

---

### Post by Bashing-om on 2014-03-01
@ Topsiho; Hello !

Your affirmation is comforting. Let us proceed.

@ thenh813; Hey, Thanks.
We do so appreciate your assistance and input. Great minds think alike ! -> proceeding on with your premise .

@ Klunker; Good morning .
I have 12.04 as a backup install on this box, later when I reboot I will check that install's "root" directory and compare. ( I do not have "synaptic" installed in this my working install )

Let's do one other run of listing the contents of that strange directory ( as root ), pay as close attention as possible to the file size, and if ALL are of size zero we will remove that directory. Then seek a cause for that directory to even exist. That may take some heavy duty sleuthing ! 

One step at a time
[INDENT][INDENT]gets us there
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-01
Hi, So rerun this?

sudo -i
ls -la EVZg3Kp2UG

After it finishes...Is it possible to scroll the page to see what else is there?

---

### Post by Bashing-om on 2014-03-01
Klunker; Yeah,

Rerun the command, will have to watch the screen as the output is MUCH greater than any buffer and due to the space constraints we can not redirect the output to a file. Try and see if there is a change in any of the file sizes from that of 0.
If you perceive that all the files are of file size zero, I propose to go ahead and remove that directory and all it's contents.

Next as Topsiho advises we will address .goutputstream files in your home directory.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by thenh813 on 2014-03-01
You cannot redirect to a file, but have you considered using the less command?
```

ls -la EVZg3Kp2UG | less

```
It allows you to scroll through the output after it finishes.

Another kind of file that is not necessary are log files, they can grow to be quite big after a while, or large in number.
I am pretty sure it is safe to delete EVZg3Kp2UG but we should examine it with this first:
```

find /root/EVZg3Kp2UG | less

```
That way we can look at individual files, and see if they are important.
If none are, I would give that folder a nice big deleting:
```

sudo rf -rf EVZg3Kp2UG/

```
 and then:
```

sudo rmdir -p EVZg3Kp2UG/

```

Combining sudo and rm in the wrong way can be bad!
Make sure you know what your deleting first.

If it takes far too long to clean up, (like more than a week or two) maybe a backup or important stuff and reinstall would be easier. I would like to avoid this if possible, as it is a last resort.

I was wondering why the text was lagging as I typed it,I just noticed Minecraft minimized and FFMpeg still encoding a five hour video hahaha. No wonder why my PC was so slow, it IS only a P4.

---

### Post by Klunker on 2014-03-01
Okay, I`ve rerun the command and it`s all zeros. Does this mean I can delete this?

---

### Post by Bashing-om on 2014-03-01
Klunker; Yep, remove it !

Correction to the above:
```

sudo -i
rm -rf EVZg3Kp2UG/
rmdir -p EVZg3Kp2UG/
exit

```

Now let's see where we stand:
```

df -h
df -i

```
At this time I expect ya have operating head room and we can update/upgrade the system !

[INDENT][INDENT]big step forward
[/INDENT][/INDENT]

---

### Post by Topsiho on 2014-03-02
I agree with the advices, that all these files, and the EVZg3Kp2UG-directory, should be removed.
In my Lubuntu 12.04 on my Acer Aspire One, this folder doesn't exist in /root.

What worries me is HOW this EVZg3Kp2UG was written into a root owned directory, and all these files within it.

As far as I know an ordinary user can not write in /root.

What program is running on the computer that has root permissions? And how is this program installed? And from what source?
What websites with a bad reputation were visited? Is WOT used to warn you when visiting a bad website? (see WOT add-on for firefox)

I guess that reinstalling is the best option after all, but only after investigating what caused this problem, if that's OK.
In April the next LTS version is published, (L)Ubuntu 14.04.

My two pennies :)

Topsiho

---

### Post by mörgæs on 2014-03-02
> **Topsiho said:**
> 
What program is running on the computer that has root permissions? 


Dozens and dozens of them. Just run **top** and see for yourself.

> **Topsiho said:**
> 
What websites with a bad reputation were visited? Is WOT used to warn you when visiting a bad website? (see WOT add-on for firefox)


There's no reason to believe that this has anything to do with browsing or an attack from outside. 

Klunker, did you enable the root account?

---

### Post by Topsiho on 2014-03-02
I know, of course, there are plenty of root programs running on the computer. Indeed, top will show that.
I was thinking of user installed programs, from other sources than the repositories, possibly from not to be trusted sources.
Something unusual has happened here, files are written in /root, where this should not happen.
Klunker knows best whether this is possible or not.
I did not succeed checking whether a bug is reported for this, as is for the similar .goutstream problem, that I mentioned.

If I remember correctly Klunker listens to or downloads music files. Maybe that caused the problem some way or the other.
No accusation, just wondering :)

Topsiho

---

### Post by Klunker on 2014-03-02
.........and we`re back!  Hah...Good work Guys! I deleted the file and got this...

[IMG]http://farm8.staticflickr.com/7289/12879874713_259769207e_c.jpg[/IMG]

The "f" command came back as invalid. 

I took a chance and rebooted... regular desktop has returned!  Music is still intact too :)  Everything seems to have returned to normal functionality.  As for what I might have done to cause this...I think it had to be the "Bleachbit" program (which is still there) and has a "Bleachbit as Root " setting...that would have been the only thing I ever would have installed that would have access to the Root.  What`s going to be the best way to get that and the unused stuff off of it?  Thanks sooo much!

---

### Post by Topsiho on 2014-03-02
Great. Congratulations :)

If you have bleachbit from the repositories, it should be OK, I guess.
I would say: try and use Bleachbit, and see whether new files are created in /root when you do so, and not when you don' t.
Thanks to Bash-om we now know how to check this. And now, how to get rid of them.
Giving root privileges to any user program should be done with the utmost care, however. I just would say: NOT.
The purpose of Bleachit is just the opposite of creating unwanted files, though :)
If you feel you need Bleachbit, then use it without giving the root privilege setting (and see whether then new files in /root are still being written or not ...)
Otherwise: just uninstall it.

Topsiho

---

### Post by Topsiho on 2014-03-02
On webpage [https://bugs.launchpad.net/bleachbit/+bug/1180863](https://bugs.launchpad.net/bleachbit/+bug/1180863) I read in post #4:

" Bleachbit is the only thing running when I get this error. It is set to overwrite free space on /home/"user", /tmp and /root. Received the same error message again today after running Bleachbit as administrator." 

I don' t understand what is meant with: " overwriting free space on  ... /root". But if this is English, all free space in the mentioned directories are overwritten, and voila, the computer doesn' t work anymore. And we have your problem reconstructed :)

Topsiho

---

### Post by Klunker on 2014-03-02
Hi Topsiho,  Huh.  Really all beyond me. I certainly don`t want to chance running Bleachbit again. What way would you suggest for me to remove unwanted items? Preferably from the normal desktop... Cheers, and thanks again for all your help.

---

### Post by Bashing-om on 2014-03-02
Klunker; Great !

Let's do a proper looksee:
```

df -h

```
[tired last night and missed the typo !]

@ Topsiho; totally agree it would behoove us to know the origin of those files - bleachkit is a most likely candidate.
My thoughts on bleachkit -> causes more harm than it helps, there is nothing bleachkit does that can not be done "better" from the terminal. Admittedly bleachkit can have it uses, but must be applied with knowledge ! 

Doing the housework in 'buntu is simple and easy and when this situation is resolved to everyone's satisfaction, we All will have that discussion then. There just ain't nothing to it. just do it from time to time.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Topsiho on 2014-03-02
If you installed bleachbit from the repositories, then either you remove it completely in Synaptic, or in the terminal with 

sudo apt-get remove bleachbit

or better still 

sudo apt-get purge bleachbit 

for that removes the configuration of bleachbit too, see

man apt-get

for the details of the use of apt-get

I ==> guess <==  that when you installed bleachbit from source, you should first find all files with 'bleachbit' in their names with, in the terminal:

locate bleachbit,

if necessary after

sudo updatedb   (this updates the database of files present on your computer)

and removing the directories and files you find this way. But first wait for what advice the others give you, for I never did it this way myself ...

Topsiho

---

### Post by Klunker on 2014-03-02
Hi, Here what I`ve got...

[IMG]http://farm8.staticflickr.com/7329/12887435185_b311c6725b_c.jpg[/IMG]


What do you think?

---

### Post by Topsiho on 2014-03-02
I guess "all your free space has been overwritten" again.
So you have to get rid of:

1) all the extra files in /root,
2) Bleachbit, especially the executable, which probably is in /bin or /sbin, or /usr/bin or /usr/bin
Look for /bin/bleachbit or /sbin/bleachbit or /usr/sbin/bleachbit or /usr/bin/bleachbit

You might first try and rename it, using sudo, before removing it definitely

:(

Topsiho

---

### Post by Bashing-om on 2014-03-02
Klunker; yeah !

I agree with Topsiho's assessment !

We need to look once more at /root, with that "du" routine, see what is transpiring. 

Need to get that "used" space down to - at a minimum - less than 85 %.

here we go
[INDENT][INDENT]again
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-02
Really? But all seems fine now. I deleted BleachBit with Synaptic, and I`m going to remove some of the music. Do you think something else is wrong?

---

### Post by Klunker on 2014-03-02
Okay, I took some music off, and deleted a couple of other programs. It`s now down to 85% full. I guess I`m going to have to get an external hard drive, as even pared down there is still about 30G of music files. Those FLAC files add up! There seems to be some other stuff I could remove, but I`m a little gun shy now...some games and things that came bundled with Lubuntu...

---

### Post by Bashing-om on 2014-03-02
Klunker; Yeah I do think.

99% device usage is not even a good thing, I say again, we need to get that usage down to less than 85% to insure that the system has the overhead to operate in.

Whatever it takes
[INDENT][INDENT]give the system some breathing room.
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-02
Klunker; OK, looking better at 85 % !

What ya might consider is to expand your system with another hard drive. Hard drives (rotating type) have gotten very cheap !
Put all your music and media on that other hard drive ?

[INDENT][INDENT]hey
[INDENT][INDENT]it is a good thought
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-02
Klunker; It's me Ethel (lol),

As we are getting ready to do some final cleanup, now is the better time to see what the kernel situation is, and maybe gain a lot of space there ! 
show us:
```

dpkg -l | grep linux-image

``` A normal user only needs to keep 2 kernels, The one presently booting, and 1 other as a backup.

And next will do the final system cleanup routine.

[INDENT][INDENT]keep whittling away
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-02
Oh. Something tells me you ain`t gonna` like this...

[IMG]http://farm8.staticflickr.com/7381/12892633893_eb73dcdc67_b.jpg[/IMG]

:redface:

---

### Post by Bashing-om on 2014-03-02
Klunker; Hey !

Do I look surprised ?

OK, given the tools we have to work with, this will have to be done the slow methodical way.
Going to take you some small amount of time;
We MUST not remove the kernel you are booting with, to see which one do:
```

uname -r

``` Hold that version number in mind on wrote on back of your eyelids. DO not mess with it !
And ya want to keep the next lower version numbered kernel as a backup.

OK going to start removing all those old un-needed kernels (images and headers), As you have synaptic installed, that will be the easiest and fastest way :

Go to Synaptic Package Manager  select status on the left-lower  pane and select installed on the left-upper pane and search for linux-image.
 select the ones you want deleted. listed in the right-upperpane.
  and mark for complete removal.
Click the Apply button in the toolbar and then Apply in the summary window that pops up.

  In addition to linux-image, also remove old versions of linux-headers and linux-restricted-modules (if you have them).

Back in terminal when the above is all done, recheck ( as think that "linux-image-extra" will also have to be removed).
```

dpkg -l | grep linux-*

``` to see what else is left to deal with.

Now all done removing images, headers, extras and maybe restricted-modules, Close Synaptic Package Manager.

Update the booting system !
```

sudo update-grub

```

Wipe off, take a break and we will do the next little steps in clean up.

[INDENT][INDENT]it ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mörgæs on 2014-03-03
Before taking the complicated approach I suggest ```
sudo apt-get autoremove
```.

---

### Post by Topsiho on 2014-03-03
I see much has happened when I was in Morpheus arms :)

I agree, both with Bashing-om and with, wait, need to copy/paste :),  Mörgæs. After the autoremove we can see whether there still are unnecessary linux-image files, and remove all except for the two most recent ones. Giving us some space.

I read the first post of Klunker, in which he said that he was running Bleachbit when his hard disk became full and his problem started. So from the start it appears that Bleachbit is the culprit. Now Klunker has removed Bleachbit from within Synaptic, one would think it can't do any harm anymore, but: how did Klunker install Bleachbit: from source, or from the repositories. And can a program installed from source be removed in Synaptic? I guess Bleachbit still is present on the computer and needs to be removed.

Topsiho

---

### Post by Topsiho on 2014-03-03
In the original post Klunker said:

"Yesterday, I tried to update and got a "Not enough hard drive space" message. So, I ran Bleachbit think I might be able to find some space, but while program was running, computer totally locks up."

So this hard disk was already quite full before he started Bleachbit, rightfully thinking that he might get some space back doing so, but the opposite happened.
Now, I can't understand how he could free space so that only 10% was in use (90% free!!) , after removing all the suspect files and their directory in /root. Before running Bleachbit there already was not enough drive space. See post #52.

I think additionally space must be recovered by moving a large amount of music files to an external USB drive. If that old Pentium has USB ports :), and otherwise maybe to DVD-roms.

Topsiho

---

### Post by Klunker on 2014-03-03
Hmm...don`t like the looks of this. Just looked at the files in Synaptic...very difficult to feel secure in what I`m deleting. Also, the auto-remove has me a wondering... I didn`t use this from the beginning because I read of it removing files it shoudn`t.  

[IMG]http://farm8.staticflickr.com/7433/12905058854_ca2e9d1956_b.jpg[/IMG]

---

### Post by mörgæs on 2014-03-03
> **Klunker said:**
> Also, the auto-remove has me a wondering... I didn`t use this from the beginning because I read of it removing files it shoudn`t. 


Please post the link.
Autoremove is one of the most secure of all maintenance commands.

---

### Post by Klunker on 2014-03-03
Hi,   "http://ubuntuforums.org/showthread.php?t=2200808 " is where I saw that it could cause issues...

---

### Post by mörgæs on 2014-03-03
Autoremove posts a lists of packages which are about to be removed. Only if you confirm the list the actual deletion takes place.

---

### Post by Bashing-om on 2014-03-03
Klunker; & mörgæs; 

I am aware that "autoremove" in later kernels has been upgraded to also remove outdated kernels, not sure where that cut off happened. Klunker is running with HES, so maybe "autoremove" will be effective. Most interested to see. As indicated, pay attention to what "autoremove" indicates that it will remove. I will say that in a bunch of years using "autoremove" I have never encountered a problem. Smart package manager  ! - I always copy/paste to a temporary text file what is going to be removed, in the unlikely event there is a problem, I then do have a means to quickly resolve - .

We are on the down hill side of this sloppyation, having gotten a handle on what is going on ( will have to watch /root and make sure that strange directory does not get re-created). Once these old kernels have been removed, all that is left is the "normal" housecleaning operation.

@ Topsiho; Continued agreement with your assessments. Get this system cleaned up and see what the situation is in a couple of weeks.

All in the care and feeding
[INDENT][INDENT][INDENT]of your ubuntu
[/INDENT][/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-03
Should I run autoremove then? Hard for me to look at a list of files and know if I`m okay to remove...

---

### Post by ibjsb4 on 2014-03-03
Hi Bashing

It my understanding that autoremove of kernels is in 13.10 and on.

see ya :)

---

### Post by philinux on 2014-03-03
> **Klunker said:**
> Should I run autoremove then? Hard for me to look at a list of files and know if I`m okay to remove...

Yep hit the y key on that.

---

### Post by Bashing-om on 2014-03-03
Klunker; Hit "y" !

As philinux prompts -- unless you have done something real strange and exotic with your system configuration, doing "autoremove" will only do you good ! As advised, though, have a good idea (copy !) of what "autoremove" will remove.

Then it is back to getting those old kernels ( images, headers and related stuff) removed from your system.

[INDENT][INDENT]let the chips fall
[INDENT][INDENT][INDENT]we DO cleanup
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-03
Hi all,  Okay, I let`er happen...but not much did.  I got this...

[IMG]http://farm8.staticflickr.com/7402/12917941813_2c1e32467a_b.jpg[/IMG]

Is that okay?  Thanks...

---

### Post by Bashing-om on 2014-03-03
Klunker; Hey ,

Looks fine. But, did you use synaptic and completely remove all those old images and header files ?

[INDENT]look'n better all the time
[/INDENT]

---

### Post by Klunker on 2014-03-03
> **Bashing-om said:**
> Klunker; Hey ,

Looks fine. But, did you use synaptic and completely remove all those old images and header files ?
[INDENT]look'n better all the time
[/INDENT]


I removed everything I thought I could, and ran auto-remove...

---

### Post by Bashing-om on 2014-03-03
Klunker; Looking good !

Almost done,

Let's see what might be left of any kernels:
Terminal command - once more :
```

dpkg -l | grep linux*

```

Now that you have full access to your system, how about using code tags when you post back requested information. Makes things so much easier and understandable.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

the end is in sight
[INDENT][INDENT]there is light there at the end of that tunnel
[/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-03
Hi,  Sorry, but It doesn`t seem possible to cut and paste out of the terminal, and I can`t type. :(  So reproducing that output would take me an hour. I hope my photo will suffice. My apologies.

[IMG]http://farm3.staticflickr.com/2860/12919679895_90b91bfb4a_b.jpg[/IMG]

---

### Post by Bashing-om on 2014-03-03
Klunker; OK !

From what I can see and understand, looking great.
Are you now booting to the desktop, /activating a terminal from the desktop you should have copy and paste abilities !/ and all is functional ?
What now results from terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```
If that runs well, what now are the space conditions ?
```

df -h

``` looking for it to be less than 85% used in any/all partition(s).

Finally, if all is well with a stable system, we will clear out the cache - starting again with a clean slate.

[INDENT]that I expect
[INDENT][INDENT]is all she wrote for this issue
[/INDENT][/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-04
Hi Bashing OM,  Still can`t cut and paste out of the terminal, but otherwise everything seems to have went well. After the update and upgrade, I`m at exactly...85%! :) So, not optimal, but functional at least! I will get some more music off of it ASAP.   Anything else I should do then?

---

### Post by Topsiho on 2014-03-04
Copying from and pasting into a terminal is easy, but you have to use the menu of the terminal, as Ctrl-c, Ctrl-x and Ctrl-v don't work in a terminal.
Not sure whether this is true for all terminals, though. Example of copied from terminal and pasted here:

-rw-------  1 jaap jaap  7473592 apr 16  2011 issuePY01_en.pdf
-rw-------  1 jaap jaap 19409838 mei 14  2011 issuePY02_en.pdf
-rw-------  1 jaap jaap 18261606 feb 18  2012 issuePY03_en.pdf


I have a small netbook, Acer Aspire One, with a very small SSD, 8 GB, and have to manually remove the unneeded Linux-image files regularly, keeping only the two latest, after a kernel update.
This I always do in synaptic, first carefully planning what to remove, on paper. Searching for linux-image, and possibly the linux-headers too. The highest numbers are the latest files. And of course I do the sudo apt-get clean routine after every update, to remove the downloaded files, which are not necessary any more.

Without this I would find the netbook unusable in a not so long time.

Topsiho

---

### Post by Bashing-om on 2014-03-04
Klunker; Hey,

We are done when these commands are run:
```

sudo apt-get clean
sudo apt-get autoclean

```

As Topsiho advises that is all there is to housecleaning !
Simple
run the du command to see what the space constraints might be;
Take a look on occasion at the size of the log files in /var/log/ (and what the logs convey);
synaptic to remove the old kernels;
sudo apt-get autoremove;
sudo apt-get autoclean;
sudo apt-get clean.

There is no need of any alternatives ! Unless something gets out-of hand -.

apt-get clean: command clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

apt-get autoremove: used to remove packages that were automatically
installed to satisfy dependencies for some package and that are no
more needed. In the newer releases of 'buntu also removes the old kernel modules.

apt-get autoclean: only removes files that cannot be downloaded anymore (obsolete).

As you now know, The system must have operating head room, or it can do nothing. At 90% used space one starts clean up, at 95% usage you have a problem to get that operating head room. Best practice is not to let it get to that point.
----------

I expect at this point all is hunky dory and pending the closing remarks I trust this thread can now be closed as solved; 1st post -> thread tools.

With my regards I say ->
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by Klunker on 2014-03-04
Just want to say thanks again to everyone that contributed to helping me out, especially you Bashing-OM. You`ve taught me some new tricks and given me the confidence to install Lubuntu on my Wife`s old laptop! :)  Again, My sincerest thanks!
Cheers!

---

### Post by Bashing-om on 2014-03-04
Klunker; Out standing !

Helping is what we do so you get the best of and enjoy 'buntu !

If this matter is concluded, do not forget to mark this thread as solved.

And hey, I happen to like Lubuntu ( xfce4 even more !) - personal preference -
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)


Keep it clean
[INDENT][INDENT]and there will be no problems
[/INDENT][/INDENT]

---

### Post by thenh813 on 2014-03-08
@Klunker
Well, congratulations, you got it cleaned up!
I guess Bleachbit forgot to delete its files.
Hopefully you can move out more files soon.
@Everyone
Sorry I haven't posted, I was really busy lately.
I just wanted to let you all know I haven't left this thread or something.
Have a nice day!

---

### Post by Klunker on 2014-03-09
Thanks for your help[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1908010") thenh813, most appreciated! :)

---

