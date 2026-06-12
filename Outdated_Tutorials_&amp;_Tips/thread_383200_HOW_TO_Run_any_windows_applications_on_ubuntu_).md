---
title: "HOW TO: Run any windows applications on ubuntu :)"
date: 2007-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by edmondt on 2007-03-13
I think it deserves another thread because it works so damn well. I can now run Paint Shop Pro XI, Photoshop CS2, Quicken XG, and pretty much any application better and faster than with [Parallels' Coherence mode on the MAC/]("http://www.parallels.com/products/coherence/") , there are other how tos on this, please follow them:

[http://www.ubuntuforums.org/showthread.php?t=224212&highlight=rdesktop](http://www.ubuntuforums.org/showthread.php?t=224212&highlight=rdesktop)

or 

[http://www.ubuntuforums.org/showthread.php?t=361528&highlight=rdesktop](http://www.ubuntuforums.org/showthread.php?t=361528&highlight=rdesktop)

I would like to add: Instead of using QEMU which is really slow, to instead use VMWare Server and install XP Pro on it. Also in the VMWare Server Console to set On host Power up to "Power on virtual machine".

Then create a shortcut on your launcher:

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Pegtop\PStart\PStart.exe" 192.168.0.126:3389 -u "My Username" -p mypassword

---

### Post by BigBastard on 2007-06-28
Answered my own question by reading :-O

BB

---

### Post by vexorian on 2007-06-28
> **BigBastard said:**
> Answered my own question by reading :-O

BB
3d acceleration in virtual machines is something we are still dreaming of... I wouldn't hold my breath...

---

### Post by edmondt on 2007-07-02
There is a patched version of the rdesktop with the following features (quoted from the website)

[https://www.fontis.com.au/rdesktop](https://www.fontis.com.au/rdesktop)

The patch currently adds the following features:

    * Connection sharing - allows a single rdesktop connection to launch multiple applications. When run in seamless mode, rdesktop creates and
      listens on a control socket. A new option allows rdesktop to be run in
      slave mode, which notifies the master rdesktop instance of a new command
      to be run and then exits. The master instance sends a client-to-server
      message to the SeamlessRDP server component, which runs the new command.
    * Icon support - SeamlessRDP X windows have the same icon as their Windows counterparts, instead of the default X icon. When a new window is created on the server, the server component sends a 16x16 icon back to the client via a server-to-client message.
    * Always-on-top windows - previously, if a window was always-on-top on
      the server, it wouldn't be on the client. It was possible to get into a
      situation where the client and server didn't agree on what window was
      topmost, which led to some unusual effects (ie a window appearing to
      slide 'under' the side of another window). Windows that are
      always-on-top on the server (WS_EX_TOPMOST flag set) now have the
      _NET_WM_STATE_ABOVE hint set, which should keep them on top on the
      client side as well.
    * Tooltips - some applications had issues with tooltips, such as
      causing their parent window to lose focus while they were displayed. The
      server component now attempts to tell when a window is a tooltip and
      so that the client can treat the window correctly.
    * Closing windows - instead of ending the whole rdesktop process when
      one client-side window is closed, a client-to-server message is sent to
      tell the server to close the corresponding server-side window.
 
[[IMG]https://www.fontis.com.au/system/files/images/seamlessrdp-screenshot-kde.medium.png[/IMG]]("https://www.fontis.com.au/system/files/images/seamlessrdp-screenshot-kde.png")

---

