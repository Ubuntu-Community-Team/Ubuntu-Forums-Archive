---
title: "Change gnome-terminal default size"
date: 2006-01-19
forum: Outdated Tutorials &amp; Tips
---

### Post by viscount on 2006-01-19
Does it annoy you that gnome-terminal does
not remember the size when you drag it around?

Well it annoyed me a lot so I went to #gnome and
finally got an answer, which can be found here:
[http://bugzilla.gnome.org/show_bug.cgi?id=155147](http://bugzilla.gnome.org/show_bug.cgi?id=155147)

You could rename the /usr/bin/gnome-termainal 
app then create a script with the proper geometry
and place it in /usr/bin/gnome-terminal like this:
~~~
#!/usr/bin/sh
gnome-terminal --geometry=80x15
~~~

But what I chose to do is just right click on the gnome-terminal
icon on my task bar, select propertys, then change the command to
**Command: gnome-terminal --working-directory=%f --geometry=80x15**

And its done, gnome-terminal will pop up with the size that I have
specified, however it still wont remember a size by dragging, but 
at least now I  know how to set its' default size.

Hope this helps.

---

### Post by dtmilano on 2006-09-28
Well, there's another way of doing it.
Take a look at [gnome-terminal-launcher]("http://gnome-tla.sourceforge.net") and you will be able to specify geometry as well as other extra command line options in GConf.

There's also [Installation and configuration instructions]("http://gnome-tla.sourceforge.net/wiki/index.php/Gnome-terminal-launcher_installation_and_configuration").

---

### Post by dog on 2006-09-28
> **viscount said:**
> Does it annoy you that gnome-terminal does
not remember the size when you drag it around?

Well it annoyed me a lot so I went to #gnome and
finally got an answer, which can be found here:
[http://bugzilla.gnome.org/show_bug.cgi?id=155147](http://bugzilla.gnome.org/show_bug.cgi?id=155147)

You could rename the /usr/bin/gnome-termainal 
app then create a script with the proper geometry
and place it in /usr/bin/gnome-terminal like this:
~~~
#!/usr/bin/sh
gnome-terminal --geometry=80x15
~~~

But what I chose to do is just right click on the gnome-terminal
icon on my task bar, select propertys, then change the command to
**Command: gnome-terminal --working-directory=%f --geometry=80x15**

And its done, gnome-terminal will pop up with the size that I have
specified, however it still wont remember a size by dragging, but 
at least now I  know how to set its' default size.

Hope this helps.


I have added the terminal to the panel (as well as other apps I use frequently). right-clicking on the icon and selecting properties allows me to add --geometry=120x50 to the command box so that terminal always opens with this geometry.
Hope this helps.


dog

---

### Post by KucingKelabu on 2006-11-23
Thanks for the tip :) Solves my mysery :D

---

### Post by z0mbie on 2008-01-28
What if you're using shortcuts?

----NM, I'll just create another run_command entry for the customized gnome-terminal command and shortcut in gconf instead of the default run_command_terminal.

---

### Post by nooblot on 2008-06-29
Now why TF don't the gnome people put this option into Preference setting ?????
And I'm talking about the "latest and greatest" release....

Y'know sometimes I get the feeling there are Linux people out there who really do want to make people (specifically noobs) hate Linux  :mad:

---

### Post by fedex1993 on 2008-06-29
also you can just edit the launcher and att eh --geometry to the launcher

---

### Post by weboide on 2008-09-12
If you want to change permanently the gnome-terminal default size , try this:

[http://www.codealpha.net/tips/gnome/45-how-to-change-gnome-terminal-default-size-ubuntu]("http://www.codealpha.net/tips/gnome/45-how-to-change-gnome-terminal-default-size-ubuntu")

It worked perfectly for me. Just follow the steps.

---

### Post by BOBSta on 2008-09-25
Ah-ha!  Thanks Viscount et al.  This has been bugging me for a while.  nooblot is right - why isn't this an option in the Profile?  "man gnome-terminal" is no help either, as it only says:

> 
--geometry=GEOMETRY
                 X geometry specification (see "X" man page), can be specified once per window to be opened.

So you quit and try "man X" and that doesn't work, just giving the VERY helpful:

> 
No manual entry for X
See 'man 7 undocumented' for help when manual pages are not available.

Anyway, I'm now very happy with my default 120x40 terminal.

Thanks
BOBSta

---

### Post by incubus on 2008-10-11
Yes, arguably the safest way is to edit the entry that launches gnome-terminal and append --geometry to it.

That said, I just learned a clever trick to specify the default size.  This is from the Fedora forum, but I tested and it works in Ubuntu as well.  See post #4 at:

[http://forums.fedoraforum.org/showthread.php?t=45607](http://forums.fedoraforum.org/showthread.php?t=45607)

Needless to say, backup your files before trying anything -- this is a system-wide configuration.

incubus

---

### Post by CodeNosher on 2008-10-21
I've been looking for this all day.

I think this is the best way I've found:

edit the gconf key:
/desktop/gnome/applications/terminal/exec

mine is:

gnome-terminal --geometry 80x39-0-0

Then I use:
/apps/metacity/global_keybindings/run_command_terminal

and set it to:
<Mod4><Hyper>t

Now I can use the 'Window' key to launch gnome-terminal with --geometry passed in!  You can pass in any arguments you like.

---

### Post by tiga2001 on 2008-11-25
That's what I did, as well. But it doesn't change the behavior when you make a new terminal window from within a gnome-terminal with <Ctrl><Shift>+N

---

### Post by ziusudra on 2009-04-14
You just need to edit this file:
/usr/share/vte/termcap/xterm
and to change the line:
:co#80:it#8:li#24:\

co is for column and li is for line, for example it is for me:
:co#110:it#8:li#24:\

---

### Post by chrisinspace on 2009-05-25
> **ziusudra said:**
> You just need to edit this file:
/usr/share/vte/termcap/xterm
and to change the line:
:co#80:it#8:li#24:\

co is for column and li is for line, for example it is for me:
:co#110:it#8:li#24:\

Worked perfectly for me.

---

### Post by tiga2001 on 2009-05-25
> **ziusudra said:**
> You just need to edit this file:
/usr/share/vte/termcap/xterm
and to change the line:
:co#80:it#8:li#24:\

co is for column and li is for line, for example it is for me:
:co#110:it#8:li#24:\

Also worked for me, I forgot to post that before :-?

---

### Post by psrivats on 2010-01-11
> **ziusudra said:**
> You just need to edit this file:
/usr/share/vte/termcap/xterm
and to change the line:
:co#80:it#8:li#24:\


I use keyboard shortcut (super+space) to launch terminal, and this is the only thing that works (tested in Ubuntu 9.10). Thank you!

---

### Post by towheedm on 2010-01-23
Ok now that we got that all sorted out, does anyone know how to change the default screen position that it opens at?  Without using Compiz or launchers?

---

### Post by linux_junky on 2010-01-28
**[COLOR=Red]Solved  by [B]ziusudra** - GREAT JOB!
[/COLOR][/B][I][I][COLOR=Red]You just need to edit this file:
/usr/share/vte/termcap/xterm
and to change the line:
```
:co#80:it#8:li#24:\
```[/COLOR][/I][/I]
> **towheedm said:**
> Ok now that we got that all sorted out, does anyone know how to change the default screen position that it opens at?  Without using Compiz or launchers?
1. Place the gnome-terminal window where you want it on the desktop.
2. In the terminal type: ```
xwininfo
```3. You will be asked to click on the window that you are looking for info on... click on the gnome-terminal window that you are using.
4. The last line of information presented is about the windows geometry... copy that info to the clipboard. eg: ```
...  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +940+23  -1283+23  -1283-888  +940-888
  **[COLOR=Red]-geometry 105x35+937+0[/COLOR]**
```5. Enter command or paste in bash script: ```
gnome-terminal -**[COLOR=Red]-geometry 105x35+937+0[/COLOR]**
```note: be careful to use two "-" for the geometry option when opening gnome-terminal

Good Luck.

---

### Post by Seth Kriticos on 2010-02-03
Go to System -> Preferences -> Preferred Applications -> System (tab)

Change terminal emulator to "Custom" from the dropdown and specify the command: gnome-terminal --geometry=160x50
And execution flag: -x

Done.

---

### Post by bitboy on 2010-02-19
Thanks! That worked like a charm for me.

bitboy


> **viscount said:**
> Does it annoy you that gnome-terminal does
not remember the size when you drag it around?

Well it annoyed me a lot so I went to #gnome and
finally got an answer, which can be found here:
[http://bugzilla.gnome.org/show_bug.cgi?id=155147](http://bugzilla.gnome.org/show_bug.cgi?id=155147)

You could rename the /usr/bin/gnome-termainal 
app then create a script with the proper geometry
and place it in /usr/bin/gnome-terminal like this:
~~~
#!/usr/bin/sh
gnome-terminal --geometry=80x15
~~~

But what I chose to do is just right click on the gnome-terminal
icon on my task bar, select propertys, then change the command to
**Command: gnome-terminal --working-directory=%f --geometry=80x15**

And its done, gnome-terminal will pop up with the size that I have
specified, however it still wont remember a size by dragging, but 
at least now I  know how to set its' default size.

Hope this helps.

---

### Post by JanNeggers on 2010-04-09
> **Seth Kriticos said:**
> Go to System -> Preferences -> Preferred Applications -> System (tab)

Change terminal emulator to "Custom" from the dropdown and specify the command: gnome-terminal --geometry=160x50
And execution flag: -x

Done.

Wow, this is by far the best method posted in this thread, TY, the reason is that I don't have root rights on this pc, and with this method I can still set the terminal as I want.

---

### Post by iqbal.shirol on 2010-06-03
In Ubuntu 8.04 the path:

/usr/share/vte/termcap/xterm

The default size is always 80 columns and 24 lines.
/usr/share/vte/termcap/xterm (part of the file is shown below)
You edit the default size by changing the line (displayed in bold below)

-----------
/usr/share/vte/termcap/xterm
-----------
# This is a cut-down version of the termcap file from my box with some entries
# removed (add them back in to override the terminal's behavior):
# kI (Insert, Delete is handled programmatically)
# kP/kN (Page Up, Page Down)
# ku/kd/kl/kr (Up, Down, Left, Right)
# k1/kd2/k3/k4/k5/k6/k7/k8/k9/k; (F1-F10)
# K1/K2/K3/K4/K5 (KP Up, Down, Left, Right, Begin)
xterm-xfree86|xterm-new|xterm terminal emulator (XFree86):\
	:am:km:mi:ms:xn:\
	**:co#80:it#8:li#24:\**   #change this line for your own default size
	:AL=\E[%dL[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]C=\E[%dP[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]L=\E[%dM[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]O=\E[%dB:IC=\E[%d@:\
	:LE=\E[%dD:\
	:RI=\E[%dC:UP=\E[%dA:ae=^O:al=\E[L:as=^N:bl=^G:bt=\E[Z:\
	:cd=\E[J:ce=\E[K:cl=\E[H\E[2J:cm=\E[%i%d;%dH:cr=^M:\
	:cs=\E[%i%d;%dr:ct=\E[3g:dc=\E[P:dl=\E[M:do=^J:ec=\E[%dX:\
	:ei=\E[4l:ho=\E[H:im=\E[4h:is=\E[!p\E[?3;4l\E[4l\E>:\
	:kD=\177:\

---

### Post by tiga2001 on 2010-06-03
I don't know about the previous versions of Ubuntu, I think up 'till Ubuntu 9.10 I've had to change /usr/share/vte/termcap/xterm . But in Ubuntu 10.4, I discovered that changing this doesn't work. Then I found out that there's actually an option in gnome-terminal for this. To change, start any gnome-terminal, then go to Edit->Profile Preferences, then change predetermined size. This probably changes some config or text file on the backend, but it's located in an easy place to find. I'm using Linux Mint 9 (Ubuntu 10.4) by the way, but I think the gnome-terminal is the same.

---

### Post by Foxcow on 2010-09-24
> **tiga2001 said:**
> ... Then I found out that there's actually an option in gnome-terminal for this. To change, start any gnome-terminal, then go to Edit->Profile Preferences, then change predetermined size. This probably changes some config or text file on the backend, but it's located in an easy place to find. I'm using Linux Mint 9 (Ubuntu 10.4) by the way, but I think the gnome-terminal is the same.



I had done this but just recently, within the past 3 days or so, my custom size reverted to default, and the option to change in preferences is no longer there.  I thought I was going crazy but I checked on both of my computers.

Can anyone else back me up on this?

---

### Post by McLowry on 2010-09-26
Same problem that Foxcow just described also appears here.

In gconf-editor I can see that my default profile's configuration still contains the settings for a bigger terminal window (default_size_columns, default_size_rows).

But gnome-terminal opens in an 80x24 window and the preferences dialog has no size settings anymore.

What is going on here?

EDIT: There is a bugreport (and some duplicates) about this problem:
[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/641616](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/641616)

---

### Post by matthew.ball on 2010-09-28
> **Seth Kriticos said:**
> Go to System -> Preferences -> Preferred Applications -> System (tab)

Change terminal emulator to "Custom" from the dropdown and specify the command: gnome-terminal --geometry=160x50
And execution flag: -x

Done.
I tried this, but rather than specifying a geometry size, I just used [FONT="Courier New"]gnome-terminal --maximize[/FONT]. Alas, nothing changed.

If anyone knows, is this also a result of the bug McLowry mentioned?

---

### Post by cviorel on 2010-09-29
Another solution is to use gconf:

```
gconftool-2 --set /apps/gnome-terminal/profiles/Default/default_size_columns --type integer 160
gconftool-2 --set /apps/gnome-terminal/profiles/Default/default_size_rows --type integer 50
```

---

### Post by terryroe on 2010-09-30
Has anyone noticed that as of the last automatic update that the default window size for profiles in gnome-terminal do not seem to work?  The options have disappeared from the profile settings and the settings from gconf don't seem to be taken into account either.  Is anyone else seeing this problem?

Thanks,

TR

---

### Post by Foxcow on 2010-09-30
> **terryroe said:**
> Has anyone noticed that as of the last automatic update that the default window size for profiles in gnome-terminal do not seem to work?  The options have disappeared from the profile settings and the settings from gconf don't seem to be taken into account either.  Is anyone else seeing this problem?

Thanks,

TR


Read the thread my friend :)

---

### Post by terryroe on 2010-09-30
> **Foxcow said:**
> Read the thread my friend :)

Thanks so much Foxcow.  Really pressed for time this morning and only scanned the early part of the thread and the last entry.  Wish I'd taken more time to read the thread.  Appreciate you pointing it out to me.

TR

---

### Post by Foxcow on 2010-10-10
It looks like we are back in business for 10.10.  The setting to easily define your default terminal size is back.

---

### Post by terryroe on 2010-10-13
> **Foxcow said:**
> It looks like we are back in business for 10.10.  The setting to easily define your default terminal size is back.

Does anyone know why we can't get this fix for Lucid Lynx, or how we can get it (without a lot of hassle)?

Thanks,

TR

---

### Post by ajgreeny on 2010-11-02
See post #22.  Change the default for xterm and gnome-terminal follows suit.

---

### Post by Foxcow on 2010-11-02
> **terryroe said:**
> Does anyone know why we can't get this fix for Lucid Lynx, or how we can get it (without a lot of hassle)?

Thanks,

TR

I think the easiest way to do it is the way that ajgreeny suggested.

Too bad it hasn't been patched for Lucid.

---

### Post by tiga2001 on 2010-11-20
> **iqbal.shirol said:**
> In Ubuntu 8.04 the path:

/usr/share/vte/termcap/xterm

The default size is always 80 columns and 24 lines.
/usr/share/vte/termcap/xterm (part of the file is shown below)
You edit the default size by changing the line (displayed in bold below)

-----------
/usr/share/vte/termcap/xterm
-----------
# This is a cut-down version of the termcap file from my box with some entries
# removed (add them back in to override the terminal's behavior):
# kI (Insert, Delete is handled programmatically)
# kP/kN (Page Up, Page Down)
# ku/kd/kl/kr (Up, Down, Left, Right)
# k1/kd2/k3/k4/k5/k6/k7/k8/k9/k; (F1-F10)
# K1/K2/K3/K4/K5 (KP Up, Down, Left, Right, Begin)
xterm-xfree86|xterm-new|xterm terminal emulator (XFree86):\
	:am:km:mi:ms:xn:\
	**:co#80:it#8:li#24:\**   #change this line for your own default size
	:AL=\E[%dL[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]C=\E[%dP[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]L=\E[%dM[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/biggrin.gif[/IMG]O=\E[%dB:IC=\E[%d@:\
	:LE=\E[%dD:\
	:RI=\E[%dC:UP=\E[%dA:ae=^O:al=\E[L:as=^N:bl=^G:bt=\E[Z:\
	:cd=\E[J:ce=\E[K:cl=\E[H\E[2J:cm=\E[%i%d;%dH:cr=^M:\
	:cs=\E[%i%d;%dr:ct=\E[3g:dc=\E[P:dl=\E[M:do=^J:ec=\E[%dX:\
	:ei=\E[4l:ho=\E[H:im=\E[4h:is=\E[!p\E[?3;4l\E[4l\E>:\
	:kD=\177:\
Remember that you have to log out and log back in for the modification to work. I'm using Linux Mint 9 (Ubuntu 10.04), and after an update, my terminals suddenly lost their settings, too. The place to change its size in Profile Preferences has also disappeared for me, but editing this file still worked for me.

---

### Post by bashologist on 2010-11-21
Here's the command I use when I reformat. Just type this command then add the terminal app to your panel from the applications menu.
```

sudo perl -p -i.bak -e 's/(?<=^Exec=).*/gnome-terminal --hide-menubar --geometry 200x40+153+184/' /usr/share/applications/gnome-terminal.desktop

```
You can remove the --hide-menubar part or add whatever kinda options you prefer.

---

### Post by tiga2001 on 2010-11-21
> **bashologist said:**
> Here's the command I use when I reformat. Just type this command then add the terminal app to your panel from the applications menu.
```

sudo perl -p -i.bak -e 's/(?<=^Exec=).*/gnome-terminal --hide-menubar --geometry 200x40+153+184/' /usr/share/applications/gnome-terminal.desktop

```
You can remove the --hide-menubar part or add whatever kinda options you prefer.
That only works when you open the terminal by double-clicking on the icon, though. It doesn't work if you use the Ctrl+Shift+N keyboard shortcut.

---

### Post by mipper on 2010-12-19
The easiest way I've found of doing this is to use gconf-editor.  In a terminal...

[FONT="Courier New"]$ gconf-editor[/FONT]

Select /apps/gnome-terminal/profiles/Default

Then change the following values:

[FONT="Courier New"]default_size_columns
default_size_rows[/FONT]

and then tick the following:

[FONT="Courier New"]use_custom_default_size[/FONT]

It was the last bit that took some time to find.

Hope this helps.  There's tons of stuff in this tool if you spend a bit of time exploring.

Regards,

mipper

---

### Post by terryroe on 2010-12-19
This is fixed in Maverick Meerkat.  All is well.

TR

---

### Post by antiplex on 2011-01-30
i tried editing /usr/share/vte/termcap/xterm (restart needed) but finally preferred the solution of seth on my system running 10.04:

> **Seth Kriticos said:**
> Go to System -> Preferences -> Preferred Applications -> System (tab)

Change terminal emulator to "Custom" from the dropdown and specify the command: gnome-terminal --geometry=160x50
And execution flag: -x

Done.

so thanks a lot for sharing this!
i was looking for a solution working with shortcuts (ctrl alt t) as well as the toolbar-icon. both seems to work fine now.

---

### Post by SirGe on 2011-03-27
Changing the Preferred Application works only for things that play well with the Gnome desktop - in my case, it worked fine for Compiz'es Ctl-Alt-T binding, but did nothing for Cairo-dock, application menus, etc. 

I spent a few minutes looking to see how to use the Gnome's preferred Application binding, but could not find it quickly - could be the reason why other things, including Gnome's own menus do not play well with it...

I solved the problem the old-fashioned way. Since menu launchers and other things, that launch a terminal, do not specify an explicit path and since I wanted to do this only for my own login, it was sufficient to add a file called *gnome-terminal* to ~/bin:

```
exec /usr/bin/gnome-terminal --geometry 80x50 $*
```

My ~/bin is in my PATH, of course. I am assuming since you are using a command line/window, there is no mystery in how to add things to your PATH... But feel free to prove me wrong; I will explain.

Now the terminal launches with bigger size from everywhere.

I noticed that there is no */etc/alternatives* entry for 'terminal', would seems like a good idea. There is one for 'x-terminal', which points to */usr/bin/gnome-terminal.wrapper*. This comes straight from the *gnome-terminal* and is a perl script, that seems to do a some additional parsing for *gnome-terminal*, but it did not seem to add any obvious value in this case...

Since all the launchers, menus, etc. use "gnome-terminal", there is not much point in playing with the *alternatives* link.

---

