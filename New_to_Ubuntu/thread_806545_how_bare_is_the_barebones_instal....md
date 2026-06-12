---
title: "how bare is the barebones instal..."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by iamclueless on 2008-05-25
Recently got a hold of a couple of old laptops.  the easy thing would be to install a couple of distros built for old machines... AntiX or Puppy or whatever.

Xubuntu will be too bloated for these... so i am think a server install and building up is the way to go. 

the questio i have is how bare is it?  i dont have a problem with adding apps and services via CLI.  the problem i will have will be with drivers.  will the barebones come with the hardware support? or do i have to get specific drivers depending on the hardware i have or hardware im likely to use later

thanks

---

### Post by Inxsible on 2008-05-25
A server install will also be too bloated for it. What you want to do is install a CLI (its an option on the server CD) on it and then install whatever apps you want.

or on the other hand use a minimal install

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by aysiu on 2008-05-25
Native drivers are all in the Linux kernel, so hardware detection should be fine no matter how minimal the install it.

---

### Post by kellemes on 2008-05-25
> **iamclueless said:**
> Recently got a hold of a couple of old laptops.  the easy thing would be to install a couple of distros built for old machines... AntiX or Puppy or whatever.


I don't have experience with AntiX or Puppy but you'll be surprised to see a dist like [DSL]("http://www.damnsmalllinux.org/") (for example) providing a comfortable graphical environment demanding little resources.

---

### Post by Inxsible on 2008-05-25
Fluxbuntu is another choice you could go for, if you plan to not go thru the hassle of installing every app yourself.

---

### Post by kerry_s on 2008-05-25
> **iamclueless said:**
> Recently got a hold of a couple of old laptops.  the easy thing would be to install a couple of distros built for old machines... AntiX or Puppy or whatever.

Xubuntu will be too bloated for these... so i am think a server install and building up is the way to go. 

the questio i have is how bare is it?  i dont have a problem with adding apps and services via CLI.  the problem i will have will be with drivers.  will the barebones come with the hardware support? or do i have to get specific drivers depending on the hardware i have or hardware im likely to use later

thanks

what are the specs? you don't tell us the hardware, we can't tell you where there might be problems. alot of us run older hardware and just might be able to tell you if there is any problems we encountered.

i run a old vaio pcg-f430 450mhz 256mb ram(maxed) 2.5mb neomagic vid.
i've found using the 2.6.18 kernel works best on it, i use a debian base and build up from there, starting from etch and upgrading to lenny, cause lenny uses the 2.6.24 kernel and alot of the stuff is automated, for example xorg.conf will be blank, cause the settings are done automatic by the new xorg. i use jwm for my window manager, cause it just works. i don't bother with a gui file manager or editor, cause most of my time is spent in the web browser. i've got mine so fine tunned i barely wake the cpu up for common tasks, 90% of the time it's throttled less than 100mhz.
i have all the common things needed for light office, music, pics, etc...

---

### Post by _sAm_ on 2008-05-25
I think you want to take a look on this guide:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by iamclueless on 2008-05-25
one is a dell inspiron 4000, p3 800 with 384 of ram.  that runs mepis 7.0 but can be sluggish at times, kde hehe.  all hardware is detected except the wifi card occassionally causes a kernel panic at boot up.

the other is also a p3... sorry i dont have it in front of me... but it will be similar to the one above with a bit less ram.

id like to actually build from a command line instal.  the ultimate goal is to have these machines being used by my students and id like it to be as fast as possible.  slackware would be the obvious choice, but i need good documentation if i have to maintain several classroom computers.

thanks for letting me know the hardware detection remains intact.

i guess at this point id be looking at a bare install with xfce on it.  is there a way to get the xubuntu desktop without the apps or the libraries??? or am i looking at xfce and just tweaking it to look like xubuntu.

thanks again

---

