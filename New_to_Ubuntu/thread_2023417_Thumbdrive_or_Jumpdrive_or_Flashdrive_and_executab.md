---
title: "Thumbdrive or Jumpdrive or Flashdrive and executables"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-07-12
I'm looking for the simplest solution. In what flavor of Ubuntu and/or desktop (XFCE or Gnome or KDE) will executables on a thumb, or flash, or jump drive (a USB device) work?

I'm using XFCE and the external usb drive would not run an executable. I got some help with that, this forum, but now the drive appears as part of / (or maybe I should write that as) /thumbdrive. Anyway, as the drive needs to be portable and allow executables, what is the easiest or simplest way to get this drive working?

---

### Post by cbennett926 on 2012-07-12
These would work! If you computer will allow you to boot from a USB Device you can take a look at this page: [http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)

As for other distro's I believe they do have LIVE versions for them, and for those a CD will suffice, I am not sure if they have a USB trial version.

---

### Post by cbennett926 on 2012-07-12
Oops, just saw you asked what flavor it will work with, I recommend install the normal Ubuntu 12.04, and then installing the appropriate environment you would like, if you need any help with that I would be glad to assist you!

---

### Post by mike555 on 2012-07-12
If your trying to run Linux executables off a thumbdrive (not Windows .exe) they need to be made executable using "  gksu chmod +x %f   "

 if your going to do that often make a custom action in thunar  , then you can just rt. click on executables and make them executable.

---

### Post by Mark_in_Hollywood on 2012-07-13
> **mike555 said:**
> If your trying to run Linux executables off a thumbdrive (not Windows .exe) they need to be made executable using "  gksu chmod +x %f   "

 if your going to do that often make a custom action in thunar  , then you can just rt. click on executables and make them executable.

1 - Using this Linux exec-file is a daily occurence. Sometimes, several times a day. Will using gksu make the executable root (make me 'root')? I think I should be "user', and not root. - I'll explain why below

2 - By "rt. click on executables" Does that mean that they aren't exec. in any BUT Thunar? So, without that gksu chmod command these files are never executable, while on the thumbdrive? Can the file be made persistently executable? Without the gksu command, after being made persistently executable?

The Linux executable file on the drive is Sesame, part 2 of LastPass' two step password security. It must be executed to provide a second password, before I can access my password 'vault'. If I am 'root' does that matter to the security, allowing a potential hacked into my OS and my passwords (this assumes a lot, but I've had my passwords hacked twice in 2012. Once at TechRadar and another at Linkedin. And maybe yesterday when Yahoo had 450,000 passwords compromised. Pardon my paranoia, please.

 I want to be able to take that thumbdrive with me when I travel. I want to plug it into any computer (It has a separate MS-Win executable for that OS) and obtain some security through that.

I'm so new to this that I'm not well forming the expression of what I'm trying to do. Please forgive that.

---

### Post by mike555 on 2012-07-13
open Thunar ,click on Edit > configure custom actions > click the + button > put " gksu chmod +x %f " in the command box (without quote marks) type " Mark as Executable " in the name box, now click on the Appearance Conditions tab , put * in top box and marks by  Text files and Others files ..... close .

 now when you will be able to mark apps as executable from the rt. click menu , you should only need to do this once on each app that you haven't already done, you will need to put in your password to be super user ( so you'll not be root ,but will be user with powers temporary )

---

### Post by Cheesemill on 2012-07-13
If your drive is formatted with either FAT32 or NTFS then you cannot just mark a file as executable.

Drives that are formatted with a Windows file-system don't understand the Linux permissions system, thus trying to set them as executable will have no effect.

You need to either copy the file to a native Linux partition and set it as executable there or mount the drive in /etc/fstab with the exec option set to be able to execute files that live on a non-linux filesystem.

---

