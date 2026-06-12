---
title: "copying files from messed up hard disk"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by D._Floris on 2014-05-28
Hello,

I am very new to ubuntu, my apologies if my question is very dumb. I am helping a client to recover data from a broken LaCie external drive. Windows wouldn't read it but i 'freed' the harddisk from its plastic case and connected the drive to an old pc running Ubuntu and that does read the files reasonably fine. 
Now i am trying to copy the files on it to a new external drive, but some of the files are very slow copying, which holds up the entire queue of files. 
My trick is to copy multiple folders at once so if one file in folder stalls it doesn't stall everything. This seems to work a bit but there is a huge amount of project folders so it will take a lot of time.

Is there a program or trick that will copy in a similar way (not stall the entire queue for one file)?

I hope someone can help me.

---

### Post by papibe on 2014-05-28
Hi D._Floris. Welcome to the forum ):P

There are several tools you can use, but ddrescue could be a good candidate here.

Star taking a look at this tutorial: [Data Recovery]("https://help.ubuntu.com/community/DataRecovery"), and let us know if you have more questions.

Come here often and have fun.
Regards.

---

### Post by Richard_Romick on 2014-05-28
It sounds to me that you may want to run Spinrite on the drive before copying data.  Spinrite is a very helpful tool that will scan the hard drive for bad sectors and attempt to recover the data from it.  The bad news is that it costs money: 30$.  The good news is that if you get it, and you get a lot of people bringing hard driver that are running very slow or can't be read, you will probably make ample use of it.

I just want to emphasize before you consider buying it that it may or may not solve your current problem.  However, it sounds to me that it would fix your problem.

[https://www.grc.com/sr/spinrite.htm](https://www.grc.com/sr/spinrite.htm)

---

### Post by D._Floris on 2014-05-29
Hey thanks a lot for the tips. some seem a little daunting for me but i will try. 
At the moment the old computer is still working and the copying of folders is going slow but going. I just drag about 10 folders one by one from LaCie to the verbatim HD and when its done (usually a few hours) i repeat it for the next batch. I think it should be done before the weekend. 
After i am sure i saved the files the dumb way i am definitely trying dd rescue and spinrite with another old disk :)

---

### Post by kyle20 on 2014-05-29
[COLOR=#000000]ddrescue and spinrite are going to be your best bets. Otherwise, you could just select every folder to transfer and then walk away from your computer for a few hours :)[/COLOR]

---

### Post by stalkingwolf on 2014-05-29
download hirens tools  [www.hiren.info/pages/bootcd]("www.hiren.info/pages/bootcd")  under hard disk tools try the hdd regenerator tool.
might also try cloning the drive.

---