### Post by shifty_powers on 2008-05-25
that first one should run fluxbuntu alright... and fluxbuntu is quite a nice version of ubuntu imo...

---

### Post by Inxsible on 2008-05-25
If you are going to have your students run it, you may be better off installing a full version rather than building one up. I say this only so that you may have less headaches maintaining them.

I run Xubuntu/Fluxbuntu dual boot on a P3-1.1GHz, 256MB RAM, 30GB HDD. Although when I tried starting compiz in Xubuntu, everything slowed down to a crawl. 

Zenwalk would work great in such a machine. And so would DSL or puppy or Fluxbuntu. Yet another OS would be OsOz - based on Enlightenment DR17 as the Window Manager. Yet another is Icebuntu- based on IceWM, although that is still in development. also you will NOT like the look of IceWM unless you install the ThinBlack, Icebuntu and Ice OSX themes. I know I hated every theme that IceWM had by default!!!!

These days almost every light weight DM/WM have their own OS, so it makes it easier.  But at the same time, I also like the thrill of minimal install. The only advantage with minimal is that you can choose which programs you want as opposed to the ones that any standard distro would give you by default. For eg. you can use Thunar in minimal + Fluxbox instead of Rox-Filer (not a fan of it) that you get in Fluxbuntu. 

What are you going to use the machines for? That sometimes is the most important aspect while choosing a distro.

---

### Post by kerry_s on 2008-05-25
> **iamclueless said:**
> one is a dell inspiron 4000, p3 800 with 384 of ram.  that runs mepis 7.0 but can be sluggish at times, kde hehe.  all hardware is detected except the wifi card occassionally causes a kernel panic at boot up.

the other is also a p3... sorry i dont have it in front of me... but it will be similar to the one above with a bit less ram.

id like to actually build from a command line instal.  the ultimate goal is to have these machines being used by my students and id like it to be as fast as possible.  slackware would be the obvious choice, but i need good documentation if i have to maintain several classroom computers.

thanks for letting me know the hardware detection remains intact.

i guess at this point id be looking at a bare install with xfce on it.  is there a way to get the xubuntu desktop without the apps or the libraries??? or am i looking at xfce and just tweaking it to look like xubuntu.

thanks again


debian does xfce4 better->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

if your going barebones build up, the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

for barebones:
when it gets to package selection uncheck everything.
log in as root
apt-get install xorg gdm xfce4
reboot(ctrl+alt+delete)
log in as your user

that's just enough to get you into gui, then you can continue building from there.

---

### Post by Inxsible on 2008-05-25
> **kerry_s said:**
> debian does xfce4 better->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

if your going barebones build up, the net installer->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

for barebones:
when it gets to package selection uncheck everything.
log in as root
apt-get install xorg gdm xfce4
reboot(ctrl+alt+delete)
log in as your user

that's just enough to get you into gui, then you can continue building from there.I would not install gdm at all. Infact I wouldn't install any *dm. Just login at the CLI and then issue```
startx
``` The only purpose of gdm is for you to login. Saves a lot of space and memory.

Also kerry, could you point me to a link which lists out the advantages of using Debian Xfce as opposed to Xubuntu. I am running Xubuntu on an old laptop and I think its a bit slow - although I do have xfwm4 running since I have installed AWN. My specs are P3-1.13GHz, 256MB RAM 30GB HDD and nVidia 32 mb shared graphics

---

### Post by kerry_s on 2008-05-25
i included gdm because he said it was for his students, he might have multiple users and want to make it simple and friendly.

> Also kerry, could you point me to a link which lists out the advantages of using Debian Xfce as opposed to Xubuntu. 

it's just better, xubuntu is one of the worse xfce4 versions i have ever used. debian is just the standard xfce4, no tweaking, nothing messed up/messed with, you get it like it would be if you compiled it yourself. it's just one of those things you got to try.

