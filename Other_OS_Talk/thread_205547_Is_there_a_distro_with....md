---
title: "Is there a distro with..."
date: 2006-06-28
forum: Other OS Talk
---

### Post by saigon_82 on 2006-06-28
Hello!

[COLOR="Red"]NOTE: The following text is something like chit-chat but may contain good information for you to help me. If you think you'll understand my question without reading the chit-chat, jump over to[/COLOR] **#NO_CHITCHAT**

I have used Ubuntu pretty long and what can I say?
It's just perfect! =P~

However, I am needing something, and that is to install a Linux distro (which has the capability to use Debian [.deb] packages) WITHOUT any software other than the distro itself and the desktop environment.

For example, when I make a fresh install of Ubuntu, it has a lot of software pre-installed, like Totem, Rhythmbox, GIMP, OpenOffice, etc... what I want is to have a Linux distro without pre-installed stuff, so I would be able to have XMMS or amaroK as the ONLY music player, Kolourpaint as the ONLY image editor and only AbiWord instead of the > ultra < slow OpenOffice.

Could someone help me with this?
Ofcourse stuff related to the desktop environment (like terminal and synaptic, build-essential etc..) can be "pre"-installed, but other software not.

I have been searching for ages but not found anything.
And yes, I tried the first time I got my hands on Ubuntu the Expert Mode installation, but there was no screen letting me to choose the software to install. Also, I think a "plain" Ubuntu with only the desktop environment and the needed stuff would cut down the size of the ISO maybe 100Mb...

I have been trying to play around with the ISO image (Dapper Drake 6.06), but it did not help me.

**#NO_CHITCHAT**

Sooo, my question is, is there any Linux distro which DOESN'T have any other software pre-installed other than the needed stuff (desktop environment, needed libs, terminal, synaptic [or any other package manager]) ???
And if there is one, it would be more appreciated if it has the ability to use Debian packages (.deb files).

Thanks a lot! :-\" :-\" :-\" 
Any kind of help is very appreciated!

PS: I am sure you'll ask "why do you need this?", the answer is, I own a small company and in all the computers we have in the company (20 + Mine =P~) there is Windows Server installed, and I want to switch to any Linux distro without pre-installed stuff so I could install only the business stuff needed for our company. I am sure you will also say "you could install a distro and remove the software you don't need", but I always want to have everything clean and that task sounds a bit dirty to me.:roll:

---

### Post by knn on 2006-06-28
You might want to try [Damn Small Linux]("http://www.damnsmalllinux.org/")

> Damn Small is small enough and smart enough to do the following things:

    * Boot from a business card CD as a live linux distribution (LiveCD)
    * Boot from a USB pen drive
    * Boot from within a host operating system (that's right, it can run *inside* Windows)
    * Run very nicely from an IDE Compact Flash drive via a method we call "frugal install"
    * Transform into a [COLOR="Red"]Debian OS[/COLOR] with a traditional hard drive install
    * Run light enough to power a 486DX with 16MB of Ram
    * Run fully in RAM with as little as 128MB (you will be amazed at how fast your computer can be!)
    * Modularly grow -- DSL is highly extendable without the need to customize


---

### Post by hizaguchi on 2006-06-28
When you talk about the "expert mode" install, do you mean the "install a server" option?  That is how I do my Ubuntu to accomplish what you describe.  Just do the "install a server" process, and then when you get to the command line that it gives you, type "sudo aptitude" and you'll be in a very powerful (though ugly) package manager.  From there you can pick just the packages you want.  If you need some guidance, you can view the normal metapackages by selecting "tasks" at the bottom of the list of package categories.  That will allow you to look over the packages that come in a default install of *buntu and pick the ones you want.  Then you can install them from there, or you can write them all down and make yourself a simple little script that you can use to install them all on all of your machines without so much typing.

Otherwise, there's always Debian.  :)

---

### Post by saigon_82 on 2006-06-28
@knn: I'll take a look into Damn small Linux, thanks!
@hizaguchi: I don't mean "install a server" at the CD boot menu (where you can choose to install through text mode or to install a server), press F6 twice and you can choose between Normal and Expert Mode.

---

### Post by hizaguchi on 2006-06-28
Ohhh yeah.  I always stay away from that option out of fear. :)  The server install is pretty easy though, as long as you know what packages you want to install.  I just found out though that the Gnome package (gnome-desktop-environment) is in universe, in case you get to looking for it.

