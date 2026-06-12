---
title: "Application Directory Structure"
date: 2010-06-09
forum: Packaging and Compiling Programs
---

### Post by ItalicBold on 2010-06-09
Hi All

I am trying to port a windows c# service onto Ubuntu Server.

I have got the service functioning correctly and I am currently writing a SysV Init script to handle its stop/start etc.

I am also creating a .deb to install it, however I am a bit unsure of the directory structure and where things should go. From what I understand so far:

/etc          is for config files (if I only have one file it doesnt need its own sub folder?)
/etc/init.d   is for the SysV Init script
/var/log      is for logs
/var/run      is for pid (used by the SysV Init script to controll service)
/usr/lib      is for the installation files

/usr/sbin     nothing will go in here as 'service ... start/stop' will be used to controll the application.

Given that this service is a TCP server of sorts I imagine this should run under its own user? Does that affect the above file structure at all?

If you could please comment on if the above sounds correct or if you have any tips.

---

### Post by DoctorMO on 2010-06-09
Unless it's truly a library then your execution point should be in /usr/bin 

Having the service run as a specific user is helpful, make sure to set the sticky bit so it always runs at that user.

/etc is for global configurations, user configurations go in $HOME/.config/ I know your not doing anything with users, but just to clear up the point.

I believe sysv init is going away in Ubuntu and they're moving over to a new system which I forget the name of. So have a dig around for info on that.

---

### Post by SevenMachines on 2010-06-09
i dont know much about where c# files go but for the filesytem
structure you can use the[ Debian Filesystem Hierarchy Standard]("http://wiki.debian.org/FilesystemHierarchyStandard") for a quick overview and the actual [FHS Specifications]("http://www.debian.org/doc/packaging-manuals/fhs/fhs-2.3.html") a more complete reference. although ubuntu now uses upstart, upstart is back compatible with the sysv system (many, probably most applications have not migrated to upstart specific scripts and still use sysv init)

---

### Post by ItalicBold on 2010-06-09
Thanks. After doing some more research I have decided to follow the structure that monodevelop uses as it is itself a mono port.

This is similar to what I mentioned above with the application files residing in

/usr/lib/xxx/bin
/usr/lib/xxx/plugins
etc.

and then a wrapper script in /usr/bin. I think this was done mainly for portability purposes (the base structure stays largely the same across platforms), which is something I would like to maximise as well.

I will still make correct usage of /etc for system wide config and /var/log + /var/run.

As for the SysV Init replacement you refered to I believe this is Upstart as SevenMachines mentioned and I will try and use this instead.

---

