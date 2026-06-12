---
title: "I really want to get arch working but..."
date: 2007-06-09
forum: Other OS Talk
---

### Post by miggols99 on 2007-06-09
the configuration files are easy, but they tell me to "look in some file for what to put here". Could someone help me with this? I really would like to try Arch, but these confusing configuration files and un-userfriendly installer is stopping me.

---

### Post by Outrunner on 2007-06-09
You'll need to be more specific. What are you trying to do and when you say it says "look in some file", what file does it tell you to look in? I've never used Arch myself so I don't know what to say more than that.

---

### Post by miggols99 on 2007-06-09
I looked around. I've got it almost to a GUI! I just need to do the xorg.conf. Pacman (the package manager) is really easy :) I'm trying to install KDEmod now...

---

### Post by ynnhoj on 2007-06-09
> **miggols99 said:**
> I looked around. I've got it almost to a GUI! I just need to do the xorg.conf. Pacman (the package manager) is really easy :) I'm trying to install KDEmod now...
if you have any trouble getting x to work, check out the entry on it in the arch wiki; it's pretty helpful.

---

### Post by pelle.k on 2007-06-09
Please, search the wiki and forums before you scratch your head.
"look in some file for what to put here" is not really an accurate description of a problem.

The installer is really a reflection of what arch linux is all about, so if you don't like it, prepare to be put off by the rest of the system. If you haven't figured that out already, arch's philosophy is to take you as close to a raw linux system, while maintaining simplicity. Simplicity is a diverse word, i know, but it doesn't mean automation and less functionality in this case.
If you would have tried LFS out, you _would_ know what i'm talking about.

btw. i recommend this link;
[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by ThinkBuntu on 2007-06-09
first, update everything, with
pacman -Syu

then, for graphical interface:

pacman -S xorg kde-base

and to start it, I think:

/etc/init.d/kdm start

or maybe

/etc/rc.d/kdm start

---

### Post by .aku on 2007-06-09
> **ThinkBuntu said:**
> 
and to start it, I think:

/etc/init.d/kdm start

or maybe

/etc/rc.d/kdm start

or, add kdm to your daemons line in /etc/rc.conf

example (from my /etc/rc.conf)
DAEMONS="blahblahblahblah hal **kdm** alsa cpufreq"

*for xorg.conf, there is an easy way to make one..*
first, install *hwd*..
**pacman -S hwd**, then type **hwd -xa** to automagically generate a new xorg.conf, then modify it to your liking..

//aku

---

### Post by ThinkBuntu on 2007-06-09
Of course you have to do that, too. But that requires a restart, so to play right away, you have to use the start command.

---

### Post by miggols99 on 2007-06-10
Ok thanks for all the help guys :). I'm on Windows right now (I need some kind of GUI...) so I'll try and at least get a GUI on Arch.

EDIT: I followed your instructions .aku and ThinkBuntu, and I've got into a GUI now! I'm going to try install kdemod now. I've heard good things about it.

---

### Post by Ozzu on 2007-06-10
I'm a little late to the party, but the 'hwd' tool is really cool for just getting your xorg.conf up and running well. It's as easy as this:

pacman -S hwd
hwd -x
then cd /etc/X11 and mv xorg.conf.hwd xorg.conf

At this point, I usually install my video card drivers. So for instance, if you're using nvidia, I do a 

pacman -S nvidia
then nvidia-xconfig

And once inside the GUI, it looks all furry. I do a nvidia-settings in a term, change my vid settings to how I like them, then hit apply and then the save to config file button at the bottom of the settings screen. Boom. Video is perfect, fonts look great, etc.

---

### Post by .aku on 2007-06-10
> **Ozzu said:**
> I'm **a little late** to the party, but the 'hwd' tool is really cool for just getting your xorg.conf up and running well. It's as easy as this:

pacman -S hwd
hwd -x
then cd /etc/X11 and mv xorg.conf.hwd xorg.conf


