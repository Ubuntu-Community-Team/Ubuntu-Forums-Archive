---
title: "dwm Primer"
date: 2009-01-29
forum: Outdated Tutorials &amp; Tips
---

### Post by binarymutant on 2009-01-29
[IMG]http://farm4.static.flickr.com/3160/2955033107_956bb3c729_d.jpg[/IMG]

After an epic search for the ultimate window manager I stumbled upon dwm (Dynamic Window Manager). At only 2000 lines of pure C code I was instantly hooked. But, because of the lack of community documentation and the self proclaimed elitist userbase, dwm is rarely talked about around the Ubuntu world. Here is a primer for dwm in hopes that it will create a discussion around this great tool and maybe some more tips about customizing it. 

**Concepts:**

The core idea behind all tiling window managers is the idea of productivity. Tiling window managers increase productivity by almost never having the user remove their hands from the keyboard. Since all tasks are visible on the screen, another method of increasing computing efficiency is automatic window placement. The more popular window managers stack windows on top of each other and block access to tasks in the background. This causes the user to waste valuable time having to physically move the mouse in order to see the blocked task or risks having the user becoming distracted with the new window and possibly forgetting about the original task all together. With automatic window placement the screen is divided up into a "master" area on one side and a "stack" area on the other. When a new window is created it spawns in the "master" area and all the other windows move to the stack area. 

**Installation:**

There are a couple of ways to get dwm. The easiest being to go to  [http://www.suckless.org/dwm/]("http://www.suckless.org/dwm/") and download the tarball or simply
```
wget http://code.suckless.org/dl/dwm/dwm-5.3.1.tar.gz
```
After the tarball is downloaded, extract it with
```
tar -xzf dwm-5.3.1.tar.gz
```
A way to stay current with dwm's development is to use Mercurial, a verson control system similar to git. All development of dwm is done through Mercurial. So, if Mercurial is installed, get a working copy of the dwm repository with
```
hg clone http://code.suckless.org/hg/dwm
```

**Dependencies**
In order to get all the dependencies for building and running dwm simply do
```
sudo apt-get install build-essential libx11-dev libxinerama-dev sharutils
```

**Configuration:**

To stay simple and lightweight dwm must be compiled in order to work. To compile dwm change to the dwm installation directory and
```
make
```
```
sudo make install
```
Any changes made to dwm requires recompiling. Once dwm is compiled the last remaining obstacle to using it is the login manager. Create a new file called dwm.desktop and add this to the text
> 
   [Desktop Entry]
   Encoding=UTF-8
   Name=dwm
   Comment=This session starts dwm
   Exec=/usr/local/bin/dwm
   Type=Application

Save dwm.desktop to /usr/share/xsessions/ and your ready to login to dwm :) 
```
sudo mv dwm.desktop /usr/share/xsessions/
```
If your not using a login manager, just add this line to .xinitrc
> exec dwm
and then you will be able to use dwm with the startx command. The default dwm is a little ugly, and the keybinds are a little strange at first. Alt+Shift+Enter will bring up a new terminal. Bring up more than 2 terminals and the default tiling layout will begin to show. Alt+F changes the layout to floating and Alt+M will change the layout to monocle or fullscreen. The strange icon on the top left side of the status bar will cycle through layouts when clicked. The default dwm is pretty ugly to my eyes, but with a little customization the glossy shine of it can come out.

Customization:

