---
title: "What is the most stable debian based distro?"
date: 2009-12-01
forum: Recurring Discussions
---

### Post by emigrant on 2009-12-01
hi all, what is the most stable latest debian based distro? of course it should be userfriendly and beautiful. thank you very much.

---

### Post by earthpigg on 2009-12-01
debian stable?

---

### Post by Ozor Mox on 2009-12-01
> **earthpigg said:**
> debian stable?

Lol.

I'd agree, Debian itself. Sidux was pretty stable as well from what I tried of it. Also, what about Ubuntu LTS? 8.04 has got to be pretty rock solid by now.

---

### Post by Psumi on 2009-12-01
> **earthpigg said:**
> debian stable?

[img]http://i45.tinypic.com/33e76yx.png[/img]

> **Ozor Mox said:**
> what about Ubuntu LTS? 8.04 has got to be pretty rock solid by now.

PIXMA MP190 will not scan, need xsane git 0.999.

nvidia GTS 250 is not detected through jockey,

 various other issues.

---

### Post by Skripka on 2009-12-01
> **Psumi said:**
> 
PIXMA MP190 will not scan, need xsane git 0.999.

nvidia GTS 250 is not detected through jockey,

 various other issues.

Yea...just because something is old-does not mean it is "stable".  It just means that it is old.

---

### Post by Ozor Mox on 2009-12-01
> **Psumi said:**
> PIXMA MP190 will not scan, need xsane git 0.999.

nvidia GTS 250 is not detected through jockey,

 various other issues.

I didn't say it was perfect. Maybe if I called Ubuntu 8.04 LTS rock solid, I should call Debian Stable planet solid or something.

---

### Post by szymon_g on 2009-12-01
1. debian stable
2. if ad 1. doesn't satisfy you- try CentOS or SLED (this one isn't free).

@Skripka
right; but testing & patching software takes time (and a lot of effort)- so something stable will always be out-of-dated

---

### Post by Alex Libman on 2009-12-01
Lenny is pretty stable as far as Linuxen go, but in a few months I hope it'll be Debian Squeeze GNU/**kFreeBSD**.  :D

---

### Post by gradinaruvasile on 2009-12-01
Stable = older apps/kernel = less features/support for newer apps/hardware(wireless/sound etc). 

And ususlly this means you will have to backport/compile newer applications. Not that nice when you have to recompile tons of dependencies (because they are old too) that may break the existing ones.

For user friendliness/reasonable stability/reasonably software/hardware support i would suggest the previous (in this case 9.04) Ubuntu version. Usually it has its bugs squashed or at least known.
For stability and use friendliness i would say 8.04 but in this case you have outdated software.

Stability and not userfriendly : Debian stable.

---

### Post by Hallvor on 2009-12-01
> **emigrant said:**
> hi all, what is the most stable latest debian based distro? of course it should be userfriendly and beautiful. thank you very much.

Except Debian stable, there is always Mepis - built on a Debian stable core.

---

### Post by Skripka on 2009-12-01
> **szymon_g said:**
> 1. debian stable
2. if ad 1. doesn't satisfy you- try CentOS or SLED (this one isn't free).

@Skripka
right; but testing & patching software takes time (and a lot of effort)- so something stable will always be out-of-dated

Patches are a sub-sub-ideal solution to a problem.  Better to have fixed code, that works right in the 1st place from the guys who wrote it.  When people start patching-utter chaos ensues, and there is no telling what can happen.

It is not unreasonable to assume that one patch to fix one problem creates as any problems as it "solves" if not more elsewhere.  As I said simply because something is old does not mean it is "stable".

-Qt4.5 is light-years better than Qt4.3 that Lenny is still using.

-The implementation of Pulse Audio that Ubuntu knowingly implemented in 9.10 was borked due to patching....even after extensive ranting by the author of PA-warning *buntu about it, and testing was done.

-On Arch, a patch issued by Fedora to Xorg, was causing crashes on Nvidia and Intel adaptors a few weeks back, that patch was written by the Fedora folks to fix issues for Intel users....it didn't even accomplish that.

Odds are software will work best when run, as close to the manner in which it was designed to run.  Patches should be the last refuge to ever run to.

---

### Post by MaxIBoy on 2009-12-01
Debian Stable is the most stable Debian-based distro I know of.

---

### Post by armageddon08 on 2009-12-01
Uh...um....Debian Stable??
[EDIT]: OOps didn't read the thread the first time. Now that I read it, many people have given the same answer. :)

---

### Post by emigrant on 2009-12-01
ok im gonna give a shot to debian stable. that means lenny? and which one i should try gnome or kde?

---

### Post by Hallvor on 2009-12-01
> **emigrant said:**
> ok im gonna give a shot to debian stable. that means lenny? and which one i should try gnome or kde?

