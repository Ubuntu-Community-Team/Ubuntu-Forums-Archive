---
title: "sudo nautilus"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by umayado on 2008-06-06
Good afternoon,

the situation is this: 

I have to copy some files and folders to my file system.
Nautilus does not let me for i have no right to.

using the terminal and sudo mkdir/cp... would be an option, but might take just way too long.

after looking how to get my nautilus having accept me as its boss, i changed my su password (for it used to work before and all of a sudden it did not anymore)... 

the only effective way i have found of controlling my nautilus, is by opening it through the terminal using 

Sudo nautilus  

i never had to use that command before to be able to write on my file system.(maybe i have unlocked it at some point in my discovery of linux)

what's more, if i type

Sudo nautilus

the only thing i get is this message: 

user@ubuntu:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
user@ubuntu:~$ 


thus in my case it is not that effective afterall..

how can i fix this? 
thank you in advance!

---

### Post by django0909 on 2008-06-06
Press Alt+F2, and type 



```
gksu nautilus
```


You should have free range then :)

---

### Post by umayado on 2008-06-06
moreover, 

if i "su" in my terminal and try to run nautilus, i get this message: 

root@ubuntu:/home/user# nautilus

(nautilus:10827): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
root@ubuntu:/home/user#

i bet the answer is simple, but so am I.

thanks in advance

---

### Post by meindian523 on 2008-06-06
I think it should be ```
gksudo nautilus
```

---

### Post by umayado on 2008-06-06
> **django0909 said:**
> Press Alt+F2, and type 



```
gksu nautilus
```


You should have free range then :)


thanks for the incredible quick reply, but nautilus will not show by doing that. it seems to be disappearing as soon as i hit enter (after giving my correct pwrd).

---

### Post by django0909 on 2008-06-06
Both do the same as far as I'm aware?

edit: Try gksudo nautilus?

---

### Post by umayado on 2008-06-06
> **meindian523 said:**
> I think it should be ```
gksudo nautilus
```

thanks too for the quick one, but still no nautilus at all, not even the chance to give my pwd...

---

### Post by meindian523 on 2008-06-06
yup,they do accomplish the same function,only 'su' is for rpm-family systems,while 'sudo' is for deb-family systems.

---

### Post by avtolle on 2008-06-06
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) on why it is wise to use gksudo with a graphical application, such as Nautilus, rather than sudo.

---

### Post by umayado on 2008-06-06
user@ubuntu:~$ gksudo nautilus
Initializing nautilus-share extension


user@ubuntu:~$ gksu nautilus
Initializing nautilus-share extension


but no nautilus coming up. (also with alt F2)

typing solely nautilus starts nautilus, but restricted

---

### Post by meindian523 on 2008-06-06
Are you on a Live CD?

---

### Post by umayado on 2008-06-06
nope, but upgraded to the latest version... which takes longer to boot too...with error messages never seen before and too fast gone to write down (btw but off topic : i wish i could share my bootlog, but that seems not to work either)

---

### Post by django0909 on 2008-06-06
After a bit of google searching it would appear a lot of people get a 'segmentation fault' after updating nautilus. Did you run a recent update?

---

### Post by umayado on 2008-06-06
yes, but am not sure nautilus was one of the progs being updated.

I had better not upgraded to hardy... previous version worked just fine... even my firefox is not that good anymore...

... still glad I do not have to use windows anymore!

---

### Post by avtolle on 2008-06-06
Recent upgrades have included Nautilus.

---

### Post by umayado on 2008-06-06
thanks, as i have installed kubuntu too i ran 

"kdesu Konqueror" in alt+F2  (in ubuntu)

that seems to work, my system is finally back under my control :D
happy happy joy joy!

(still prefer nautilus though)

---

### Post by meindian523 on 2008-06-06
Well,all's well that ends well.But I would like to know why neither sudo nautilus nor gksudo nautilus would work.

---

### Post by umayado on 2008-06-06
me too

---

### Post by Golem XIV on 2008-06-06
You can try to install the gksu plugin for Nautilus:
```
sudo apt-get install nautilus-gksu
```
This gives you an "Open as administrator" option in the right-click menu.

I don't know if it'll work, though, seeing the problem that you have with **gksudo nautilus**

---

### Post by stchman on 2008-06-06
> **umayado said:**
> Good afternoon,

the situation is this: 

I have to copy some files and folders to my file system.
Nautilus does not let me for i have no right to.

