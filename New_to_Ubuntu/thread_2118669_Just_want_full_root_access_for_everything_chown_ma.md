---
title: "Just want full root access for everything chown makes no sense :("
date: 2013-02-21
forum: New to Ubuntu
---

### Post by Visrite on 2013-02-21
I've been trying to wrap my head around chmod/chown (both for those wondering) for hours now with no luck...

All I want is to be allowed to change my files permissions so I can run executables with WINE and delete the virus after it nested in my .Trash-999 folder.

What is the terminal command line to unlock my system? Completely. I want to own the directory and ALL sub folders, files, directories, and others. I want to be able to read and write the whole directory along with ALL sub folders, files, directories, and others.

I'm sick and tired of being told I can't have access to my own system, I've been searching these forums and google and I'm just so frustrated.

I want to unlock everything now, I want to be root, direct access, I'm tired of sudo not working and tired of changing things in GUI mode that automatically change back the moment I move my mouse. AHHHHHHH! Frustration..

---

### Post by the_jlx on 2013-02-21
as for terminal
sudo su
and for file manager
sudo Nautilus

shud let you fix things

---

### Post by squakie on 2013-02-21
And anyone who may be tempted, do *NOT* instructions on enabling root in this forum - this is against forum policy.

---

### Post by deadflowr on 2013-02-21
Running  sudo -i  in the terminal will give root for the duration the terminal is open or you exit the command with, exit. Any thing you do while running this way will be done as root-level.

Whatever you do, do not change system file owner and or permissions ( outside of setting them to execute or not) to any of the system folders and or files. (/, /usr, /etc, etc etc etc)
Doing so can make the system unusable.

But anyway, files for wine are sitting in your home directory so you don't need root to change them. Open the file manager nautilus and ctrl +h to view hidden folders and then look for the wine directory and right click the file you want to change and dropdown to properties and from there change the permissions.

Also this:
```
chmod +x path-to-wine-file
```

This will make the wine program executable.

Anyway what is the trash-999 file. Why not simply delete it?
If it's a virus chances are it will have no effect on Ubuntu.
And by chance I mean over 99% chance it will have no effect.

---

### Post by lisati on 2013-02-21
> **the_jlx said:**
> as for terminal
sudo su
and for file manager
sudo Nautilus

shud let you fix things

As explained [here]("https://help.ubuntu.com/community/RootSudo"), gksudo is usually preferable for nautilus

---

### Post by Primefalcon on 2013-02-21
this will explain how to enable root:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

however read all of it, and better ways to do things

---

### Post by deadflowr on 2013-02-21
> **squakie said:**
> And anyone who may be tempted, do *NOT* instructions on enabling root in this forum - this is against forum policy.

This is mostly right. However we give sudo instructions which enable root use.
To clarify, it is against forum rules, highly discouraged and just plain stupid to give instructions on how to set your system to run openly as root, from login to log out.

---

### Post by csillva on 2013-02-21
> **Visrite said:**
> All I want is to be allowed to change my files permissions so I can run executables with WINE and delete the virus after it nested in my .Trash-999 folder.

If your goal is to play around with Windows viruses, and if you are trying to figure out how to do this while having / running as root, I'd recommend installing virtual box, installing a windows on it, taking a snapshot of it clean, then playing with .... whatever it is you are playing with. 

Once you've completely borked your system to your total satisfaction, revert to clean snapshot and try again.

---

### Post by squakie on 2013-02-21
> **deadflowr said:**
> This is mostly right. However we give sudo instructions which enable root use.
To clarify, it is against forum rules, highly discouraged and just plain stupid to give instructions on how to set your system to run openly as root, from login to log out.
 
Sorry about that - I should have been more specific and said it's against policy to post instructions on giving root login.  ;)

---

### Post by DuckHook on 2013-02-21
The last thing I want to do here is make you feel like we are piling on, but someone's gotta say it:

While your frustration is completely understandable, and we all have the greatest sympathy, the first thought that occurs to most of us is that you want to fix a rattling engine by driving your car (and yourself) off a cliff.