---

### Post by saigon_82 on 2006-06-28
@hizaguchi: I can install GNOME whenever I want from it's official site, so there's no need for Ubuntu this time ;). And I don't need a server, my company's computers had Windows Server pre-installed as I bought them, but a desktop computer will do fine, that's why I want to switch to something simple.

BTW, I looked into Damn Small Linux, it just contains tooo much pre-installed/included software, look to this list:
> XMMS (MP3, CD Music, and MPEG), FTP client, Dillo web browser, links web browser, FireFox, spreadsheet, Sylpheed email, spellcheck (US English), a word-processor (FLwriter), three editors (Beaver, Vim, and Nano [Pico clone]), graphics editing and viewing (Xpaint, and xzgv), Xpdf (PDF Viewer), emelFM (file manager), Naim (AIM, ICQ, IRC), VNCviwer, Rdesktop, SSH/SCP server and client, DHCP client, PPP, PPPoE (ADSL), a web server, calculator, generic and GhostScript printer support, NFS, Fluxbox window manager, games, system monitoring apps, a host of command line tools, USB support, and pcmcia support, some wireless support.  

And for my company I maybe just want to have _XMMS, Firefox, Nano, calculator, system monitoring stuff, USB support_. To install what I need from scratch is very easy as long as the distro allows the usage of debian packages.. I think you all get the point, but where to get the ultra-lite distro? I guess there's nothing like this, but please help me if you can. Thanks!

---

### Post by hizaguchi on 2006-06-28
As far as I know, the "server" install in Ubuntu doesn't install a server in the sense that it's preconfigured to serve files and stuff.  I think it's just a wording for "base system with a command line".  As far as I know, it's the same thing you get from a Debian install without picking the desktop environment option.  Somebody correct me if I'm wrong on that.

Are you going to be using some kind of proprietary software that's only available as a .deb package?  Or is there some other reason you're wanting .deb compatability?  Because Arch Linux is a very good, clean distro with a very minimal base install.

---

### Post by m0gsi on 2006-06-28
BTW what do you want this for? If it is for a newbie who only need one of everything because choice confuses him/her then just edit the menus!

If it for size then you could just remove the unneeded packages your self?

---

### Post by m0gsi on 2006-06-28
Oh sorry i didn't read the bit at the bottom. Still if you create your own uninstall script to remove what you want it could be quick enough...

---

### Post by Azrael on 2006-06-28
Debian network install?

---

### Post by Buffalo Soldier on 2006-06-28
[QUOTE=Azrael]Debian network install?[/QUOTE]I agree, this fits all the requirement.

---

### Post by GuitarHero on 2006-06-28
Wouldnt it be possible to make a script to remove all applications then install just what you want?  Like automatix but with uninstallation also.  I don't know of your knowledge, but im sure you could find someone to make you one if you dont know how.(i would but im new to linux).

you could put the script on a cd or floppy and just run it on all your computers.

---

### Post by ozstriker on 2006-06-28
You could use the server install of Ubuntu, and then aptitude or apt-get what you need. 
x-window-system-core
gnome
then the programs you want.

---

### Post by RRS on 2006-06-28
Found these instructions in a similar thread yesterday and saved 'em for some unknown future  experiment.

> Base System Only:
"You can do (from the Alternate Install CD) a server install and then
```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
```

and then just use Synaptic to install stuff.

Or if you're really comfortable with the terminal, do a server install and just type
```
aptitude
```

Similar to a couple of the previous post's but seem to me a little more specific and seem to cover what you're looking for.

---

### Post by kop316 on 2006-06-28
I would agree with a Debian Network install. All you get is a Desktop Environment, and the rest you have to apt-get.

---

### Post by saigon_82 on 2006-06-30
Thank you all for the replys!
I'll look into Debian network install and maybe try Ubuntu's server install..

