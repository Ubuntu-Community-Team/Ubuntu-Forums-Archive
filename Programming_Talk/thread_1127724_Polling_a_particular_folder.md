---
title: "Polling a particular folder"
date: 2009-04-16
forum: Programming Talk
---

### Post by mbeach on 2009-04-16
Hi,

I have a need to allow a remote server (legacy terminal application) not on my network to drop some files onto my server, for subsequent action.  It is a flat text file which will be 'printed' from that application.  The print function can print to a ipp printer or the print routine can be crafted to scp the print file.

My first inclination is to set up a samba printer on my local server, use the "print command" and open up a port on the firewall where the remote application can print its file, and my print command script would deal from there.

The other option, and the one I'd rather attempt is to allow the remote server to scp a file to a particular folder.  My issue there is knowing when to act on the file.  Particularly I'm wondering about knowing when the file is fully there (ie don't act on the file if it is still being copied) and also how to continuously poll the folder.  I'd prefer not to have a cron job running every minute.  I thought there might be a setting in sshd_config which allowed for calling a post-receive file routine, but I cannot find such a setting.

Anybody have any direction for me?  How does one continuously monitor a folder?

---

### Post by unutbu on 2009-04-16
inotify provides a mechanism for monitoring filesystems.
Name your favorite programming language, and it probably has an interface to the inotify API.

There is also a package called "incron" which is sort of like cron, except that it executes commands triggered by filesystem events instead of being triggered by datetime stamps.

There is also a package called "inotify-tools" which I haven't used but seems to provide inotify commands which can be placed in bash scripts.

Finally, I am also rather partial to dirmon: [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)

---

### Post by odyniec on 2009-04-16
> **mbeach said:**
> Anybody have any direction for me?  How does one continuously monitor a folder?

Inotifywatch (included in the inotify-tools package) might be what you need. You could write a shell script that runs in the background and parses the events reported by inotifywatch, and whenever there's a notification of a new file being created in the monitored directory, processes the new file.

---

### Post by mbeach on 2009-04-16
thanks for the prompt replies - I'll take a look at these.

---

### Post by mbeach on 2009-04-16
> **unutbu said:**
> 
Finally, I am also rather partial to dirmon: [http://ubuntuforums.org/showthread.php?t=1104716](http://ubuntuforums.org/showthread.php?t=1104716)

looks perfect for what I'm after.  Another reason to dig deeper into python (been trying to find some time in the last year).

Thanks,
mb.

---

