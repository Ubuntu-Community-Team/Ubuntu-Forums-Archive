---
title: "HOWTO: Upgrade Xubuntu to Xfce 4.4rc1"
date: 2006-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by SlugO on 2006-09-05
As you probably know Xubuntu uses version Beta1 of the upcoming Xfce 4.4 desktop environment. It has since been updated twice, to Beta2 and most recently Release Candidate 1. If you want to know what's new in them you can find the changelogs [here(B2)]("http://www.xfce.org/release_notes/4.4beta2_changelog.txt") and [here(RC1).]("http://www.xfce.org/release_notes/4.4rc1_changelog.html") And over [here]("http://thunar.xfce.org/news.html#2006-09-03") you can find a nice visual explanation about the new features that Thunar 0.4.0 has, the biggest one probably being the addition of Trash.
[ATTACH]15344[/ATTACH]

[COLOR="#ff0000"][SIZE="4"]NOTE:[/SIZE][/COLOR] I can't guarantee that I've found all the dependencies yet. If your installation aborts due to a missing one and you restart your system, your themes will look messed up and Xfce might act a bit strange but it shouldn't be anything too serious. Installing the missing dependencies and completing the installation will fix this. Or atleast it did for me ;) I take no responsability of broken systems, updating your desktop environment is quite a big operation so proceed with caution.

[COLOR="#ff0000"][SIZE="4"]EDIT:[/SIZE][/COLOR] **Many people** seem to be getting an error at every startup that says: Unable to contact the Xfce trash service. Read the solution below.

[COLOR="#ff0000"][SIZE="4"]Possible problems:[/SIZE][/COLOR]
[LIST]
[*]For some people **USB has stopped working**. In my experience installing gnome-volume-manager fixes these problems.
[*]xarchiver permanently took over file-roller that I'd like to use as the default archiver in Gnome.
[/LIST]

You can run the installer in your existing Xfce or Gnome desktop. Apparently you can also install it from Ubuntu without xubuntu-desktop although I haven't tried it myself. I've only tried it in Dapper, not sure if it works in Edgy. This topic does have one reply that says that it doesn't.


[SIZE="4"]1. Install the dependencies[/SIZE]
Paste this into the terminal:```
sudo apt-get install build-essential libxml-parser-perl libgtk2.0-dev libxml2-dev libvte-dev libxpm-dev libdbh1.0-dev libxfce4mcs-dev liburi-perl libCGI-perl libwww-perl libxml-perl libdbus-1-dev libdbus-glib-1-dev xorg-dev
```

[SIZE="4"]2. Get Xfce 4.4rc1[/SIZE]
Download it from [here]("http://www.xfce.org/archive/xfce-4.3.99.1/installers/xfce4-4.4RC1-installer.run") or just paste this to the terminal:```
wget http://www.xfce.org/archive/xfce-4.3.99.1/installers/xfce4-4.4RC1-installer.run
```

[SIZE="4"]3. Run the installer[/SIZE]
After the download has finished go to the terminal and the directory where the .run file is and type:```
chmod +x xfce4-4.4RC1-installer.run
```Then:```
sudo ./xfce4-4.4RC1-installer.run
```

[SIZE="4"]4. Choose the options[/SIZE]
The installer is a pretty straightforward wizard but you do need to note a few things:[LIST][*]The correct installation folder is /usr/local, this is the default when you run it with sudo
[*]Decide if you need a composition manager. I wouldn't recommend for older maschine.
[*]Extra optimizations have worked fine for me. Read the description and decide if you want them.
[*]Configure display manager. I've chosen yes for this one.
[*]Choosing the sound manager is a bit more tricky one. I think Xfce uses OSS by default but you can enable ALSA from this option. I chose yes for my newer computer and no for my older one. Sound works on both but on the newer computer I can't control it from the panel thingy anymore. So I'd choose no, don't enable ALSA.
[/LIST]

[SIZE="4"]5. Wait[/SIZE]
The installer takes a while. If it doesn't complete successfully then it's missing some dependecies. Please tell me if you get errors. Starting it again and completing successfully will fix the problems an aborted installation might have caused.


[SIZE="4"]6. Done[/SIZE]
Enjoy your new Xfce 4.4rc1 :mrgreen: Might take a restart to get er up and running completely, not sure.