yep, a little, and only to say what I already posted hours ago (about hwd)...
did you actually read the thread before posting ?

//aku

---

### Post by pelle.k on 2007-06-10
Go easy on the guy. At least he was helpful, even though i agree you should read a thread before posting, but we all do mistakes :)

---

### Post by .aku on 2007-06-10
Yeah, I should calm down a bit..
Sry.

Maybe I'm having a bad one today, 
but still I think filling up the forums with stuff someone else has already said is just plain dumb.

But I apologize if I was rude..

---

### Post by thecdn on 2007-06-11
Seems to be lots of good arch knowledge here. I installed on the weekend and played with it some - love the look the speed, and pacman, but I couldn't get amarok to play. Every time it said couldn't start the engine (I'm at work and can't remember the exact message). 

I did follow the beginner guide but I guess I need the guide for really dumb people - this is the first time I've tried anything other than a do most everything for you distro. I read some threads on the arch forum but nothing I tried would get past this. Any ideas?

---

### Post by .aku on 2007-06-11
> **thecdn said:**
> Seems to be lots of good arch knowledge here. I installed on the weekend and played with it some - love the look the speed, and pacman, but I couldn't get amarok to play. Every time it said couldn't start the engine (I'm at work and can't remember the exact message). 

I did follow the beginner guide but I guess I need the guide for really dumb people - this is the first time I've tried anything other than a do most everything for you distro. I read some threads on the arch forum but nothing I tried would get past this. Any ideas?

Hey,
about Amarok..
Have you installed '**amarok-engine-xine**' ??
```
pacman -S amarok-engine-xine
```
If yes, is it selected in Amarok preferences ?

//aku

---

### Post by thecdn on 2007-06-11
> **.aku said:**
> Have you installed '**amarok-engine-xine**' ??

I installed 'amarok-base'

> If yes, is it selected in Amarok preferences ?

Will check when I get home tonight. Thanks for the info.

---

### Post by .aku on 2007-06-11
> **thecdn said:**
> I installed 'amarok-base'

Will check when I get home tonight. Thanks for the info.

Ok..
I can't remember if **amarok-engine-xine** is a dependency for **amarok-base**...
at least it doesn't state it as one on the arch site..?
Try installing it and selecting xine as the default sound engine in Amarok preferences..

Let me know how it goes..

//aku

---

### Post by thecdn on 2007-06-12
amarok-engine-xine was already installed

xine is the only option for sound engine and is already selected.

The proper error message, which I'm still getting, is:
"xine was unable to initialize any audio drivers"

---

### Post by .aku on 2007-06-12
Does any sound work at all?
Is the soundcard working / drivers set up ?
Is **alsa-lib** installed ?

[http://wiki.archlinux.org/index.php/ALSA_Setup]("http://wiki.archlinux.org/index.php/ALSA_Setup")

Can you give more info from your system ?
Please post the output of **lspci** if you can ?

//aku

---

### Post by Rumor on 2007-06-12
@thecdn
Is alsa listed in the daemons in your /etc/rc.conf file?

---

### Post by kazuya on 2007-06-12
very educational forum link, I shall be installing arch tonight or tommorrow night.

---

### Post by thecdn on 2007-06-12
I'll check for the above stuff and post the results when I get home later. I want to say alsa is in rc.conf but after a half dozen or so installs over the last 3-4 days I can't be 100% sure at the moment :)

---

