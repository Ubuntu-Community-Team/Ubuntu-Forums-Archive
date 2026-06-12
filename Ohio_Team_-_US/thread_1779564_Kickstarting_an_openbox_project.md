---
title: "Kickstarting an openbox project"
date: 2011-06-10
forum: Ohio Team - US
---

### Post by skellat on 2011-06-10
So, what would it take for an openbox-desktop metapackage to be created?

---

### Post by canthus13 on 2011-06-10
I'm not really sure... I'll be looking into that after I mow the lawn tomorrow.

Jason

---

### Post by canthus13 on 2011-06-10
Hmm.. at first glance, it appears that the first step is to put together the exact system we want.  Once I have a machine dedicated to this, I can do a clean install from a minimal CD and add exactly what we want.  The hard part with this is that several packages we'd need are not included in the repos, so we'd have to build and maintain the packages as well.

Jason

---

### Post by skellat on 2011-06-10
There's likely going to need to be some PPA action then?

---

### Post by canthus13 on 2011-06-10
At first, but the packages will have to make it into the repos eventually.

---

### Post by skellat on 2011-06-12
Are there any hardware needs on your end, canthus13, that would need to be met before building could take place?

---

### Post by canthus13 on 2011-06-12
A hard drive... ~20gb would be perfect. other than that, I've got a machine that will do just fine.  My old sauerbraten server (which didn't die after all... It decided to boot back up) will be the guinea pig.  I'll need to scare up another mouse as well, but I think I have one lurking around somewhere.  as soon as I have that, I can start with a minimal CD and pull things together to build a first draft, so to speak.  I've got most of the packages and features I want already set up on my main system, but it was built on a gnome install, so I'm not quite sure what needs to stay and what can go.

Jason

---

### Post by canthus13 on 2011-06-17
Ok.  Now that I've got 10.04 working in vmware player (11.04 wouldn't work...), here's a starting setup.  I installed the 10.04 mini cd with *NO* packages selected. All of these packages so far are available in the repos, and will get you to where I am with little effort other than adding stuff to autostart and rc.xml

```
openbox                 # Openbox.
xinit                   # This installs a host of other packates that get Xorg up and running
gnome-terminal          # Most other terminals I've tested don't pass control characters properly to applications running inside
tint2                   # task list/clock/tasktray
wicd                    # network configuration tool 
nitrogen                # wallpaper manager
gmrun                   # This gives us our alt-f2 box
chromium-browser        # not much to say here... it's a web browser.
obmenu                  # openbox menu configuration tool
obconf                  # openbox configuration
slim                    # login manager -May change to lightdm once I can install natty on a regular machine as slim doesn't support remote login
```


~/.config/openbox/autostart.sh
```
# Run the system-wide support stuff
. $GLOBALAUTOSTART
# Programs to launch at startup
tint2 &				# Taskbar and tasktray
nitrogen --restore & 		# Restore the background
wicd-client & 			# wicd Network manager
```

insert this into ~/.config/openbox/rc.xml under <!-- Keybindings for window switching -->

```
<keybind key="A-F2">
      <action name="execute">
        <execute>gmrun</execute>
      </action>
    </keybind>

```

If you want the menu.xml, I'll post that too.

---

### Post by canthus13 on 2011-06-18
I now have tint2 0.11 working on my main machine after some initial issues caused by stupid default behavior.  Next step is to package it, which is something I've never done before...

Jason

---

### Post by canthus13 on 2011-06-18
Just a quick note -  I've started up ##openbox-desktop on freenode to kind of keep the discussion from taking over the LoCo channel.

---

### Post by skellat on 2011-06-21
I nominate leafpad for the GUI text editor.  nano remains essential too.

---

### Post by canthus13 on 2011-06-21
nano is included on the mini CD... it's part of the base install. :)

--Jason

---

### Post by skellat on 2011-06-21
> **canthus13 said:**
> nano is included on the mini CD... it's part of the base install. :)

Adding leafpad in lieu of gedit or mousepad would be good, then.

---

### Post by skellat on 2011-06-21
Picking applications for this gets interesting.

Applications need to be in the main repos and not in a PPA.  The worst thing to have happen is to have to span multiple PPAs...or make a huge honkin' PPA to cover everything.

The working proposed list of GUI apps for this is so far:

Media player -- VLC
Text editor -- leafpad
Word processor -- abiword
Spreadsheet -- gnumeric
Image Viewer -- gpicview or feh
Terminal -- ???

---

### Post by canthus13 on 2011-06-21
Ok... for the calendar, install gsimplecal and then edit /.config/tint2/tint2rc, adding clock_lclick_command = gsimplecal under the # Clock heading.

--Jason

---