using the terminal and sudo mkdir/cp... would be an option, but might take just way too long.

after looking how to get my nautilus having accept me as its boss, i changed my su password (for it used to work before and all of a sudden it did not anymore)... 

the only effective way i have found of controlling my nautilus, is by opening it through the terminal using 

Sudo nautilus  

i never had to use that command before to be able to write on my file system.(maybe i have unlocked it at some point in my discovery of linux)

what's more, if i type

Sudo nautilus

the only thing i get is this message: 

user@ubuntu:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
user@ubuntu:~$ 


thus in my case it is not that effective afterall..

how can i fix this? 
thank you in advance!

By doing a:

```
gksudo nautilus
```

you will indeed give nautilus root permissions.  I would be careful as accidentally deleting an important file could be bad.

The command line for deleting or adding important info is a good check as you cannot accidentally hit the delete key.

Be careful.

---

### Post by umayado on 2008-06-06
> **Golem XIV said:**
> You can try to install the gksu plugin for Nautilus:
```
sudo apt-get install nautilus-gksu
```
This gives you an "Open as administrator" option in the right-click menu.

I don't know if it'll work, though, seeing the problem that you have with **gksudo nautilus**


I have tried this after your recommendation, but still, after a hopegiving terminal session, gksu nautilus did not have any effect

user@ubuntu:~$ gksu nautilus
Initializing nautilus-share extension
user@ubuntu:~$

---

### Post by Golem XIV on 2008-06-06
> **umayado said:**
> I have tried this after your recommendation, but still, after a hopegiving terminal session, gksu nautilus did not have any effect

user@ubuntu:~$ gksu nautilus
Initializing nautilus-share extension
user@ubuntu:~$

Sorry, I wasn't clear enough.  After installing nautilus-gksu, you need to right-click on the folder you want to open in Administrative mode and select "Open as administrator" from the menu that appears.

---

### Post by cariboo on 2008-06-06
After you install nautilus-gksu you have to logout and then log back in again before it will work.

Jim

---

### Post by umayado on 2008-06-06
indeed after re-logging in the option "open as administrator" does show.
after clicking it the first time it asks me for my password... but still no privileges. after trying it again it not only does not ask a password again, it does not even open the selected folder...

---

### Post by cariboo on 2008-06-06
I just tried it and after you enter your password another window opens and you can do what you need. So if you want to copy files from your home directory to a directory you don't have write permissions do you have to open both directories as administrator.

Just a thought what is it exactly that you are trying to do?

Jim

---

### Post by umayado on 2008-06-06
> **cariboo907 said:**
> 

Just a thought what is it exactly that you are trying to do?



copying files from my partition to my system folder ( usr/share ) in order for a prog to work... (works via the terminal and also via konqueror, but nautilus does not seem to give me the permission to write on it in any way... althoug it used to perfectly right before my upgrade to hardy)

---

### Post by kellemes on 2008-06-06
> **meindian523 said:**
> yup,they do accomplish the same function,only 'su' is for rpm-family systems,while 'sudo' is for deb-family systems.

Not at all..
su is for **becoming** another user, the default is root but you can "su john" and become john.
Ubuntu has no root-account by default, and so typing "su" is pointless because it's default is (non existing) root.
With sudo you can run a command as another user (default root), it'll ask for your password, it will **not** make you root!
/etc/sudoers gives you a hole lot of flexibility to manage sudo privileges.
sudo is very handy when you have multiple administrators on your system, since there is no root-password to share.
Having no root-account is safer also, crackers will first try to crack the root-account, rather pointless when there isn't any.
And so they need to guess a username and password, chances are they'll try to crack another system.

sudo seems to be used a lot on Debian based systems but you can run it on every linux system and surely you'll find it installed or at least available on most desktop oriented systems.

---

### Post by DarkDancer on 2008-06-06
Just to chime in I have exactly the same problem.

---

### Post by meindian523 on 2008-06-07
> **kellemes said:**
> Not at all..
su is for **becoming** another user, the default is root but you can "su john" and become john.
Ubuntu has no root-account by default, and so typing "su" is pointless because it's default is (non existing) root.
With sudo you can run a command as another user (default root), it'll ask for your password, it will **not** make you root!
Well,of course,but in this case,OP wanted to be root,and su and entering his password would have given him root privileges in terminal,thence he could launch nautilus as root.

---