Customizing dwm is the best part of the tiling window manager experience! Those default keybinds are awkward to me and frankly the colors aren't too appealing. All the customizable parts of dwm are located in a file called config.def.h. Copying config.def.h to a new file called config.h will safely let you edit the customizations while still having a way to revert back to the defaults. 
```
cp config.def.h config.h
```
The config.h should look like this
```

/* See LICENSE file for copyright and license details. */

/* appearance */

static const char font[]            = "-*-terminus-medium-r-normal-*-14-*-*-*-*-*-*-*";
static const char normbordercolor[] = "#cccccc";
static const char normbgcolor[]     = "#cccccc";
static const char normfgcolor[]     = "#000000";
static const char selbordercolor[]  = "#0066ff";
static const char selbgcolor[]      = "#0066ff";
static const char selfgcolor[]      = "#ffffff";
static unsigned int borderpx        = 1;        /* border pixel of windows */
static unsigned int snap            = 32;       /* snap pixel */
static Bool showbar                 = True;     /* False means no bar */
static Bool topbar                  = True;     /* False means bottom bar */
static Bool readin                  = True;     /* False means do not read stdin */
static Bool usegrab                 = False;    /* True means grabbing the X server
                                                   during mouse-based resizals */

/* tagging */
static const char tags[][MAXTAGLEN] = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };
static unsigned int tagset[] = {1, 1}; /* after start, first tag is selected */

static Rule rules[] = {
	/* class      instance    title       tags mask     isfloating */
	{ "Gimp",     NULL,       NULL,       0,            True },
	{ "Firefox",  NULL,       NULL,       1 << 8,       True },
};

/* layout(s) */
static float mfact      = 0.55; /* factor of master area size [0.05..0.95] */
static Bool resizehints = True; /* False means respect size hints in tiled resizals */

static Layout layouts[] = {
	/* symbol     arrange function */
	{ "[]=",      tile },    /* first entry is default */
	{ "><>",      NULL },    /* no layout function means floating behavior */
	{ "[M]",      monocle },
};

/* key definitions */
#define MODKEY Mod1Mask
#define TAGKEYS(KEY,TAG) \
	{ MODKEY,                       KEY,      view,           {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask,           KEY,      toggleview,     {.ui = 1 << TAG} }, \
	{ MODKEY|ShiftMask,             KEY,      tag,            {.ui = 1 << TAG} }, \
	{ MODKEY|ControlMask|ShiftMask, KEY,      toggletag,      {.ui = 1 << TAG} },

/* helper for spawning shell commands in the pre dwm-5.0 fashion */
#define SHCMD(cmd) { .v = (const char*[]){ "/bin/sh", "-c", cmd, NULL } }

/* commands */
static const char *dmenucmd[] = { "dmenu_run", "-fn", font, "-nb", normbgcolor, "-nf", normfgcolor, "-sb", selbgcolor, "-sf", selfgcolor, NULL };
static const char *termcmd[]  = { "uxterm", NULL };

static Key keys[] = {
	/* modifier                     key        function        argument */
	{ MODKEY,                       XK_p,      spawn,          {.v = dmenucmd } },
	{ MODKEY|ShiftMask,             XK_Return, spawn,          {.v = termcmd } },
	{ MODKEY,                       XK_b,      togglebar,      {0} },
	{ MODKEY,                       XK_j,      focusstack,     {.i = +1 } },
	{ MODKEY,                       XK_k,      focusstack,     {.i = -1 } },
	{ MODKEY,                       XK_h,      setmfact,       {.f = -0.05} },
	{ MODKEY,                       XK_l,      setmfact,       {.f = +0.05} },
	{ MODKEY,                       XK_Return, zoom,           {0} },
	{ MODKEY,                       XK_Tab,    view,           {0} },
	{ MODKEY|ShiftMask,             XK_c,      killclient,     {0} },
	{ MODKEY,                       XK_t,      setlayout,      {.v = &layouts[0]} },
	{ MODKEY,                       XK_f,      setlayout,      {.v = &layouts[1]} },
	{ MODKEY,                       XK_m,      setlayout,      {.v = &layouts[2]} },
	{ MODKEY,                       XK_space,  setlayout,      {0} },
	{ MODKEY|ShiftMask,             XK_space,  togglefloating, {0} },
	{ MODKEY,                       XK_0,      view,           {.ui = ~0 } },
	{ MODKEY|ShiftMask,             XK_0,      tag,            {.ui = ~0 } },
	TAGKEYS(                        XK_1,                      0)
	TAGKEYS(                        XK_2,                      1)
	TAGKEYS(                        XK_3,                      2)
	TAGKEYS(                        XK_4,                      3)
	TAGKEYS(                        XK_5,                      4)
	TAGKEYS(                        XK_6,                      5)
	TAGKEYS(                        XK_7,                      6)
	TAGKEYS(                        XK_8,                      7)
	TAGKEYS(                        XK_9,                      8)
	{ MODKEY|ShiftMask,             XK_q,      quit,           {0} },
};

/* button definitions */
/* click can be a tag number (starting at 0),
 * ClkLtSymbol, ClkStatusText, ClkWinTitle, ClkClientWin, or ClkRootWin */
static Button buttons[] = {
	/* click                event mask      button          function        argument */
	{ ClkLtSymbol,          0,              Button1,        setlayout,      {0} },
	{ ClkLtSymbol,          0,              Button3,        setlayout,      {.v = &layouts[2]} },
	{ ClkWinTitle,          0,              Button2,        zoom,           {0} },
	{ ClkStatusText,        0,              Button2,        spawn,          {.v = termcmd } },
	{ ClkClientWin,         MODKEY,         Button1,        movemouse,      {0} },
	{ ClkClientWin,         MODKEY,         Button2,        togglefloating, {0} },
	{ ClkClientWin,         MODKEY,         Button3,        resizemouse,    {0} },
	{ ClkTagBar,            0,              Button1,        view,           {0} },
	{ ClkTagBar,            0,              Button3,        toggleview,     {0} },
	{ ClkTagBar,            MODKEY,         Button1,        tag,            {0} },
	{ ClkTagBar,            MODKEY,         Button3,        toggletag,      {0} },
};
[/QUOTE]
It might look daunting to edit but it's really very simple. It may be written in C but knowing how to program is not required. The /* Appearance */ section defines the look and feel of dwm. The /* Tagging */ section defines windows rules, The /* Layout(s) */ section defines the layouts and everything under the /* Key definitions */ section defines your mouse and key bindings. To change the colors used by dwm edit these variables
> 
static const char normbordercolor[] = "#cccccc";
static const char normbgcolor[]     = "#cccccc";
static const char normfgcolor[]     = "#000000";
static const char selbordercolor[]  = "#0066ff";
static const char selbgcolor[]      = "#0066ff";
static const char selfgcolor[]      = "#ffffff";

```
The variable name comes first, example: normbordercolor[] = "#cccccc"; is the color for the normal border color. It is set to grey in this example. Change the "#cccccc" to the color you want. You can use any hexidecimal color, more commonly called html color codes. On the left side of the default status bar the numbers one through nine are displayed. If clicked these numbers switch virtual desktops. Moving windows to the other virtual desktops is as easy as hitting Alt+Shift+1-9. To change the virtual desktops names from numbers to something more familiar, edit the line under the /* Tagging */ section that looks like
[QUOTE]
static const char tags[][MAXTAGLEN] = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };

