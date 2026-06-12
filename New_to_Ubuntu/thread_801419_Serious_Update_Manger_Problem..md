---
title: "Serious Update Manger Problem."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by MrMoose9000 on 2008-05-20
I'm using the latest version of Ubuntu, if anybody asks. (8.04, I believe? I'm not really sure).

Anyways, so a couple of days ago, i logged on only to find that the "Update Arrow", had been replaced with a red circle, with a line in the middle- kind of like a stop sign. I clicked on it, and opened update manager. It loaded for a few minutes, and finally i got this: 

[B]A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hardy-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/B]

Now, I figured that it could have been a minor error (which was actually pretty stupid, thinking back on that now), and just let it go by. Now, I'm getting irritated and worried about this. I could just re-install the disc, though i really don't feel like waiting three hours to upgrade it to the latest distro, or to even install the earlier version itself. 

Since I really hate to ask noob questions, I figured i would try and find a solution my self. When holding my cursor over the "stop sign", it says "Please search apt-get in the terminal to see what is wrong." So, i open the terminal, and type apt-get. All that comes up is a list of about three java files, it says that the command is not found:
**bash: apt: command not found**

Anybody know what's wrong or have a solution?

Also, I did search the forum if somebody decides they want to
drop the ever-so popular "Its called a search bar" comment.

---

### Post by MrMoose9000 on 2008-05-20
I hate to bump, and I'll most likely get banned for this or something, but no one seems to see this thread.

---

### Post by wpshooter on 2008-05-20
First, go into software sources and try a different server.

Thanks.

---

