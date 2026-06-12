---
title: "*gasp* I just installed Debian..."
date: 2010-03-26
forum: Recurring Discussions
---

### Post by Psumi on 2010-03-26
Pros:
1. Debian is much faster.
2. It takes up less RAM (most of the time.)
3. It gave me 6 extra MB of Physical RAM that was previously unusable in ubuntu.

Cons:
1. (-ish) su - instead of sudo.
2. backports.org is needed to get pidgin 2.6.6 and MSN working.
3. backports.org upgrading breaks Rodent theme, so have to install gnome-icon-theme.

Overall, it's a very nice distribution, no wonder Ubuntu based itself off of it.

---

### Post by _h_ on 2010-03-26
A new adventure for you everyday. :)

---

### Post by XubuRoxMySox on 2010-03-26
Congratulations! It was easier than you expected, wasn't it? Which Debian are you using (Lenny, Squeeze, or Sid)? I'm using Squeeze/Xfce. Light, fast, stable, bug-free!

-Robin

---

### Post by Psumi on 2010-03-26
> **dixiedancer said:**
> Congratulations! It was easier than you expected, wasn't it? Which Debian are you using (Lenny, Squeeze, or Sid)? I'm using Squeeze/Xfce. Light, fast, stable, bug-free!

-Robin

Lenny with backports.

---

### Post by descendent87 on 2010-03-26
Rather than using lenny with backports you should try squeeze, newer packages but still pretty damn stable

---

### Post by Psumi on 2010-03-26
> **descendent87 said:**
> Rather than using lenny with backports you should try squeeze, newer packages but still pretty damn stable

I'll think about it, but doubtful.

---

### Post by NightwishFan on 2010-03-26
Personally I would say to use Testing or selectively update some packages from it. Using Lenny is to be admired though for the dedication to wanting stability. Have fun with Debian, it is the most excellent software project I have ever known to exist.

Edit: I run sid on my desktop without any crashes or issue, however I recently have switched to testing because I do not need to move up in packages a lot. I am currently running Ubuntu on my laptop because I enjoy the out of the box functionality and the small papercuts I tend to notice.

---

### Post by blueshiftoverwatch on 2010-03-26
I started using Debian Testing a few weeks ago. For the most part it seems just like Ubuntu. But, there are a few things that Ubuntu does automatically that Debian doesn't. For example, I'll need to manually setup Pulse Audio.

---

### Post by Zoot7 on 2010-03-26
I use Squeeze myself, I prefer build the debs from source to get the apps from the Sid repo, which is very up to date. I've Lenny on my desktop, merely because I need a good sound stable distro that doesnt' update all that often as I don't get to sit in front of it too often.

TBH I'm done with the Debian spinoffs at this stage, I don't think I'll look elsewhere from Debian itself again. I'm really looking forward to the next release of Squeeze, I gather they've a good load of trouble with the freeze right now though (bug count too high).

---

### Post by caravel on 2010-03-26
> **Psumi said:**
> Cons:
1. (-ish) su - instead of sudo.
Not a con, that's how its supposed to be done (despite what some may think).

---

### Post by Psumi on 2010-03-26
> **blueshiftoverwatch said:**
> I started using Debian Testing a few weeks ago. For the most part it seems just like Ubuntu. But, there are a few things that Ubuntu does automatically that Debian doesn't. For example, I'll need to manually setup Pulse Audio.

Pulse Audio, lol.

Anyway, I used the lenny >> Squeeze full-upgrade method; everything went smoother than I thought o_O

Also, anyone know how to get the latest midori for debian i386 without having to make it from source? 0.1.8 seems a bit old in comparison to 0.2.4... (though sid has 0.2.4-1 in its repos.)

But I have to use gnash now, because flash is crashing midori 0.1.8 and iceweasel 3.5.8. This is a problem, because no youtube videos load with gnash.

---

### Post by NightwishFan on 2010-03-26
If it isnt a core package, you could add sid temporarily and install midori, then disable sid. There might be a cleaner way to accomplish this same thing, but I do not know.

---

