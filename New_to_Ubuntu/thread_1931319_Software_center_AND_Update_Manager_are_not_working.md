---
title: "Software center AND Update Manager are not working"
date: 2012-02-25
forum: New to Ubuntu
---

### Post by 01Dunno on 2012-02-25
Hi there!

Last night i tried to install the online game Conquer Online on me laptop.
Ofcourse i needed Wine to do so, but i read on a few sites that some people incountered problems with that.
Then i found someone who solved those problems using PlayOnLinux:
[http://ubuntuforums.org/showthread.php?t=783616](http://ubuntuforums.org/showthread.php?t=783616)
i started following te steps, but being the noob i am, i think i messed something up
i thought that the code:

sudo wget [http://playonlinux.botux.net/playonlinux_hardy.list](http://playonlinux.botux.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux                      

was used to expand PlayOnLinux after u had installed it, so before i entered that in Terminal i used the code:

git clone [https://github.com/PlayOnLinux/POL-POM-4](https://github.com/PlayOnLinux/POL-POM-4)

[FONT=Verdana]doing that, i also had to download that "git" thing.

when that was done
i went to apps-->games to see if i actually downloaded POL, but i couldn find it ?
i did see i could get it from the software center so i clicked it. but then my software center didn't open. i tried opening it again and again, even after restarting my laptop but it would just start blinking and then stop. do nothing.
i also noticed that red circle thingy at the upper right corner of my screen indicating an error: a problem accured when checking for updates.
and that's when i noticed my update manager was also not working as it should.

today i wanted to find out if others had the same problems and they did.. sort of
cuz non of the solutions helped.

this is what i did:
[B]
sudo apt-get update[/B]
output:

E: Type '-1' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
[/FONT]
[FONT=Verdana]i also tried deleting lists first as some people recommended:[/FONT]
**sudo rm /var/lib/apt/lists/* -vf**
output:
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

[FONT=Verdana]then i tried: **software-center**
output:[/FONT]
2012-02-25 14:52:14,346 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 213, in __init__
    self.cache.open()
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 209, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 93, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 140, in open
    self._list.read_main_list()
SystemError: E:Type '-1' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list

as for the update manager
when i open it i get:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '-1' is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list'


i hope i gave enough information for someone to help me =/
i'd really appreciate it cuz i don't want to go back to windows.
ubuntu's different and i was just beginning to like (except libre office, he's kinda a pain in the *** sometimes)
also i think it's a fun way to learn about programming and stuff??

a big thanx in advance!!


NOTE: please keep in mind i am completely new at this, so sorry if this is something i should already know

---

### Post by cortman on 2012-02-25
This looks fixable. Kudos to you for providing plenty of information and the clearly written post. Makes it MUCH easier to help with.
Can you run

```
sudo rm -r /var/lib/apt/lists
```

Then

```
sudo rm /etc/apt/sources.list.d/playonlinux*
```

Then

```
sudo apt-get purge playonlinux
sudo apt-get update
sudo apt-get install playonlinux
```

You really shouldn't have to do anything with git or github, or even adding extra repositories. Playonlinux is available in the standard Ubuntu repos.

If any of these commands don't work or return error messages, please post them here.
Good luck!

---

### Post by aceace40 on 2012-03-18
I have a similar problem and could not get a readable list

with the update manager I get the following message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wi

ne-ppa-oneiric.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'

:lolflag:

---

