---
title: "what's this i see with 'sudo nautilus'?"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by smokingates on 2014-07-05
O.S : ubuntu 14.04LTS
when i open a terminal and run sudo nautilus i get the following in the terminal but the nautilus opens as it should:

[FONT=arial black](nautilus:3389): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
[/FONT]

---

### Post by plucky on 2014-07-05
> **smokingates said:**
> O.S : ubuntu 14.04LTS
when i open a terminal and run sudo nautilus i get the following in the terminal but the nautilus opens as it should:

[FONT=arial black](nautilus:3389): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
[/FONT]

Have you ever enabled file sharing (samba) on the system?

In your normal user account, open Nautilus, right click on a folder and select "Local Network share". Tick the box in the window that opens, to share the folder and the system will install network sharing service. Once it is installed,that error message should go away and you will be able to share folders across your network.

Good Luck

---

### Post by smokingates on 2014-07-05
I had samba on my ubuntu that was running in virtualbox with windows as host however I have since deleted the windows partitions on my HD and installed Ubuntu 14.04LTS 3 times, each time I chose the "remove and re-install" option and none of those 3 have been anywhere near samba - at least to my knowledge. The reason for having it before was to try to share files and folders from windows to ubuntu. I want to do all BUT share files and folders on this network. Thank you for your help thus far.

---

### Post by capscrew on 2014-07-05
> **smokingates said:**
> O.S : ubuntu 14.04LTS
when i open a terminal and run sudo nautilus i get the following in the terminal but the nautilus opens as it should:

[FONT=arial black](nautilus:3389): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
[/FONT]

The 2 error messages; neither one of them are not really attributable to Samba.  

The first error message (  Gtk-WARNING **: Failed to register ...) is a GUI warning because you opened a GUI application directly from the terminal using the wrong command.  

FYI:  The correct command is: ***gksudo nautilus***.  Using sudo with a GUI application causes userspace environment problems.   

The second error message (Nautilus-Share-Message: Called "net usershare info" ...) is a Nautilus application error message.  It is saying the there is no */var/lib/samba/usershares *directory.  This is normal if you haven't created any usershares.  The error is most likely due to you using *sudo* instead of *gksudo*.  I would look in */root/.config/nautilus *to see what is there.  You really should have nothing as the root user should not be using Nautilus at all.  The command *gksudo* runs the *nautilus* command as root but uses the calling username environment.

No amount of fiddling with Samba will cure either of the problems.  Stop using *sudo* for GUI applications and clean up the *root* users environment.

---

### Post by ajgreeny on 2014-07-05
You should **NEVER** use sudo for a GUI application, always gksudo, gksu, or kdesu if using kubuntu.  If you do so it is possible that you might lock yourself out of your user account on a machine as a result of wrong ownership of files and folders.

See Root-Sudo in my signature for more info.

---

### Post by philinux on 2014-07-05
Gksudo and others are deprecated now and not recommended any more. Pkexec is the new boy but it is not straightforward either.

Discussion here.

[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

---

### Post by ajgreeny on 2014-07-05
> **philinux said:**
> Gksudo and others are deprecated now and not recommended any more. Pkexec is the new boy but it is not straightforward either.

Discussion here.

[http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

WOW!!

That certainly is not straightforward, is it; most of the discussion in your linked post went over my level of understanding.

Are you suggesting that gksudo or gksu are unsafe to use?  If so, how do we get to a file-manager with root privileges, as when I try thunar-pkexec in terminal it gives errors.  I am aware of how to get to a terminal with root privileges, and from there can open thunar also with root privileges, but gksu[do] was, or is, still very useful as a timesaver.

PS:
I have just read that link again and as an example, it looks as it it may be possible to edit the current files in /usr/share/polkit-1/actions/ for synaptic and change the application shown from synaptic to thunar.

I am just about to try that and will report back.

---

### Post by philinux on 2014-07-05
@ajgreeny
Well yes indeed. Gksu is now not installed by default either. But between you and me ;) I still use gksu nautilus or I use nano on a system file.

Although post nine in that link has a simpler option that could easily made into an alias to use.

---

### Post by ajgreeny on 2014-07-05
> **philinux said:**
> @ajgreeny
Well yes indeed. Gksu is now not installed by default either. But between you and me ;) I still use gksu nautilus or I use nano on a system file.

Although post nine in that link has a simpler option that could easily made into an alias to use.
Thanks.  My attempt to edit the policy file for synaptic and change it to thunar did not work even after a reboot, so there is obviously more to it than I hoped.

I am aware that gksu is not installed by default as I also always install it and use it quite a lot, as well as in thunar-custom-actions. I will look again at that thread and see if I can sort it out.

---