with only 256mb ram, why not just go to a wm, ditch those de's altogether.
if you use debian you can use rungetty to auto log in and startx in bash_profile, so from power-on/reboot it will load straight to the desktop. no need to login and type startx.

---

### Post by Inxsible on 2008-05-25
> **kerry_s said:**
> it's just better, xubuntu is one of the worse xfce4 versions i have ever used. debian is just the standard xfce4, no tweaking, nothing messed up/messed with, you get it like it would be if you compiled it yourself. it's just one of those things you got to try.

with only 256mb ram, why not just go to a wm, ditch those de's altogether.
if you use debian you can use rungetty to auto log in and startx in bash_profile, so from power-on/reboot it will load straight to the desktop. no need to login and type startx.I guess i will give it a go.

I currently dual boot Xubuntu and Fluxbuntu. Can't say I am a fan of the default Rox Filer and Kazehakase (since I use quite a few plugins on Firefox). I am planning to get rid of Xubuntu - if Debian xfce is better as you say. I still want to be able to run xfwm4 - just so I can have my AWN ;-)

Also I am going to install a minimal with Enlightenment on the other partition. At the moment I am currently trying out IceWM & PekWM installed in the Xubuntu installation, Fluxbox(in fluxbuntu) to see what I like.

The default for Fluxbox works for me - except i will probably change some apps that I like to use. IceWM is good only in 3 themes (ThinBlack, IceOSX and Icebuntu) The default themes are bullcrap.

The only problem with going only WM is that i cannot have any compositor (AWN doesnt work with xcompmgr at least for me) for AWN. I also tried using wbar (not a dock - just a launcher) but still. I couldn't even get it to start. Although, in all honesty, I just tried it a couple of times and then uninstalled it.

---

### Post by iamclueless on 2008-05-25
ok thanks for the responses so far.  

here is the goal. i want students to be able to use:
    Firefox, OpenOffice, Scribus, a media player of sort, some basic accessories (text editor, calculator, calendar, clock, etc.) a basic photo editor.

i was thinking Xfce due to the more user friendly environment.  Will have to day pass on Fluxbox, im comfortable with it... but cant have moaning students about how rubbish it looks. I guess i could add the icons but thats too much work.  now IceWM i could definitely go with.

i know there are better suited distros for what i want... but the goal is to maintain 10 or so laptops.  Id like as much good documentation and forum info i can read online - and Ubuntu is great for that.

if dropping gdm or any login manager then id be happy to drop it.

---

### Post by Inxsible on 2008-05-25
The default look of fluxbox is much better than IceWM, IMO.

But see what you are comfortable with. Enlightenment is also lightweight and said to have a lot more eye candy than the other lighter WMs. So may wanna try that out too.


and yes, Ubuntu does have much better support from this community than any other distro. But having said that, this forum also has an Other OS Talk section where you can get help for other distros - although the help might not be as fast as for the ubuntu based distros

---

### Post by iamclueless on 2008-05-25
yeah i like this forum for that.  when i started i was just asking questions.. then i realised whatever it is i needed i could actually find on the forum or the docomentation.

apologies for starting this thread though... hehe. im restricted to  slow internet cafe machines. and dont have the luxury to filter through the forum.

actually i think ive sorted out a potentially easier plan
is there a list of all the apps included in the various buntus (but not the libararies)i can look at and change. that way i can simply do a command line install and pick the stuff i want.

---

### Post by kerry_s on 2008-05-25
given the way you want to use the machines you might want to look into ltsp->
[http://www.ltsp.org/](http://www.ltsp.org/)

it would give you far better control, you only have to deal with 1 install, etc...

---

### Post by iamclueless on 2008-05-26
thanks for that kerry

yup i would definitely consider this using edubuntu.  only at this point i dont have the hardware for it.  no new pc to use as server, no extra wires for the setup.  I read the wireless thin clients and thats definitely worth a look into... need to beg the school for money i guess.  I have more than enough information to put together a proposal i think.  thanks again

---