[SIZE="4"]7. Old Thunar getting in the way? (optional)[/SIZE]
I noticed that even though the installer successfully installed Thunar 0.4.0, the older 0.3.1 still popped up every now and then. Xubuntu couldn't decide which to use so it was pretty random, though mostly 0.3.1. Maybe it's because it's still the version in Synaptic.

To fix this I installed a Thunar 0.4.1 from svn. Beware that it might not be as stable as 0.4.0 for example. [Here are the instuctions.]("http://ubuntuforums.org/showthread.php?t=95934&highlight=thunar+svn") Don't use the debs, they're pretty old. If you get an error during thunar configuration about tar-ustar then install automake1.9.

To completely replace 0.3.1 I replaced that HOWTO's last command, sudo make install (for thunar directory) with```
sudo checkinstall
``` so that it would replace it for good. Of course you have to first install it with```
sudo apt-get install checkinstall
```The version number for Thunar when using checkinstall seems to be incredibly long and is causing troubles for some. If you notice that's it's a long list of numbers then change it to 0.4.1svn for example. Now you can enjoy a brand spanking new Thunar with a trash can and everything :mrgreen:


[SIZE="4"]8. Fixing the trash error at startup (optional)[/SIZE]
The error's being caused by xfdesktop being loaded before Thunar.
Paste this into terminal:```
sudo cp /usr/local/etc/xdg/xfce4-session/xfce4-session.rc /usr/local/etc/xdg/xfce4-session/xfce4-session.rc_backup

sudo gedit /usr/local/etc/xdg/xfce4-session/xfce4-session.rc
```Then switch the commands of Client2_Command and Client3_Command so that it looks like this:```
Count=4
Client0_Command=xfwm4
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=False
Client2_Command=Thunar,--daemon
Client2_PerScreen=False
Client3_Command=xfdesktop
Client3_PerScreen=False
```This way Thunar loads before xfdesktop.

Okay, that should be it. During the next login remember to change your default session from Xfce 4.2 to Xfce 4 (or from 4 to 4.4, seems to vary a bit). If you have any problems, especially with dependencies, report them here.


P.S.
[Here's the thread]("http://ubuntuforums.org/showthread.php?t=213348") that inspired this HOWTO.
Thanks for the additional help videodrome.

---

### Post by gurgle on 2006-09-05
thanks for this. will it work on my 64-bit machine running ubuntu x64?

---

### Post by SlugO on 2006-09-05
> **gurgle said:**
> thanks for this. will it work on my 64-bit machine running ubuntu x64?Hmm.. I'm not sure. There's just a .run installer that doesn't mention anything about platforms. It seems to  configure and install the programs from source so there aren't binaries inside. My guess is that it will work.

---

### Post by gurgle on 2006-09-05
should i run this from a already-install version of xubuntu? if so, should i use the edgy 2 release or the 6.06 lts version?

---

### Post by SlugO on 2006-09-05
> **gurgle said:**
> should i run this from a already-install version of xubuntu? if so, should i use the edgy 2 release or the 6.06 lts version?You can start the installer in an existing (X)Ubuntu. In other words, it can be run in both Gnome and Xfce (as long as you have xubuntu-desktop installed). As for Edgy it probably will work the same way. These aren't distro oriented packages or anything.

---

### Post by SlugO on 2006-09-05
[COLOR="Silver"]*Sorry, double post. Damn on/off forum connection...*[/COLOR]

---

### Post by Logic* on 2006-09-05
Thanks SlugO

I had to install xorg-dev too before I could compile XFCE

---

### Post by SlugO on 2006-09-05
> **Logic* said:**
> I had to install xorg-dev too before I could compile XFCEStrange, I didn't need it.

---

### Post by zenrox on 2006-09-06
xorg-dev is needed for the built in compsiting manger works right
please add the the howto 
thx ](*,)

---

### Post by gurgle on 2006-09-06
ok, i got it to install, but i cant get THunar .4 to replace the old .3 version. I cant remove it from Synaptic, because it tells me it wants to remove xubuntu-desktop as well. 

i download and ran the GUI installer from this page:

[http://thunar.xfce.org/download.html](http://thunar.xfce.org/download.html)

but i still cant find the new thunar :(

---

### Post by Rui Pais on 2006-09-06
> **gurgle said:**
> ok, i got it to install, but i cant get THunar .4 to replace the old .3 version. I cant remove it from Synaptic, because it tells me it wants to remove xubuntu-desktop as well. 

i download and ran the GUI installer from this page:

[http://thunar.xfce.org/download.html](http://thunar.xfce.org/download.html)

but i still cant find the new thunar :(
Hi, 
have you run the installer with sudo or as a normal user?
Remember that your installation path must be on your environment $PATH 

hth.

---

### Post by SlugO on 2006-09-06
> **gurgle said:**
> ok, i got it to install, but i cant get THunar .4 to replace the old .3 version. I cant remove it from Synaptic, because it tells me it wants to remove xubuntu-desktop as well. 

i download and ran the GUI installer from this page:

[http://thunar.xfce.org/download.html](http://thunar.xfce.org/download.html)

but i still cant find the new thunar :(Read the end of my HOWTO.
I had the same problem until I installed 0.4.1 from svn.

---

### Post by Rui Pais on 2006-09-06
> **SlugO said:**
> I had the same problem until I installed 0.4.1 from svn.

Why not remove first the old thunar (deb) with synaptic?

Using the installer for 0.4.0rc1 and choosing /usr/local (the default, if installer runs as root) make thunar binaries install on /usr/local/bin which usually is on environment path.

Using svn one can install a (too) much more instable version, i think...

---

### Post by SlugO on 2006-09-06
> **Rui Pais said:**
> Why not remove first the old thunar (deb) with synaptic?Removes xubuntu-desktop.

> Using the installer for 0.4.0rc1 and choosing /usr/local (the default, if installer runs as root) make thunar binaries install on /usr/local/bin which usually is on environment path.Is there a better place to install it in?

> Using svn one can install a (too) much more instable version, i think...Hasn't crashed a single time for me.

---

### Post by Rui Pais on 2006-09-07
> **SlugO said:**
> 

[QUOTE=Rui Pais]Why not remove first the old thunar (deb) with synaptic?
Removes xubuntu-desktop.[/QUOTE]

hi, 
xubuntu-desktop is just a meta package. Check the last line of ```
aptitude show xubuntu-desktop
```
>  It is safe to remove this package if some of the desktop system packages are
 not desired.

About the better place, thats optional but i always prefer /opt/ to anything that is not installed via debs/apt. 
Don't like things not easy to uninstall mixed with my system. Of course thats a personal taste :).

---

### Post by Metacarpal on 2006-09-07
When I tried to use sudo checkinstall, it failed to build the package.  Here is the output from the log file:
```
dpkg-deb: unable to check for existence of archive `/home/metacarpal/xfce4-svn-source/thunar/thunar_0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r23103
0.4.1svn-r': File name too long

```

