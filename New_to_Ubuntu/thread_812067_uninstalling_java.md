---
title: "uninstalling java"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by gallen on 2008-05-29
Hi

I am a complete and total noob at linux and was trying to install java as a test at installing something that wasn't a .deb file, i downloaded the latest self installing .bin file thingy and managed to turn it into a executable file by following several web guides and about half an hours experimentation. I then installed it but it appears to have installed to the desktop as i have a folder called jre1.6.0_05 permanently stuck there and i cannot figure out how to remove it. I tried searching for it using synaptic but i cant find it. It shows a graphic of a padlock and tells me that i am not the owner and that root is. I understand that Ubuntu doesn't let you get access to root for security reasons but i'm stuck well and truly.

If anybody out there is willing to help a total noob i would be grateful.

cheers

---

### Post by dorkdork777 on 2008-05-29
I'm no expert at installing/uninstalling software, but if you know that you *definitely* need to remove that folder, here's how to do it.

First of all, run this command:
```
gksudo nautilus
```
That will open a single window of the file manager with root permissions. In the left-hand column, go into File System, then into the folder called "home". Go into the folder corresponding to your username, then into Desktop. From there you can delete the folder.

I'm not 100% certain that will fix your problem, but that's how to remove the folder.

---

### Post by ChompTheMan on 2008-05-29
Simply deleting the folder will remove Java.  Open a terminal and

```
sudo rm -r Desktop/jre1.6.0_05
```

If you are going to attempt this again then follow the instructions here: [http://www.java.com/en/download/help/5000010500.xml#install]("http://www.java.com/en/download/help/5000010500.xml#install")

---

### Post by gallen on 2008-05-30
Hi All

Thanks guys that did the job perfectly, do you know if there are any good books that have these commands written down in super clear language so i can practice as i see Linux playing a bigger role in my life and would like to become more competent.

Many Thanks

---

### Post by mick222 on 2008-05-30
hi these web pages give a lot of info on using the terminal be careful though some commands can damage your systym 

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=2](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=2)

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=2](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=2)

 I find the second link to be very good if a bit technical at times , me not being the most experienced linux user.

---

### Post by Miljet on 2008-05-30
> **ChompTheMan said:**
> Simply deleting the folder will remove Java.  Open a terminal and

```
sudo rm -r Desktop/jre1.6.0_05
```

If you are going to attempt this again then follow the instructions here: [http://www.java.com/en/download/help/5000010500.xml#install]("http://www.java.com/en/download/help/5000010500.xml#install")

Those instructions will not work in Ubuntu! I tried for about a week before I realized that it is only for Red Hat (and its variants.) Scroll back up on the page and check out the operating systems it will work on.

---