### Post by DarkDancer on 2008-06-07
Yes, yes, all the above is true, but I think we have lost focus here that the OP (and myself) can try any of the means to open nautilus with root access and nautilus will not open.

---

### Post by meindian523 on 2008-06-07
lol,the OP had his problem solved via Konqueror,and we all are clueless why nautilus wouldn't open with sudo,without even giving an error message.So,presently,we can't help you.Refer above post in which we said "We want to know why Nautilus wouldn't open"

Say,would syslogs give some info?

---

### Post by DarkDancer on 2008-06-07
Actually, it gives an error, "Segmentation fault" though I have no clue what that means....

Ok, now I know what it means, it's trying to write to a location where, for whatever reason it's can't write....still doesn't help much I guess....

---

### Post by meindian523 on 2008-06-07
That means it's trying to write to memory it doesn't own.In short,it's crashing because process management won't allow it to write to memory which does not belong to it.That means process management is doing it's work properly,you might consider filing a bug against nautilus if you can get tracebacks or the core-dump file.
Just a note,gksudo nautilus runs fine on my machine ,so it has very doubtful grounds for a bug report.Also,there's no reported bug for this particular problem,so presumably this is a problem with just the boxes of the two of you guys.

---

### Post by monkeymind90 on 2008-06-07
I'm having the same problem here. I tried gksu and gksudo, but neither opened nautilus. I also cannot open gedit, also because of a segmentation fault. I first noticed it after I installed nautilus-script-audio-convert, but I also updated shortly before. Any help would be appreciated.

---

### Post by DrFugly on 2008-06-07
I have the same error myself, very annoying. I even tried reinstalling sea-horse and nautilus. No avail.

---

### Post by yesudeep on 2008-06-11
Please install nautilus-dbg using

(user)$ sudo aptitude install nautilus-dbg

Can you guys show us the output of 

(user)$ sudo -s -H
(root)# gdb nautilus
(gdb) run
....
(gdb) bt
...
#We need to see what happens here.
...

Cheers,
Yesudeep.

---

### Post by cariboo on 2008-06-11
I just tried gksu nautilus and it opened in /root, I have nothing extra installed.

Jim

---

### Post by peterthewolf on 2008-06-12
While the segmentation problems and the like are outstanding. I suggest you install thunar via synaptic and then invoke by sudo thunar.

---

### Post by didli on 2008-06-12
Hi, I have the problem too, nautilus won't open in root after I mess up some things with gvfs (which it's the buggiest thing Ubuntu has ever released I think, got a lot of problems with it).
I had tried to aptitude remove & purge nautilus, reinstall, etc, no way.
It looks like something is broken with nautilus, something related only to nautilus root config. Maybe we could get it to work if we "reset" the config files ?
But where are these config files ? /root/.config/(?) ?
Thanks

---

### Post by EmilPilafi on 2008-06-15
I had the same problem with gdm and nautilus. I don't know where this problem is really located, but I solved it in my pc by booting in recovery mode.
I made a repair of packages. Now it seems nautilus and login window are working. 

Absolute Beginner Talk

---

### Post by umayado on 2008-06-17
> **yesudeep said:**
> Please install nautilus-dbg using

(user)$ sudo aptitude install nautilus-dbg

Can you guys show us the output of 

(user)$ sudo -s -H
(root)# gdb nautilus
(gdb) run
....
(gdb) bt
...
#We need to see what happens here.
...

Cheers,
Yesudeep.

[B][I][COLOR="Purple"]OK, after 
(gdb) run

i get this in my treminal :[/COLOR][/I][/B]

[Thread debugging using libthread_db enabled]
[New Thread 0xb6b23720 (LWP 3729)]
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:3729): WARNING **: Unable to add monitor: Operation not supported
[New Thread 0xb5413b90 (LWP 3744)]
[New Thread 0xb499db90 (LWP 3745)]
[Thread 0xb499db90 (LWP 3745) exited]
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[New Thread 0xb499db90 (LWP 3754)]
[Thread 0xb5413b90 (LWP 3744) exited]

[B][I][COLOR="Purple"]... and a window pops up (nautilus?! looks slightly different) in which i indeed am able to create folders and such on my filesystem. trying to use the original nautilus still does not let me do this.

[/COLOR][/I][/B]

---

### Post by umayado on 2008-06-17
now even the "kdesu Konqueror" does not work anymore in alt f2....

"command not found!"...

I'm lost here

---

### Post by aysiu on 2008-06-17
> **umayado said:**
> now even the "kdesu Konqueror" does not work anymore in alt f2....

