---
title: "Can I remove unity and run Xubuntu only?"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by rojaasensei on 2011-10-24
I recently upgraded to 11.10.  It wasn't much fun, to say the least.

Anyway, I installed Xubuntu, and love it.  The problem is I still have unity as an option.  I would like to remove it.

When I try to do so through synaptic it wants to download a lot of new packages which I assume is to install some version of gnome (maybe).  Is there a safe way to convert my system to Xubuntu only?

I tried the PsychoCat method but it left me unable to sign in to any desktop.

Your advice is welcome.  I don't use Unity or Gnome desktops, but I am constantly getting reminders of updates I don't want to bother with.

---

### Post by fantab on 2011-10-24
Install Xubuntu... instead of assembling Xfce and removing Unity.

You can remove Unity from the Synaptic... just don't worry about the new packages it wants to install...

---

### Post by mike555 on 2011-10-24
better to do a clean install of Xubuntu (backup first) then add what you want ......

---

### Post by collisionystm on 2011-10-24
> **rojaasensei said:**
> I recently upgraded to 11.10.  It wasn't much fun, to say the least.

Anyway, I installed Xubuntu, and love it.  The problem is I still have unity as an option.  I would like to remove it.

When I try to do so through synaptic it wants to download a lot of new packages which I assume is to install some version of gnome (maybe).  Is there a safe way to convert my system to Xubuntu only?

I tried the PsychoCat method but it left me unable to sign in to any desktop.

Your advice is welcome.  I don't use Unity or Gnome desktops, but I am constantly getting reminders of updates I don't want to bother with.

Try this.. It just may work!
Backup your personal files first

sudo apt-get install tasksel

sudo tasksel

uncheck Ubuntu Desktop using the space bar

Check Xubuntu desktop using the space bar

hit OK

let it run and reboot.

---

### Post by Kilz on 2011-10-24
This page (from a staff member here) may help you do just that.
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by rojaasensei on 2011-10-24
> **Kilz said:**
> This page (from a staff member here) may help you do just that.
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

I did try Psychocats but it left the system unstartable and had to reinstall

---

### Post by JKyleOKC on 2011-10-24
> **rojaasensei said:**
> The problem is I still have unity as an option.  I would like to remove it.

When I try to do so through synaptic it wants to download a lot of new packages which I assume is to install some version of gnome (maybe).  Is there a safe way to convert my system to Xubuntu only?

I tried the PsychoCat method but it left me unable to sign in to any desktop.

Your advice is welcome.  I don't use Unity or Gnome desktops, but I am constantly getting reminders of updates I don't want to bother with.I support the idea of removing stuff as posted in Psychocat's link, then doing a clean install of Xubuntu. Don't worry about all the Gnome-like stuff that will be installed; XFCE itself uses lots of Gnome tools behind the scenes, but keeps them mostly out of sight.

When you do the clean install, set up a separate partition for /home. This will make future updating much easier, but it will still be a good idea to keep an offline backup of your data anyway just in case some disaster takes out your hardware.

EDIT: Just saw your reply above. Yes, it will be necessary to re-install after clearing out the Unity stuff -- but if you install Xubuntu then, rather than Unity, you'll be where you want to go. Just be sure to download and burn the Xubuntu Live CD before you start.

---

