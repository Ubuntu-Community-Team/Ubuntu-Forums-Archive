---
title: "Problems with SAMBA GUI tool in 11.10"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by NickB. on 2011-10-25
I am working with a fresh install of 11.10, installed samba from the software center, and I cannot get the GUI tool to work.  That doesn't mean I'm dead in the water (I can fumble through the other methods to get there) but I have seen references in multiple places to this issue and I was curious if this was a real problem or a me-problem.

All of the packages appear to be installed/updated properly.  Launching from Dash, it prompts for authenticated access and then nothing happens.  Launching from a command line (**gksu system-config-samba**) it *was* giving this error 4 times:[INDENT]*(gksu:8137): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",*
[/INDENT]...and then nothing.  I found a reference to that error, and it went away with a[INDENT]**sudo apt-get install gtk2-engines-pixbuf**[/INDENT]So now when I try to launch from a command line, no errors now... just nothing.  For reference:


**dpkg -l | grep samba**
[I]ii  samba                                  2:3.5.11~dfsg-1ubuntu2                  SMB/CIFS file, print, and login server for Unix
ii  samba-common                           2:3.5.11~dfsg-1ubuntu2                  common files used by both the Samba server and client
ii  samba-common-bin                       2:3.5.11~dfsg-1ubuntu2                  common files used by both the Samba server and client
ii  system-config-samba                    1.2.63-0ubuntu4                         GUI for managing samba shares and users[/I]


**dpkg -l | grep smb**
[I]ii  libsmbclient                           2:3.5.11~dfsg-1ubuntu2                  shared library for communication with SMB/CIFS servers
ii  python-smbc                            1.0.10-0ubuntu2                         Python bindings for Samba clients (libsmbclient)
ii  smbclient                              2:3.5.11~dfsg-1ubuntu2                  command-line SMB/CIFS clients for Unix
[/I]

Any ideas how to further troubleshoot system-config-samba - is there a log file somewhere?


Regards.

---

### Post by NickB. on 2011-10-27
I gave it a couple days and a couple of sudo apt-get upgrade -f (in case something changed somewhere). but now when I try the gksu launch option it returns this (is this a trace?):

**gksu system-config-samba**
[I]Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade
[/I]
I installed glade and the error went away... but no change to the Samba GUI - gksu just returns to the prompt and launching from dash prompts for credentials and then goes away.

Is anyone else having this problem with 11.10?

---

### Post by Leap Frog on 2011-10-30
Yes, I'm having the exact same problem.  Fresh install of 11.10 on a new drive, followed by an update.  Same diagnostics from [B]gksu system-config-samba

NB: [U][https://bitbucket.org/janto/pynetkey/issue/21/unable-to-locate-theme-engine-in](https://bitbucket.org/janto/pynetkey/issue/21/unable-to-locate-theme-engine-in)
[/U]
and[U]

[https://bitbucket.org/janto/pynetkey/issue/19/ubuntu-1110-support](https://bitbucket.org/janto/pynetkey/issue/19/ubuntu-1110-support)
[/U] [/B]

---

### Post by Leap Frog on 2011-10-30
FYI, adding pyNeighborhood to the slate of installed software is a work-around.

---

### Post by Maddog Battie on 2011-10-31
I've hit this problem also. Can you tell me how to "FYI, adding pyNeighborhood to the slate of installed software is a work-around."?

Cheers. MdB

---

### Post by Maddog Battie on 2011-10-31
On another thread I found the following which fixed it for me:

sudo apt-get install gtk2-engines-pixbuf
sudo apt-get install glade-gtk2

---

### Post by NickB. on 2011-11-03
> **Leap Frog said:**
> FYI, adding pyNeighborhood to the slate of installed software is a work-around.

That fixed it for me - thanks!

for reference:
[B]
sudo apt-get install pyNeighborhood[/B]

---

### Post by gordintoronto on 2011-11-03
But what did you want to do? I frequently try different versions/distros, I always set up and use shared folders, but I've never needed to use the Samba GUI tool.

---

### Post by adrian0301 on 2011-12-13
> **NickB. said:**
> That fixed it for me - thanks!

for reference:
[B]
sudo apt-get install pyNeighborhood[/B]



That worked for me too! (same problem)

---

