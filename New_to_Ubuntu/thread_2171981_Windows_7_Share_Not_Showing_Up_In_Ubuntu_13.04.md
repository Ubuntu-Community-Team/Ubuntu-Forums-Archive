---
title: "Windows 7 Share Not Showing Up In Ubuntu 13.04"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by Bob_Blake on 2013-09-02
I finally decided to dive into Ubuntu, and I've got it successfully installed alongside Windows 7 on my Lenovo Thinkpad X1 Carbon.  Everything appears to be working smoothly, with one exception: I've got a Windows 7 PC on my home network set up with a couple of shared folders, and I can't seem to get it to show up in Ubuntu.  I've never had any trouble with any of my other computers.

If I go into the Ubuntu file manager, I can see my network - and I can see my router's built-in share (READYSHARE).  But not my other PC.  I've tried setting my workgroup in smb.conf, which didn't help.  I've tried searching around, but can't seem to find anyone with this same problem.  Am I missing something simple?

Thanks in advance!

---

### Post by cariboo on 2013-09-03
There could be several problems. The first one to check, is to see if the two systems are in the same work group, Ubuntu uses workgroup as the default, and if I remember correctly Windows 7 home version uses MSHOME. When you open Nautilus and click Browse Networks, you should see all the systems with shares properly setup displayed in the window, there should also be a Windows network icon, when you click on that do you see any work groups?

---

### Post by Bob_Blake on 2013-09-03
Thanks for the response.  I've updated my Ubuntu workgroup in smb.conf to match the one that my other computer is set to - and when I go into "Browse Networks" and then click on "Windows Network" I do see the workgroup.  However when I click on that, all that shows up is my router and the Ubuntu laptop itself.  No Windows machine.  Any other ideas?

---

### Post by sandyd on 2013-09-03
Ive sometimes noticed that it _doesnt_ show up, but you can browse the shares from both sides (windows and linux) by directly entering the IP of the computer that you want to access. In windows, typing \\ip-address-here should open the shares on the computer. Also, make sure you have homegroups disabled, or else sharing will not work on the windows side.

---

### Post by Bob_Blake on 2013-09-04
Okay, if I use smbclient with the IP address, I can connect to any of my shares and browse from the terminal.  However that doesn't give me access from any GUI elements, which would be nice because I use that computer as a file server.  

I also tried running:
```
smbclient -L //192.168.1.101
```

After entering my password, this is the response that I got to that command:

```
session request to 192.168.1.101 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[BOBDESKTOP] OS=[Windows 7 Professional 7601 Service Pack 1] Server=[Windows 7 Professional 6.1]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    D$              Disk      Default share
    E$              Disk      Default share
    F$              Disk      Default share
    H$              Disk      Default share
    I$              Disk      Default share
    IPC$            IPC       Remote IPC
    K$              Disk      Default share    
    Multimedia      Disk      
    Music           Disk      
    U$              Disk      Default share
    Users           Disk      
    Y$              Disk      Default share
    Z$              Disk      Default share
session request to 192.168.1.101 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available

```

It seems like there are a lot of errors related to "Called name not present", however it was able to resolve the name of the computer and its OS information.  Could this be part of the problem?

Also, incidentally, I do have homegroups enabled on the Windows machine - it seems like that might prevent IT from seeing the Ubuntu machine, but not vice-versa.  Maybe I'll try disabling it anyway and see what happens.

---

### Post by sandyd on 2013-09-04
Do you have winbind installed btw?

---

### Post by Bob_Blake on 2013-09-04
Okay, I tried disabling homegroups and restarting my Windows machine; I still can't see its shares from my Ubuntu laptop.  Also, it appears that I do have winbind installed, though I've never done anything to configure it.

Any other ideas?

---

### Post by Bob_Blake on 2013-09-04
One more thing - I just tried mounting the shared folder using its IP address.  I sudo mkdir'd a folder under /media, then sudo edited my fstab file to include this line:

```
//192.168.1.101/Multimedia/Music /media/Music cifs guest,uid=1000 0 0
```

That got a "Music" folder mounted in the Nautilus sidebar; however when I click on it there is just an empty directory.

Not sure if that helps or not, just thought I'd mention it.  Thanks!

---