I personally use these names in my own config.h but use whatever suits your needs
> 
static const char tags[][MAXTAGLEN] = { "Main", "Web", "More" };

My example shows the second virtual desktop called Web because I tag my browser windows to it. The /* Tagging */  section in config.h also provides a way to control and move  new windows. For instance both Firefox and Gimp are floating, Firefox will spawn on virtual desktop 9 and Gimp will spawn wherever it's started from.
> 
static Rule rules[] = {
	/* class      instance    title       tags mask     isfloating */
	{ "Gimp",     NULL,       NULL,       0,            True },
	{ "Firefox",  NULL,       NULL,       1 << 8,       True },
};

Further down, 
> 
/* key definitions */
#define MODKEY Mod1Mask

The MODKEY is set to Alt by default and every key binding for dwm starts with the MODKEY. In order to change the MODKEY from Alt to the Windows Key replace the Mod1Mask to Mod4Mask. If urxvt is the terminal of choice instead of xterm edit the line
> 
static const char *termcmd[]  = { "uxterm", NULL };

Many people create patches for dwm and share them on the developer's [URL
=http://lists.suckless.org/dwm/]mailing list[/URL]. The patch I like a lot is the fibonacci patch [http://www.aplusbi.com/dwm/dwm-5.2-fibonacci.diff]("http://www.aplusbi.com/dwm/dwm-5.2-fibonacci.diff") because it makes the "Stack" area spiral :)
To apply the fibonacci patch download the diff into the dwm installation directory, be aware that this patch changes config.def.h and not config.h
```

patch -p1 config.def.h dwm-5.2-fibonacci.diff

```
If you notice the right side of the status bar has an "EOF" it's because GDM and other login managers close standard output to dwm before executing it. To replace the "EOF" with a clock create a new file and add this text to it
> 
while true
do
echo `date`
sleep 1
done | dwm

Save it somewhere and make it executable with this command
```
chmod a+x filename
```
Go back and edit /usr/share/xsessions/dwm.desktop to execute the newly created file
> 
   [Desktop Entry]
   Encoding=UTF-8
   Name=dwm
   Comment=This session starts dwm
   Exec=/home/username/filename
   Type=Application