Any suggestions?

---

### Post by SlugO on 2006-09-08
> **Metacarpal said:**
> When I tried to use sudo checkinstall, it failed to build the package.  Here is the output from the log file:

Any suggestions?

Hmm.. Is that bunch of 0.4.1svn-r23103's its version number? It chose a similar, insanely long version number for me too by default. Change it to just one 0.4.1svn-r23103 and maybe it'll work.

---

### Post by k3nz0 on 2006-09-08
After I did the upgrade everything worked fine. but I kept getting an error message that it couldn't find the trash service and something about thunar.
I found that Thunar was located at two locations.  /usr/local/bin and /usr/bin.  The new one was installed in /usr/local/bin. so I renamed the old one in /usr/bin and copied the new one to it's location. rebooted and no more error messages. I don't know how many of you are having this same problem.
My volume control doesn't work anymore. well it works, but the volume control panel doesn't work anymore. I have to use the alsamixer command to turn the volume up and down. anyone else have the sound problem? I tried installing with both the alsa option and without.

---

### Post by SlugO on 2006-09-08
> **k3nz0 said:**
> After I did the upgrade everything worked fine. but I kept getting an error message that it couldn't find the trash service and something about thunar.
I found that Thunar was located at two locations.  /usr/local/bin and /usr/bin.  The new one was installed in /usr/local/bin. so I renamed the old one in /usr/bin and copied the new one to it's location. rebooted and no more error messages. I don't know how many of you are having this same problem.
My volume control doesn't work anymore. well it works, but the volume control panel doesn't work anymore. I have to use the alsamixer command to turn the volume up and down. anyone else have the sound problem? I tried installing with both the alsa option and without.

