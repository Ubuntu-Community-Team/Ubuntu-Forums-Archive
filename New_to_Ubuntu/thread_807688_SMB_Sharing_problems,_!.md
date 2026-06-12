---
title: "SMB Sharing problems, !"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-26
Hi,
trying to share a windows folder, from ubuntu. However when I try I get this message: 

'net usershare' returned error 255: net usershare add: cannot share path /media/disk/Robin's Folder as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

I check the smb.conf, to find that this line doesn't exist. I did uncomment the line: usershare max shares = 100

But didn't help..
Any clues would be great..
Thanks for considering! ;]

---

### Post by ZabiGG on 2008-05-26
> **hungryOrb said:**
> Hi,
Ask the administrator to add the line "usershare owner only = False" 
    to the [global] section of the smb.conf to allow this.

I check the smb.conf, to find that this line doesn't exist. I did uncomment the line: usershare max shares = 100

Just find the Global header in the file, and paste 

usershare owner only = False

on a new line at the end

Hope this helps :)

---

### Post by hungryOrb on 2008-05-26
Thankyou Zabigg! Will try it! :D

---

### Post by kewljoe on 2008-07-02
I just ran into this problem BUT I am a UBUNTU NOOB so where is this smb.conf file ?? Ive tried searching for it w/ google desktop and cannot find its location....

---

### Post by Krydahl on 2008-07-02
/etc/samba/smb.conf

---

### Post by superprash2003 on 2008-07-02
to edit the smb.conf file go to the terminal and type sudo gedit /etc/samba/smb.conf and a text editor would open with the file.. edit the file and save/close it

---

### Post by beholdforiambob on 2008-07-11
what is the etcetera implied in ect

-sorry as you can tell I'm a total noob

---

### Post by jamesrfla on 2008-07-11
You need to reboot. I had the same problem. If you still have the problem after reboot then you didn't have my problem.

---

### Post by beholdforiambob on 2008-07-11
forget every thing i have posted. I figured it out. it was a simple copy paste error I had forgotten to put a space between gedit and /ect/samba/smb.conf

---

