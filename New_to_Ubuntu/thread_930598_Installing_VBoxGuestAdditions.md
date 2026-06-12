---
title: "Installing VBoxGuestAdditions"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by JayCeeEll on 2008-09-26
I have installed Ubuntu as a guest OS running in VirtualBox hosted on Windows XP Pro SP3.

In the help for VirtualBox it says: 

> Mount the VBoxGuestAdditions.iso file as your Linux guest's virtual CD-ROM drive, exactly the same way as described for a Windows guest in Section 4.2.1.1, “Mounting the Additions ISO file”.

Change to the directory where your CD-ROM drive is mounted and execute as root:

sh ./VBoxLinuxAdditions-x86.run


I have been able to mount the ISO, but when I run the terminal application I have no clue how to change to the CDRom (mounted as cdrom0 under the media browser)
I have tried various commands including CD that might have worked under windows, but no joy.

I have also tried to use ALT-F2 on the .run file but Ubuntu say it must be run as Administrator.

So could someone please tell me how to
1) Change to cdrom0 in Terminal

2) run "sh ./VBoxLinuxAdditions-x86.run" as administrator.

---

### Post by Thelasko on 2008-09-26
To run a program as an administrator you need to put the command "sudo" before the program you intend to run.

As for changing your directory to the CD drive, I cheat.  I just drag the file to the terminal window and it automatically inserts the path into the command line.

In summary, open the terminal and type sudo, then drag the "VBoxLinuxAdditions-x86.run" file over to the terminal window and the path to the file should be displayed, press enter.  You will be prompted to enter your password, do so.

---

### Post by JayCeeEll on 2008-09-26
Worked like a charm thanks. :)

---

