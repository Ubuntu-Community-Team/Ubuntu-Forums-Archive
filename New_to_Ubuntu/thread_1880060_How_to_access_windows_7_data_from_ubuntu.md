---
title: "How to access windows 7 data from ubuntu"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by lws.jazz on 2011-11-12
I just downloaded and installed ubuntu onto my Dell Inspiron mini 1012 hard drive running Win 7. I just want to find out how to access my music and pictures from Ubuntu. I don't see windows mounted as a partion in the home window. thanks in advance

---

### Post by jjex22 on 2011-11-12
Thats odd, it should appear as xxGB Filesystem in the left hand panel? try going to /media and see if anything is mounted there?

---

### Post by lws.jazz on 2011-11-13
Nothing in the left panel. I checked under "media," nothing there. 

When i installed ubuntu i didn't get prompted for a partition, i don't know if that matters.

thanks for the effort, btw.

---

### Post by deltacomp on 2011-11-13
what is the output of sudo fdisk -l

---

### Post by deltacomp on 2011-11-13
Hello again, go to this site and check it out. I think it will help
 
[the site ]("http://www.liberiangeek.net/2011/10/filesharing-between-windows-and-ubuntu-11-10-oneiric-ocelot/")

---

### Post by lws.jazz on 2011-11-13
i was able to activate samba, and the application shows up in dash, but after i click on it, and enter my password, the app doesn't appear. i entered an incorrect password into the samba log in to see if that was the problem but it gave me a incorrect password error. so it is accepting the password, just not displaying the program.

---

### Post by coffeecat on 2011-11-13
> **lws.jazz said:**
> When i installed ubuntu i didn't get prompted for a partition, i don't know if that matters.

Did you run a file called wubi.exe from within Windows? If you did, you have a wubi installation which is created in a virtual disk inside your Windows partition.

If you have a wubi system, click on "File System" in the left pane of a file browser window and open the /host folder.

---

### Post by beew on 2011-11-13
Is that WUBI? In a normal dual boot you should be able to mount the win7 partition from File System on the Nautilus's left panel. When  you open Naitilus, go to View > Side Pane and make sure that it is checked, otherwise of course you won't see anything.

If it is WUBI then this may not work, never use it.

---

### Post by lws.jazz on 2011-11-13
yeah, the sidebar is visible in the nautilus home screen, there's nothing mounted for windows.

thanks for all of your efforts, everyone.

---

### Post by Mark Phelps on 2011-11-13
When you install using Wubi, the Windows filesystem is automatically mounted, not under /media, but under /host.  Look there and you will find it.  You don't have to mount it because it's already mounted.

---

### Post by lws.jazz on 2011-11-13
thanks everyone, i went ahead and just replaced windows with ubuntu. i was going to eventually anyway. closing this out.

---

