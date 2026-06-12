---
title: "Sharing /home between distros?"
date: 2007-05-30
forum: Other OS Talk
---

### Post by ThinkBuntu on 2007-05-30
Sigh...

Today, I installed Sidux on a spare partition and chose my /home partition to mount accordingly from the installer. Well, during my first login to Sidux, it pretty much wiped away all of my KDE settings, such that when logging back into openSuSE I didn't even have a KMenu. So I backed up my home partition, deleted the user and added myself again (which is a breeze in openSuSE), and am doing my best to restore the old configuration. What a shame, considering that that configuration was the accumulation of many, many tweaks.

How do you share a /home partition between distros without this happening, especially when using the same desktop environment? I'm beginning to feel that having a separate /home partition is only useful if your base system craps out, and you need to newly install another distro.

Anyway, that's the last remnant of my distro-hopping/sampling on this laptop. openSuSE all the way!

---

### Post by theonlyrealperson on 2007-06-12
Heh, I just did that with Debian and CentOS. 

Instead of wiping my setting though, it locked the user out of both systems. I can't log in to either with that name anymore. Even deleting the home directory and the user and re-adding them didn't work. I had to ctrl+alt+bskpace out of X and add a new user to each with a completely new username for each.

I've never had any problems though if you keep the users from intermingling with each other. Or, if one distro uses Gnome and the other KDE.

---

### Post by ThinkBuntu on 2007-06-12
> **theonlyrealperson said:**
> Heh, I just did that with Debian and CentOS. 

Instead of wiping my setting though, it locked the user out of both systems. I can't log in to either with that name anymore. Even deleting the home directory and the user and re-adding them didn't work. I had to ctrl+alt+bskpace out of X and add a new user to each with a completely new username for each.

I've never had any problems though if you keep the users from intermingling with each other. Or, if one distro uses Gnome and the other KDE.
What do you think of CentOS? Does it have a place outside of servers?

---

### Post by theonlyrealperson on 2007-06-12
I really only used it as a home server. So, I basically only ran Apache, Cups, Samba, and SSH on it. It handled those things really well though. Especially Samba/NFS, which I have had a problem with in Ubuntu as a server. 

I did install it on my much faster laptop, but it only lasted about five minutes when I went Google-ing to figure out how to get the wireless working. Most people seemed to be really unhappy with CentOS and the Intel 2200BG, so I wiped it from my laptop and tried something else.

I don't like the YUM installer one bit. I'm really not a fan of the whole .rpm stuff, actually. Especially when Debian is such a breeze to work with...

All in all, it's a mixed bag. It works really well as a server, and it's easy to configure. I can't think of anything else you'd use it for though. The software selection isn't fantastic, and I never got the hang of "rpm hell" to install outside of YUM.

---

### Post by igknighted on 2007-06-12
When you share a /home, generally you should not use the same username for both accounts.  If you want to port your settings, copy and paste at first to see how it works.  For bookmarks and such you can link the .mozilla folder, but general settings I would never risk like that.

---

### Post by happy-and-lost on 2007-06-13
I just symlink my .mozilla folder and a few other essential /home folders when trying out new distros. Less destructive that way :)

---

### Post by jingo811 on 2007-11-11
> **igknighted said:**
> When you share a /home, generally you should not use the same username for both accounts.  If you want to port your settings, copy and paste at first to see how it works.  For bookmarks and such you can link the .mozilla folder, but general settings I would never risk like that.

So if I have user Bill on my /home partition for Ubuntu and uses Azureus.
How do I make the download folder for my Linux isos show on my other Linux distro lets say Debian with user Linus?
That is I want both my Linux distros save new iso files to the same physical folder without having to recreate and update things for the other distro when I logout and boot.

Can you guys show me how you do when you symlink a configurations .folder for another distro?

And also if possible how to symlink a command to some shortcut name?
I'm using ssh to my webhost and I can't use TAB to auto complete long path names.

---

### Post by VCSkier on 2007-11-13
I, too, am trying to figure out how to "symlink" several of the folders in the home folder of one user to the same folder in a different user, on another distribution.  Is this possible, and if so, are there any other implications regarding permissions and ownerships?  I'd like to be able to download my torrents to my ~/iso/ folder, regardless of which distribution I'm booted into, as well as edit documents and rip/listen to audio.  What is the best way to do this?

---

### Post by scorp123 on 2007-11-13
> **ThinkBuntu said:**
>  How do you share a /home partition between distros  If you want to use the *same* username (e.g. "joe-user") then you'd have to make sure that the distros are *very similar* but not *too similar* ... For example you probably could share your /home between a new Gutsy installation and a Fluxbuntu installation ... whatever settings these two write into your /home probably won't get into each other's way and you would have access to all your movies, music etc. from both distros and you could try and find out which one you like better.

Sharing /home between e.g. OpenSUSE and Kubuntu most likely will *NOT* work ... both have KDE and very very specific settings, so chances are that the two distros will overwrite each other's settings everytime you do something.

Workaround: Use two different usernames but the same user ID's (e.g. 1000). You could have one user for SUSE (e.g. "joe-suse") and one user for Kubuntu (e.g. "joe-kubuntu"), and you make sure that both accounts in both distros get the same "uid" ... which defaults to 1000 these days if I am not mistaken. After both distros are successfully installed you'd have two directories in your /home:
/home/joe-suse
/home/joe-kubuntu

But because the same UID number is used --and that's what matters on the filesystem level-- you'd have full access to the other folder without risking to overwrite anything by accident or by merely using the other distro (because each distro would write its settings into its own folder e.g. the different KDE settings would not collide ...)

---

### Post by jingo811 on 2007-11-14
> **scorp123 said:**
> 

Workaround: Use two different usernames but the same user ID's (e.g. 1000). You could have one user for SUSE (e.g. "joe-suse") and one user for Kubuntu (e.g. "joe-kubuntu"), and you make sure that both accounts in both distros get the same "uid" ... which defaults to 1000 these days if I am not mistaken. After both distros are successfully installed you'd have two directories in your /home:
/home/joe-suse
/home/joe-kubuntu

But because the same UID number is used --and that's what matters on the filesystem level-- you'd have full access to the other folder without risking to overwrite anything by accident or by merely using the other distro (because each distro would write its settings into its own folder e.g. the different KDE settings would not collide ...)

That looks like a clean and clever solution will try it when I have time TNX.

---

### Post by VCSkier on 2007-11-14
Same here, once I figure out how to create symlinks, I will most likely reinstall openSUSE and make a new user that matches the UID of my Ubuntu user.  Also, can you change the user id of an existing user account, or is the id permanent once the user is created?  Thanks!

---

### Post by g2g591 on 2007-11-14
symlinks: open a terminal and type ln -s (target_directory) (linkname)
eg g2g591@kubuntu$ln -s /home/g2g591-debian/downloads downloads
will create a symbolic link between the directory /home/g2g591-debain/downloads and create a link called downloads in the current working directory

---

### Post by VCSkier on 2007-11-14
And this works for directories as well?  So /home/suse/Documents/ can really just be a link to /home/ubuntu/Documents/ ?  Thats great.  Thanks so much guys.

---