"command not found!"...

I'm lost here
Are you using KDE 4?

If so, try ```
kdesu /usr/lib/kde4/bin/konqueror
```

---

### Post by Morticutor UK on 2008-06-18
> **yesudeep said:**
> Please install nautilus-dbg using

(user)$ sudo aptitude install nautilus-dbg

Can you guys show us the output of 

(user)$ sudo -s -H
(root)# gdb nautilus
(gdb) run
....
(gdb) bt
...
#We need to see what happens here.
...

Cheers,
Yesudeep.


I'm having the same problem - here's my output.

 Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb441eb90 (LWP 6892)]
0x00000000 in ?? ()
(gdb) bt
#0  0x00000000 in ?? ()
#1  0xb76acc79 in ?? () from /usr/lib/libgio-2.0.so.0
#2  0xb76a67b4 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0xb75e969b in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb75e7a6f in ?? () from /usr/lib/libglib-2.0.so.0
#5  0xb736e4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb72efe5e in clone () from /lib/tls/i686/cmov/libc.so.6

---

### Post by umayado on 2008-06-20
> **aysiu said:**
> Are you using KDE 4?

If so, try ```
kdesu /usr/lib/kde4/bin/konqueror
```

same output: "command not found"
(using ubuntu, under kubuntu konqueror still works like a charm)

---

### Post by aysiu on 2008-06-20
There is no Konqueror in Ubuntu.

```
gksudo nautilus
```

---

### Post by aysiu on 2008-06-20
There is no Konqueror in Ubuntu.

```
gksudo nautilus
```

---

### Post by umayado on 2008-06-23
there is in mine...

---

### Post by aysiu on 2008-06-23
Maybe try ```
sudo apt-get update
sudo apt-get install kdesudo konqueror
which konqueror
kdesu konqueror &
```

---

### Post by esquared on 2008-06-25
I am also having the same problem.  (Hardy)  Mine happened right after a hard lockup and power down.  One of my disks failed the disk check during boot, I did a ctrl+D, system booted fine, but I lost all the data on one of my drives,  Glad I was going to do a fresh reinstall / format soon anyway.

---

### Post by Tatty on 2008-06-25
A Segmentation Fault "usually" suggests you have a hardware problem.  It might be a software problem, but bets are on hardware - especially if you have more than one application crashing with a segmentation fault.

Try swapping the ram if you can and see if that helps.

[http://aplawrence.com/Unixart/segmentation_fault.html](http://aplawrence.com/Unixart/segmentation_fault.html)

---

### Post by mikedep333 on 2008-06-28
If this is a hardware failure, then we all have hardware failures, because I am getting the same segmentation fault message. Far more likely by an order of magnitude is a bug in ubuntu somewhere. Somebody who has debug installed should file a bug report, and in the meantime a workaround would be very much appreciated.

BTW: This bug has another implication. If you try to browse for files in a graphical application like file-roller or gedit, it crashes. I therefore conclude that this is a bug in shared portion of gnome/nautilus.

UPDATE - installing thunar and mousepad from xfce is working well enough for me in the meantime.

---

### Post by mysticalzero on 2008-06-29
Well, I have the same problem.

Nautilus crashed when I attempt to open a folder using the "Open with administrator" right-click context menu item. 

Output of dmesg:
```
[ 1854.634512] nautilus[23440]: segfault at 00000000 eip 00000000 esp b62d425c error 4
[ 2098.015145] nautilus[23369]: segfault at 55000020 eip b76652d6 esp bffdf610 error 4
[ 2105.950666] nautilus[25456]: segfault at 7c000020 eip b76fd2d6 esp bfa99560 error 4
[ 2198.890901] nautilus[26281]: segfault at 00000000 eip 00000000 esp b62cb25c error 4
[ 2214.383303] nautilus[26414]: segfault at 00000000 eip 00000000 esp b383f25c error 4
[ 2306.563702] nautilus[27164]: segfault at 00000000 eip 00000000 esp b634725c error 4
[ 2941.811092] nautilus[25504]: segfault at ac000020 eip b77452d6 esp bffc0640 error 4
[ 3413.546015] nautilus[32464]: segfault at dc000020 eip b77252d6 esp bfabe950 error 5
[ 3435.918150] nautilus[4542]: segfault at 00000000 eip 00000000 esp b68aa25c error 4
[ 3571.977015] nautilus[6434]: segfault at 00000000 eip 00000000 esp b635325c error 4

```

Output of gdb nautilus:
```
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]
[New Thread 0xb6ab6720 (LWP 13326)]
Initializing nautilus-share extension
seahorse nautilus module initialized
[New Thread 0xb6271b90 (LWP 13343)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb6271b90 (LWP 13343)]
0x00000000 in ?? ()
(gdb) bt
#0  0x00000000 in ?? ()
#1  0xb761cc79 in ?? () from /usr/lib/libgio-2.0.so.0
#2  0xb76167b4 in ?? () from /usr/lib/libgio-2.0.so.0
#3  0xb755869b in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7556a6f in ?? () from /usr/lib/libglib-2.0.so.0
#5  0xb72dd4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb725fe5e in clone () from /lib/tls/i686/cmov/libc.so.6

```

Besides, I realised the following was shown under nautilus's dependencies in synaptic package manager.

```
Conflicts: libnautilus2-2
Replaces: libnautilus2-2
```

Is there anything wrong with that? Could this be the cause?


Any help will be appreciated.

Edited:

Problem solved. Weird as it seems, what I did was just force nautilus to an older version(2.22.2-0ubuntu4) and then update it to the latest version(2.22.3-0ubuntu2). And again, gksu nautilus works. But, one thing remains. Whenever I closed an elevated nautilus window, "segfault" appears in dmesg. Well, who cares. Afterall, the main problem is gone.:)

