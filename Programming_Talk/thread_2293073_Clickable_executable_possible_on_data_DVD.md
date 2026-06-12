---
title: "Clickable executable possible on data DVD?"
date: 2015-09-02
forum: Programming Talk
---

### Post by VanillaMozilla on 2015-09-02
Newbie question here.  I'm a Linux *user* and an old Windows command-line programmer, with little knowledge of *nix scripts.

Is it possible to distribute a program on a data DVD that can be started under Linux with a mouse click?  The solution must be convenient for naive users, so prior user preparation cannot be assumed.  It's acceptable if a dialog opens that asks permission to run in userspace, but installation or commands such as chown or chmod are asking too much of the user.  Is this possible under Linux?  Small scripts and creative solutions are allowed.

The objective is to write a menu system that will call a media player such as the VLC Player, to display high-definition videos.  It would be a simple substitute for video DVDs and BlueRay, without the resolution limits and hardware requirements.  The problem is described further here:  [http://ubuntuforums.org/showthread.php?t=2292388](http://ubuntuforums.org/showthread.php?t=2292388) .  A program that could run a command like
vlc --play-and-exit <filename>
might work very nicely, for example.  (I have no hesitation about recommending VLC, since it would not be a requirement for viewing the videos.)

I understand that something like
java <jar> ...
might work (?), except that Java may not be present on all systems.  Creative solutions encouraged.

---

### Post by TheFu on 2015-09-03
Newby answer:  
* [http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
* [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

Read the parts about file permissions and mounting.  Optical disks don't have any permissions - permissions are set in the mount options. Therefore those can be anything you like. Scripting that wouldn't be impossible, just some careful thought needed. Definitely not something I'd have time to do for free. There are lots of examples of installation scripts.

You could create a liveCD with a Linux install, preloaded with programs and all the data already on it.  Something like TinyCore would be where I started to keep the wasted amount for the OS to a minimal size. I would be surprised if this hadn't already been done by someone else.  [http://sourceforge.net/projects/limp-vkk-ver1/](http://sourceforge.net/projects/limp-vkk-ver1/)

Never assumed java.  Security professionals have been training end-users to remove java from their systems.

---

### Post by VanillaMozilla on 2015-09-03
> **TheFu said:**
> Optical disks don't have any permissions 
Yes, that's what I figured.  Presumably because they are readonly devices.  I'll take that as a "no".

> **TheFu said:**
> permissions are set in the mount options.
Good idea.  That might actually work, although the required setup might be a little too advanced for the application.

Thanks.  Believe it or not, this is helping me to think about the problem, and maybe to refine it.

---

