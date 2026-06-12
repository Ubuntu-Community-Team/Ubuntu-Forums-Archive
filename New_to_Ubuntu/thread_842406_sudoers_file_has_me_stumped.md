---
title: "sudoers file has me stumped"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Jalexxi on 2008-06-27
I'm setting up a computer and I've encountered a problem which I can't seem to find the solution to. I need to do one very simple thing, I want to give a user the privilege to run one single command (smbmount) as root, because I want to mount a samba share on a server on startup (I'm using rc.local for that). When using the root user, everything works fine, but the non-root users need this mount to happen as well, but they don't have the privileges required to mount it. I tried to edit the sudoers file, but it's completely unfathomable to me. Can anyone help me out?

---

### Post by Hospadar on 2008-06-27
You should add that user to the "admin" group, generally you don't ever change sudoers unless you have a very complicated server type setup

---

### Post by Jalexxi on 2008-06-27
The reason I'm not making the user a full administrator is because I don't want to give root access, or access to administrative functions for that matter. All I need is that single command that can be run as root.

---

### Post by gn2 on 2008-06-27
> **Jalexxi said:**
> I'm setting up a computer and I've encountered a problem which I can't seem to find the solution to. I need to do one very simple thing, I want to give a user the privilege to run one single command (smbmount) as root, because I want to mount a samba share on a server on startup (I'm using rc.local for that). When using the root user, everything works fine, but the non-root users need this mount to happen as well, but they don't have the privileges required to mount it. I tried to edit the sudoers file, but it's completely unfathomable to me. Can anyone help me out?

The Network browsing link in my signature might be useful.

---

### Post by caljohnsmith on 2008-06-27
> **Jalexxi said:**
> I'm setting up a computer and I've encountered a problem which I can't seem to find the solution to. I need to do one very simple thing, I want to give a user the privilege to run one single command (smbmount) as root, because I want to mount a samba share on a server on startup (I'm using rc.local for that). When using the root user, everything works fine, but the non-root users need this mount to happen as well, but they don't have the privileges required to mount it. I tried to edit the sudoers file, but it's completely unfathomable to me. Can anyone help me out?
Sure, just do "sudo visudo" to open up sudoers with vi, or if you prefer to use nano like I do, you can use "export EDITOR=nano && sudo -E visudo".

To give the user the privilege to run the command as root, with their password, just put a line at the end of the file that looks like:
```
<username> ALL = PASSWD: /usr/bin/smbmount
```
Make sure that path to the smbmount command is correct, and of course replace <username> with their username.

---

### Post by Jalexxi on 2008-07-01
Thanks, caljohnsmith, that did the trick! Also, the nano command was handy, I prefer that editor as well.
I'll try the Thunar network browsing too, thanks for the tip, gn2!

---

### Post by FeyerbrandX on 2008-07-05
> **caljohnsmith said:**
> Sure, just do "sudo visudo" to open up sudoers with vi, or if you prefer to use nano like I do, you can use "export EDITOR=nano && sudo -E visudo".

I am having the same problem as Jalexxi was, I want to make firestarter start without requiring the password to initialize.

I've tried the above commands, sudo visudo in the terminal just seems to allow me to read without editing ability (not even entering text), the nano type command allows me to enter text, but my own ignorance keeps me from *saving* the file.  If you can help me to save this file, it'd be appreciated.

---

### Post by sisco311 on 2008-07-05
in nano:
Ctrl+o Enter - save
Ctrl+x - exit
Ctrl+x, Y, Enter - save and exit

---

### Post by FeyerbrandX on 2008-07-05
Thanks Sisco,

I've managed to add the following strings to the end of the sudoers file:

hpuntu ALL=NOPASSWD:/usr/sbin/firestarter
Jason ALL=NOPASSWD:/usr/sbin/firestarter

In line with what the firestarter site recommended, however they still don't recognize the bypass at startup.  Am I overlooking a space, or adding one that shouldn't be?

---

### Post by bodhi.zazen on 2008-07-05
> **FeyerbrandX said:**
> Thanks Sisco,

I've managed to add the following strings to the end of the sudoers file:

hpuntu ALL=NOPASSWD:/usr/sbin/firestarter
Jason ALL=NOPASSWD:/usr/sbin/firestarter

In line with what the firestarter site recommended, however they still don't recognize the bypass at startup.  Am I overlooking a space, or adding one that shouldn't be?

You should not be starting Firestarter this way. Firestarter is a graphical front end for iptables and should be used to configure iptables only (Firestarter should then be closed). Your firewall will remain active, even with rebooting.

As you can see, firestarter runs as root and should not be used to monitor your network.

Even better then firestarter, use ufw :

        [uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

---