Hmm.. I wonder if it would work if you'd install it in /usr..? I wouldn't try to install it in /opt like Rui suggested cos I doubt that it would automatically start from there. But don't have any idea about /usr.

I actually got the error message on my newer computer where I have Ubuntu and Kubuntu too that there isn't a Thunar that could use the Trash or something. Even after I installed the svn version. But I didn't really focus on fixing it cos I use Gnome on this computer.

The sound problem is weird, I only got it when I chose ALSA.

---

### Post by Metacarpal on 2006-09-08
> **SlugO said:**
> Hmm.. Is that bunch of 0.4.1svn-r23103's its version number? It chose a similar, insanely long version number for me too by default. Change it to just one 0.4.1svn-r23103 and maybe it'll work.

Oh.  Yup.  That was it, all right.  Changed the version number and it worked like a charm.  In fact, I'm enjoying the new and improved XFCE and Thunar with Trash support right now.

---

### Post by Izuil on 2006-09-09
I think i've sucessfully installed thunar and xfce but now everytime i start the computer i get an error that says: Unable to contact the xfce trash service.
Make sure you have a file manager installed that supports the xfce trash service such as thunar.

Help me please

---

### Post by jlacroix on 2006-09-10
Won't work for me in Edgy. I have posted the relevant output below. The log file is too big and it freezes Firefox when I try to post all of it.

```

mkdir: cannot create directory `/usr/local/man': File exists
make[3]: *** [install-man1] Error 1
make[3]: Leaving directory `/tmp/xfce4-4.4RC1-installer/exo/docs/reference'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/tmp/xfce4-4.4RC1-installer/exo/docs/reference'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/tmp/xfce4-4.4RC1-installer/exo/docs'
make: *** [install-recursive] Error 1
!! Failed to install exo to /usr/local, see the errors
!! above for details on the problem.

```

---

### Post by SlugO on 2006-09-10
> **Izuil said:**
> I think i've sucessfully installed thunar and xfce but now everytime i start the computer i get an error that says: Unable to contact the xfce trash service.
Make sure you have a file manager installed that supports the xfce trash service such as thunar.

Help me pleaseDamn, this thing seems to happen to quite a few ppl. And I'm afraid that I don't know the solution yet...> Won't work for me in Edgy. I have posted the relevant output below. The log file is too big and it freezes Firefox when I try to post all of it.Maybe it doesn't work in edgy then. I haven't been able to test it since I don't have it.

---

### Post by lepre on 2006-09-10
> **Izuil said:**
> I think i've sucessfully installed thunar and xfce but now everytime i start the computer i get an error that says: Unable to contact the xfce trash service.
Make sure you have a file manager installed that supports the xfce trash service such as thunar.

Help me please

this happens here too.

i think it's becuase of thunar 0.3 and 0.4 (one hasn't the trash)

i'll now try to install 0.4.1 and see if it fix


edit: i fixed thunar (reinstalling 0.4.0 and uninstalling 0.3 from synaptic) but i still got the error :(

---

### Post by max.diems on 2006-09-10
Or just wait for 6.10 and get 4.4final?

---

### Post by lepre on 2006-09-10
> **max.diems said:**
> Or just wait for 6.10 and get 4.4final?

just for a single message at startup?

i should remember you that dapper comes with beta2 so rc1 should be better/more stable ;)

---

### Post by Neo40 on 2006-09-10
> **lepre said:**
> just for a single message at startup?

i should remember you that dapper comes with beta2 so rc1 should be better/more stable ;)

I think dapper comes with xfce4 beta1 (version 4.3.90.2) and not 2...So its pretty "old"...

---

### Post by lepre on 2006-09-10
> **Neo40 said:**
> I think dapper comes with xfce4 beta1 (version 4.3.90.2) and not 2...So its pretty "old"...

i had beta2 and didn't remember to have upgraded it, anyway, surely rc it's better than beta (any) 8)

---

### Post by Metacarpal on 2006-09-11
When I go to Change Session on the login screen, I have two options for xfce now: one that just says "xfce" and one that says "xfce 4.4".  If I choose the former, I get the trash service error.  If I choose the latter, everything's great.

See if you have an entry for "xfce 4.4" and see if that works for you.