Yes, that means Lenny. What is best depends on your preferences. They all work very well; Gnome, KDE, XFCE or LXDE... Keep in mind that Lenny has KDE 3.5, so you won`t have a bleeding edge KDE 4 desktop if you want to try it out.

---

### Post by Zoot7 on 2009-12-01
+1 for Debian Stable.

The only problem really is that it ages rapidly, if you want the most up to date software you'll have to use either Testing or Unstable sadly.

---

### Post by emigrant on 2009-12-01
> **Zoot7 said:**
> +1 for Debian Stable.

The only problem really is that it ages rapidly, if you want the most up to date software you'll have to use either Testing or Unstable sadly.
that means its like ubuntu hardy?

---

### Post by Skripka on 2009-12-01
> **emigrant said:**
> that means its like ubuntu hardy?

Naw Lenny is more up-to-date than Hardy.  Hardy was a snapshot of Debian Lenny in 4/2008.  Lenny was released quite a bit afterwards.

---

### Post by XubuRoxMySox on 2009-12-01
**+1 to Mepis** for rock-stable and beautiful (KDE), well supported and has a community forum to rival Ubuntu Forums.

-Robin

---

### Post by szymon_g on 2009-12-01
> **Zoot7 said:**
> +1 for Debian Stable.

The only problem really is that it ages rapidly, if you want the most up to date software you'll have to use either Testing or Unstable sadly.

why not to use apt-pinning? thanx that, you have got a stable base + quite new apps (of course, it isn't as stable as 'pure' debian stable)

---

### Post by Zoot7 on 2009-12-01
> **emigrant said:**
> that means its like ubuntu hardy?
More or less, there are some areas where Debian Lenny is more up to date, and others where it's not.

> **szymon_g said:**
> why not to use apt-pinning? thanx that, you have got a stable base + quite new apps (of course, it isn't as stable as 'pure' debian stable)
The main problem with the "Cutting Edge" apps is running into Dependency issues. For instance you can't install greater than version 0.99 of Vlc on Hardy.

---

### Post by Exodist on 2009-12-01
> **emigrant said:**
> hi all, what is the most stable latest debian based distro? Of course it should be userfriendly and beautiful. Thank you very much.
 
debian stable

---

### Post by szymon_g on 2009-12-01
> **Zoot7 said:**
> The main problem with the "Cutting Edge" apps is running into Dependency issues. For instance you can't install greater than version 0.99 of Vlc on Hardy.

hm... but installing apps from other repos (like: from testing under stable) by aptitude -t testing install app_name (... or something like that, i don't remember ;P) will install all dependancies of that app (of course, only if they are met,- otherwise it would bring problems even when running on 'native' version). sure, from the other hand, that installing some application will bring so many dependencies, that they will replace half of running system

---

### Post by Psumi on 2009-12-01
> **szymon_g said:**
> hm... but installing apps from other repos (like: from testing under stable) by aptitude -t testing install app_name (... or something like that, i don't remember ;P) will install all dependancies of that app (of course, only if they are met,- otherwise it would bring problems even when running on 'native' version). sure, from the other hand, that installing some application will bring so many dependencies, that they will replace half of running system

Newer Depends need to be provided by repo as well.

Hence why midori ppa requires webkit ppa.

---

### Post by Zoot7 on 2009-12-01
> **szymon_g said:**
> hm... but installing apps from other repos (like: from testing under stable) by aptitude -t testing install app_name (... or something like that, i don't remember ;P) will install all dependancies of that app (of course, only if they are met,- otherwise it would bring problems even when running on 'native' version). sure, from the other hand, that installing some application will bring so many dependencies, that they will replace half of running system

> **Psumi said:**
> Newer Depends need to be provided by repo as well.
Yeah that's exactly the problem.

---

### Post by emigrant on 2009-12-02
after installing Debian lenny, 
can i still stay here in this forum or should i move to another forum since the problems are different in both the distros?

---

### Post by ZankerH on 2009-12-02
> What is the most stable debian based distro?

protip: You used both of the words its name contains in the title thread.


SPOILER:
[COLOR="White"]Stable branch of Debian GNU/Linux, aka "Debian stable".[/COLOR]

---

### Post by emigrant on 2009-12-02
> **ZankerH said:**
> protip: You used both of the words its name contains in the title thread.


SPOILER:
[COLOR=White]Stable branch of Debian GNU/Linux, aka "Debian stable".[/COLOR]
:popcorn:

---

### Post by quinnten83 on 2009-12-02
> **emigrant said:**
> after installing Debian lenny, 
can i still stay here in this forum or should i move to another forum since the problems are different in both the distros?

Installing anything other than Ubuntu = immediate bannishment from the forums, how dare you taint our forums with thoughts and OS's different than our own?

Nah, just kidding, people pretty much don't care around here. And most terminal commands are the same anyhow :D

---

### Post by emigrant on 2009-12-02
> **quinnten83 said:**
> Installing anything other than Ubuntu = immediate bannishment from the forums, how dare you taint our forums with thoughts and OS's different than our own?

Nah, just kidding, people pretty much don't care around here. And most terminal commands are the same anyhow :D

thanks :popcorn:
if that is not the case i would have to abandon the idea of installing lenny. i checked the debian user forum and the most users ever online is 137 :(
i doubt, being still not registerd, i ever get a post replied there.

---

### Post by Exodist on 2009-12-02
> **emigrant said:**
> after installing Debian lenny, 
can i still stay here in this forum or should i move to another forum since the problems are different in both the distros?
 
LOL you can stay.. I use Lenny also.. :D

---

### Post by emigrant on 2009-12-02
is the installation process as easy as ubuntu?
or very hard like red hat?

---

### Post by Hallvor on 2009-12-02
> **emigrant said:**
> is the installation process as easy as ubuntu?
or very hard like red hat?

[http://mikeoverip.wordpress.com/2009/03/11/debian-5-lenny-step-by-step-installation-with-screenshots/](http://mikeoverip.wordpress.com/2009/03/11/debian-5-lenny-step-by-step-installation-with-screenshots/)

---

### Post by emigrant on 2009-12-02
> **Hallvor said:**
> [http://mikeoverip.wordpress.com/2009/03/11/debian-5-lenny-step-by-step-installation-with-screenshots/](http://mikeoverip.wordpress.com/2009/03/11/debian-5-lenny-step-by-step-installation-with-screenshots/)thank you
im planning to install from  DVD and hope the procedure is the same?

---

### Post by Psumi on 2009-12-02
> **emigrant said:**
> thank you
im planning to install from  DVD and hope the procedure is the same?

Unlike Ubuntu though, you must manually add yourself as a sudoer.

---

### Post by cascade9 on 2009-12-02
Yes, the DVD install process is the same. 

The only major difference between the 'small' CD installer, the normal CD installer and the DVD installer for debian is the amount of software on the disc. Small just have the very basics, everything else is downloaded. CD has more software, and will probably do most/all of your install with no downloading. The DVD holds a lot more info, and will probably not need to download anything from the internet for most systems. If you get _all_ the DVD images (and select the right option) you can run debain totally offline. Thats 5 DVDs, so its not for everyone.You will possibly still need the net for some software thats not in the debian repos though.

> **Psumi said:**
> Unlike Ubuntu though, you must manually add yourself as a sudoer.

I actually see this as a strength for debian. Rather than have the same login/sudo password, having a login password and su password makes more sense to me. (yes, I know you can change that and have a dfferent sudo password to login password with ubuntu)

---

### Post by Hallvor on 2009-12-02
> **emigrant said:**
> thank you
im planning to install from  DVD and hope the procedure is the same?

There is no reason to install from a DVD if you have access to high speed internet. Just pick CD1 with the desktop environment of yout choice, or even the netinstall cd.

[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)

---

### Post by Hallvor on 2009-12-02
> **Psumi said:**
> Unlike Ubuntu though, you must manually add yourself as a sudoer.

You don`t need sudo. Some people prefer it, but you don`t need it.

---

### Post by Psumi on 2009-12-02
> **Hallvor said:**
> You don`t need sudo. Some people prefer it, but you don`t need it.

What do you use instead? I need sudo a lot on Ubuntu.

---

### Post by cascade9 on 2009-12-02
I just use su, run what I have to, exit su. Easy.

---

### Post by Hallvor on 2009-12-02
> **Psumi said:**
> What do you use instead? I need sudo a lot on Ubuntu.

```
su
```

Then enter root password and do whatever you want.

So instead of ```
sudo gedit /etc/apt/sources.list
``` you  type ```
su
``` enter root password and then ```
gedit /etc/apt/sources.list
```

---

### Post by Psumi on 2009-12-02
Kind of like

sudo -i

---

### Post by RiceMonster on 2009-12-02
> **Hallvor said:**
> ```
su
```

Then enter root password and do whatever you want.

*snip*

to run one command, you can also do su -c 'command'. As for graphical applications, it's better to use gksu or gksudo (for kde there's kdesu and kdesudo as well).

> **Psumi said:**
> Kind of like

sudo -i

Sort of. su means switch user, and it defaults to root, so when you type su, you're actually logging in as root. Not the case with sudo.

---

### Post by emigrant on 2009-12-02
my internet is dead slow and what im gonna do is to download the  DVDs from elsewhere. and with seperate root account its no problem iv done this in fedora.

---

### Post by Chame_Wizard on 2009-12-02
Debian self.:lolflag:

---

### Post by snowpine on 2009-12-03
I am surprised nobody has mentioned Debian OldStable (currently Etch)--surely it is more stable than Lenny?

---

### Post by Diluted on 2009-12-03
Apparently Etch support will be discontinued in Feburary, so it's better to start with Lenny for less hassle in the future.

---

### Post by cascade9 on 2009-12-03
Not as far as I know. 

The debian devs hold back until they think its stable. No dates set in stone, so if lenny wasn't stable it wouldn't have been released.

---

### Post by bodhi.zazen on 2009-12-03
Debian or Ubuntu 8.04

---

### Post by chris200x9 on 2009-12-03
freeBSD?

---

