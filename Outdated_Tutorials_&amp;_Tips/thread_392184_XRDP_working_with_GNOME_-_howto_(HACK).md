---
title: "XRDP working with GNOME - howto (HACK)"
date: 2007-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by richardward101 on 2007-03-24
This solution is a bit of a messy hack, but it should work until xrdp/Xvnc are fixed.

What is XRDP?

It is a vnc-like server to allow you to connect to ubuntu from a windows machine (or using rdesktop) in the same way that Windows Remote Desktop does. (i.e. no additional software on the windows machine is needed). website [here]("http://xrdp.sourceforge.net/").

What is this guide

This guide will help set up xrdp on Ubuntu and, optionally get it working with GNOME (this has been a difficulty for many people). The GNOME solution is a bit of a hack, and certainly not perfect, but its the first working solution I've seen. It has been tested by myself on Edgy only, although it should work on any other version too. Let me know!
The manner in which it works with gnome is to have an extra layer of vnc (using x11vnc). The problem is that you MUST have already logged on as yourself before trying to use xrdp. But IMO its better than nothing. The end result is actually a lot more like the bahaviour of RDP on Windows XP.

The first two sections (sufficient for running kde with xrdp) should be usable by anyone, and can be easily undone.

The third section should probably only be used by those who understand what the instructions do.





THE GUIDE:

1) GETTING XVNC TO WORK

xrdp relies on Xvnc, which has problems with fonts (which we will fix!)

```
sudo apt-get install Xvnc
```

now create a password file for Xvnc (this password is only for testing now, it will not be needed later so anything can be used)

```
vncpasswd
```

now, running Xvnc at the moment will probably not work. try it:
```
Xvnc :1
```
It will almost definitely give erroros about fonts but if it doesn't exit outright, and instead waits around for a connection you can proceed to section 2).

Otherwise, you need to link to your fonts directory so that you can run Xvnc.

```
cd /usr/share/X11
sudo mv fonts fonts.bak
```
This renames your fonts folder. If something drastic goes wrong, just rename it back!

now to link to the proper folder:
```
sudo ln -s /usr/share/fonts/X11/ fonts
```
now try Xvnc again:
```
Xvnc :1
```
and hopefully it wont crash, which should mean xrdp can run properly!






2) INSTALLING XRDP

It needs to be downloaded and compiled, so we'll need to install some tools:

```
sudo apt-get install build-essential libpam0g-dev libssl-dev x11vnc vncviewer fakeroot checkinstall x11vnc
```

now download the latest version (0.3.2) from sourceforge, or type

```
cd ~
wget http://mesh.dl.sourceforge.net/sourceforge/xrdp/xrdp-0.3.2.tar.gz
```

now, cd to the folder you downloaded it to and type:

```
tar -zxvf xrdp-0.3.2.tar.gz
cd xrdp-0.3.2/
make
fakeroot checkinstall
 
```
If it asks questions just accept the defaults
This will result in an error about not being able to install the package, but ignore that.
Once its done there should be a .deb package in the xrdp folder that can be installed in the usual manner (by double-clicking it, or using sudo dpkg -i _packagename_)

The package can be uninstalled by using synaptic or ```
sudo apt-get uninstall xrdp
```

now run ```
sudo /usr/local/xrdp/xrdpstart.sh
```

If you run KDE then the howto is now complete!

either way test it by running ```
rdesktop localhost
```

You should be able to log in if you have KDE installed but it probably wont work if you use gnome. This seems to be a problem with Xvnc, and there currently seems to be no proper solution(i'm not sure about other desktop environments like XFCE).



EDIT --- it has been pointed out to me that at this point usingthe command ```
sudo apt-get install vnc4server=4.1.1+xorg1.0.2-0ubuntu1
```
to downgrade to a different version of vnc4server makes gnome work fine.
However, following section 3 will enable xrdp to run like the windows version: i.e display the same session as you were previously logged onto. If this is what you want, follow the instructions below, however you may be better advised to instead use rdp as it was meant to be used, then run x11vnc on their previous display. Proceed only if you understand whats going on, and its limitations.



3) GNOME

Now comes messy but necessary part if you really want gnome.

