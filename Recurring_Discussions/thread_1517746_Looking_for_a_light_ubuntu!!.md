---
title: "Looking for a light ubuntu!!"
date: 2010-06-25
forum: Recurring Discussions
---

### Post by t1nm@n on 2010-06-25
Hello guys... i have been tampering with #!linux adn other light weight distros... but i'm trying to setup a light environment where i can work. So i picked up fluxbox and started messin' with it. it's very hard on the configuration part. but out of all the DE's i tried i'm most happy with fluxbox. but i'm having trouble with themes and other stuff..please tell me what i should do to get a functional light weight lucid....

---

### Post by warfacegod on 2010-06-25
You could try LXDE. Use Synaptic to install it into an existing 'buntu then change the session before you login.

SliTaz is very fast and lightweight but it's not a 'buntu.

You could build your self a minimal install of Lucid.

---

### Post by bodhi.zazen on 2010-06-25
Moved to Recurring discussions.

You can try crunchbang or Lubuntu.

Alternates also include installing with the minimal CD and building up. Add a minimal gnome, kde, or xfce (not the desktops, is no kubuntu-desktop).

Search , there are tons of tutorials on how to do this.

fluxbox takes a little time to learn, but the config files are all text files so it is not *too* bad.

Openbox is similar to Fluxbox, some fine it easier to learn then Fluxbox.

You can also try Zenix, Fluxbox + XFCE + a few security apps.

