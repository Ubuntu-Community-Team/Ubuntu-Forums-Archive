---
title: "[SOLVED] Flash won't install...Intrepid on AMD64"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by justchange on 2008-10-31
I just started running Ubuntu a couple of weeks ago. AND I LOVE it! *(Though the learning curve is moderately painful, at first... until I learned that these excellent forums are part of the package!)*

So, I pulled up one of two matched boxes: AMDx64 ; MSI-7191 MB, 512M, 160GB (the other just got a clean install of Hardy, 3 days ago), and I dual-booted from XP with Intrepid.

The install went flawlessly! (Hardy choked on the onboard ATi x200 video, but 8.10 sailed right over it, asking if I wanted the freebie or proprietary driver.)

On the web, however, I found a problem with Flash.
The Adobe install recognizes Linux up to Ubuntu 8.04, but there's no option for x64.

I tried the .deb install and Package Installer errored out with **[COLOR="Red"]Error: Wrong architecture 'i386'[/COLOR]**.

I tried the APT install, but a small window keeps popping up:
**Could not find package 'adobe-flashplugin'.** 

I tried searching around in Ubuntu for a solution (though being a total nUUb, I'm not so surprised.)

And at Adobe, but found no reference to the x64 issue.

Got any ideas?
[I](And if you're going to include command-line stuff, please be gentle... like you're dealing with your 'special needs' little brother, ok?)
[/I]
Thanks.:)

---

### Post by perlluver on 2008-10-31
In synaptic search for flashplugin-nonfree.  Or you can install ubuntu-restricted-extras.

---

### Post by SunnyRabbiera on 2008-10-31
try the links on this page:
[http://packages.ubuntu.com/intrepid/amd64/flashplugin-nonfree/download](http://packages.ubuntu.com/intrepid/amd64/flashplugin-nonfree/download)

choose a server that is closest to you, installing the flash package should work like installing a windows .exe

---

### Post by diablo75 on 2008-10-31
Try this:

Click Applications>Add/Remove.

Change the filter to "All Available Applications" and do a search for the word "restricted".

That should result with an item below that says "Ubuntu Restricted Extras"

Check that off and click Apply Changes at the bottom to install.  this will also install Java and other Win32 video codecs, as well as flash 10.  Let us know if it works for you.

---

### Post by Crafty Kisses on 2008-10-31
Try running the following commands:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
Once you have run those commands, run the following command:
```
sudo apt-get install ubuntu-restricted-extras
```
That should clean the package manager and get you going.

---

### Post by justchange on 2008-11-01
My thanks to all of you who responded.

I'm sure that any of the recommendations would have worked... and, while I know I need to get familiar with the command line, ***diablo75*** made it easy for me with the GUI-driven response. (This will help with the *Beginner's Guide to the Ubuntu Galaxy* that I am journaling as I go. I'm finding the experience much like Indiana Jones's as he had to step off into the abyss to reach the Holy Grail. After the Windows support experience, it took a leap-of-faith to step into this unknown. How refreshing an experience it's been!)

Following ***diablo75***'s step-by-step directions produced the expected results with no stress. (Well, there was that 75 object download! So, to pass the time and its being Halloween, I was distracted from a quick reply by the neighborhood 'block party' and a few free brews.)

Once again, I am amazed and impressed by the Ubuntu community.
Thanks, again.

---

### Post by diablo75 on 2008-11-01
Good to hear!  Glad I could help.  :guitar:

---