### Post by hhh on 2010-03-26
[http://packages.debian.org/sid/midori](http://packages.debian.org/sid/midori)

Scroll down, click i386, choose mirror, open a terminal, cd to download directory, then...
```
dpkg -i midori_0.2.4-1_i386.deb
```

Done.

---

### Post by yeleek on 2010-03-26
> **Psumi said:**
> Pros:
1. Debian is much faster.
2. It takes up less RAM (most of the time.)
3. It gave me 6 extra MB of Physical RAM that was previously unusable in ubuntu.

Cons:
1. (-ish) su - instead of sudo.
2. backports.org is needed to get pidgin 2.6.6 and MSN working.
3. backports.org upgrading breaks Rodent theme, so have to install gnome-icon-theme.

Overall, it's a very nice distribution, no wonder Ubuntu based itself off of it.

Got to admit if it wasn't for their attitude re software (look at iceweasle for example and all the dependencies that it links to) I'd be a full time Debian user.  Would give up some cutting edge features from repositories for a more stable/mature build.

---

### Post by Pogeymanz on 2010-03-26
> **caravel said:**
> Not a con, that's how its supposed to be done (despite what some may think).

Could you elaborate? I've never heard this comment before. Are you saying that sudo shouldn't exist or maybe that it's only better for complex multi-user computers?

---

### Post by chris4585 on 2010-03-26
The way sudo works in ubuntu can be copied pretty easily in debian, and any other linux too.

---

### Post by Roasted on 2010-03-26
> **caravel said:**
> Not a con, that's how its supposed to be done (despite what some may think).

The term "supposed to be done" is simply a relative opinion.

I personally prefer using sudo, but there are really no pros/cons to either side - simply a matter of personal preference.

---

### Post by caravel on 2010-03-26
> **Pogeymanz said:**
> Could you elaborate? I've never heard this comment before. Are you saying that sudo shouldn't exist or maybe that it's only better for complex multi-user computers?
The latter - sudo is for giving regular users privileges to carry out certain specific administrative tasks (it's not designed as a subtititute for full root access).  For your every day single user desktop system you simply log in as root.  Believe it or not that's how Debian (and most other Linux distros) are set up.  On a single user desktop, the Ubuntu implimentation of sudo is pointless.

Though if people want to use sudo, they can.  I'm just pointing out that the "Ubuntu way" is not necessarily always the right way.

---

### Post by swoll1980 on 2010-03-26
> **NightwishFan said:**
>  Using Lenny is to be admired though for the dedication to wanting stability. 
.
Lenny is only stable by default. If you go pushing backports into it, or adding repositories to it, it's no longer stable.

---

### Post by Psumi on 2010-03-26
added the contrib repos to it, and now flashplugin-nonfree is installed, and everything works in midori.

switched to an openbox session, removed all of the xfce cruft, using lxpanel, pcmanfm and slim.

Quite an admirable low-end configuration!

idles with midori without flash on at 89 MB of RAM usage.

---

### Post by NightwishFan on 2010-03-26
Excellent, I am glad you like Debian. Please keep us in the loop about what you think.

---

### Post by prodigy_ on 2010-03-26
I tried Lenny recently. Gnome ended up broken right after the first login. No kidding, the system was OK for just less than 5 minutes.

The new low.

---

### Post by caravel on 2010-03-26
> **prodigy_ said:**
> I tried Lenny recently. Gnome ended up broken right after the first login. No kidding, the system was OK for just less than 5 minutes.

The new low.
Funnily enough that hasn't happened to me in the few hundred times I've installed it...

Perhaps the problem is between keyboard and chair?

---

### Post by prodigy_ on 2010-03-26
> **caravel said:**
> Perhaps the problem is between keyboard and chair?
OMG, you've nailed it. Since I used default partitioning and there aren't any other important choices, must be that my mere presence somehow magically breaks Debian installation routine.

/sarcasm off

---

### Post by malspa on 2010-03-26
> **dixiedancer said:**
> Congratulations! It was easier than you expected, wasn't it?

That's how I felt when I finally got around to installing Debian.  I though it was going to be much more difficult, so I avoided it for a long time.

---

### Post by Chronon on 2010-03-26
Debian was the first desktop distribution that I used.  It seems just about as accessible as Ubuntu to me.

---

### Post by seth elohim on 2010-03-26
Wow, shows what a newb i really am. I thought Ubuntu WAS debian, not just based on it!:redface:

---

### Post by bwhite82 on 2010-03-26
> **seth elohim said:**
> Wow, shows what a newb i really am. I thought Ubuntu WAS debian, not just based on it!:redface:

*facepalm*

On another note, you can install sudo via apt (or Synaptic). You need only add yourself to the sudoers file. Read: man sudoers. Debian is the Grand Daddy of a whole lot of distros, it may not come with as much "polish" as some of the spin-offs but I think you'll be pleased with its performance.

---

### Post by MarcusW on 2010-03-27
Sudo exists in debian aswell, it's just not configured by default. (in later releases, choose "do not allow root login" for sudo to be configured automatically)

---

### Post by RandomJoe on 2010-03-27
I just recently tried Debian again.  It's been years since the last time, and back then I never was successful with installing for one reason or another - quite frustrating.  It's as simple as can be now!

I tried it this time around because I bought an OpenRD Client and Sheevaplug and needed an ARM5 distro - which Ubuntu just dropped.  Liked what I saw there so much that I now have it installed on a PPC Mac Mini and an Intel Mac Mini.  All three of those are in "server" type applications, so no X or desktop environments.

---

### Post by oOarthurOo on 2010-04-15
> On a single user desktop, the Ubuntu implimentation of sudo is pointless.

It's not pointless. You may disagree with it, but they have rather clearly stated rationale for anyone who cares to read about it: [The Point]("https://help.ubuntu.com/community/RootSudo")

> sudo is for giving regular users privileges to carry out certain specific administrative tasks (it's not designed as a subtititute for full root access).

Velcro was designed for space flight, but other people have decided to make other uses for it. Like me, you may think it's a horrible idea to put them on adult size shoes, but that's not for us to decide. All we have to decide, is what to do with the sudo that is given us.

> For your every day single user desktop system you simply log in as root. Believe it or not that's how Debian (and most other Linux distros) are set up. 

I am going to assume you don't mean, what you've written here, and that a clarification is required. Because as written, it is far, far worse a statement than using sudo as a root replacement. You never log into an x-session (desktop) with root.

---

### Post by MarcusW on 2010-04-16
> **caravel said:**
> The latter - sudo is for giving regular users privileges to carry out certain specific administrative tasks (it's not designed as a subtititute for full root access).  For your every day single user desktop system you simply log in as root.  Believe it or not that's how Debian (and most other Linux distros) are set up.  On a single user desktop, the Ubuntu implimentation of sudo is pointless.

Though if people want to use sudo, they can.  I'm just pointing out that the "Ubuntu way" is not necessarily always the right way.

Debian is set up the way you set it up, it asks you at install if you want root or sudo and you can configure sudo later even if you don't choose it at install.

Btw, "sudo -s" for "full root access". I have root accounts on both my computers but I never have to use them since "sudo -s" does the samething, except it seems to link ~ to MY home folder, and not /root.

---

### Post by kevCast on 2010-04-16
> **prodigy_ said:**
> OMG, you've nailed it. Since I used default partitioning and there aren't any other important choices, must be that my mere presence somehow magically breaks Debian installation routine.

/sarcasm off

Most likely a hardware issue.

---

### Post by luceerose on 2010-06-08
Regarding Sudo;
When you first install run the installer in advanced mode.
It will ask you if you want to allow login as root. Select no.
Debian will then behave exactly as Ubuntu does with sudo & you can always add a root password after installation if you want Debian's default behavior back.

I'm using Ubuntu Lucid on my first computer, Debian Sid on my 2nd, Ubuntu Maverick on my 3rd & Debian Squeeze on my laptop.
I'm even using some packages from the experimental repositories on Sid. I must have been very lucky with it so far because I haven't broken Sid even once yet.
I love Sid & I'll continue to use it on my 2nd computer. It's just been a breeze with everything ever since install. Even Flash was just a one file install with Synaptic.

---

### Post by Shining Arcanine on 2010-06-09
> **Psumi said:**
> Pros:
1. Debian is much faster.
2. It takes up less RAM (most of the time.)
3. It gave me 6 extra MB of Physical RAM that was previously unusable in ubuntu.

Cons:
1. (-ish) su - instead of sudo.
2. backports.org is needed to get pidgin 2.6.6 and MSN working.
3. backports.org upgrading breaks Rodent theme, so have to install gnome-icon-theme.

Overall, it's a very nice distribution, no wonder Ubuntu based itself off of it.
How much RAM do you have and how much of it is usable under Debian? I ask because I am running Gentoo Linux and I am currently missing a little under 2.5MB of RAM at the moment, which I assume has to do with how I compiled the kernel. Certain options disable certain regions of memory for safety purposes, so I am curious whether or not Debian is using them because if Debian is using them, then that means that the warnings about them in the kernel configuration menu are overblown and I could turn them off to get a little more available RAM.

---

### Post by formaldehyde_spoon on 2010-06-10
> **Shining Arcanine said:**
> How much RAM do you have and how much of it is usable under Debian? I ask because I am running Gentoo Linux and I am currently missing a little under 2.5MB of RAM at the moment, which I assume has to do with how I compiled the kernel. Certain options disable certain regions of memory for safety purposes, so I am curious whether or not Debian is using them because if Debian is using them, then that means that the warnings about them in the kernel configuration menu are overblown and I could turn them off to get a little more available RAM.

Check the burnt beans next to his name: he's been banned.

---

### Post by cariboo on 2010-06-10
@Shining Arcanine

The stock 32-bit Ubuntu kernel now supports up to 64Gb of ram the  Physical Address Extension (PAE) kernel as it's known has been the default for the last 2 releases. The 64-bit kernel supports virtually an unlimited amount of ram.

Previous to Karmic the default 32-bit kernel supported up to 3.5Gb ram with zero problems.

---