**More Links:**
[http://wiki.archlinux.org/index.php/Dwm]("http://wiki.archlinux.org/index.php/Dwm")
[http://ubuntuforums.org/showthread.php?t=642808]("http://ubuntuforums.org/showthread.php?t=642808")

Hopefully this primer will get anyone ready to start using dwm and share any other knowledge they pick up elsewhere.

---

### Post by InfinityCircuit on 2009-01-29
It might be easier to just compile from the Debian source:

```
sudo aptitude install devscripts debian-keyring
sudo aptitude build-dep dwm
dget -x http://ftp.debian.org/debian/pool/main/d/dwm/dwm_5.3.1-2.dsc
cd dwm-5.3.1
debuild
sudo debi
```

In this case, Intrepid has the same version as Debian Sid, so this step isn't even necessary.

The Debian source has a very nice feature that lets you define custom configs and patches inside the debian/ directory while maintaining a pristine upstream source.

Some other links: [http://www.suckless.org/dwm/tutorial.html](http://www.suckless.org/dwm/tutorial.html)

In general, the homepage is now a lot less elitist and has a lot more information than before.

---

### Post by BoneKracker on 2009-02-11
Gee, in Gentoo, it's just:```
emerge dwm
```
Also, your configuration changes get saved so they don't get wiped out by updates.  (This may not be the case in Ubuntu, unless you follow InfinityCircuit's guidance; so make sure you back up your edits to the 'config.h' header file somewhere so you can restore them if they get nuked but an update.)

Good tips above!  Here are a couple more to help get started.  This is a system-wide Xsession you can use (I don't recall where this goes in Ubuntu):
```
#!/bin/sh

# call user status message script or use default

DIR=${HOME}/.dwm
if [ -f "${DIR}"/dwmrc ]; then
        /bin/sh "${DIR}"/dwmrc &
else
    while true; do
        xsetroot -name "$(date +"%a %b %-e %T")"
        sleep 1
    done &
fi

# start terminal emulation daemon
/usr/bin/urxvtd -q -o -f

# start window manager
exec /usr/bin/dwm
```
That will pump the date and time to the status area of the window manager, unless the user has created their own ~/.dwm/dwmrc file (in which case it will execute that instead).  Note: if you see references to dwm reading status text on stdin, that's no longer correct; starting with version 5.4 you do this with xsetroot as shown above.

Most people won't want that "terminal emulation daemon" line.  It's there because I use unicode-rxvt in daemon mode instead of the slow memory-hog xterm.  That line starts urxvtd (daemon), which is then shared by multiple urxvtc (client) terminals.  This significantly reduces the amount of memory required to have multiple X terminals open*.  If you don't intend to use urxvtd/urxvtc, just delete those two lines.

Here's an example of a per-user status generator script (such as would be called by the system-wide xsession above):
```
# ~/.dwm/dwmrc
# Purpose: called by /etc/X11/Sessions/dwm.
# send status text to be displayed at the top of the window

while true; do
        xsetroot -name "Load: $(uptime | sed 's/.*,//') \
                $(date +"%a %b %-e %-I:%M:%S %p")"
        sleep 1
done
```
You can have it send whatever text you want, at whatever frequency you want, and it will be shown in the dwm "bar".  For example, you could have it show number of unread emails, wireless signal strength, cpufreq, and hddtemp.  Whatever you can code that will come out as a single string that will fit.

*To use a terminal emulator other than xterm, you have to replace "uxterm" in config.h with whatever you want to use.  In my case, as shown above, I have the urxvtd daemon started by my Xsession script (that way it automatically dies when I end my X session).  That takes care of the terminal daemon, but what about the terminal client?  By default, when you press 'Mod1 Enter', dwm will launch xterm (called as 'uxterm' to get unicode support).  Since I want it to start urxvtc (the unicode-rxvt client) instead, I replaced this line in config.h:
```
static const char *termcmd[]  = { "uxterm", NULL };
```
with this:
```
static const char *termcmd[]  = { "urxvtc", NULL };
```

It's that simple.  That goes for whatever terminal emulator you choose.  Most don't have a "daemon mode", so you don't have to worry about starting it in your xsession.  You just need to change "uxterm" in config.h to whatever terminal emulator you want to use, as above.  While xterm is very standard and works great, it's slow and it's a memory hog, so use it's probably a good idea to use something else.

To use any variant of xterm (xterm, rxvt, urxvt, mrxvt, aterm, Eterm, wterm, etc.), you have to set up some decent X resources.  Otherwise it will look like dog-poo.  How you do this is up to you.  You can research X resources for your terminal emulator of choice on the web, and you can read about X resources in the man pages for xterm and X.  But here is one approach:

Instead of using an ~/.Xdefaults file (the old way), I use the X resources manager to make the settings available to all X applications, including remote ones.  To do this, I put default settings for my terminal emulator of choice (e.g. urxvt) in my system-wide Xresources file.  I also put my own customizations in a ~/.Xresources file.  I also put a copy of the system-wide defaults in a ~/.Xresources file in /etc/skel, so each new user will automatically get a copy when I 'adduser').  That gives them a basis upon which to begin customizing.  If they delete their ~/.Xresources file, it falls back to the system-wide default Xresources file.  It's also not a bad idea to have settings in there for xterm as well, so it can be used comfortably as a fall-back if your terminal emulator of choice isn't working.  Here is an example:

```
!Xft settings:

! most people should have 96 here
Xft*dpi:                98
Xft*hinting:            true
! hintstyle 3 for flat-panel displays 
Xft*hintstyle:          2
Xft*antialias:          true
! uncomment/adjust for flat-panel display
!Xft*rgba:              rgb

! URxvt settings

URxvt*font: xft:Bitstream Vera Sans Mono:pixelsize=13
!URxvt*font: xft:Bitstream Vera Sans Mono:size=9
!URxvt*font: x:-*-fixed-medium-r-normal-*-14-*-*-*-*-*-*-*

URxvt*loginShell: true
URxvt*scrollstyle: plain
URxvt*scrollBar: true
URxvt*scrollBar_right: true
URxvt*termName: rxvt

URxvt*background: #000010
URxvt*foreground: #ffffff
URxvt*cursorColor: magenta
URxvt*color0: #000000
URxvt*color1: #9e1828
URxvt*color2: #aece92
URxvt*color3: #968a38
URxvt*color4: #414171
URxvt*color5: #963c59
URxvt*color6: #418179
URxvt*color7: #bebebe
URxvt*color8: #666666
URxvt*color9: #cf6171
URxvt*color10: #c5f779
URxvt*color11: #fff796
URxvt*color12: #4186be
URxvt*color13: #cf9ebe
URxvt*color14: #71bebe
URxvt*color15: #ffffff

! XTerm settings:

XTerm*faceName: Bitstream Vera Sans Mono
XTerm*faceSize: 10
!XTermfont: xft:Bitstream Vera Sans Mono:pixelsize=14
XTerm*background: #000010
XTerm*foreground: #ffffff
XTerm*cursorColor: magenta
XTerm*color0: #000000
XTerm*color1: #9e1828
XTerm*color2: #aece92
XTerm*color3: #968a38
XTerm*color4: #414171
XTerm*color5: #963c59
XTerm*color6: #418179
XTerm*color7: #bebebe
XTerm*color8: #666666
XTerm*color9: #cf6171
XTerm*color10: #c5f779
XTerm*color11: #fff796
XTerm*color12: #4186be
XTerm*color13: #cf9ebe
XTerm*color14: #71bebe
XTerm*color15: #ffffff
```

One way to get around messing with all that scary X windows stuff is to use a relatively light libvte-based terminal, such as sakura.  I'm sure Debian/Ubuntu have it in their repos.  Just install it, and in config.h replace "uxterm" with "sakura", or "lxTerminal" or whatever you choose.  Then you don't need all that foo*color stuff in .Xresources (and depending on how Ubuntu has things set up, you probably don't need to mess with X resources at all). The libvte approach is nowhere near as light as urxvtd/urxvtc, but it's lighter than xterm, and it's simple.  There are a number of libvte-based terminal emulators available, which you can find by searching the web.  The terminals included in Rox and Xfce4 are also reasonably light and libvte-based.

In my opinion, the lightest, fastest way to go, if you often use multiple terminals simultaneously, is the urxvtd/urxvtc method I've shown. (And I think most tiling wm users probably do use multiple terminals frequently.)  But to each his own.

The approach I've described above allows you to establish a working system-wide configuration with defaults for multiple users while also accommodating the preferences of individual users.  There are many different ways to go (including not having a system-wide Xsession and just having your own ~/.xinitrc file).  This post is not intended to show how to set up X, just to show a way to get started with dwm.  The main points here are how to send status text to the window manager, how to use something other than xterm, and how to provide for system-wide and user-specific settings.  The rest is context.

Also, another very similar and excellent window manager is wmii, which is written by the same author.  I find dwm is a tad lighter and wmii is more flexible and featureful.  Both are extremely light and fast.  Other popular tiling window managers include Xmonad, ion3, and Awesome.  And a recent addition similar to dwm is scrotwm, which I haven't tried.

Somebody may need to correct some of what I've said to adapt it to Ubuntu, which I haven't used in a couple years.  Please feel free.

Enjoy!  Fight the bloat!

---

### Post by adamlau on 2009-02-19
This is what my .xinitrc looks like (not sure what the Ubuntu equivalent is, but the following provides a simple framework to work with):

```
#!/bin/sh

xscreensaver -no-splash &
/usr/local/bin/urxvtd -q -f -o &
#xsetroot -name "$(date + "%a %b %d %l:%M %p")"; sleep 1m; done &
export OPERAPLUGINWRAPPER_PRIORITY=0
exec /usr/local/bin/dwm
```

[IMG]http://i275.photobucket.com/albums/jj281/adamchrista/Screenshots/archdwmurxvt-29.png[/IMG]

---

### Post by sarah.fauzia on 2009-03-20
This is an amazing thread. I just downloaded dwm (on ArchLinux), and even though the ArchLinux documentation is good, I still have some questions. Like how to pipe urxvt into the status bar, for instance? I've figured out conky, and I'm beginning to really enjoy using dwm. I've read that, "once you go tiling, you never go back." :)

This thread needs more attention, and a sticky.

---

### Post by binarymutant on 2009-03-22
> **sarah.fauzia said:**
> Like how to pipe urxvt into the status bar, for instance?
I'm still not sure how to do this unfortunately, I had a script that did this but I ended up deleting it without backing it up. I think it made a FIFO pipe and it worked liked awesomewm's awesome-client file. If I ever run across this again, I'll post it here. Hopefully someone else will know how.

---

### Post by keithpeter on 2009-05-23
I'm ressurecting this thread because I'm trying to compile dwm.

What do I need to install on 9.04 Jaunty cli environment to compile dwm?

I've got build-essentials, but what else do I need (make currently fails)

cheers

---

### Post by binarymutant on 2009-05-23
> I've got build-essentials, but what else do I need (make currently fails)

Get these dependencies too libx11-dev, libxinerama-dev, sharutils 
Thanks, you won't regret compiling dwm :)

---

### Post by keithpeter on 2009-05-23
> **binarymutant said:**
> Get these dependencies too libx11-dev, libxinerama-dev, sharutils 
Thanks, you won't regret compiling dwm :)

Thanks, dwm compiled without errors bit now. For future reference

```
sudo aptitude install build-essential ibx11-dev libxinerama-dev sharutils 
```

Removed the repository version of dwm and ran sudo make install, edited the .xinitrc file as suggested and greeted with X server giving up type messages. Then realised I had 'exec dwm &' in the .xinitrc file, so changed that and it works fine. 

Do I need to have dmenu already installed or does it arrive with dwm?

*Fun all this isn't it? I mean, you can't imagine being able to alter the whole user interface in Wndows can you?*

Cheers

---

### Post by binarymutant on 2009-08-02
dmenu is packaged seperately in dwm-tools
sudo apt-get install dwm-tools

---

### Post by Cortux on 2009-09-10
> **binarymutant said:**
> dmenu is packaged seperately in dwm-tools
sudo apt-get install dwm-tools
 
 
Is this command good enough for newbies, i cant understand what everyone said before this. Is DWM only for terminal use? Even if it is, I just want it.

---

### Post by binarymutant on 2009-09-10
dwm is like Gnome or KDE, a very good Window Manager. dwm-tools is a collection of scripts and apps for dwm. For more information please see: [http://www.suckless.org/dwm/]("http://www.suckless.org/dwm/")

---

### Post by Cortux on 2009-09-11
> **binarymutant said:**
> dwm is like Gnome or KDE, a very good Window Manager. dwm-tools is a collection of scripts and apps for dwm. For more information please see: [http://www.suckless.org/dwm/](http://www.suckless.org/dwm/)
 
Is there a similar application that I can use in Gnome, I saw someones desktop who had a simalar feature where he had a number of windows evenly spaced out and when he selected one of them it increased in size to fit the whole screen. Although I think he was using KDE, I hope there is something simalar in Gnome.

---

### Post by binarymutant on 2009-09-11
Personally, I've never heard of anything like that sorry. There might be a compiz plugin or something that does tiling though, but I'm unsure :/

---

### Post by Cortux on 2009-09-11
> **binarymutant said:**
> Personally, I've never heard of anything like that sorry. There might be a compiz plugin or something that does tiling though, but I'm unsure :/
 
 
Ok, Thanks.
 
If I get to meet that guy again, hopefully soon. I will ask him.

---