If you do have a virus nested in your system through WINE, then it got there precisely because Windows programs are built to demand system privileges to function and Windows idiotically gives it to them. You are now asking for instructions to totally hose your Ubuntu security and bring it down to a Windows level so that you can deal with a virus that exists only because Windows starts out with a hosed security model. That reasoning just blows my mind.

You are looking at Linux restrictions as impediments. In fact, they are the very safeguards that make it tough for nasties like the virus you are currently dealing with to infect Linux systems. If you find it difficult to *chown* and *chmod*, to say nothing of gaining root privileges, then a piece of dumb malicious code certainly won't be able to do it. And this is the very safeguard that you now want to dismantle.

The members of this forum are happy to help you deal with whatever problems you are having. Deleting whatever is in an infected directory is not really that difficult. But, speaking only for myself, I've resolved not to give instructions that dismantle the Linux security model. The last thing we need as a Linux community is security that's as lousy as Windows'.

Re: virus in directory. You can delete the whole directory with:```
sudo rm -rf /path_to_directory/.Trash-999
```Re: More powerfully, hit <Alt>+<F2> to bring up the run application dialogue box. Doing:```
gksudo nautilus
```will invoke nautilus in root mode and let you delete every directory in creation, from root on downwards if you so wish. Want to delete hidden directories too? Just <Ctrl>+<h> to unhide them. Now you can go to town on those too.

No one is telling you that you can't have access to your own system. The two simple commands above give you all the access you could wish for. The irony is that Linux is actually the system that lets you do anything you want. If anyone is denying you access to your own system, it's the proprietary OSes who won't let you change a shred of their code (but that's another discussion for another day).

It is much more accurate to say that Ubuntu puts safeguards in place to prevent people from doing dangerous and stupid things to their system and to their data. *chown* and *chmod* are part of a system that prevents baddies from looking at your private files. *sudo* is designed to make you pause before inadvertently deleting your whole installation (as I did when I first started in Linux and harboured exactly the same misconceptions that you now have). If you work with these features rather than fight against them, you will find that they repay your time and effort with advantages you never dreamed of. And the members of this forum are more than willing to help you get there.

---

### Post by Visrite on 2013-02-22
I think I've tried the sudo rm -rf /path/.Trash-999 and the Terminal just prompts me again and nothing seemed to happen.

Also how do you get out of the code box when making a post?

I  also tried to shred the folder in the .Trash-999 and it just says  permission denied. I thought when I deleted something permanently from  the regular trash it was suppose to be whipped. Apparently it just gets  filed in .Trash-999 and the corrupt and infected files are still there  but not visible even after unhidding files.

---

### Post by albandy on 2013-02-22
> **Visrite said:**
> I think I've tried the sudo rm -rf /path/.Trash-999 and the Terminal just prompts me again and nothing seemed to happen.

Also how do you get out of the code box when making a post?

I  also tried to shred the folder in the .Trash-999 and it just says  permission denied. I thought when I deleted something permanently from  the regular trash it was suppose to be whipped. Apparently it just gets  filed in .Trash-999 and the corrupt and infected files are still there  but not visible even after unhidding files.

sudo chmod 777 .Trash-999 -R
sudo rm -rf .Trash-999

---

### Post by deadflowr on 2013-02-22
Where exactly is the file located?

---

