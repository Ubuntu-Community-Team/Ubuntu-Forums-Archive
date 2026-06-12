---
title: "Sharing files between Win7 (host) and Ubuntu 12.04 (guest) in VirtualBox"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by OrchidStar on 2012-06-25
Hi- I am running Windows 7 64bit (host) and Ubuntu 12.04 64-bit (guest) in Oracle VirtualBox. I have attempted to share a folder between the host and guest OS. I installed Guest-Additions and have setup my shared folder in the Settings -> Shared Folders within VirtualBox. Since I set up my shared folder to automatically mount in ubuntu it can be seen in the /media directory in Ubuntu.  My problem is that I can see the shared folder but not the files that I added to it from the Windows side. Nor can I see the files I placed in the shared folder from Ubuntu. So basically I can see the shared folder but not the files within it. So I can't seem to share any of the files between Win7 and Ubuntu. Does anyone know what the problem might be?

Thanks in advance.

---

### Post by critin on 2012-06-25
> **OrchidStar said:**
> Hi- I am running Windows 7 64bit (host) and Ubuntu 12.04 64-bit (guest) in Oracle VirtualBox. I have attempted to share a folder between the host and guest OS. I installed Guest-Additions and have setup my shared folder in the Settings -> Shared Folders within VirtualBox. Since I set up my shared folder to automatically mount in ubuntu it can be seen in the /media directory in Ubuntu.  My problem is that I can see the shared folder but not the files that I added to it from the Windows side. Nor can I see the files I placed in the shared folder from Ubuntu. So basically I can see the shared folder but not the files within it. So I can't seem to share any of the files between Win7 and Ubuntu. Does anyone know what the problem might be?

Thanks in advance.

You will also need to permit the SHARE the files inside of folders.  Do that on permissions tab.  Do permissions AND shares in the same places.  You can right click, go to PROPERTIES and work from there.

---

### Post by OrchidStar on 2012-06-25
> **critin said:**
>  Do that on permissions tab.  Do permissions AND shares in the same places.

Thanks for your response.

I agree that something isn't right with my permissions since both guest and host can't see the files but only my shared folder.

Here is what my settings are:
In Ubuntu settings under the permissions tab  I can't seem to get the File access selection to stay on "Read and Write" after selecting the close button. I also tried selecting the Apply permissions to enclosed files button...that didn't work. However, when I open up a terminal and check the permissions on the folder (ls -l) and a test text file that I created,  both say that the user and the group has permission to read, write, and execute files within my shared folder.  Note that my user is part of the group vboxsf.
Also, my shared file has folder sharing enabled and is shared by any user on the system (which is just me).

---

### Post by critin on 2012-06-25
> I can't seem to get the File access selection to stay on "Read and Write" after selecting the close button.

The text won't be there, but it is if the permissions were given.  Mine is blank too.  I would say it's a Win7 issue.  I run XP and am able to read/write from ubuntu and XP. 
There are three areas to permit sharing.  One is right clicking on the folder, the next two are in Properties.  I use them all.  I also have Samba installed.  If you didn't install it, it would be installed when you gave permission for the files inside to be shared--it would have asked if you wanted to install the program to allow sharing.

I don't know Win 7--sorry.
I'm trying to set up Win 8 to network, but haven't got past the password dilemma yet.  lol  XP is so simple!

---

### Post by OrchidStar on 2012-06-25
> **critin said:**
>   I also have Samba installed.  If you didn't install it, it would be installed when you gave permission for the files inside to be shared--it would have asked if you wanted to install the program to allow sharing.


I also installed Samba previous to this post thinking that would help but  nope. On another computer I had I used Win7 (host) with Ubuntu 10.04 LTS (guest) in VirtualBox and I was able to share files no problem. So it could be 12.04 or like you mentioned Win7. It's hard to tell...maybe the combination. I always found sharing files across Wiindows and Ubuntu not as simple as it seems. If I can't find a solution I'll probably install 10.04 again and work with that.

---

### Post by critin on 2012-06-25
Here's a link I intend to study. I hope it has the answers you need.

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

---

