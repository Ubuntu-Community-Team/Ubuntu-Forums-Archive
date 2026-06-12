---
title: "Minimal Distro"
date: 2008-10-23
forum: Other OS Talk
---

### Post by thirdoculus on 2008-10-23
I've been using Linux on and off for about 4 years. Now since I don't play PC games anymore I've decided to use Linux as my default OS. I've been using Ubuntu for about 3 months now and it's alright; it's just runs and feels bloated.

I'm looking for a light, minimal distro. I've already installed and configured Arch, and Arch is fine, but I'm looking for something minimal like it but with less self configuration.

Don't get me wrong, Arch is cool and all, but I would like an easier system to build up towards it in the long run. I'd consider myself a more experienced user, not an Advanced power user, but I do know my way around the system.

Any suggestions?

Thanks.

P.S. By minimal, I don't mean a small distro thats built for older hardware, this computer is practically new.

---

### Post by kerry_s on 2008-10-23
you can do a ubuntu or debian base build up. once you get X and a window manager the rest is a snap.

ubuntu:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

debian stable:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)
lenny beta:
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso)


in debian just uncheck everything at package selection.
in ubuntu it's command line install.

**apt-get install xorg synaptic your-wm**
in debian exit from root type> exit, log in as the user> startx

**sudo apt-get install xorg synaptic your-wm**
in ubuntu just type> startx

open synaptic and build away, add what ever you want to complete you.

there's only 1 way to get exactly what you want and that is to do it yourself.

---

### Post by sethvath on 2008-10-23
If you want a system that is custom suited to you and you alone, arch and gentoo is the way to go. Building a minimal debian system from scratch and adding in modules you need is still not as configurable compared to arch. One file to edit and modify all system fonts etc like in arch? Hard to beat that.

---

### Post by notwen on 2008-10-23
I'd personally recommend Debian of any sort.  It's no where near as light as a base Gentoo/Arch install, but if you want minimum configurations for a fresh install I would say Debian or perhaps trying Xubuntu server and building up from there.  You may also want to consider looking into some of the box/icewm distros that have surfaced in the past year or two.(ie. [boxbuntu]("http://boxbuntu.com/"), [crunchbang]("http://crunchbang.org/"), K.Mandla's [Ubuntu GTK1.2 Remix]("http://ubuntuforums.org/showthread.php?t=933720"))

Good luck w/ the search, I use to hunt for a minimal distro w/ little to no configuration needed, but have always fallen back on Debian Stable.  =]

---edit---
You could always try the latest releases of [dsl]("http://www.damnsmalllinux.org/")/[puppy]("http://www.puppylinux.org/")/[antix]("http://antix.mepis.org/") to see if they meet your needs/expectations as well.

---

### Post by kerry_s on 2008-10-23
> **notwen said:**
> I'd personally recommend Debian of any sort.  It's no where near as light as a base Gentoo/Arch install, but if you want minimum configurations for a fresh install I would say Debian or perhaps trying Xubuntu server and building up from there.  You may also want to consider looking into some of the box/icewm distros that have surfaced in the past year or two.(ie. [boxbuntu]("http://boxbuntu.com/"), [crunchbang]("http://crunchbang.org/"), K.Mandla's [Ubuntu GTK1.2 Remix]("http://ubuntuforums.org/showthread.php?t=933720"))

Good luck w/ the search, I use to hunt for a minimal distro w/ little to no configuration needed, but have always fallen back on Debian Stable.  =]

---edit---
You could always try the latest releases of [dsl]("http://www.damnsmalllinux.org/")/[puppy]("http://www.puppylinux.org/")/[antix]("http://antix.mepis.org/") to see if they meet your needs/expectations as well.