### Post by DuckHook on 2013-02-22
It would help to know the full path to the .Trash-999 file that you are trying to delete. I'm curious where this is. I've never come across a 999 trash file before. Such trash files are usually created when a person or process deletes something outside of their /home directory on a different partition or removable media. The 999 is the user ID of the person deleting. Since Ubuntu assigns user ID starting at 1000, and root is 0, I don't know where the 999 suffix comes from. Please open a terminal and post output of the following:```
id
```then,```
awk -F":" '{ print "username: " $1 "\t\tuid:" $3 }' /etc/passwd
```Let's see who user ID 999 belongs to.

On a very important related note, how do you know that this trash contains a virus, or that you were infected through an executable running WINE? Are you assuming it's a virus or do you have confirmation such as a viral scan? All details you remember are critical on this one to providing help.

> Also how do you get out of the code box when making a post?I'm afraid I don't understand this question. When posting, I don't ever see a code box--just the posting box that I type into. When I need to define something as code, I just highlight it and click on the hash (#) tag. I never find myself in a code box. Then it's just clicking on "Submit Reply" button to complete post.

> I also tried to shred the folder in the .Trash-999 and it just says permission denied. I thought when I deleted something permanently from the regular trash it was suppose to be whipped. Apparently it just gets filed in .Trash-999 and the corrupt and infected files are still there but not visible even after unhidding files.Again, I'm not aware of a "shred" option in the trash. Do you mean permanently delete? I'm not just picking nits here. There is a real shred program in Ubuntu and it performs a different function than what you are trying to do. If you in fact have a shred option, then I'm wondering if you are using Ubuntu. And finally, if, as I suspect, you have user ID 1000, then Ubuntu will not let you delete trash from user 999. This is a security feature that disallows one user from deleting the files of another. If you invoke the nautilus file manager using gksudo as many previous posts have already suggested, then you will have root privileges and can delete any trash you like.

I'm shutting it down for the evening now, but will look in on this thread again in the morning. Please post output requested above as soon as you can.

---

### Post by Warren Hill on 2013-02-22
There are lots of good reasons why Ubuntu does not enable root by default see here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for a few.

If you need to run a GUI application as root simply press Alt-F2 and enter **gksu** or **gksudo** followed by the name of the program. For example

```
gksu nautilus
```Runs the file manager as root.

Or in a terminal type

```
sudo -i
```Then the commands you need to run as **root**

Then when you are done 

```
exit
```An alternative is just to prefix the commands that need it with sudo for example

```

fdisk -l #does not work unless you are root 
sudo fdisk -l #does work: lists the drives on your computer