### Post by .aku on 2007-06-12
EDIT: Just try what Rumor suggested.. It worked for me (back in the days) when I had no sound in Arch..
There was something else too (hardware wasn't recognized, on my older laptop),
so I had to modprobe the module for my soundcard/chip, (snd_intel8x0) if I remember right.. ??

Read the Arch wiki, it's really helpful..

---

### Post by _narayan on 2007-06-12
Yes, the Arch wiki is outstanding. It's a one stop shop for all that ails ya

---

### Post by thecdn on 2007-06-12
Music!! I have music!!!  I'm not 100% sure, but I think the command from the wiki that put me over the hump was  "pacman -S alsa-oss" as it was the only command that didn't result in an 'already installed' message, or was something I knew I had done.

Thanks to everyone for their help in this. Now to hit the wiki again and figure out why my usb stick doesn't mount.........

---

### Post by pelle.k on 2007-06-12
well, i've never needed to install alsa-oss myself. Only needed to unmute alsa mixer (or the equivalent from kmix). You do know alsa is muted by default, right? oss isn't. maybe thats why it's working all of a sudden...
Speaking of sound. If you install alsa-utils (should be all you need to have sound working) you get a daemon (alsa) that you can add in rc.conf. It's responsible for saving/setting sound levels at startup/shutdown. Just a tip.

---

### Post by .aku on 2007-06-13
> **thecdn said:**
> Music!! I have music!!!  I'm not 100% sure, but I think the command from the wiki that put me over the hump was  "pacman -S alsa-oss" as it was the only command that didn't result in an 'already installed' message, or was something I knew I had done.

Thanks to everyone for their help in this. Now to hit the wiki again and figure out why my usb stick doesn't mount.........

About usb stick mounting ...

I installed **hal** and **dbus**  (**pacman -S hal dbus**), and added **hal** to the *daemons* array (*in front of kdm*) in **/etc/rc.conf**..

Also, I had to add myself (user) to groups:
*gpasswd -a username groupname*

like this:
```
gpasswd -a aku hal
gpasswd -a aku dbus
```

I cannot recall what was necessary, but for example my user account is in groups *audio, optical, storage, hal, dbus, wheel*..
I think adding yourself to groups **hal, dbus & storage** could be useful in your situation..


//aku

---

### Post by pelle.k on 2007-06-13
No need to be in hal and dbus to automount external devices. Just as a comparison, the only groups i'm a member of is;

wheel - sudo
audio - well, to have audio on the desktop of course!
optical - you might need it to burn to cd/dvd
storage - to access other disks/partitions (and possibly automount)
power - powersave lets user suspend/hibernate etc.
users - well duh! ;)

---

### Post by ThinkBuntu on 2007-06-13
What was stopping my devices from automounting before was my daemons line. I added dbus (not just hal) and that took care of things nicely.

---

### Post by .aku on 2007-06-13
> **ThinkBuntu said:**
> What was stopping my devices from automounting before was my daemons line. I added dbus (not just hal) and that took care of things nicely.

I've never had dbus in my daemons array, and I still have automounting..

To Pelle.K, I wasn't sure about the groups, hal & dbus are a bit confusing..
But I also think that the user should be in group 'storage' for automount..

//aku

---

### Post by ThinkBuntu on 2007-06-13
> **.aku said:**
> I've never had dbus in my daemons array, and I still have automounting..

To Pelle.K, I wasn't sure about the groups, hal & dbus are a bit confusing..
But I also think that the user should be in group 'storage' for automount..

//aku
I just took it off, and now I have no problems. It's strange because before it appeared to be the solution. In any case it works great! I'm loving GNOME in Arch.

---

### Post by pelle.k on 2007-06-13
About dbus and hal. It is the combo that lets you automount, but you only need hal, since it starts dbus as a dependency.
If you run powersave, both acpid, hal and dbus will be started automatically, thus if you add one of them as well you will have an extra one and it will "fail" (or both will fail).

If you're unsure you could just check out the beginning of an rc script (daemon) your wondering about. It's only a few lines of bash...

---

### Post by .aku on 2007-06-13
> **pelle.k said:**
> 
If you run powersave, both acpid, hal and dbus will be started automatically, thus if you add one of them as well you will have an extra one and it will "fail" (or both will fail).


Oh, I didn't know this one.. Thanks for the pointer pelle ! ;)

//aku

---