To explain:
XRDP uses a file called startwm.sh to determine which Desktop environment to use. Any program can be run in this file (the defaults are things like gnome-session, but gnome session can't run inside Xvnc).

The only solution I can find is to first run x11vnc, which runs a vnc server that captures an already running session (hence the need to be logged in already) and then run vncviewer in fullscreen mode instead of having a desktop environment running.

so, backup startwm.sh
```
cd /usr/local/xrdp/
sudo mv startwm.sh startwm.sh.bak
sudo gedit startwm.sh
```

and enter the following code into the file:
```
#!/bin/bash
x11vnc -display :0 -localhost &
sleep 5
vncviewer localhost:0 -fullscreen
```

and make it executable:
```
sudo chmod +x startwm.sh
```

Now, make sure you are logged on to your desktop, go to a windows machine and log onto you ubuntu machine using remote desktop, and hopefully it'll work.



PS. This guide is entirely my own work. I found the font fix on these forums, i'm not sure where but its posted many times by many people. The hack I came up with myself. This is my first tutorial and I wrote it in a bit of a hurry as I was so excited to have found a way to make xrdp, ubuntu and gnome work together; I've been trying for about a year - periodically looking for solutions. All comments, criticisms, sugesstions and requests for help are welcome, but try to post exactly where things went wrong and what any errors were.
Good luck.

---

### Post by Webspot on 2007-03-31
I've set up the server. I have gnome and kde installed on this computer. Whenever I try to connect to rdp, I get KDE. Is there a way to change this?

---

### Post by richardward101 on 2007-04-03
Yes, there should be.

If (as I infer from your message) you have installed xrdp and done nothing else, the file you need to look at is /usr/local/startwm.sh (which needs to be edited by root).
If you look at this file it should be clear (without knowing EXACTLY whats going on - I don't quire know exactly either) that the first Desktop it tries too run is KDE. the solution it to delete the bits that don't refer to gnome (or just delete everything and put your own startup command in). However, as described just before part 3, gnome cannot run in xrdp unless you downgrade Xvnc, so follow the instructions just before part 3. however, if you want to rdp into your existing session automatically (as per windows, except you must be already logged in from GDM or KDM), then follow the instructions in part three.
I'm going to rewrite this guide in a better format with better descriptions of the different options, if you can't get it running as you want before I do that then feel free to PM me on these forums.

---

### Post by Webspot on 2007-04-04
I am sure I had changed that file. But I guess I didn't, as I found the default stuff in it. 

Changed the file and it works fine now.

Thanks!!

---

### Post by Eazy© on 2007-06-06
Hi!
I'm trying to install xrdp on Feisty but I get this error:
```
/usr/bin/ld: cannot find -lxrdp
collect2: ld returnerade avslutningsstatus 1
make: *** [xrdp] Fel 1

```

Any idea?

---

### Post by Kagee on 2007-06-08
Same error, english text, i need help to :(
```

gcc -L/usr/gnu/lib -L../libxrdp -Wl,-rpath,. -o xrdp xrdp.o xrdp_process.o xrdp_listen.o xrdp_bitmap.o xrdp_wm.o xrdp_painter.o xrdp_region.o xrdp_cache.o xrdp_font.o funcs.o xrdp_login_wnd.o lang.o list.o file.o os_calls.o thread_calls.o xrdp_mm.o -ldl -lpthread -lxrdp
/usr/bin/ld: cannot find -lxrdp
collect2: ld returned 1 exit status
make: *** [xrdp] Error 1
```

---

### Post by Kagee on 2007-06-25
I had to make as root, deaktivate "Remote Desktop" in Feisty , install vncserver and do Xvnx :1 to make it work

---

### Post by SmartestAzz on 2007-08-28
Getting this to work in Ubuntu 704 has kept me up late.  In the end, I installed tightvncserver to solve the problem.  I followed the instructions in the Install.txt document bundled with xrdp 4.0 with some minor alterations - installed x11vnc.  Can anyone tell me why vncserver and vnc4server would not work, yet tightvncserver did?

---

### Post by kneo79 on 2007-09-30
Sorry I'm a really newbie...
Where can I find Xvnc and Xrdp repository for Ubuntu???
If I try:
```
sudo apt-get install Xvnc
```
I get:
```
Can't find Xvnc
```

---

### Post by albsen on 2007-10-22
I tried the to follow the howto but couldn't find the Xvnc (only x11vnc) and didn't succeed in build xrdp from source... could anyone provide an ubuntupackage?

---

### Post by jeremyk@bellsouth.net on 2007-10-25
Here is what I did:

sudo apt-get install vncserver
sudo apt-get install libpam0g-dev
sudo apt-get install libcurl4-openssl-dev
download xrdp 0.4
tar -zxf xrdp-0.4.0.tar.gz
cd xrdp-0.4.0
make
sudo make install
sudo /usr/local/xrdp/xrdp_control.sh start

Then use RDP client to connect.

---

### Post by tomcat2007 on 2007-10-26
> **jeremyk@bellsouth.net said:**
> Here is what I did:

sudo apt-get install vncserver
sudo apt-get install libpam0g-dev
sudo apt-get install libcurl4-openssl-dev
download xrdp 0.4
tar -zxf xrdp-0.4.0.tar.gz
cd xrdp-0.4.0
make
sudo make install
sudo /usr/local/xrdp/xrdp_control.sh start

Then use RDP client to connect.

That worked for me, but only after installing KDE.  Now I just need to figure out how to get rid of all the gnome stuff.  I've removed and purged it with aptitude but I still have the clutter of gnome applications on my menus.

---

### Post by eaglesfan17 on 2007-10-26
Does anyone know what port xrdp uses so that I can forward that port on my router? Does it use the same port that Windows Remote Desktop (3389) uses?

---

### Post by tomcat2007 on 2007-11-02
> **eaglesfan17 said:**
> Does anyone know what port xrdp uses so that I can forward that port on my router? Does it use the same port that Windows Remote Desktop (3389) uses?It does if you're accessing an XRDP server via the Windows RDP client.

---

### Post by tomcat2007 on 2007-11-03
Just ran a netstat after RDPing from a Linux client to a Linux server & that connection also uses 3389.  Wanted to doublecheck using a Linux client since [to my recollection] XRDP requires VNC to be installed.

---

### Post by Snowdan on 2008-04-27
Firstly great HowTo followed the steps and have everything working like a charm as per your guide. I can RDP in and open multiple sessions and also using the change to startwv.sh take display:0. But as I use Xfce which is compatible with Xvnc I wanted to change the startwm.sh to open a vncserver on a given port and then open a fullscreen vncviewer. But when I log in I get the standard console and if I then source the startwm.sh it does as I expect. I cant find much in the way of forums for xrdp alone so was hopping some one can see my mistake.

startwm.sh 
```

 #!/bin/bash
vncserver :84 &
sleep 2
vncviewer localhost:84 -x11cursor -fullscreen -passwd ~/.vnc/passwd
```

I know the second time I run this it will state a vncserver is running but I have tried starting the vncserver separately and just having the last line and still no luck. Can someone point out what I'm missing. Thanks

Dan.

---

### Post by Scdv2 on 2008-09-03
I followed the above steps and it originally worked fine.  after restarting the Ubuntu machine I am receiving:

"Because of a protocol error, this session will be disconnected.  Please try connecting to the remote computer again."

on the Windows Xp machine.

I tried restarting the xrdp server however i am continuing to receive this message.

can someone please help

---

### Post by tgellen on 2008-10-08
> **Scdv2 said:**
> I followed the above steps and it originally worked fine.  after restarting the Ubuntu machine I am receiving:

"Because of a protocol error, this session will be disconnected.  Please try connecting to the remote computer again."

on the Windows Xp machine.

I tried restarting the xrdp server however i am continuing to receive this message.

can someone please help

This is because your XP box now has the latest version of the Remote Desktop Client 6.0 (probably via Service Pack 3). If you are using Hardy (8.04) you need to upgrade xrdp to the latest version from Cedric Schieli PPA ([https://launchpad.net/~cschieli/+archive](https://launchpad.net/~cschieli/+archive)). Incidentally this the same version of Remote Desktop Client that's included with Vista.

NOTE: This new version is included in Intrepid. I wish they'd officially backport it to Hardy.

---

### Post by SilverWave on 2008-12-24
Hi Guys, thanks for this HowTo, information on xrdp is thin on the ground.

[B]I am using Ibex 8.10 and found that the package for xrdp works fine.

I first installed tightvncserver and then xrdp.[/B]

On my Ubuntu machine I have set my firewall to allow port 3389.

I used mstsc from the command line on my windows laptop (in options I cleared pw and user name) this connects to xrdp and shows the xrdp menu list.

Now the defult option is:
Module: sesman-Xvnc
Username: silverwave
password:

I enter my password and all works fine, that is I can see my desktop and most of my apps work ok (although the theme is missing).

This is however not good enough as when I run VitualBox it dies on me.

Looking at the way this module works it seems as if I am getting another session created based on my username and desktop but its not 100%.

So looking at the other options 
[I]
Menu:
sesman-Xvnc
console
vnc-any
sesman-any
rdp-any
sesman-X11rdp[/I]

console looked just what I wanted.

Now the console menu item details are:
module: console
password: 

Now once I input my username and pw this works exactly as I want - that is I see my real desktop and Virtualbox works etc.

**The only problem is that when connecting via console a dialogue box pops up (on my ubuntu 8.10 box) asking:**
 
[I]Question
----------------------------------------
Another user is trying to view your desktop.
A user on the computer 'localhost' is trying
to remotely view or control your desktop.
Do you want to allow them to do so?

[Refuse][Allow]
----------------------------------------[/I]
[B]
So how do I disable this?[/B]

System>Preferences>Remote Desktop
vino-preferences
[Set your remote desktop access preferences]

Seemed to be the answer but to no avail, I think these options are specific to vino ;)
[B]
So does anyone know where the configuration option is relating to xrdp's module "console"?[/B]
[See UPDATE below]

**Notes1:**
FILES
       /usr/bin/sesman
       /usr/bin/sesrun
       /etc/xrdp/sesman.ini
       /var/log/sesman.log
       /var/run/xrdp/sesman.pid

       /home/silverwave/.vnc
       passwd
       sesman_passwd
       gold:1.log
       gold:1.pid
       xstartup

xstartup
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
/etc/X11/Xsession

**Notes2**
User folders update
xdg-user-dirs-gtk-update
"Update common folders names to match current locale"

IIRC this was asking to change my folders names - I think I caught it when connecting via "console" and said NO.
Just to be safe I went system>preferences> sessions> and unticked it.

**Notes3**
xrdp's module "console" seems to be easy to break - sometimes I get "some problem" error messages and the only way to get it working is rebooting.
**Anyone know what I should be stopping/restarting?**
[UPDATE] System> Preferences> "Remote Desktop" ticking "Require Encryption" causes problems, untick and you can login to Console again.
xrdp module "sesman-Xvnc" never has a problem always works.

So to recap I am 95% there, I just need to know how to turn off the confirmation prompt.
__________________

[B][UPDATE]
System> Preferences> "Remote Desktop" Is the correct way to disable the confirmation prompt!

I went back through it from the start, step by step, and it works this time!

Yeah!!![/B]

xrdp Module "console" works out of the box (looks as if it uses GNOME vino-server).
xrdp Module "sesman-Xvnc" needs tightvncserver to work.

Now on to putty and ssh tunneling :D
__________________

[xrdp-keygen]
If you want to generate your own rsa key the command is:

xrdp-keygen xrdp

---

### Post by RealG187 on 2009-02-10
Is this method faster than VNC?

---

### Post by Circa Lucid on 2009-12-10
> **RealG187 said:**
> Is this method faster than VNC?
From what I've seen, RDP runs a heck of alot faster on both Linux and Win machines than VNC.

---

### Post by Steve1961 on 2010-01-03
It does run very fast and in karmic it works well, although you have to configure it first.  i found that when installing it from synaptic it tried to pull in tightvnc.  I wanted it to use the default vino server so I could connect to an existing session, which tightvnc doesnt allow.  But the solution is simple:

1. install tightvncserver
2. install xrdp
3. uninstall tightvnc server
4. run sudo service xrdp stop
5. sudo nano /etc/xrdp/xrdp.ini and just modify the top two sections:

```
[globals]
bitmap_cache=yes
bitmap_compression=yes
port=49500
crypt_level=high
channel_code=1

[xrdp1]
name=sesman-Xvnc
lib=libvnc.so
username=ask
password=ask
ip=127.0.0.1
port=5900

```

As you can see I've changed the default xrdp port, set encryption to high, and ensured that 5900 is the vnc port (which vino uses)

6. configure remote desktop from the Gnome menu
7. run sudo service xrdp start
8. make sure whichever port you use, in this example 49500, is open in your firewall and that you forward that port in your router
9. connect using the ip address and port number e.g. 1.2.3.4:49500
10 alternatively, which i do, tunnel it over ssh e.g. 

```
ssh -L 49500:localhost:45900 user@remote_machine
```

11. then just connect via localhost:49500

There's just one gotcha.  I found that I could connect fine from XP and from another linux box using the terminal server client, but from windows 7 it was no go as it through up a protocol error.  However, even here the solution is fairly simple - just use an old version of the remote desktop client on windows 7.  The how to for this is [here]("http://sourceforge.net/projects/xrdp/forums/forum/389417/topic/3455726")

---

### Post by Steve1961 on 2010-01-03
One more thing whilst I remember.  If you use the vino server you wont be able to set the resolution of the remote desktop, it will display at whatever the native resolution is.  If this is a problem just use tightvncserver and remember to modify the port from 5900 to 5901.  Unfortunately you'll find the keymap is screwed up when you do this.  The workaround is to edit ~/.vnc/xstartup file and add 'export XKL_XMODMAP_DISABLE=1' (without the quotes) before the last line /etc/X11/Xsession

---

### Post by jrssystemsnet on 2010-02-16
For anybody still looking, I put together a "cookbook" to getting xrdp working both for controlling the active local login session and/or a "clean" unrelated session, using either Vino or TightVNC.

[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

---

### Post by mantorpcity on 2010-03-03
> **jrssystemsnet said:**
> For anybody still looking, I put together a "cookbook" to getting xrdp working both for controlling the active local login session and/or a "clean" unrelated session, using either Vino or TightVNC.

[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)

You rule. Thanks a lot for this link.

---

### Post by totalz on 2010-03-10
> **jrssystemsnet said:**
> For anybody still looking, I put together a "cookbook" to getting xrdp working both for controlling the active local login session and/or a "clean" unrelated session, using either Vino or TightVNC.

[http://ubuntuwiki.net/index.php/Xrdp,_installing](http://ubuntuwiki.net/index.php/Xrdp,_installing)


The wiki doc is very good, I just following it step by step, and I did comment out the twm!

However, I still get
[IMG]http://img689.imageshack.us/img689/2067/xrdp.png[/IMG]

Where can I check the log for errors?

thanks 1st :p

---

### Post by jrssystemsnet on 2010-03-17
> **totalz said:**
> The wiki doc is very good, I just following it step by step, and I did comment out the twm!

However, I still get
[IMG]http://img689.imageshack.us/img689/2067/xrdp.png[/IMG]

Where can I check the log for errors?

thanks 1st :pTotalz, what version of Windows is that?  I have heard that the version of Remote Desktop Connection in Win7 won't work with earlier RDP servers; perhaps that's the problem.  (I only have Windows XP clients to test with.)

Maybe you could try doing an RDP in from localhost, using Ubuntu's built-in Terminal Server Client, to see if that's the problem?

---

### Post by totalz on 2010-03-18
> **jrssystemsnet said:**
> Totalz, what version of Windows is that?  I have heard that the version of Remote Desktop Connection in Win7 won't work with earlier RDP servers; perhaps that's the problem.  (I only have Windows XP clients to test with.)

Maybe you could try doing an RDP in from localhost, using Ubuntu's built-in Terminal Server Client, to see if that's the problem?


Thanks jrssystemsnet,

I wish I can try xrdp locally, but it's a server afar, which is why I'm trying to rdp to it in the 1st place, all I have now is SecureShell ;)

I wonder if I can find an older Windows RDP client to run in Win7!?

Just checked, there's some RD Gateway settings in Win7 RD client, probably not related, but will try to see if I can get a more detailed error...

---

### Post by totalz on 2010-03-25
I started getting 100% cpu because whenever I started vncserver, sth forks up a lot of vmware-user-wra

see details here: [http://ubuntuforums.org/showthread.php?p=9020560#post9020560](http://ubuntuforums.org/showthread.php?p=9020560#post9020560)

all I did was follow the wiki...

please help!

---