---

### Post by wolfen69 on 2008-06-30
i too am now getting: ```
Initializing nautilus-share extension
seahorse nautilus module initialized
Segmentation fault

```
when i type gksudo nautilus. i am looking for an answer, but havnt found it yet. nautilus will not initialize no matter what i do. hmmmmm. from the looks of this thread, there are a few others that have the same problem. has anyone filed a bug report?

---

### Post by wolfen69 on 2008-06-30
i thought there might be a more elegant solution, but a simple uninstall(completely remove)/reinstall fixed it. just make sure to do ```
sudo apt-get autoremove
``` before reinstalling. can i give myself a thanks? ciao.

---

### Post by meindian523 on 2008-06-30
I'll give you one on your behalf. :P :)

---

### Post by daitheflu08 on 2008-07-01
Okay back to the solution to his original question.  

I came across this error but ONLY when the system was unable to read from a particular device.  In this case, I was burning a DVD.  As soon as I stopped burning it, it opened with a simple sudo nautilus like I had been doing.

---

### Post by Lem98 on 2008-07-01
> **yesudeep said:**
> Please install nautilus-dbg using

(user)$ sudo aptitude install nautilus-dbg

Can you guys show us the output of 

(user)$ sudo -s -H
(root)# gdb nautilus
(gdb) run
....
(gdb) bt
...
#We need to see what happens here.
...

Cheers,
Yesudeep.

Ok, that's it. I'm on Ubuntu Hardy 64 bit.

(gdb) run
Starting program: /usr/bin/nautilus 
[Thread debugging using libthread_db enabled]
[New Thread 0x7f9f0102a7a0 (LWP 14857)]
[New Thread 0x40cf5950 (LWP 14870)]
Initializing nautilus-open-terminal extension
Initializing nautilus-share extension
seahorse nautilus module initialized
[New Thread 0x414f6950 (LWP 14875)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x40cf5950 (LWP 14870)]
0x0000000000000000 in ?? ()
(gdb) bt
#0  0x0000000000000000 in ?? ()
#1  0x00007f9efd642e66 in ?? () from /usr/lib/libgio-2.0.so.0
#2  0x00007f9efd6561bf in ?? () from /usr/lib/libgio-2.0.so.0
#3  0x00007f9efd65042e in ?? () from /usr/lib/libgio-2.0.so.0
#4  0x00007f9efcf76bf7 in ?? () from /usr/lib/libglib-2.0.so.0
#5  0x00007f9efcf75054 in ?? () from /usr/lib/libglib-2.0.so.0
#6  0x00007f9efbe783f7 in start_thread () from /lib/libpthread.so.0
#7  0x00007f9efbbe7b2d in clone () from /lib/libc.so.6
#8  0x0000000000000000 in ?? ()
(gdb)

I've noticed this problem just today, I'm sure a few days ago it was't there. I install all security and proposed upgrades, as soon as they're released.

Oh, I have the same problem with gdmsetup: segmentation fault. It runs for less than a second, then suddenly crashes. Noticed today, never before. But I *rarely* open gdmsetup.