### Post by skellat on 2011-06-21
It appears that gsimplecal needs packaging.  The upstream code can be found at [https://github.com/dmedvinsky/gsimplecal](https://github.com/dmedvinsky/gsimplecal)

---

### Post by skellat on 2011-06-21
The working proposed list of GUI apps for this is so far:

 Media player -- VLC
 Text editor -- leafpad
 Word processor -- abiword
 Spreadsheet -- gnumeric
 Image Viewer -- gpicview or feh
 Terminal -- ???
 File manager -- nautilus

:guitar:

---

### Post by canthus13 on 2011-06-25
I've got the base system installing on the test machine right now.  6GB is a bit tight, but it'll do for the moment.

---

### Post by bodhi.zazen on 2011-07-01
s/gmrun/dmenu
s/chromium/midori
s/gnome-terminal/sakura

And I would add lxappearance to the config tools

---

### Post by skellat on 2011-07-01
Current List

```
openbox                 # Openbox.
xinit                   # This installs a host of other packates that get Xorg up and running
gnome-terminal          # Most other terminals I've tested don't pass control characters properly to applications running inside
tint2                   # task list/clock/tasktray
wicd                    # network configuration tool 
nitrogen                # wallpaper manager
gmrun                   # This gives us our alt-f2 box
chromium-browser        # not much to say here... it's a web browser.
obmenu                  # openbox menu configuration tool
obconf                  # openbox configuration
slim                    # login manager -May change to lightdm once I can install natty on a regular machine as slim doesn't support remote login
VLC                     # Media player
leafpad                 # Text editor
abiword                 # Word Processor
gnumeric                # Spreadsheet
gpicview		# Image viewer
```

After suggestions from Bodhi Zazen and myself, the new proposed list:

```
openbox                 # Openbox.
xinit                   # This installs a host of other packates that get Xorg up and running
sakura                  # Most other terminals I've tested don't pass control characters properly to applications running inside
tint2                   # task list/clock/tasktray
wicd                    # network configuration tool 
nitrogen                # wallpaper manager
dmenu                   # This will require packaging.  Upstream seems to be here: http://tools.suckless.org/dmenu/
midori                  # More traditional browser based on webkit
obmenu                  # openbox menu configuration tool
obconf                  # openbox configuration
slim                    # login manager -May change to lightdm once I can install natty on a regular machine as slim doesn't support remote login
VLC                     # Media player
leafpad                 # Text editor
abiword                 # Word Processor
gnumeric                # Spreadsheet
gpicview		# Image viewer
aria2			# Download manager
sshfs			# Gets around needing gigolo or other tools to mount SFTP
pcmanfm-nohal		# File manager
apt-offline		# Offline package management tool.  Need to package the latest version possibly.  See: http://apt-offline.alioth.debian.org/
apt-offline-gui		# GUI front-end for offline package management tool.  Need to package the latest version possibly.  See: http://apt-offline.alioth.debian.org/
evince			# PDF viewer
gdebi			# Graphical manual package installer
curl			# Used for scripts like TTYtter
ttytter			# Really needs packaging as it handles StatusNet/Identica as well as Twitter.  Upstream: http://www.floodgap.com/software/ttytter/
sox			# Audio swiss army knife
libsox-fmt-all		# Draws in all available format supports for sox
ntp			# Going to need it just for ANY client to handle Twitter's being picky as of late
ttf-droid		# Decent font family for most applications
ttf-beteckna		# Retro font
vorbis-tools		# Ogg Vorbis support
```

Punted sideways for the moment maybe:
```
gmrun                   # This gives us our alt-f2 box
```

---

### Post by bodhi.zazen on 2011-07-01
Well, I would drop both leafpad and abiword =)

Take a look at gedit and cream, both offer more creature comforts then leafpad such as spell checking and syntax highlighting.

abiword to me seems clunky, sort of in between a full featured word processor and light weight application without doing either very well, but I understand it is popular with some.

Cream is cross platform and I use it on both windows (@ work) and linux.

[http://cream.sourceforge.net/](http://cream.sourceforge.net/)

---

### Post by skellat on 2011-07-01
> **bodhi.zazen said:**
> Well, I would drop both leafpad and abiword =)

I can see the point for ditching leafpad.  I'm going to have to take another look at gedit's dependencies to see how much it brings to the party.

> **bodhi.zazen said:**
> abiword to me seems clunky, sort of in between a full featured word processor and light weight application without doing either very well, but I understand it is popular with some.

I definitely want to keep abiword as it has a fabulous file format conversion function that works even from the command line.  abiword can transmogrify word processing files similar to what sox does to audio files.  I have it installed on my SheevaPlug for just that reason.  It may be a clunky word processor but as a preprocessor it does wonders as the successor to wv and antiword.

---

### Post by bodhi.zazen on 2011-07-02
As long as you have thought about it, stay with abiword then.

When evaluating cream or gedit, look at functionality first, dependencies second.

---

### Post by canthus13 on 2011-07-04
What I'm aiming for is something that is as comfortable to use as Gnome was before Unity. I'm not really shooting for ultra-lightweight, and don't have a problem with using GTK apps.. As far as gmrun goes, I'm sticking with it.  everyone is familiar with the alt+f2 key combo giving you a dialog to execute a program. dmenu is just, well, ugly and alien to most people. As for the others... Midori is ugly, but aside from that, I don't have a problem with it, really.

I guess we should outline the goals of this a bit more clearly before we go much further.  Ultimately, I'm envisioning something that can be transitioned to from Gnome with a fair amount of ease, so we can pick up all the refugees from Unity.  ;)

--Jason

---

