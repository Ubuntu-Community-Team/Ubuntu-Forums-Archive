---
title: "How do I make a Startup Disk?"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by Melita on 2013-03-16
I need to make a startup disk for my Ubuntu 12.04. Could you please tell me where I can find instructions for using the 'Startup Disk Creator' found in Ubuntu Applications.

Thank you

---

### Post by sudodus on 2013-03-16
Please wait a while and consider what you have and what you want before going ahead! We are many people here to help :-)

- Please post the specs of your hardware, at least cpu, ram and graphics chip/card

- Please let us know what main tasks you want to run on the computer

- Would you prefer CD, DVD or USB for the boot drive.

Then we can suggest what iso file(s) to download, how to check them with md5sum, and how to make a boot CD/DVD or USB drive.

---

### Post by sudodus on 2013-03-16
The startup disk creator is rather self-explanatory, but you have more information here

[[COLOR=#ff0000]https://help.ubuntu.com/community/Installation/FromUSBStick[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Melita on 2013-03-16
> **sudodus said:**
> Please wait a while and consider what you have and what you want before going ahead! We are many people here to help :-)

- Please post the specs of your hardware, at least cpu, ram and graphics chip/card

- Please let us know what main tasks you want to run on the computer

- Would you prefer CD, DVD or USB for the boot drive.

Then we can suggest what iso file(s) to download, how to check them with md5sum, and how to make a boot CD/DVD or USB drive.

I already have Ubuntu 12.04 installed in my computer - Main Board Asus P5LD2. For this, I downloaded Ubuntu on to a DVD and installed successfully. In the 'Applications' at Home page I saw the 'Startup Disk Creator'. I am assuming this to be something that I can create and use in the event of a boot failure. If I am correct in assuming this, then I want to create a bootable disk, on a DVD (I don't have CDs), and keep it with me.

Thank you.

---

### Post by kuifje09 on 2013-03-16
Just for in case of rescue your system you could use your install DVD.  Just boot it to maintanance or recue mode or even a shell prompt.

But I just found a tutorial movie here: [http://www.youtube.com/watch?v=DaP6nin7sFw](http://www.youtube.com/watch?v=DaP6nin7sFw)

---

### Post by sudodus on 2013-03-16
> **Melita said:**
> I already have Ubuntu 12.04 installed in my computer - Main Board Asus P5LD2. For this, I downloaded Ubuntu on to a DVD and installed successfully. In the 'Applications' at Home page I saw the 'Startup Disk Creator'. I am assuming this to be something that I can create and use in the event of a boot failure. If I am correct in assuming this, then I want to create a bootable disk, on a DVD (I don't have CDs), and keep it with me.

Thank you.

No it is not exactly like that. Startup disk creator is a tool to create an Ubuntu install USB drive, which is an alternative to an Ubuntu install CD/DVD drive. If you want a backup, there are other tools for that. I suggest that you get an external drive with USB and or eSATA connection(s) and use some kind of backup tool.

There are several ways to make backups:

- Clonezilla can make an image, that can be used to restore an exact copy of your file systems on the internal drive.

- rsync can be used to backup partitions, directory trees etc more or less automatically. There are several GUI tools, that use rsync as the backend (the engine under the hood).

- Other tools, that have their own engines.

Browse the internet for ***linux backup tools*** or something similar. Or ask for tips here or in a new thread with an appropriate title to attracts those who are interested in backup.

---

### Post by Melita on 2013-03-17
Than you for this comprehensive information. I will make another post as you suggest in a different section of the forum.

Kind regards.

---

