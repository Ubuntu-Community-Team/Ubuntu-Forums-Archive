---
title: "Can someone explain to me xinit, xorg, and .nvidia-settings-rc"
date: 2020-07-29
forum: New to Ubuntu
---

### Post by dakahn on 2020-07-29
So I'm trying to unravel why my monitor rotation setting's aren't saved session to session. To follow (only some of) that great drama you can read [this thread ]("https://ubuntuforums.org/showthread.php?t=2447860")opened in hardware support.

I have a higher level question that could help me get this resolved. Can someone in plain language explain to me X -- in particular xinit, xorg and how they relate to each other or translate to .nvidia-settings-rc?

For more specifics I'm trying to get my nvidia-settings to persist session to session [which should be possible]("https://manpages.ubuntu.com/manpages/bionic/man1/nvidia-settings.1.html") (checkout section 3) by specifying exactly that in an xinit file in your home directory. This doesn't seem to work at all and so there must be something I'm miissing. 

Thanks in advance.

---

### Post by TheFu on 2020-07-29
Those questions are much larger than possible to answer in these forums.  Start with learning about x11 by reading the wikipage for that.  I have 7+ thick books about x11 from the 1990s.  It is a very big ask, especially without saying what you already know.  Start with wikipedia.

nvidia software has never really worked beyond the drivers and for getting information, IME.  Best to ignore it.  I do.

Maybe the easy answer is to just use wayland instead of x11?

---

### Post by dakahn on 2020-07-30
Hmmm, no offense but I seriously doubt that "xinit, xorg and how they relate to each other or translate to .nvidia-settings-rc?" is too deep and complex a question to answer on an internet forum. I get not wanting to -- totally fair. Also seems inadvisable to suggest a user swap x11 for wayland in 'New to Ubuntu' when they can't get their monitor rotation to persist, no?

---

### Post by TheFu on 2020-07-30
Ok - I'll make a short attempt, but these are not the questions that someone "New to Ubuntu" usually asks. It gets deep, quick, and assumes some understanding of how the display server is started and how separate that is from logins.

Here goes, 

xorg is the replacement project to XFree86 which was the X11 client, server, and protocol implementation for PCs.  Read the wikipedia to learn more than most end-users need to know. I doubt that is your real question, but don't want to guess.  
[https://www.x.org/wiki/](https://www.x.org/wiki/)  
[https://en.wikipedia.org/wiki/X.Org_Server](https://en.wikipedia.org/wiki/X.Org_Server) which is not as useful as the 
X/Windows wikipedia: [https://en.wikipedia.org/wiki/X_Window_System_core_protocol](https://en.wikipedia.org/wiki/X_Window_System_core_protocol)  The architecture diagram is extremely helpful for understanding, assuming client/server systems aren't totally new.  The key thing to realize is that the X/client is the remote system and the X/Server is the system we are sitting behind. This is backwards of almost all Client/Server architectures in the world.

xinit is how the X11/Server gets started. From the manpage (run **man xinit** to see it, or use **xman**) - which you have on your system too:
```
xinit - X Window System initializer
DESCRIPTION
       The xinit program is used to start the X Window System server and a first
       client  program  on  systems that are not using a display manager such as
       xdm(1) or in environments that use multiple window  systems.   When  this
       first client exits, xinit will kill the X server and then terminate.

       If  no  specific  client program is given on the command line, xinit will
       look for a file in the user's home directory called .xinitrc to run as  a
       shell  script to start up client programs.  If no such file exists, xinit
       will use the following as a default:

            xterm  -geometry  +1+1  -n  login  -display  :0
...
```
There are about 4 more pages which explain the environment variables, commands, and config files used. All useful information to know, but not to memorize.

nvidia-settings is a helper to create some initial settings that nvidia thinks are good. There are 2 types of file output it can create - an xorg config file and an nvidia-specific card control file.  Usually, that output **has** to be stored in the user's HOME for both, since running GUI programs with sudo is a terrible idea. I've played with nvidia-settings on a few systems and always found it to generate less-than-useful output.  There is nothing special about .nvidia-settings-rc as a filename except to the nvidia-settings program.  X11 doesn't know anything about it.  
Until nvidia-settings gets run again only if we setup a way for that to happen. ~/.xinitrc or ~/.xprofile would be where I started. There is a manpage which explains that program.
```
$ nvidia-settings --load-config-only  --config=/path/to/home/.nvidia-settings-rc 
```might be useful. I don't know. Never needed it. Maybe put that into your ~/.xprofile or ~/.xinitrc which gets run whenever a new X11 session is started? Again, IDK.  When I run that command, nothing happens that I can tell, but unless some funky gamma changes or resolution changes are inside it, I doubt I'd notice.

The /etc/X11/xorg.conf.d/whatever-nvidia.conf file gets found when the X/Server is initialized.  For Ubuntu Desktops, that would be a boot, but only if a GUI login manager gets run, which is optional.  If a mouse can be used, then some display server (wayland or X11) are running prelogin.

For fun, just tested nvidia-settings with rotation enabled. That rotated the screen when "Apply"'d, but refused to save the file.
> ERROR: Unable to open X config file '/u/thefu/.nvidia-settings-rc2' for writing.
I tried multiple other locations and filenames with the same issue.  [https://ubuntuforums.org/showthread.php?t=1482283](https://ubuntuforums.org/showthread.php?t=1482283) suggested that writing to the file doesn't work, but that the "Show Preview" button would allow the generated xorg.conf to be seen, which could be select/pasted into the real xorg.conf.d/some-x-settings-file.conf using sudoedit.  The "Show Preview" DOES show the config file, just hidden so the window containing it has to be resized larger.  Inside is a reasonable xorg config file with whatever settings. I saw the "rotation" settings in the "screen" section when I chose a rotated screen option.  That should make the settings whatever you want for each monitor connected, since it happens pre-login, pre-login manager.  But until you try it, who knows?

There are manpages for xorg.conf and xorg.conf.d which explains their functioning, settings, order of reading, etc.  I find it best to start from a skeleton config file and fill in the parts I need specifically only. File names need to end with ".conf" to be read.  20-nvidia.conf is the active one on my system. In the same directory, "AA-automatic" is an old file that doesn't get used. The manpage confirms this.

Sorry. I'm not good at "plain language."

Swapping Wayland for X11 is a 1 button toggle on the login page for someone running normal Ubuntu. Just click the "gear" to see the option. I don't know which version of Ubuntu you have, but since 17.10, Wayland has been there.  I used Wayland for about 30 minutes once, about 2 yrs ago. Long enough to discover that it didn't have key features I rely on constantly, daily, 50x a day.  But I work differently than most typical home users, so they probably would like the greater performance that Wayland provides to local windows.  Wayland appears to have screen rotation working for KDE and some versions of newer Gnome Shell. [https://www.phoronix.com/scan.php?page=news_item&px=KDE-Wayland-Screen-Rotate](https://www.phoronix.com/scan.php?page=news_item&px=KDE-Wayland-Screen-Rotate)   [https://wiki.gnome.org/ThreePointTwentyone/ReleaseNotes](https://wiki.gnome.org/ThreePointTwentyone/ReleaseNotes)  It is unclear whether this Gnome-shell version only works for Intel GPUs or includes all GPUs.  I don't use Gnome or KDE.

Sorry if my looking for a rotation solution got in the way of what you really wanted to know.  Almost every program has some sort of config file and initialization file on Unix. There are system-wide versions of both and per-username versions.

---

