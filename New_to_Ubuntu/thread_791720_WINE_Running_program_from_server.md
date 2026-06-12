---
title: "WINE Running program from server"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by thomsany on 2008-05-12
Hi!!
I have a software that I usually run on Windows from my company server. Its made in Visual Foxpro. I usually connect to the network share and run the EXE file from the server and run it live over the network.
I tried doing that using WINE but when the program opens up, it tries to look for files inside my home folder, not the remote folder where the software is located.
Any suggestions on how I can make WINE tell the program to look for the required files in the path where the EXE files is located?

Thanks much in advance,

Teo

---

### Post by Six_Digits on 2008-05-12
I would say you'd actually have to try installing the program in wine. It runs from its own little "File System". I'm pretty sure you cant use wine at all to run programs that are already installed on a Windows partition.

---

### Post by Rhubarb on 2008-05-12
I'm not too sure how it'd be possible to do this, especially if the server that's hosting the files is running windows.

But, it may just be possible to get it working.  You may have to run a script to copy the executable across to a client's .wine directory.
Failing that, it is possible to tell wine to use any directory name so it doesn't have to use ~/.wine
Have a look here:
[http://wiki.winehq.org/wineprefixcreate](http://wiki.winehq.org/wineprefixcreate)

---

### Post by Six_Digits on 2008-05-12
I think I misunderstood. You already installed it in wine? You're just looking for the files for it? Try copying them over from windows to the ~/.wine/drive_c/Program\ Files/ etc. directory.

---

### Post by thomsany on 2008-05-12
Can't copy the files over to the WIne folder because they change everytime. It has a FoxPro DB that users use across the network.
I got wine to see my network folder. It assigned the D: letter in the Winecfg.
Now what I want to do is just run the EXE file on the shared folder using Wine. For some reason wine doesn't look for the remote files in the other machine but tries to look for them on my local .wine folder.
I just want wine to use the files in the folder where I run the wine application from.

Regards,
Teo

---

### Post by thomsany on 2008-05-12
Can't copy the files over to the WIne folder because they change everytime. It has a FoxPro DB that users use across the network.
I got wine to see my network folder. It assigned the D: letter in the Winecfg.
Now what I want to do is just run the EXE file on the shared folder using Wine. For some reason wine doesn't look for the remote files in the other machine but tries to look for them on my local .wine folder.
I just want wine to use the files in the folder where I run the wine application from.

Regards,
Teo

---

### Post by Mauler5858 on 2008-05-12
Another idea is that if your company has a citrix server see if they will publish that application on the citrix server, and you can install the citrix ICA client on your computer and be able to run that natively.

Citrix is a program that runs all the backend stuff and processing of the program on the server, and then really all the client sees is the 'visual' side of it.  this way a program can run on any client there is a citrix client app for.

---

### Post by thomsany on 2008-05-13
ok got it working!! I did an automatic wine scan for drives and it found my network drive.
Now, is there a way I can reassign the drive letter for a particular share?

Regards,
Teo

---

### Post by bodhi.zazen on 2008-05-13
> **thomsany said:**
> ok got it working!! I did an automatic wine scan for drives and it found my network drive.
Now, is there a way I can reassign the drive letter for a particular share?

Regards,
Teo

yes. All the "drives" are located in ~/.wine/dosdevices

They are all symbolic links.

so ....

ls -l ~/.wine/dosdevices

to show the links ...

Then ...

unlink f:

ln -s /path/to/share/from/above/command ~/.wine/dosdevices/f:

in this example using f: , you can unlink and then re-link any letter you like.

---

### Post by thomsany on 2008-05-14
Excelent!!! Thanks soooo much :)
gotta love Ubuntu!!
I am not using Windows at all...

---