EDIT: And incase I want install the KDE do I change **gdm** into **kdm** in the above command?
EDIT2: And if I want to install XFCE, what is the command then?
Sorry if I make any inconvience for you.

Thank you very much!=D> :-\" :grin:

---

### Post by knn on 2006-06-30
[QUOTE=saigon_82]Thank you all for the replys!
I'll look into Debian network install and maybe try Ubuntu's server install..

I have one question though, for what is this:


EDIT: And incase I want install the KDE do I change **gdm** into **kdm** in the above command?
EDIT2: And if I want to install XFCE, what is the command then?
Sorry if I make any inconvience for you.

Thank you very much!=D> :-\" :grin:[/QUOTE]

For kde, replace gdm with kdm, remove icewm, and add kde-core. For xfce you might want xdm (altough both gdm and kdm will work fine with it), and xfce4. Both kde-core and xfce4 only install the very basic destop.

---

### Post by jacksaff on 2006-06-30
Download a Debian net install ISO. It's pretty small (can't find mine right now so can't remember how small) and has just the bare minimum to get debian up and running. Doesn't have a graphical desktop (they are not essential at all) so if you are afraid of the terminal make your first command apt-get install desktop-of-your-choice.

---

### Post by 3rdalbum on 2006-07-01
Have you heard of Puppy Linux? It's a lightweight Live CD (installable) with IceWM and as many programs as will fit alongside the OS in 60 megs.

There is a derivitive which JUST has the operating system and GUI, virtually no other programs included. It fits in some ridiculously small amount of space, like 30 megs or something. I can't remember its name at the moment, but it's compatible with Puppy's DotPup packages and many users create DotPups for popular programs. You might want to look into it, especially since it's made to look a bit like classic Windows and you mentioned that it was for a Windows to Linux migration.

---

### Post by saigon_82 on 2006-07-02
Thanks for all the replies, I am sure my needs will be filled :D  
I wasn't able to install Ubuntu yet, as I came yesterday from my cruise, I was in Sweden \\:D/ 

However, I had the time to try Debian network install, but it didn't like my PC :(
I tried to install it several times, but it was just popping me errors I didn't understand.
So, I decided not to use it, but instead use the server install of Ubuntu.

I have one question though, if I install XFCE as the desktop environment, will it include stuff like mousepad or do I have to install it myself through apt-get? If it's so, then it's good, else it's bad and I don't have my needs filled.

EDIT: I looked into Puppy Linux, and it's far from what I want, but thanks for the suggestion 3rdalbum.

Thanks!

---

### Post by knn on 2006-07-02
[QUOTE=saigon_82]Thanks for all the replies, I am sure my needs will be filled :D  
I wasn't able to install Ubuntu yet, as I came yesterday from my cruise, I was in Sweden \\:D/ 

However, I had the time to try Debian network install, but it didn't like my PC :(
I tried to install it several times, but it was just popping me errors I didn't understand.
So, I decided not to use it, but instead use the server install of Ubuntu.

I have one question though, if I install XFCE as the desktop environment, will it include stuff like mousepad or do I have to install it myself through apt-get? If it's so, then it's good, else it's bad and I don't have my needs filled.

EDIT: I looked into Puppy Linux, and it's far from what I want, but thanks for the suggestion 3rdalbum.

Thanks![/QUOTE]

mousepad is a dependency of xubuntu-desktop and rox-filer. It's not included with xfce. You'll have to install these things separately or install xubuntu-desktop (which contains a lot of apps, like abiword, gimp, gaim etc.)

---

### Post by saigon_82 on 2006-07-02
[QUOTE=knn]mousepad is a dependency of xubuntu-desktop and rox-filer. It's not included with xfce. You'll have to install these things separately or install xubuntu-desktop (which contains a lot of apps, like abiword, gimp, gaim etc.)[/QUOTE]

Thanks for the info! I just wrote a mini-guide on installing a customized install of Ubuntu. I think I'll post it here soon.

Thanks again for all your help!
Most of the credit goes to knn! Thanks!

---