---

### Post by Bree on 2006-09-11
> **Metacarpal said:**
> When I go to Change Session on the login screen, I have two options for xfce now: one that just says "xfce" and one that says "xfce 4.4".  If I choose the former, I get the trash service error.  If I choose the latter, everything's great.

See if you have an entry for "xfce 4.4" and see if that works for you.

didn't work :(

---

### Post by Neo40 on 2006-09-11
I do have the trash error with xfce 4.4-RC1 too. Maybe if I delete my ~/.config it could solve the problem? I can not try it right now but I'll do tonight...

---

### Post by Metacarpal on 2006-09-11
Did you do the instructions for [installing the latest Thunar]("http://ubuntuforums.org/showthread.php?t=95934&highlight=thunar+svn") through subversion?  If so, did you replace the last line in that howto with```
sudo checkinstall
``` instead of running that last sudo make install?

---

### Post by jlacroix on 2006-09-11
I can't get rid of the trash error either. I looked for duplicate thunar entries with slocate but couldn't find any at all.

---

### Post by Metacarpal on 2006-09-12
Pardon my ignorance, but do you have Synaptic? (I'm working on a Gnome/xfce hybrid, don't know if Synaptic is installed in Xubuntu by default, too...)  If so, what version number of Thunar are you showing?

---

### Post by Camino on 2006-09-13
about the trash service error:

I added the following lines to the file:

~/.config/xfce4-session/xfce4-session.rc

> 
[Failsafe Session]
Count=4
Client0_Command=xfwm4
Client0_PerScreen=False
Client1_Command=xfce4-panel
Client1_PerScreen=False
Client2_Command=Thunar,--daemon
Client2_PerScreen=False
Client3_Command=xfdesktop
Client3_PerScreen=False


Took me some time to find the right place, but now it´s working fine. I have found the hint here:

[http://forum.xfce.org/index.php?topic=2762.0](http://forum.xfce.org/index.php?topic=2762.0)

Bye

---

### Post by m3talgod on 2006-09-14
For me it worked by removing all files in the ~/.cache/sessions/ directory. :D 

I have also applied Camino's tip, but that alone didn't help.

---

### Post by thewayofzen on 2006-09-14
I had the trash error at first too.
The problem on my system was pretty simple.
Xfce as it is installed from synaptic on ubuntu installed to 
/usr/bin/
The default location for an install with RC1 is /usr/local/bin/

Now here is the problem.

For some reason xfce cannot decide which thunar it is using.
It would seem that sudo thunar will run the new svn thunar as it is found in /usr/local/bin/ as root.. with the new trash.
Simply running thunar by itself without the sudo will run the old default thunar... NO TRASH.

Im not sure why this happens..But that seems to be the problem.

Once i removed  /usr/bin/thunar and /usr/bin/Thunar and replaced them with the new versions.. i was gold. 

All it required me to do was this.

sudo rm /usr/bin/thunar  
sudo rm /usr/bin/Thunar

then

sudo cp /usr/local/bin/Thunar /usr/bin/Thunar && sudo cp /usr/local/bin/thunar /usr/bin/thunar

Basically REMOVE the old thunar stuff from /usr/bin and replace it with the new stuff found in /usr/local/bin/  and no more problems

Its not the prettiest fix.. and as messy as it is.. it WORKS...

*shrug*

---

### Post by sawjew on 2006-09-14
I have tried everything here to get the trash to work in Thunar.  I have installed the SVN version of thunar using checkinstall and I am using version 0.4.1 at all times I have checked.  When I delete anything using the delete command in the menu it is going to trash but the trash applet will not recognise it.

The applet just has a warning message, no trash icon, which says > Failed to connect to the Trash. The name org.xfce.FileManager was not provided by any .service 

Does anyone know how to get this to work?

---

### Post by Star on 2006-09-14
I need help with this too. None of the posted suggestions have worked for me.

---

### Post by sawjew on 2006-09-14
The trash icon on the trash applet appears briefly and the applet behaves normally for a few seconds after something enters the trash but the error returns soon after.  The trash appears to work fine within thunar itself.

Does anyone know of a way to put a trash applet on the desktop?

---

### Post by GStubbs43 on 2006-09-14
Hey, I tried to do this, but it failed. The error log is too long, I also tried the pastebin thing and it didn't work... but the actual install windows says this at the end:

> **Extension Library:**
Running Configure... Done
Running Make All... Failed

The end of the error log says:
> !! Failed to build exo, see the errors above
!! for details on the problem.


Anyone know what to do? Thanks! :biggrin: :frown: :confused:

**UPDATE:** I ran it again without the Extra optimizations and I got past the Extension Library, but now it says:
> **Xfce Volume Control**
Running Configure... Failed

---

### Post by sawjew on 2006-09-15
I have found out that the trash applet works perfectly when thunar is open but the error message returns as soon as the thunar window is closed.  Does anyone know how to fix this?

I have the new XFCE4.4rc1 working really well including the composite manager so I have nice transparent windows and menus and drop shadows.  It does slow the system down a little so I may not keep it but it works well.  At this rate I may end up with Xubuntu on my desktop as well.

There are a couple of things that I have lost in the upgrade which I would like to restore if anyone can help me;
[LIST]
[*]the logout window now only displays logout, restart and shut down, does anyone know how to restore the hibernate option etc.
[*]when restart is checked it now asks for a password which it never used to, is there any way to go back to the old restart
[*]does anyone know how to restore the xubuntu splash screen with the mouse running in the wheel?
[/LIST]

Also does anyone know how to display the desktop icons as shown here [http://thunar.xfce.org/news.html#2006-09-03]("http://thunar.xfce.org/news.html#2006-09-03")

---

### Post by lepre on 2006-09-15
i'm having some problems after the upgrade, beside the trash.

for example, do you have to type your password to restart/shut down the system?

ok: i got the aswer from the post above (didn't see the new page), so another problems (which i tought it was related) is xfmedia which can't play mp3 (it works in xmms). it tells me i don't have the permissions on the files (but i have) and i have to run it with sudo to make it work.

---

### Post by sawjew on 2006-09-15
I am having major problems now, the system is basically unusable.  I cannot open any application with gksu or gksudo because the window will not accept anything I type in it.  I can't open a terminal, I have tried xfce terminal, aterm, xterm, none of them will work I just receive an input/output error.  I can't use the run dialog or the verve command line because they will not accept keyboard input.  Abiword will take keyboard input but neither mousepad or gedit will.  

I have tried deleting all cache information and settings and starting clean.  I have tried starting with xfdesktop disabled and all non-essential services disabled.  I have changed the settings so thunar comes on before xfdesktop.  I am just about out of ideas.

this all started when I unchecked and rechecked to allow xfce to handle the desktop.  This showed the new desktop icons, trash, home and filesystem but immediately led to a whole swag of errors which have crippled my system.

I am about to reinstall and trying to decide whether to install edgy or not.  just a warning to be cautious when doing this upgrade.

---

### Post by lepre on 2006-09-15
it's possible to go back to beta2? :(

---

### Post by BoHu on 2006-09-15
The upgrade went very well for me. I did get the error message that others got but was able to fix it using suggestions from this discussion -

1. at login set session to xfce 4.4

2. sudo rm /usr/bin/thunar 
sudo rm /usr/bin/Thunar
sudo cp /usr/local/bin/Thunar /usr/bin/Thunar && sudo cp /usr/local/bin/thunar /usr/bin/thunar

---

### Post by Metacarpal on 2006-09-15
I may have to do that... After several days of goodness, I got the trash error last night.

---

### Post by GStubbs43 on 2006-09-15
> **GStubbs43 said:**
> ...... I ran it again without the Extra optimizations and I got past the Extension Library, but now it says:


All right it is all installed, I think... 
I am now in 4.4rc1, but I can't change some settings, such as background... When I select Settings>Desktop Settings, it says 
> Xfce Settings Manager error:
No such plugin "backdrop"

and Splash Screen says
> Xfce Settings Manager error:
No such plugin "splash"

I haven't checked all of the settings yet, but those are two I have gotten errors with so far. Any ideas? :confused: Thanks! :roll:

---

### Post by Neo40 on 2006-09-16
Hello,

I don't konw if this is because I upgraded to xfce4.4RC-1, but now thunar doesnt refresh automatically changes in directories. For example, if I create a fool directory, I wont see it in Thunar. I installed fam and hal but didnt work. Someone can help me to fix this?
Thanks!

---

### Post by lepre on 2006-09-16
> **Neo40 said:**
> Hello,

I don't konw if this is because I upgraded to xfce4.4RC-1, but now thunar doesnt refresh automatically changes in directories. For example, if I create a fool directory, I wont see it in Thunar. I installed fam and hal but didnt work. Someone can help me to fix this?
Thanks!

same here

---

### Post by Lou Quillio on 2006-09-16
> Xfce Volume Control
Running Configure... Failed

```
apt-get install libasound2-dev
```

LQ

---

### Post by Cartwheels4amile on 2006-09-17
I just installed Xfce 4.4rc1 last night, and everything looks great (no trash error even!) except for one thing. I can't seem to get my battery monitor to work. I can add it to the panel, but as soon as I close the "Configure Battery Monitor" window, it's gone. Does anyone know a fix for this?

---

### Post by NerdyShinobi on 2006-09-18
> **SlugO said:**
> You can start the installer in an existing (X)Ubuntu. In other words, it can be run in both Gnome and Xfce (as long as you have xubuntu-desktop installed).


Actually, SlugO, I followed your directions basically from a fresh Dapper install, and they worked without flaw.  I did compile Thunar from SVN to see if I could get rid of the Trash error (I couldn't), but that was my only deviation.  All in all, this is a great how-to!

---

### Post by Lou Quillio on 2006-09-18
> **NerdyShinobi said:**
> I did compile Thunar from SVN to see if I could get rid of the Trash error (I couldn't)
The trash error's caused by [FONT="monospace"]xfdesktop[/FONT] being started before the [FONT="monospace"]thunar[/FONT] daemon.  Here's the fix:

[http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706](http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706)

LQ

---

### Post by Metacarpal on 2006-09-18
> **Lou Quillio said:**
> The trash error's caused by [FONT="monospace"]xfdesktop[/FONT] being started before the [FONT="monospace"]thunar[/FONT] daemon.  Here's the fix:

[http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706](http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706)

LQ

Ohhhhhhhh... That explains it.  Thanks!!

---

### Post by darkteckno on 2006-09-19
Good guide thanks!!

---

### Post by SlugO on 2006-09-20
Just added most of the fixes to the HOWTO.

---

### Post by lepre on 2006-09-20
is there a way to disable the trash?

---

### Post by iseebluuue on 2006-09-22
Rui Pais is correct, I was having trouble with Thunar 0.3.1 so I just removed it from the terminal (it said xubuntu-desktop would also be removed but the total amount to be uninstalled was only 2.9MB). Voila, after the removal of 0.3.1 I now have Thunar 0.4.0rc1 in all instances. Thanks for this guide, but I think you could make it simpler by taking this route to solve the Thunar conflict. :)

---

### Post by Cartwheels4amile on 2006-09-22
Why is my PSP refusing to automount now that I installed 4.4 RC1? Is there any way to return to Beta 1? It actually worked better for me. I'm having all sorts of problems with RC1 :(

---

### Post by slapys on 2006-09-22
I am having the exact same experience. No USB device will automount, and I can't do it using the command line either.

---

### Post by Cartwheels4amile on 2006-09-22
For being a release candidate, this thing is really borked.

I've heard things about people going back to Beta 1... how do I go about this?

---

### Post by KiXeR on 2006-09-23
i've upgraded to RC1 without any problem but the main prblems are the refreshmet when creating a folder or downloading a file into a folder. It doesn't apeer until i press F5 and the USB devices are not mounting.

---

### Post by nwgray on 2006-10-04
I got this error when running the installer (from the log file):

## Running installer-gui (without debugging)
./installer-gui
./installer-gui: symbol lookup error: ./installer-gui: undefined symbol: g_type_register_static_simple

Thoughts? What am I missing?

Thx

---

### Post by Comendante on 2006-10-10
I install the last version of Xfce, but I can't change thunar, for the newsest version. I install it for instruction in this HOWTO'S:
[http://ubuntuforums.org/showthread.php?t=95934&highlight=thunar+svn](http://ubuntuforums.org/showthread.php?t=95934&highlight=thunar+svn)
But when I copy the last command i see :
```
root@mateusz:/home/mateusz# cd xfce4-svn-source/thunar/
root@mateusz:/home/mateusz/xfce4-svn-source/thunar# sh autogen.sh Preparing package directory /home/mateusz/xfce4-svn-source/thunar...
Running glib-gettextize --force --copy...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize --automake --copy --force
Patching file 'po/Makefile.in.in'
Running libtoolize --force --copy...
Running gtkdocize --copy...
Running aclocal-1.8   -I /usr/share/xfce4/dev-tools/m4macros -I /usr/share/xfce4/dev-tools/m4macros...
Running autoheader...
Running automake-1.8 --add-missing --copy --gnu...
configure.in:41: option `tar-ustar' not recognized
root@mateusz:/home/mateusz/xfce4-svn-source/thunar#
```

What i must do ?? I haven't go any idea.

---

### Post by SlugO on 2006-10-12
> **Comendante said:**
> What i must do ?? I haven't go any idea.I'm not sure about the stuff where it prompts to copy files but I think I got that tar-ustar error too and solved it by installing automake-1.9 or something like that :) The latest version anyways.

---

### Post by pizzigati on 2006-10-13
I've got solutions to two of the problems mentioned in this thread (and I don't think they've been given as of yet). Of course they probably won't work for everybody, but they work like a charm for me.

1) Trash error:
See post at [http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706](http://forum.xfce.org/index.php?topic=2762.msg11706#msg11706) (currently last post).
Related to D-BUS

2) USB mounting:
Apt-get gnome-volume-manager and set to start up with XFCE autostarted applications. This will automount your usb devices.

Cheers.

---

### Post by dpny on 2006-11-24
Simple question: can I use the basic instructions in this thread to install 4.4RC2? In addition to more polish I'm hoping it will allow me to hibernate my laptop, which seems to be missing in RC1.

---

### Post by dpny on 2006-11-25
I answered my own question--yes, it works. Got the Suspend option back by changing my login screen to the Ubuntu default. Learn something new every day. . .

---

### Post by battlehorse on 2006-12-05
> 
Got the Suspend option back by changing my login screen to the Ubuntu default.


What do you mean by "changing the login screen to the Ubuntu default" ? I have the same problem but I haven't yet figured out how to resolve it ... 

Thanks

---

### Post by fiery on 2006-12-06
Hey battlehorse,

I downgraded xfce4-session back to the Xubuntu version to get the Suspend and Hibernate option back at logout*. Mind you, I have followed sawjew's way of upgrading from Xubuntu to RC2 ([http://www.ubuntuforums.org/showpost.php?p=1816635&postcount=25](http://www.ubuntuforums.org/showpost.php?p=1816635&postcount=25))  with the addition of adding the corsac repository shown at the bottom of [http://pkg-xfce.alioth.debian.org/](http://pkg-xfce.alioth.debian.org/), so not quite sure if we are quite at the same setup.

* While I have the Suspend and Hibernate option available again, the one time that I tried to Hibernate, it appeared to do it OK, but then I got an error when starting up again saying that it didn't unmount properly. So I think I need to look at that a bit further... 

Hope this helps.

Cheers,

---

### Post by battlehorse on 2006-12-06
I have found a way to fix my issues ( remember that I have installed XFCE 4.4RC2 using the graphical installer available at xfce.org and using apt-get for all the necessary libraries ):

to get the suspend/resume buttons back, I had only to choose "**Default System Session**" as my preferred session at the login screen ( previously I was using "XFCE Session" ).

Btw this change fixed also the "battery panel applet" problem which some other users reported ( the applet won't stay on the panel unless you are using the Default System Session ).

When using the "Default System Session" I was not able to use the sound (the mixer settings would always reset the volumes to zero) and I had the re-install xfce enabling the **alsa option**, which in turn forces you to apt-get the package **libasound2-dev** . 

Hope this helps someone else!

---

### Post by azuretech on 2006-12-24
I just upgraded to Xfce 4.4rc2 and while the upgrade seemed to go okay, I've noticed that I've lost all my Desktop shortcuts.... (the original Xubuntu install displayed whatever was in ~/Desktop as icons on the desktop, with Xfce4.4rc2 nothing in the ~/Desktop directory is displayed)   minimized applications do appear on the desktop as icons however.

I've also lost the right click menu to add items to the desktop that I used to have in the original Xubuntu install..... Any suggestions on how I can get the old behavior (or at least something like it) back?

---