i agree, i tried lenny, but it seemed slower, so what if the stuff in stable is older, it just works. i'm using a custom debian etch, built from the base install up, running on 450mhz 256mb ram and everything opens instantly, there's no wait(except firefox, takes 5sec's).
i installed all lite programs, no bloat.

---

### Post by bttb on 2008-10-23
Hi there,

I think you don't need to bother changing your distro. To keep it simple lets say there are only two kinds of distros: The sources based ones (e.g. Gentoo) and the binaries based ones (e.g. Ubuntu).

**Pros and Cons sources based distros:**
- you can get rid of a lot of stuff, really minimizing the amount of software that gets installed
- they take a lot of time to setup and maintain

**Pros and Cons binaries based distros:**
- every package comes with a fixed list of dependencies you can't remove/packages are built with all or most features enabled to satisfy all users
- they take less time to setup and maintain

One can still minimize the "bloat" of distros like Ubuntu, because a lot of packages that are installed by default can be removed (tracker and compiz for instance to name a few). I'm down to 1035 packages, all-in-all around 2.1 GByte. And lets be honest, space isn't really an issue nowadays. Also Ubuntu doesn't feel slower than any other distro either.

Even if it was a little slower the speed argument would be more than zeroed out taking into account the huge amount of time saved while installing and maintaining.

Bye bye

---

### Post by chucky chuckaluck on 2008-10-23
hey, kerry, what window manager is that in your screenshot? jwm?

---

### Post by CraigPaleo on 2008-10-23
There is [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) . Personally though, I would just try to slim down the existing system. 

__________________
[Raw Meat Diet for Humans]("http://www.rawpaleodiet.com")

---

### Post by Sorivenul on 2008-10-23
I personally second the suggestion of a "ground-up" Debian or Ubuntu install from the netinstall images.  Once you've tried this approach to either, you'll probably never go back to the LiveCD or alternate install CD.  Good luck.

---

### Post by kerry_s on 2008-10-23
> **chucky chuckaluck said:**
> hey, kerry, what window manager is that in your screenshot? jwm?

yeap, i still use jwm, just love it, i can do more things with jwm than i can do with any other window manager.
etch has an older version that doesn't look as good as the 1 in lenny, but it's no big, still works just as good.

the way i setup the desktop launcher through you off huh? :lolflag:

you should have seen it earlier i was swallowing all kinds of dock apps, that menu was wmdrawer, than i decided i really don't want to do icons. now it's just set the same as my right click.(see pic)

i'm keeping it simple, i have xexec on alt+f2 to launch any program i don't list or that aren't already set as run actions in rox.

my jwmrc:

```
<?xml version="1.0"?>

<JWM>

<StartupCommand>

xsetroot -solid black
rm -f ~/.serverauth.*
rm -f ~/.xsession-errors

</StartupCommand>

        <RootMenu onroot="3">
                
                <Restart label="Restart"/>
                <Separator/>
                <Menu label="Logout">
                <Exit label="Exit X" confirm="false"/>
                <Program label="Reboot">sudo shutdown -rf now</Program>
                <Program label="Shutdown">sudo shutdown -h now</Program>
                </Menu>
                <Separator/>
                <Program label="Suspend">sudo s2ram -f</Program>
                <Separator/>
                <Program label="Hibernate">sudo s2disk</Program>

        </RootMenu>

        <Tray  valign="center" halign="left" layer="0" layout="vertical">

                <TrayButton icon="menu.png"/>
                <TrayButton label="Synaptic">exec: sudo synaptic</TrayButton>
                <TrayButton label="Terminal">exec: xterm -T "Terminal" -fn 9x15</TrayButton>
                <TrayButton label="File Manager">exec: rox</TrayButton>
                <TrayButton label="Web Browser">exec: xmessage -fn 12x24 -center -timeout 5 "launching web browser" | iceweasel</TrayButton>

        </Tray>

        <Tray  valign="top" halign="center" height="64" autohide="true">

                <Pager/>

        </Tray>

        <Tray  x="0" y="-1" height="32">

                <TrayButton icon="desktop.png">showdesktop</TrayButton>
                <TaskList/>
                <Dock/>
                <Clock format="%l:%M  ">xclock -g +790+665 -digital -strftime "%A %b %d,%Y"</Clock>
                <TrayButton label="-">exec: amixer set PCM 3-</TrayButton>
                <TrayButton label="+">exec: amixer set PCM 3+</TrayButton>

        </Tray>

        <BorderStyle>
                <Font>helvetica</Font>
                <Width>3</Width>
                <Height>20</Height>
                <Foreground>black</Foreground>
                <Background>gray90</Background>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#4A5966</ActiveBackground>
        </BorderStyle>

        <TaskListStyle>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#4A5966</ActiveBackground>
        </TaskListStyle>

        <TrayStyle>
                <Font>helvetica</Font>
                <Background>gray90</Background>
                <Foreground>black</Foreground>
        </TrayStyle>

        <PagerStyle>
                <Outline>black</Outline>
                <Foreground>gray90</Foreground>
                <Background>#888888</Background>
                <ActiveForeground>#8899AA</ActiveForeground>
                <ActiveBackground>#3A4956</ActiveBackground>
        </PagerStyle>

        <PopupStyle enabled="false"></PopupStyle>

        <MenuStyle>
                <Font>helvetica</Font>
                <Foreground>black</Foreground>
                <Background>gray90</Background>
                <ActiveForeground>white</ActiveForeground>
                <ActiveBackground>#3A4956</ActiveBackground>
        </MenuStyle>

        <Icons>
                <IconPath>$HOME/.icons</IconPath>
        </Icons>

        <Desktops count="4"/>
        <DoubleClickSpeed>400</DoubleClickSpeed>
        <DoubleClickDelta>2</DoubleClickDelta>
        <FocusModel>click</FocusModel>
        <SnapMode distance="2">border</SnapMode>
        <MoveMode>outline</MoveMode>
        <ResizeMode>outline</ResizeMode>

        <Key key="Up">up</Key>
        <Key key="Down">down</Key>
        <Key key="Right">right</Key>
        <Key key="Left">left</Key>
        <Key key="Return">select</Key>
        <Key key="Escape">escape</Key>

        <Key mask="A" key="Tab">next</Key>
        <Key mask="A" key="F4">close</Key>
        <Key mask="A" key="#">desktop#</Key>
        <Key mask="A" key="F1">root</Key>
        <Key mask="A" key="F2">exec: xexec</Key>
        <Key mask="" key="Print">exec: scrot %T.png;xmessage -fn 12x24 -center -timeout 2 "Screenshot done"</Key>
        <Key mask="A" key="Print">exec: xmessage -fn 12x24 -center "click or click drag to select";scrot -sb %T.png</Key>
        <Key mask="CA" key="Print">exec: xterm -fn 10x20 -g 40x1+0+0 -e scrot -cd 5 %T.png;xmessage -fn 12x24 -center -timeout 2 "Screenshot done"</Key>
</JWM>


```

---

### Post by cardinals_fan on 2008-10-23
There's SliTaz...

---

### Post by Hallvor on 2008-10-24
> **thirdoculus said:**
> I've been using Linux on and off for about 4 years. Now since I don't play PC games anymore I've decided to use Linux as my default OS. I've been using Ubuntu for about 3 months now and it's alright; it's just runs and feels bloated.

I'm looking for a light, minimal distro. I've already installed and configured Arch, and Arch is fine, but I'm looking for something minimal like it but with less self configuration.

Don't get me wrong, Arch is cool and all, but I would like an easier system to build up towards it in the long run. I'd consider myself a more experienced user, not an Advanced power user, but I do know my way around the system.

Any suggestions?

Thanks.

P.S. By minimal, I don't mean a small distro thats built for older hardware, this computer is practically new.


You may want to look at TinyMe. It is very fast, looks very nice and is easy to configure. You won`t feel much bloat there, I can tell you.

---

### Post by EV500B on 2008-10-24
Or if you're searching for very minimal distros. 
Go for SliTaz.:smile:

Even smaller than DamnSmallLinux(50Mb)

SliTaz(27Mb)
\\:D/

---

### Post by chris4585 on 2008-10-25
I suggest my [Plusone (+1)]("http://boxbuntu.com/") Light when it comes out of beta

The ISO is 317mbs as of now.

---

### Post by erykroom on 2008-10-25
You can slim down your old distro, but if you want all to be light and fast and already configuered I suggest Linux mint 5 fluxbox edition. Its really fast and does everything I want.
[http://www.linuxmint.com/blog/?p=404](http://www.linuxmint.com/blog/?p=404)

---

### Post by snowpine on 2008-10-25
Another vote for SliTaz... it is an inspiring distro!

---

### Post by mikjp on 2008-10-25
Slackware.

---

### Post by benerivo on 2008-10-25
I'd go with debian as it is easier than arch, although have you considered a minimal install of ubuntu from the alternate cd? Either of these is an easy way to use the power of your pc without having unnecessary stuff installed or loaded in the background.

---

### Post by loell on 2008-10-25
also PUD linux.

---

### Post by Shazaam on 2008-10-25
About as minimal as you can get, fits on a floppy....
[http://www.menuetos.net/index.htm](http://www.menuetos.net/index.htm)

---

### Post by em4r1z on 2008-10-28
Since you're already configuring Arch, I'd stick with it. What about a base installation of Debian Testing or Sidux? I install xorg, gnome/kde-core, g/kdm and firefox, and start building up a system from there. I only suggested rolling relase distributions because once you personalize them you won't touch the configuration files in years.
Like you, I like minimal installations because I like to have control and not because the lack of system resources.

---

### Post by SomeGuyDude on 2008-10-28
You're not going to get a minimal distro that doesn't require self-configuration, because the two ideas are contradictory.

The way a minimal distro works is that it installs only what is needed/desired, but there's no way for the installation CD to inherently "know" what the minimal pieces it should install are. It's like asking for a suit that fits perfectly without having to measure yourself, you know?

---

### Post by basenvironment on 2008-10-29
> **thirdoculus said:**
> ... looking for something minimal like it but with less self configuration. ...

That is the great thing about debian. It is minimal but the basics are handled for you but you are always free to adjust the defaults should you not like them. Heck, you can even set debconf to different levels depending on if you want more questions asked or less questions asked about configuration. 

[http://wiki.debian.org/debconf](http://wiki.debian.org/debconf)
[http://www.debianadmin.com/debconf-debian-configuration-management-system.html](http://www.debianadmin.com/debconf-debian-configuration-management-system.html)


.

---

### Post by thirdoculus on 2008-10-30
> **basenvironment said:**
> That is the great thing about debian. It is minimal but the basics are handled for you but you are always free to adjust the defaults should you not like them. Heck, you can even set debconf to different levels depending on if you want more questions asked or less questions asked about configuration. 

[http://wiki.debian.org/debconf](http://wiki.debian.org/debconf)
[http://www.debianadmin.com/debconf-debian-configuration-management-system.html](http://www.debianadmin.com/debconf-debian-configuration-management-system.html)


.

Holy crap, I seriously forgot about this thread!:lolflag: But I sucked it up and just stayed with Arch.

---

### Post by SomeGuyDude on 2008-10-31
> **thirdoculus said:**
> Holy crap, I seriously forgot about this thread!:lolflag: But I sucked it up and just stayed with Arch.

Didn't feel like changing, or did you decide Arch was just the better option?

---

### Post by sengines on 2008-10-31
> **kerry_s said:**
> you can do a ubuntu or debian base build up. once you get X and a window manager the rest is a snap.

ubuntu:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)


Ok so where is the link for Ubuntu 8.10 "Intrepid Ibex" Minimal CD AMD64?

not beta

---