```

---

### Post by Elfy on 2013-02-22
> I think I've tried the sudo rm -rf /path/.Trash-999 and the Terminal just prompts me again and nothing seemed to happen.
If you ran the command and then the terminal went back to the prompt - it did what you asked without error. You won't get a 'Hi - we did that and all is ok' message.

You'll be told if you try to do something and it fails.

---

### Post by Visrite on 2013-02-22
The file was located at:

/media/ubuntu/harddrivealphanumeric/.Trash-999

I auto updated in Windows 7 and it installed SP1 and I did a routine scan and it told me a bootkit was installed. After research it looks like this was a pretty common thing to happen with the release of W7SP1. I've been trying to save windows and the bootkit deleted my system restore points. I really wish I could afford an external hard drive to backup all my files, including pictures of my children I never get to see. (Divorce) 

Anyway, I knew it was in the .Trash-999 because my avast told me it was still on the hard drive in that folder.

@DuckHook

Here is the output

```
ubuntu@ubuntu:~$ id
uid=999(ubuntu) gid=999(ubuntu) groups=999(ubuntu),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),107(lpadmin),124(sambashare)
ubuntu@ubuntu:~$ awk -F" :" '{ print "username: " $1 "\t\tuid:" $3 }'  /etc/passwd
username: root:x:0:0:root:/root:/bin/bash        uid:
username: daemon:x:1:1:daemon:/usr/sbin:/bin/sh        uid:
username: bin:x:2:2:bin:/bin:/bin/sh        uid:
username: sys:x:3:3:sys:/dev:/bin/sh        uid:
username: sync:x:4:65534:sync:/bin:/bin/sync        uid:
username: games:x:5:60:games:/usr/games:/bin/sh        uid:
username: man:x:6:12:man:/var/cache/man:/bin/sh        uid:
username: lp:x:7:7:lp:/var/spool/lpd:/bin/sh        uid:
username: mail:x:8:8:mail:/var/mail:/bin/sh        uid:
username: news:x:9:9:news:/var/spool/news:/bin/sh        uid:
username: uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh        uid:
username: proxy:x:13:13:proxy:/bin:/bin/sh        uid:
username: www-data:x:33:33:www-data:/var/www:/bin/sh        uid:
username: backup:x:34:34:backup:/var/backups:/bin/sh        uid:
username: list:x:38:38:Mailing List Manager:/var/list:/bin/sh        uid:
username: irc:x:39:39:ircd:/var/run/ircd:/bin/sh        uid:
username: gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh        uid:
username: nobody:x:65534:65534:nobody:/nonexistent:/bin/sh        uid:
username: libuuid:x:100:101::/var/lib/libuuid:/bin/sh        uid:
username: syslog:x:101:103::/home/syslog:/bin/false        uid:
username: messagebus:x:102:105::/var/run/dbus:/bin/false        uid:
username: avahi-autoipd:x:103:106:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false        uid:
username: usbmux:x:104:46:usbmux daemon,,,:/home/usbmux:/bin/false        uid:
username: whoopsie:x:105:110::/nonexistent:/bin/false        uid:
username: kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false    uid:
username: rtkit:x:107:114:RealtimeKit,,,:/proc:/bin/false        uid:
username: speech-dispatcher:x:108:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh        uid:
username: colord:x:109:117:colord colour management daemon,,,:/var/lib/colord:/bin/false        uid:
username: lightdm:x:110:118:Light Display Manager:/var/lib/lightdm:/bin/false    uid:
username: avahi:x:111:120:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/falseuid:
username: hplip:x:112:7:HPLIP system user,,,:/var/run/hplip:/bin/false        uid:
username: pulse:x:113:121:PulseAudio daemon,,,:/var/run/pulse:/bin/false    uid:
username: saned:x:114:123::/home/saned:/bin/false        uid:
username: ubuntu:x:999:999:Live session user,,,:/home/ubuntu:/bin/bash        uid:
username: clamav:x:115:125::/var/lib/clamav:/bin/false        uid:
```

When you copy and paste stuff in a code box it puts the box in your reply typing. Then you're stuck there.

My AV says that the corrupt or infected files are no longer on the hard drive. I've been told it can jump to a router so I'd like advice on how to scan that for viruses. 

I would also like to know if/how to retrieve my windows key from ubuntu. Its worn on the case.

I'd like to thank everyone for their comments you've all been very helpful. I think after I save these files I'm going to create a VM and try ubuntu from scratch. I hear there is a text I can read an it will help me build ubuntu from the ground up and I feel I can learn a lot if I do just that.

Additionally I think I'll mark this as closed as my initial question seem to have been answered. You can still comment after solved right?

---

### Post by audiomick on 2013-02-22
> **Visrite said:**
>  You can still comment after solved right?

Yep, and I believe you can come back and change it back to "unsolved" if you change your mind.

---

### Post by bigmonmulgrew on 2013-02-22
Hi I noticed you first asked for some clarification of chmod and chown and got a debate on the merits of not opening root.

Its a bad idea to fully open a system but heres a basic explanation of chown and chmod

**chown**

This is to change who the owner of a file is. The owner can be both a user and a group. You will see files marked as root:root or user1:user1.

This is because you might want to set access permissions for a user and group differently.

For example you could have the ownership set user1:family
You could then give user1 read, write and execute permission and only give family read permissions. You might do this with a music archive so only you can add/remove tracks but anyone in the family can play them.

You set the ownership of a file like this
```
chown user:group /directory/file
```

you can change the permissions on a directory like this

```
chown user:group /directory
```

This wont change the ownership on any files in the directory but any new files will take the settings of the parent folder.

If you do want to change the sub-directories and files you can use -R (recursive) like this

```
chown -R user:group /directory
```

if a file belongs to another user or root you will have to use sudo to edit it.

```
sudo chown user:group /directory/file
```

if a file or folder is owned by root:root it is usually a VERY bad idea to change it. If you change anything owned by root:root you will at best make your system vulnerable and at worst completely screw it up. a lot of stuff needs to be owned by root:root to work. you should never change ownership from root:root to anything else unless you are an expert and have a very good reason and know what you are doing.

**chmod**

chmod is used to change the permissions. You can change the permissions on a file or folder for the owner, the group and for public.

Generally you will set read, write and execute permissions for these, although there are some more complex options.

It is usually a bad idea to give public write permissions or execute permissions. If someone connects to your system and you have public write permissions then anyone will be able to modify your files. If you give public write permissions on system files then you are opening up a serious security hole.

In the music example above you would give the owner (you) read, write and execute permissions, you would give group read and execute permissions and you would give public no permissions. I'm not sure you need execute permissions for music but for this example why not...

There are lots of ways to use chmod but I like using the numbers. heres an example

```
chmod 750 /directory/file
```

The first number sets the permissions for owner, the second number sets the permissions for group and the last one sets the permissions for public.

The numbers work like this
1= execute
2= write
4= read

You add the numbers together to give the permission you want, 4+2+1=7 so that gives read, write and execute.
4+1 =5 so that gives read and execute.
0 give no permissions.

You can also use recursive with chmod the same way you do with chown
```
chmod -R 750 /directory
```

Again anything owned by root or another user needs you to do sudo before editing.

you can google for the manual pages if you need the more advanced commands for both

All this should give you an idea how to get read and write access to anything you like but as I said if the owner is root:root then changing that is a bad idea.

AS you mentioned WINE, and i dont really use it you might find the ownership is set to root:WINE

This would mean its owned by root but the WINE group has access to it. If you just want to be able to edit wines files without using sudo you could add yourself to the WINE group.

I'm not sure of the security implications of this but I'd think that beyond screwing up wine there wouldnt be any serious issues.

---

### Post by bigmonmulgrew on 2013-02-22
by basic I meant long :D

---

### Post by DuckHook on 2013-02-22
Ahh...

First time you've mentioned a W7 install, though I suspected this when you mentioned virus. You should note that Windows-based AV apps will sometimes give false positives when scanning Linux partitions because they don't know what they are seeing and just default to crying wolf.

Just looked it up and the 999 UID is assigned to first system user account defined by a normal user. It's just a pure guess, but I suspect that you created this account trying to invoke root and your OS now defaults to this as your UID. Continuing to operate as User 999 may make things difficult for you. I don't know if your /home directory is owned by 999 or 1000 (as it would be in a regular install). Remember, you can't access directories/files belonging to another user.

Your *awk* string contained an extra space that generated verbose output, but no harm done. We got what we wanted. As a tip, in future, it's best to copy and paste commands from code box into terminal with mouse.

I highly recommend [Psychocat's]("http://www.psychocats.net/ubuntu/index") site to familiarize yourself more with Ubuntu in general. Because you are running WINE, [this]("http://ubuntuforums.org/showthread.php?t=510812") sticky is fantastic for learning security despite the fact that it is quite deep and involved. Pay special attention to the WINE section and to NOT run it as root (not a good idea for any common app, but especially WINE). Digesting both will give you a better understanding of why Ubuntu does things the way it does.

---

### Post by bab1 on 2013-02-22
> **bigmonmulgrew said:**
> ...

```
chown user:group /directory
```

This wont change the ownership on any files in the directory but any new files will take the settings of the parent folder.

This is not true of any default Debian/Ubuntu Linux system.  You have to set SIUD/SGID bits to have inheritance.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.zzee.com/solutions/unix-permissions.shtml#setuid") for the relevant info.  I believe this is so of RedHat/CentOS/SUSE too, but I have only slight experience with those distros.

---

### Post by bab1 on 2013-02-22
> **DuckHook said:**
> 
Just looked it up and the 999 UID is assigned to first system user account defined by a normal user. It's just a pure guess, but I suspect that you created this account trying to invoke root and your OS now defaults to this as your UID...

I think the OP was running a LiveCD version.  In that instance the user is *ubuntu* with no password.  See below in red (provided by the OP)```
username: [COLOR="Red"]ubuntu:x:999:999:Live session user[/COLOR],,,:/home/ubuntu:/bin/bash
```

The first user created on an fresh install is always 1000.

Edit: FWIW you can print a list of users like this```
getent passwd
```

---

### Post by DuckHook on 2013-02-22
> **bab1 said:**
> I think the OP was running a LiveCD version

If so, you mean he's been trying to delete a file from a DVD??? How would he have installed WINE? or run W7 AV?

@OP

Please clarify.

---

### Post by Armann on 2013-02-22
Good thread, great read, thanks. :popcorn:

---

### Post by bab1 on 2013-02-22
> **DuckHook said:**
> If so, you mean he's been trying to delete a file from a DVD??? How would he have installed WINE? or run W7 AV?

@OP

Please clarify.

You can install apps using a LiveCD.  I have installed Samba Server myself.  It's not persistent, but you can do it.  I can't see any reason why you can't install Wine.  If you mount a partition you can save data too.  The system that is running is a compressed image that is inflated when booted (init).  It's true the DVD files can't be changed from read only.

---

### Post by DuckHook on 2013-02-22
> **bab1 said:**
> You can install apps using a LiveCD.

I know it can be done. It was more a series of... ehmm... rhetorical questions...

---

### Post by Morbius1 on 2013-02-22
> **Visrite said:**
> All I want is to be allowed to change my files permissions so I can run executables with WINE .....
Just as a side note: Wine can't even determine if an *.exe file has a Linux executable bit set so it doesn’t matter if it's executable or not.

When you double click test.exe the following command is run:
```
cautious-launcher test.exe wine start /unix                      
```Cautious-launcher is the thing that checks to see if it's executable not Wine ( also holds true for a java jar file ). The thing to do is either bypass or disassociate cautious-launcher from Wine: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

Option 2 in that link no longer works because setting a custom command in Nautilus is now verboten - it's a feature so it had to go. But you can install the Thunar file manager and get it back.

As another side note I wouldn’t do this on a drunken bet:
> chmod -R 750 /directoryYou just made every single file executable. The Jedi way is something like this:
```
chmod -R a+rwX,g-w,o-rwx /directory
```All folders will be 750
All Files will be 640 except those that were executable to begin with.

---

### Post by bab1 on 2013-02-22
> **Morbius1 said:**
> ... The Jedi way is something like this:
```
chmod -R a+rwX,g-w,o-rwx /directory
```All folders will be 750
All Files will be 640 except those that were executable to begin with.


;-)  Absolutely +1

---

### Post by androideka31 on 2013-02-22
Are you having trouble with the syntax of the command or just understanding what it does?

---

### Post by Visrite on 2013-02-23
Clarifications:

Was W7 computer
Only wanted to run a program to seek and destroy the rootkit with WINE
Was using Ubuntu from LiveCD mode, that seems to be part of the overall problem with portions of what was causing my frustration.

This has been a very interesting 2 weeks and learning experience. But my mission is complete and I'm sticking with my new full install of Ubuntu 12.10. Billy G can go up a creek.

With all of your help I've been able to subdue a virus, save my data, and learn that Windows does in fact belong out on the infant populous and I need to grow up and use a real OS. ;)

Interestingly enough I was able to use the LIveCD to transfer files to an old iPhone to back up my data. I just thought the subterfuge of Microsoft&#8217;s and Apple's OSes to transfer important data was priceless and I was hooked. Ubuntu is freeing and powerful. I love it so much now that I want to build a linux OS from scratch for the learning and for moding my iPhone into a mobile tech troubleshoot platform.

Oh and the explanations of permissions in this thread have been way more helpful, understandible, and seemed less dry then others. I did noticed some information may have been copy and pasted from other sources, but you guys jazzed it up so my fickle brain can understand it. Thanks!

---

### Post by bigmonmulgrew on 2013-02-25
> **Morbius1 said:**
> 
As another side note I wouldn’t do this on a drunken bet:
You just made every single file executable.

Yeah, I just wanted an example and showing a reall bad example was probaly not a good idea.

> 
The Jedi way is something like this:
```
chmod -R a+rwX,g-w,o-rwx /directory
```All folders will be 750
All Files will be 640 except those that were executable to begin with.

Show off!

---

