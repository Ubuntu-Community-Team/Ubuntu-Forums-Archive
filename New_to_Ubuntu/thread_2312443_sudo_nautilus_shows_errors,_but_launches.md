---
title: "sudo nautilus shows errors, but launches"
date: 2016-02-04
forum: New to Ubuntu
---

### Post by helm10101 on 2016-02-04
Everytime I type "sudo nautlius" it gives me this:

(nautilus:2203): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2203): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2203): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

But it still launches.
What is it?

Thanks

---

### Post by Vladlenin5000 on 2016-02-04
First of all, don't do that. NEVER!
There's no reason whatsoever to open Nautilus as root but if you really want to do it, never with *sudo*. Graphical apps should never be opened with sudo. Read this [http://manpages.ubuntu.com/manpages/precise/man1/gksu.1.html](http://manpages.ubuntu.com/manpages/precise/man1/gksu.1.html) and use it instead of *sudo.*

BTW, why do you think you need root?

---

### Post by helm10101 on 2016-02-04
I didn't quite understand what that means (I'm new to Linux and Ubuntu), so I don't really know what X terminal emulator is or the other stuff.
And also, the article tells you what gksu and gksudo do, and not why I shouldnt do sudo nautilus, so , why I shouldn't do that? :KS

I needed root because I wanted to access the EFI folder located in /boot/, because I'm using rEFInd, and I see some older boot options when I boot, although I deleted these OS, such as openSUSE or I also see something like vmlinuz, which stucks the PC if I choose it, so I wanted to edit refind.conf file to not some, and also to remove the extension ".efi" from openSUSE folder on /boot/ so rEFInd won't detect it.

It worked btw and now I only see Windows and Ubuntu at boot on rEFInd :)!

---

### Post by Vladlenin5000 on 2016-02-04
The reason why you shouldn't use it like you did has been discussed here and everywhere else *ad nauseum*. In a nutshell, it can easily mess with the permissions in your own userspace and just a small wrong action can render your entire OS unbootable and unusable. Those should be reasons enough, don't you think?
Also you don't need - and probably should avoid it altogether - Nautilus to mount partitions, including the ESP.
And you probably shouldn't be doing what you just said - deleting things directly in the ESP - considering there are commands for that, like [*efibootmgr*]("http://linux.die.net/man/8/efibootmgr").

I know, a lot to learn but you should do the effort if you intend on deploying OSs installations and particularly dual-boot scenarios. However, right now, much more important that the things you need to learn are those that you should UNLEARN, those stemming directly from your Windows background and mentality. Then, it all boils down to the pursuit of the 'best practices' which often should be the only practices.

---

### Post by Frogs Hair on 2016-02-04
> [COLOR=#000000]why I shouldn't do that? [/COLOR]:KS

[http://askubuntu.com/questions/270006/why-user-should-never-use-normal-sudo-to-start-graphical-application](http://askubuntu.com/questions/270006/why-user-should-never-use-normal-sudo-to-start-graphical-application)

---

### Post by helm10101 on 2016-02-04
> **Frogs Hair said:**
> [http://askubuntu.com/questions/270006/why-user-should-never-use-normal-sudo-to-start-graphical-application](http://askubuntu.com/questions/270006/why-user-should-never-use-normal-sudo-to-start-graphical-application)

Wow, thanks, that was comprehensive. I didn't understand all I must admit :D

---

### Post by yetimon_64 on 2016-02-04
> **helm10101 said:**
> Wow, thanks, that was comprehensive. I didn't understand all I must admit :D

Generally that is good info, one mistake I spotted with it ... "sudo **chmod** -R $USER:$USER" should read as "sudo **chown** -R $USER:$USER". 
Although the mistake is mentioned in the comments the answer giver has not yet corrected the command. Something to be aware of if you do have a problem with your home files owned by root because of sudo usage.

Also using sudo is ok **_*IF*_** you use the "--set-home" or "-H" switch. From "man sudo" ... > -H, --set-home
                 Request that the security policy set the HOME environment variable to the home directory spec&#8208;
                 ified by the target user's password database entry.  Depending on the policy, this may be the
                 default behavior.

Edit: generally speaking OP using gksudo or gksu etc is far safer for a new starter, that is what I'd recommend, even though it is possible to use the set home switch with sudo.

---

### Post by mastablasta on 2016-02-05
here is an easier explanation with pics, so you can see what can happen if you start graphical apps with sudo: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by helm10101 on 2016-02-05
Thanks everyone.
I did install the gksu package.
and when I tried to do gksudo nautilus, it gave me internal error and deleted all my desktop and stuck my laptop, what caused this?

Edit: after typing gksudo nautilus (after restart), it never created a new line in terminal and I must exit the terminal, and it warns me that a process is still running (although I closed nautilus)
It leaves the cursor hanging without creating new user@pc: line .

---

### Post by howefield on 2016-02-05
> **helm10101 said:**
> Thanks everyone.
I did install the gksu package.
and when I tried to do gksudo nautilus, it gave me internal error and deleted all my desktop and stuck my laptop, what caused this?

gksu is not installed by default for a reason.

As has been said above you are probably better using sudo -H <insert graphical package name here>

Shrug.

If you haven't already, I'd suggest getting a (pristine) working system and cloning it, either with Clonezilla or Macrium or something else like it. Your life and learning curve might be made a little sweeter :)

---

### Post by vasa1 on 2016-02-05
As for the warnings and messages you see when launching GUI applications from the terminal (with or without *sudo -H*) see: [http://askubuntu.com/a/422400](http://askubuntu.com/a/422400)

---

### Post by Morbius1 on 2016-02-05
> Edit:  after typing gksudo nautilus (after restart), it never created a new  line in terminal and I must exit the terminal, and it warns me that a  process is still running (although I closed nautilus)
It leaves the cursor hanging without creating new user@pc: line .                                                                                              
Because you are invoking nautilus in the foreground. When you close nautilus the terminal will resume to a "user@pc" prompt. 

If I may make a suggestion: Don't invoke gksu in a terminal. Use "Run" instead: Alt-F2

Anyhoo, gksu invokes "sudo -H" among some important other things. That's why it was invented.

---

### Post by Geoffrey_Arndt on 2016-02-05
Sometimes, Windows Power users start using Linux as if they were still running Windows.   Doesn't work so well until (or IF) they learn Linux.   Then they wind up with an install that has so many incorrect modifications, it becomes very unstable.   Then, they think Linux is somehow bad, hard, etc, etc., when the original problem is PEBKAC (problem exists between keyboard and chair).   Literally, there are HUNDREDS such threads on this forum.

EDIT:   to be a bit fairer to the OP, often this "downward spiral" starts happening . . . . because . . . . the users hardware is not especially Linux friendly.   Things like dual graphics, dual sound-cards, low support printers (lexmark, some canon models), and so the new Linux user feels compelled to fix all the issues quickly, and doesn't succeed in doing so.    Either ALL or MOST of these issues can be avoided if prospective new Linux users can be steered to the companies like Zareason and System76 that design pre-installed Linux systems.   It makes a world of difference.

---