[http://zenix-os.net/index.php?nav=features](http://zenix-os.net/index.php?nav=features)

---

### Post by t1nm@n on 2010-06-25
hey i tried that dude ...fluxbox scores better with my pc... i also tried lubuntu and slitaz.
i also tried antix and honestly it was rocksolid...that would be the functionality i would be looking for. but in an ubuntu system is what i'm looking for.
and hey thanks for your reply.

i want to use fluxbox as a functional desktop as in antix which uses i think fluxbox+openbox

---

### Post by kaldor on 2010-06-25
Sounds like Wolvix or Wolvix cub is just for you; XFCE, openbox, LXDE, fluxbox. 

Check the link in my sig.

---

### Post by t1nm@n on 2010-06-25
ah!! dude thats based on slackware.... i just started with linux.

anyway nice suggestion heard goodstuff about suse and wolvix being light on the needed time.. So i'm changing my question ; if you were to need a lightweight desktop with full functionality which all stuff would you choose... heres my side view

filemanager => PCmanFM (the greatest i've seen), also thinking about gentoo fm
DE => fluxbox

what is there for more completeness ?????

---

### Post by philinux on 2010-06-25
Peppermint

[http://peppermintos.com/](http://peppermintos.com/)

---

### Post by warfacegod on 2010-06-25
This might be of some use: [http://ubuntuforums.org/showthread.php?t=1479900](http://ubuntuforums.org/showthread.php?t=1479900)

---

### Post by t1nm@n on 2010-06-25
@philinux i checked out that tooo it seems tools like image editor need net connection...personally i dont get that concept... of course i may be wrong... if you guys have used lubuntu pls tell me how i can get my internet ...ie chrome takes ages to even come up with the login screen from my ISP. if thats out of the picture i'm happy with lubuntu.... peppermint is a derivative of mint ..is'nt that right.

how about giving some utility names...like from my post above....

thanks for the replies

@warfacegod thanks love the utilities...good bunch of them... also puppy linux package list helped me a lot. And i found gnomecommander as a very useful filemanager has most of the options as with gentoo fm

thanks a lot guys

---

### Post by mooreted on 2010-06-25
Don't know why no one mentioned OpenBox. OB is awesome and with obconf and obmenu it's really easy to set up.

---

### Post by t1nm@n on 2010-06-25
open box is good.

Do you guys know how to have the composting in fluxbox as we can do in openbox

---

### Post by jhsu802701 on 2010-06-25
Ubuntu isn't really intended to be a lightweight distro.  I suggest antiX Linux for these reasons: 1.  LIGHTWEIGHT: It will run on computers from the Windows 98 era.  I can tell you that antiX is FAST on just 256 MB of RAM.  256 MB for antiX is probably like at least 1 GB for Ubuntu. 2.  Compatibility with the Debian repository: In this respect, antiX is comparable to Ubuntu. 3.  User-friendly: Unlike Debian or Crunchbang, antiX is easy to use. 4.  More stable: antiX is derived from MEPIS, which is derived from Debian testing instead of Debian unstable.

---

### Post by mooreted on 2010-06-26
Puppy Linux is also pretty amazing for being so small. If it wasn't for some of the heavier stuff I do on my system, I could probably use Puppy for general purpose use.

---

### Post by NightwishFan on 2010-06-26
As suggested you can't beat building up your own system. Download and burn the mini iso.
[_32-bit Lucid_]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-i386/current/images/netboot/mini.iso")
[_64-bit Lucid_]("http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso")

Then choose to install a command line system. After the base system installs run the command below. It will install Xorg, XDM a minimal graphical login screen (optional, as you can login in on the CLI and run startx), and the fluxbox window manager (You can change this to anything you want, such as openbox). You can optionally add a graphical package manager or a web browser as well.
```
sudo aptitude update && sudo aptitude install xorg xdm fluxbox xterm
```

Other programs a recommend for a small and fast system, the names of them are their package names in Ubuntu, so just add the name to the end of the above command. Note these are optional, just some light programs I personally have used.

[LIST]
[*]wicd: Network manager to replace Networkmanager-Gnome. (Highly Recommended! Make sure you add you wireless card under preferences though. Probably wlan0)
[*]synaptic: A package manager to install/remove packages
[*]slim: An optional replacement for xdm
[*]midori: A web browser based on webkit
[*]xpdf: PDF viewer
[*]sylpheed: A GTK+ email client.
[*]exaile: A music player written in python
[*]gxine: Xine video player
[*]xfburn: A replacement for brasero
[*]ristretto: Image viewer
[*]mousepad: Text editor
[/LIST]

---

### Post by snowpine on 2010-06-26
Linux Mint (based on Ubuntu) has a nice Fluxbox edition.

---

### Post by t1nm@n on 2010-06-26
thanks both of you.... nightwishfan when i connect to the internet i'm welcomed by my isp's login page..i have to login before i can use the internet... i cant use w3m with this aspect .... however i like your strategy.. i once tried gentoo minimal..and that was a tragedy (they really mean it when they meant it was for experts ;)).

---

### Post by Tibuda on 2010-06-26
> **t1nm@n said:**
> open box is good.

Do you guys know how to have the composting in fluxbox as we can do in openbox

xcompmgr, the same app you use to have compositing in openbox

---

### Post by t1nm@n on 2010-06-26
thanks daniel... do you guys know how we can install the nvidia driver in antix...i have been able to work with it in virtualbox...so far its good runs with 64mb ram

---

### Post by t1nm@n on 2010-06-26
> **snowpine said:**
> Linux Mint (based on Ubuntu) has a nice Fluxbox edition.
well their edition is based on elyssa (on hardy)... but nice suggestion though ...
thanks

---

### Post by alexan on 2010-06-27
> **t1nm@n said:**
> Hello guys... i have been tampering with #!linux adn other light weight distros... but i'm trying to setup a light environment where i can work. So i picked up fluxbox and started messin' with it. it's very hard on the configuration part. but out of all the DE's i tried i'm most happy with fluxbox. but i'm having trouble with themes and other stuff..please tell me what i should do to get a functional light weight lucid....

If the hardrive space is not a problem, but the ram&resource. I do suggest you regular ubuntu.. then

**sudo apt-get install jwm menu pcmanfm**
Then try relog in jwm DM and use pcmanfm to manage the desktop.

---

### Post by NightwishFan on 2010-06-27
I did a test install with Virtualbox. I got Ubuntu 10.04 34mb/128mb with xorg and fluxbox.

---

### Post by snowpine on 2010-06-27
> **t1nm@n said:**
> well their edition is based on elyssa (on hardy)... but nice suggestion though ...
thanks

Nope. Helena Fluxbox is here: [http://www.linuxmint.com/rel_helena_fluxbox.php](http://www.linuxmint.com/rel_helena_fluxbox.php)

And Isadora Fluxbox is in testing and should be ready soon. :)

---

### Post by t1nm@n on 2010-06-27
wicked snowpine ..thanks a bunch
have you guys tried papuglinux...i'm running it from virtualbox... so far so good

---

