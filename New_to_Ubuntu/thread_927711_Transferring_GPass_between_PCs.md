---
title: "Transferring GPass between PCs"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Matuku on 2008-09-23
I've recently bought a new PC and, as such, would like to transfer my GPass file, containing my passwords, over to the new PC; how would I go about this? I tried just copying the *.gps file over but it opened up blank.

If this is not possible can someone suggest a good, cross-platform, portable password manager?

---

### Post by Eaglesway on 2011-08-20
I have upgraded to Ubuntu 11.04 from 8.04
I want to transfer my gpass from the old system to the new. I have done it before previous versions.... ie from 8.04 to 8.04 on another computer. 

When copying the 3 gpass files (gpass, gpass-convert and gpasswd) to 11.04 it says that I don´t have permissions to copy files into the /user/bin

I Logged in as root in the terminal, and tried to change the permissions on the /user/bin ... it wouldn´t let me...... and tried to copy the files from my desktop to the /user/bin file directly.... and it still won´t let me .............. it still says I don´t have permission
Any ideas? 
Thanks

---

### Post by Eaglesway on 2011-08-21
I found a long list of about 20 files in different folders that have something to do with gpass. 

I have managed to change the permissions so I could copy the gpass files from my 8.04 system to the 11.04 system.... in /user/bin/..... into user/share/.... into user/share/doc/info/ etc etc

Despite copying at least 10 of the gpass files across, there is none of my entries visible when I open gpass on the 11.04 system. 

Does anyone have ideas as to which gpass file is the essential one..... (ie the file that holds my data) ..... or why it worked when I copied gpass, gpass-convert and gpasswd from the /user/bin in the 8.04 system and why it won´t work when I do the same thing copying into the 11.04 system. 

Thanks

---

### Post by Herman on 2011-11-17
If you're still using 11.04 you'll still be using GPass, you just need to look inside your /home/username directory and click 'View', 'Show Hidden Files', then look for your .gpass folder. When you copy it to your new installation it should be recognized next time you open GPass.

In 11.10 we're not using GPass anymore, apparently it's been superceded by Revelation Password Manager, See the following thread,[B] [GNOME Password Manager gone]("http://ubuntuforums.org/showthread.php?t=1862647&highlight=gpass") :D
[/B]

---

