---
title: "HOWTO - Dapper chroot on Edgy for LightScribe"
date: 2006-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by po0f on 2006-12-21
[SIZE="5"]**HOWTO - Dapper chroot on Edgy for LightScribe**[/SIZE]

**2007-02-26**

I no longer have an Edgy machine to keep this guide up-to-date.  I've been using Feisty the past couple of weeks, and it looks like (haven't tried to burn a DVD yet) 4L-gui works just fine!  At least it detects the drive as a LightScribe drive, which was Edgy's problem.  I will still try to help troubleshoot any issues anyone has, so please don't hesitate to ask; I'm not totally abandoning this guide.

This is my first HOWTO so please, bear with me.  :)

As of now, LightScribe support for Edgy is unavailable.  Lacie supports only Fedora Core 5, Ubuntu 6.06, and a few others.  If you already have Edgy installed, and don't feel like downgrading just to get LightScribe support, this HOWTO is for you.

(This guide has been modified for Dapper from [this one](http://www.ubuntuforums.org/showthread.php?t=24575).  Really, without it, this guide wouldn't have been possible.)


**Step 1: Install The Stuff We'll Need**
We need to install debootstrap and dchroot to start off with.  debootstrap will "boot strap" a bare-bones Dapper environment for us to work with, and dchroot will let us chroot into that environment:
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install debootstrap dchroot[/FONT]
```


**Step 2: Configure The chroot environment**
Now, to actually set up and boot strap the chroot environment:
```
[FONT="Courier New"]$ gksu gedit /etc/dchroot.conf

    # Add the following...
dapper /dapper_chroot
    # Done

$ sudo mkdir /dapper_chroot
$ sudo debootstrap --arch i386 dapper /dapper_chroot http://archive.ubuntu.com/ubuntu
    # This step takes a while, be patient
$ sudo chroot /dapper_chroot
    # We are now in the chroot as root
dapper_chroot# dpkg-reconfigure locales
    # Didn't seem to do anything, is this step needed?
dapper_chroot# tzconfig
    # Only if you want to change your chroot's timezone from UTC[/FONT]
```
(Keep this terminal open, as we will shortly be coming back to it.)


**Step 3: Configure apt For The chroot**
The boot-strapped chroot has a pretty pathetic looking /etc/apt/sources.list, let's beef it up a little.  ;)
(Outside of the chroot):
```
[FONT="Courier New"]$ gksu gedit /dapper_chroot/etc/apt/sources.list

    # Add the following (as your morals allow)...  ;)
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
    # Done[/FONT]
```
(You kept that terminal open, didn't you?)
```
[FONT="Courier New"]dapper_chroot# aptitude update
dapper_chroot# aptitude upgrade
dapper_chroot# exit[/FONT]
```
At this point, you can close this terminal.  We'll open another one anyway.  (Using root is bad, mmkay?)


**Step 4: Configure The chroot Just Like Edgy**
Now, we copy over all of the relevant Edgy configs that will let us use the Dapper chroot *almost* like it were Edgy.  (Do this outside of the chroot):
```
[FONT="Courier New"]$ sudo cp /etc/passwd /dapper_chroot/etc
$ sudo cp /etc/shadow /dapper_chroot/etc
$ sudo cp /etc/group /dapper_chroot/etc
$ sudo cp /etc/sudoers /dapper_chroot/etc
$ sudo cp /etc/hosts /dapper_chroot/etc
$ sudo mkdir -p /dapper_chroot/media/cdrom0
$ gksu gedit /etc/fstab

    # Add the following...
/home /dapper_chroot/home none bind 0 0
/tmp /dapper_chroot/tmp none bind 0 0
/dev /dapper_chroot/dev none bind 0 0
/proc /dapper_chroot/proc proc defaults 0 0
/media/cdrom0 /dapper_chroot/media/cdrom0 none bind 0 0
    # Done

$ sudo mount -a[/FONT]
```


**Step 5: Change Your ~/.bashrc**
Now, before we enter the chroot, we'll change our PS1 variable in ~/.bashrc to give us a clue that we are indeed in our chroot'ed environment.  (Outside of the chroot):
```
[FONT="Courier New"]$ sudo touch /dapper_chroot/.dapper_chroot
$ gedit ~/.bashrc

    # Add the following...
if [[ -f /.dapper_chroot ]]; then
    PS1="[\u@\h:/dapper_chroot/\w]\$ "
else
    PS1="[\u@\h:\w]\$ " # or whatever you had it set as
fi
    #Done[/FONT]
```


**Step 6: Installing LightScribe Software**
We need some software before we can actually use our LightScribe burner.  Let's chroot into Dapper and install it now:
```
[FONT="Courier New"]$ dchroot -d
dapper_chroot$ sudo aptitude install alien libstdc++5 gksu wget
dapper_chroot$ cd ~
dapper_chroot$ wget http://www.lacie.com/download/drivers/4L-1.0-r6.i586.rpm
dapper_chroot$ wget http://www.lacie.com/download/drivers/lightscribe-1.4.113.1-linux-2.6-intel.rpm
dapper_chroot$ sudo alien 4L-1.0-r6.i586.rpm
dapper_chroot$ sudo alien lightscribe-1.4.113.1-linux-2.6-intel.rpm
dapper_chroot$ sudo dpkg -i 4l_1.0-1_i386.deb lightscribe_1.4.113.1-1_i386.deb[/FONT]
```

Note: if you are having problems using 'sudo', refer to [this thread](http://www.ubuntuforums.org/showthread.php?t=295677) for a solution.


**Step 7: We're Almost Done!**
That was painless, eh?  Now, while still in the chroot (just to see if it works):
```
[FONT="Courier New"]dapper_chroot$ gksu 4L-gui[/FONT]
```
Voila, 4L-gui should have loaded right up!  Awesome.


**Step 8: Setting Up A Script**
Now, to set up a script that will let us run 4L-gui (and possibly other) programs in a Dapper environment.  (Outside of the chroot):
```
[FONT="Courier New"]$ gksu gedit /usr/local/bin/dapper_chroot

    # Add the following...
#!/bin/bash
/usr/bin/dchroot -d "`echo $0 | sed 's|^.*/||'` $*"
    # Done

$ sudo chmod 755 /usr/local/bin/dapper_chroot
$ sudo ln -s /usr/local/bin/dapper_chroot /usr/local/bin/4L-gui[/FONT]
```
By creating a symlink from dapper_chroot to any program installed *inside* the chroot, we are able to run our programs more easily.
```
[FONT="Courier New"]$ gksu 4L-gui[/FONT]
```

If you just want to "play" around inside the chroot, just execute the following:
```
[FONT="Courier New"]$ dchroot -d[/FONT]
```

Enjoy!  :D

(Please leave feedback, questions, corrections, or hatemail.  I'd love to hear it.)

**[UPDATE]**
2007-01-21:
[list]
[*]Removed setuid recommendation; use `gksu 4L-gui` to run 4L-gui.
[/list]

---

### Post by Coldbird on 2006-12-24
Nice Stuff - Definently will put it to use as I got a Lightscribe DVD+DL Burner in my Notebook ;-)

---

### Post by kevenden on 2006-12-25
Kudos!  This is a great workaround!  :cool:

---

### Post by po0f on 2006-12-26
kevenden,

So it does work for you?  Are there any steps that are a little unclear or just something that I could explain better?  I plan on reformatting it a little bit, just to make it easier to scan through.

---

### Post by Toolbelt on 2007-01-02
I could run the 4L-gui in Edgy with the how-to above, but could not print without root priveledges.  But wow, I did not think this would be solved in the three months since I switch from that other software to Ubuntu.  Thank you for the grey-matter that went into this how-to!

---

### Post by po0f on 2007-01-02
Toolbelt,

I'm glad it worked for you.  :)

I was considering downgrading to Dapper when I got my LightScribe burner, but decided to instead figure out a way to get it to work on Edgy.  I'm thinking of rewriting the guide, should I have clarified more about the need for sudo access to run 4L-gui?

---

### Post by grcastleton on 2007-01-04
Thanks a million! My lightscribe burner was the last piece of hardware I couldn't get working on my new laptop with ubuntu. Only thing I noticed in the how to - I think under step 3 where it says

> $ gksu /dapper_chroot/etc/apt/sources.list

you meant

gksu gedit /dapper_chroot/etc/apt/sources.list

unless there's something there I'm missing. Also as a side note, I had previously built and tried to install .deb of the lightscribe packages with alien on my edgy system, so when I was going through your tutorial I tried to use those debs and they wouldn't install. Worked fine when I used alien from inside the chroot though.

---

### Post by po0f on 2007-01-05
grcastleton,

Yeah, that was a typo, thanks for pointing it out.  :D

When you use alien, I'm assuming that it tries to build a deb that will run on *that* system, not just a generic deb.  Maybe this was your problem.

I'm working on a new way to get this working without having all those filesystems bound-mounted at boot-up.  I ran into an issue with trying to remount one of those filesystems (/tmp).  Maybe a wrapper script.  Check back in a couple of days.  :)

---

### Post by Ubbi on 2007-01-05
All right till this point
>    # Add the following...
/home /dapper_chroot/home none bind 0 0
/tmp /dapper_chroot/tmp none bind 0 0
/dev /dapper_chroot/dev none bind 0 0
/proc /dapper_chroot/proc proc defaults 0 0
/media/cdrom0 /dapper_chroot/media/cdrom0 none bind 0 0
    # Done

$ sudo mount -a

when I type the last line it says
 mount point /dapper_chroot/media/cdrom0 does not exist ](*,) 
I've tried to go on but it doesn't work... I'm going slightly mad.. please help me!

---

### Post by po0f on 2007-01-06
Ubbi,

Before running `sudo mount -a`, run `sudo mkdir -p /dapper_chroot/media/cdrom0` first, that should fix it.

Added it to the commands above as well.

---

### Post by Ubbi on 2007-01-06
It worked... thank you! 

Now it's all ready.. if all works fine I'll set you as my primary god...:KS

---

### Post by Ciego on 2007-01-08
"dapper" is spelled wrong on one of those lines that is why you got the error.  It is the line that creates the directory.  Just add the missing "p" and it should work.

---

### Post by Ciego on 2007-01-08
I am getting this error when I try to run sudo commands in the chroot.  Any ideas?

desktop:~$ sudo aptitude install alien libstdc++5 gksu
sudo: unable to lookup jblind-desktop via gethostbyname()

RESOLVED: with info from this thread   [http://www.ubuntuforums.org/showthread.php?t=295677](http://www.ubuntuforums.org/showthread.php?t=295677)

---

### Post by cjking on 2007-01-10
Thank you   it worked.  Only problems I had where:
                 sudo failed in dapper ------ corrected it by editing the dapper hosts file

                  wget not found in dapper ------ didn't bother to track this one down just downloaded the files to the edgy desktop and copied them to the dapper dir


Again thanks for all the work.

---

### Post by Ciego on 2007-01-10
I had both of those problems also.

An alternative to downloading and transfering the wget files is to just use apt-get and install wget while chrooted in dapper.  I did it that way and it worked.


to get into dapper chroot
```
$ dchroot -d
```
then to install wget within dapper
```
$ sudo apt-get install wget
```

---

### Post by po0f on 2007-01-10
'sudo' failing inside of the Dapper chroot didn't happen to me at all.  Are you guys manually editing your /etc/hosts file from Edgy for whatever reason before copying it over?  I don't use a firewall or have weird network requirements (my Linux box isn't connected to a network unless I need it to be), but I'll be glad to point it out to future users.  (I'll add a link to the solution that Ciego posted earlier.)

Yeah, and as for the 'wget' error, that was just dumb on my part.  I already had the files downloaded from when I previously tried to get it working.  I'll fix that as well.

---

### Post by Ciego on 2007-01-10
I had to change my /etc/hosts (the one in the dapper_chroot) from this
```

127.0.0.1 localhost
127.0.1.1 USER-desktop.WORKGROUP

```
to this
```

127.0.0.1 localhost USER-desktop
127.0.1.1 USER-desktop

```
Where USER = my user name and WORKGROUP = my workgroup name

I cannot remember why, but I think I had to change this file for something else previously,

---

### Post by GIFRATE on 2007-01-10
Thank you, It worked without problem for me

Steph

---

### Post by straps on 2007-01-16
Very very useful stuff, it worked well for me, thanks

---

### Post by Arukuro on 2007-01-19
Hi there thanks for the great post it helped a bunch with installing but i am having a problem with the labeler whenever i open it up everything is fine until i try to print when i click on print it tells me that it dosent recognise the drives on my computer.  in anycase was wondering if anyone else had this problem its a new lighton dvd burner and as far as i know everything works on it my system recongized it so im not sure what to do.  if you or anyone else could point me in the right direction id be in your debt so thx a bunch

---

### Post by po0f on 2007-01-19
Arukuro,

The only thing I can think of is that maybe your DVD burner isn't a LightScribe burner.

[EDIT]

Can you give me a link to the product's web page?  Or just the make and model.

---

### Post by jpneron on 2007-01-21
I just wanted to say "Thanks", it all worked for me. It's burning a label as I type...:) 

It did feel like I was swatting a fly with a sledgehammer to make it work, but in the end, it's all good.

Oh, one small problem, it's doesn't run as root, even tho' I entered the chmod command. The permissions still look like:

lrwxrwxrwx 1 root root 28 2007-01-21 12:37 4L-gui -> /usr/local/bin/dapper_chroot

I can get around it, but I'm curious about why it's running as root.

Thanks.

---

### Post by po0f on 2007-01-21
jpneron,

Yeah, having a whole chroot for just one program is overkill.  Nothing is holding you back from installing other stuff that you can't get quite working under Edgy in that chroot though.  :)

I could have sworn setting setuid on the script would allow a symlink that points to it run setuid as well, but I guess not.  For whatever reason, I *thought* it worked on my box, but it doesn't.  Stupid me.  :)  (I must have been running as root when I tested it.)

For now, the recommendation is to run it by `gksu 4L-gui`.  I'll edit the first post to reflect this.

(More weird behavior; it's acting like "4L-gui" isn't in my path.)  I'll work on it some tonight.

---

### Post by jpneron on 2007-01-21
> **po0f said:**
> 
Yeah, having a whole chroot for just one program is overkill.  Nothing is holding you back from installing other stuff that you can't get quite working under Edgy in that chroot though.  :)


Hmm, there's nothing else I need at the moment, but you're right, I'm all set to go if I do need it...:)

---

### Post by neoaddict on 2007-01-27
I get to the gksu part, but then it tells me that:

(gksu:30550): Gtk-WARNING **: cannot open display:   

Any ideas why?  Every time I try to reconfigure X, X crashes my Edgy session...

---

### Post by po0f on 2007-01-29
neoaddict,

So you've installed 4L-gui and are trying to run it?  Maybe this will fix it:
```
[FONT="Courier New"]$ DISPLAY=:0 gksu 4L-gui[/FONT]
```

---

### Post by pokereth on 2007-01-31
I'm getting the same error.  The exact error is:

```

(gksu:14081): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gksu:14081): Gtk-WARNING **: cannot open display:  
```

```
$ DISPLAY=:0 gksu 4L-gui
```
didn't work either

---

### Post by Mike'sHardLinux on 2007-02-25
po0f, just wanted to say thanks! Your tutorial worked for me!

---

### Post by watson540 on 2007-02-25
I too have the same problem as the above mentioned. I just wanted to remind those like me who cant run the gui program that there is also a cli program that is also installed, very easy to use. I'm burning a print right now in console :)

---

### Post by po0f on 2007-02-25
watson540,

Are you inside the chroot when you run the command `gksu 4L-gui`?  I don't remember having problems running it at all from outside the chroot.

---

### Post by po0f on 2007-02-26
**Update**:

I no longer have an Edgy machine to keep this guide up-to-date. I've been using Feisty the past couple of weeks, and it looks like (haven't tried to burn a DVD yet) 4L-gui works just fine! At least it detects the drive as a LightScribe drive, which was Edgy's problem.

I will still try to help troubleshoot any issues anyone has, so please don't hesitate to ask; I'm not totally abandoning this guide.

(Added the above to the first post as well.)

---

### Post by watson540 on 2007-03-06
Just wanted to point out that there is a newer version of the light scribe software. I only found it on lightscribe.com though, not lacie's site.   lightscribe-1.4.142.1-linux-2.6-intel.rpm

Trying it again for the third time, second time i did it i couldnt even get cli to work, so I dunno. Hoping it was due to an error I caught while installing the chroot

---

### Post by po0f on 2007-03-06
watson540,

Is there any way I could rewrite/reorder the steps to make it easier to understand?  Should I break it down into smaller steps, and give more information?  I know I pretty much pasted just commands and added two-bit commentary where I felt it was needed; so if you have any insight as to how I could better the HOWTO, I would be more than willing to listen.  :)

---

### Post by watson540 on 2007-03-06
I think you did fine in explaining it. I got the cli mode working again but it still won't connect to my running x server from within or outside of the chroot. 

:~# 4L-gui 
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


but cli works fine although i would like to use it to use real pictures and adjust them and junk.

~# 4L-cli enumerate
Using /etc/lightscribe.rc
Drive path: /dev/hda
Usable: 1
Full name: MATSHITA - DVD-RAM UJ-851S  - 1.50
Model: DVD-RAM UJ-851S 
Manufacturer: MATSHITA
Capabilities: monochrome 
Drive inner radius: 21700
Drive outer radius: 59000

It baffles me as to how a process from within a chroot can connect to a running X server anyway
Another edit: The gui works fine if i run it from outside the chroot, but it still wont detect the drive. The gui also works as well without the chroot and by just installing locally, but again...it wont detect the drive. I need to way to run it from inside the chroot. Could it be I have the DISPLAY variable wrong? also I wonder if i can run it on a seperate X server much like gamers do when they have xgl on one server already. Im going to go ahead and try to run a full blown X session from within the chroot :)

---

### Post by watson540 on 2007-03-06
Well hell, I;ve ran X from within a chroot before! I'm downloading 500 megs worth of ubuntu-desktop from within the chroot right now :). It's gotta work

Another thought i had. If you happen to have a dapper cd laying around (i dont) , you could always use the program Reconstructor (its a friggin ecstasy filled goldmine of an app) to rip a dapper live cd directly into a chroot. Would definitely save time from downloading everything, and plus the chroot it makes already has X in it ! Would have to play around a little to make dchroot work with it though but just a thought

EDIT!! 
**ok guys i FINALLY got it, but not after a little sweat and tears. It's so crappy my new hp laptop locks up all the time under linux, seems like it doesnt matter what option i pass to the kernel at boot. so it turned what shold have been a hour long job into a 4 hour job. It was friggin hard as hell to install the nvidia drivers under a chroot'ed dapper environment while running an edgy kernel, heh. If you're one of the lucky onhes who CAN axtually get a display without having to friggin compile proprietARY drivers (not even the ones in the repo work for me) then you are in luck!!**

OK, If you can't get 4L-gui to work, it keeps giving you errors about not anting to connect to x server, AND if you dont mind using up abput 1.4 gigs just to be able to burn a lightscribe disk then do this in the chroot....

apt-get install ubuntu-desktop

That will take a while as it installs X, hopefully you wont need to compile a nvidia driver like i had to cause its a whole world of trouble. After ubuntu-desktop installs in the chroot, stay in there and just type 'startx'!! You will then hae a fully blown x server running under a dapper environment!! LIGHTSCRIBE AWAY!!
THANKS POOF FOR THE HOWTO WISH I COULD GET IT GOING LIKE YOU DID BUT  2 GIGS AND A WHOLE USELESS CHROOT LATER I CAN BURN LIGHTSCRIBE :) :) :) :) :)

---

### Post by po0f on 2007-03-11
watson540,

I'm sorry my how-to as posted didn't work for you, but glad you got it figured out.  :)

---

### Post by trent dillman on 2007-03-30
...

---

### Post by po0f on 2007-03-30
trent dillman,

I had actually edited that part of the default ~/.bashrc out of mine and forgot about its existence.  :)

I don't recall whether it showed up in the window list for me or not on Edgy.  Actually, I just ran it on Feisty, and it doesn't show up in the panel list either, with Beryl *or* Metacity.  Weird.

---

### Post by trent dillman on 2007-03-30
...

---

### Post by Betelgeuse on 2007-04-05
Thank you...
I can now use my new Asus 1612-BL drive... 
I'm using kubuntu, so, I've changed gksu to kdesu and gedit to kate and done all the setup by copy-pasting from this thread. :)

---

### Post by randomnote1 on 2007-05-22
Thanks so much Watson!  I am now running Dapper on top of Edgy and successfully burning lightscribe images!  This actually works out pretty well because I'm running the server install of edgy so I can just keep dapper on the screen at all times.  Anyway, thanks a bunch!

---

### Post by aay on 2007-05-25
Thanks for the howto!  Question.  What models of the Lacie drives are working for people?  Do the portable drives work with Firewire or just USB2?  Also, will the software work only with Lacie drives?  I know that HP also makes similar drives and I'm wondering if people can write to these as well under linux.

Thanks,

Adam

---

### Post by po0f on 2007-06-19
aay,

I'm using neither a Lacie nor an HP LightScribe drive; mine's a Samsung SH-S182M if it means anything to you.  And glad to see people are still using and finding this guide useful.  :)

---

### Post by Sciamano on 2007-06-26
How do we "uninstall" all this dapper_chroot thing?
Lightscribe software now works under Feisty, so I would like to get rid of all this workaround (which was great, btw) but have no idea about how to do that!

---

### Post by randomnote1 on 2007-06-26
you should be able to just delete the directory that you installed dapper in.

---

### Post by Sciamano on 2007-06-27
Yes, I know I can delete the directory, but I would like to know if that's enough, or there is any other operation needed. Thanks

---

### Post by po0f on 2007-07-10
Sciamano,

Deleting the directory should suffice, though you could also `sudo apt-get remove dchroot debootstrap` if you no longer have a need for those programs.  Oh yeah, and you could clean up /etc/fstab.  And get rid of the /usr/local/bin/dapper_chroot / /usr/local/bin/4l-gui scripts if you haven't already.  I think that covers it.  :)

---

### Post by nebriv on 2007-10-26
I just wanted to point out that this also works on ubuntu 7.10 Gusty Gibbon.

---

### Post by rlhanson on 2008-11-19
Will this work for amd64. if so what modifications to the chroot, if any are needed? Also will this work on 'Hardy" or "Intrepid"?

---

### Post by nzalmeida on 2008-12-15
Worked it out, now running

Works great :D

Just made sudo 4L-gui


It worked great until then tried step 8 and now makes this

[nzalmeida@nzalmeida-desktop:~]$ gksu 4L-gui
I::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::[chroot dapper] A executar comando: "4L-gui "
/bin/bash: 4L-gui: command not found
::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::::[nzalmeida@nzalmeida-desktop:~]$ 
[nzalmeida@nzalmeida-desktop:~]$ 
[nzalmeida@nzalmeida-desktop:~]$ 

Any suggestion ???

---