However, if I login in X as root, I surely can run nautilus an gdmsetup smoothly.

Hope this helps, bye.

---

### Post by BirdWatcher on 2008-07-04
Okay guys, here's my "solution",

After reading through this thread I noticed someone had a problem while burning a DVD.
I then realized I had an empty DVD in my burner because at some point I wanted to make a backup (I was not burning!).
Opened the burner, removed the DVD, closed it again.
entered "sudo nautilus" and presto! :popcorn:

As I am fairly new to Linux I really have no idea what the problem was/is, but I guess that you guys can make more of it.

Registered immediately to let you guys in on this.
My english can be somewhat rusty, so apologies for that.

Greetz
André

---

### Post by Lem98 on 2008-07-05
> **BirdWatcher said:**
> Okay guys, here's my "solution",

After reading through this thread I noticed someone had a problem while burning a DVD.
I then realized I had an empty DVD in my burner because at some point I wanted to make a backup (I was not burning!).
Opened the burner, removed the DVD, closed it again.
entered "sudo nautilus" and presto! :popcorn:

As I am fairly new to Linux I really have no idea what the problem was/is, but I guess that you guys can make more of it.

Registered immediately to let you guys in on this.
My english can be somewhat rusty, so apologies for that.

Greetz
André

Great! :)

I've just removed an empty CD, and now both problems are solved: with nautilus and with gdmsetup.

**Thanks a lot**,

bye.

---

### Post by helmingstay on 2008-07-07
> **Lem98 said:**
> 
I've just removed an empty CD, and now both problems are solved: with nautilus and with gdmsetup.


Hmmm.  I call that a work-around rather than a solution.  Segfaulting on an empty cd is definitely a problem, as is having to downgrade a package.

Is it possible to turn off nautilus handling of media insert events to temporarily "solve" this?  All i want at present is for nautilus to handle desktop/status bar.

I tolerate nautilus in lack of other really compelling, non-3d desktop managers (I use openbox for window manager, bash for files).  To some extent, the vast scope of what nautilus handles makes these annoyances inevitable.  Worse, the bug report for this was marked as invalid without explanation and then pointed to here, which doesn't seem to inspire one to write nautilus/gnome bug reports.  ( see [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/245931]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/245931") )

Users tend not to switch app packages frequently.  If I'm forced to use thunar/xfce (or in my instance wicd instead of NetworkManager) for a week and I'm satisfied, I'm unlikely to switch back.

just my $.50... :)

---

### Post by sirgogo on 2008-07-07
Why don't you try ending the X-server session and the current nautlius session (gdm exit)? Then you can start both again from the terminal screen (Ctrl+Alt+F1/F7)

---

### Post by robgue on 2008-07-07
wow.I had the same problem. Finally just took out a blank dvd the was sitting in the drive and the above worked. I can run sudo nautilus without the segmentation fault error.:confused:

---

### Post by VitalBodies on 2008-07-14
I had just burned a label with LightScribe for a blog article I was doing on how to install LightScribe in Ubuntu. I did not need to add data to the disk as I was just checking the label burner. Flipped the disk to the data side for whenever the next data burn might be and thus BROKE Nautilus. Had the same error you all had... Removed the disk and FIXED Nautilus. 

Just a side note: This error does not happen with the disk label side down but only data side down. In other words, only when the data side is towards the laser. 

I wonder if this only happens with blank disks? 

Answer, yes...

---

### Post by mc4man on 2008-07-14
Maybe this (in relation to blank media) is due to the fact that when you have 'unmounted removable media' on the system and run gksudo nautilus the behavior is for the media to be auto mounted by root. For instance, if you insert a usb thumb drive, unmount it but don't remove it and then run gksudo nautilus the drive will get mounted owned by root. So in the case of blank media which doesn't get mounted root tries to mount and can't.

Side note
If you go to system -> administration -> Authorizations you can give yourself Explict Authorizations in the storage section for several things. The first one and the third one are the most useful. So in the case above I can unmount the drive owned by root. The third one allows you to mount your other partitions (Ext2,3 ect.) with full permissions by just d. clicking

---

### Post by Mazehero55 on 2008-09-30
MY GOD, I was freaking out until I got to the end of the thread and realized I had a blank DVD in my drive.:D
Yeah this is a major problem, I'm sure many people who didn't find this thread gave up on ubuntu when all along it was just a blank disc in their drive.

---

