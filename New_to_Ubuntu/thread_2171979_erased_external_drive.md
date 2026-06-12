---
title: "erased external drive"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by mikhaell on 2013-09-02
Hi,
I accidentally erased my passport external disk (forgot it was in the computer while using startup disk creator with another usb...)
Now i can't access the passport at all (computer cannot read files; input /output error). Is there any way to retrieve the files, or at least use the passport which isnn't working now?
thanks

---

### Post by Jonathan Precise on 2013-09-02
Try testdisk. Also, _**DO NOT WRITE TO THE DRIVE!!!!!**_&#8203; This can overwrite your data.

---

### Post by mikhaell on 2013-09-02
i downloaded testdisk but don't know how to use it. example- what is my partition table type? many thanks

---

### Post by mikhaell on 2013-09-02
i don't mind losing the info on my passport- but at this point it is not working at all (says that it cannot read some of the files and there is an input/output error)- any thoughts on how to format the drive?

---

### Post by Jonathan Precise on 2013-09-02
> **mikhaell said:**
> i downloaded testdisk but don't know how to use it. example- what is my partition table type? many thanks

Just run testdisk from the terminal. Check in Gparted for your USB, usually /dev/sdb. But check first!!!

---

### Post by Jonathan Precise on 2013-09-02
> **mikhaell said:**
> i don't mind losing the info on my passport- but at this point it is not working at all (says that it cannot read some of the files and there is an input/output error)- any thoughts on how to format the drive?

To format, use Gparted, and format the partition.

---

### Post by mikhaell on 2013-09-02
none of this works- i still can't mount my passport. I get the message : Sorry, could not display all the contents of &#8220;My Passport&#8221;: Error when getting information for file '/media/*name*/My Passport/WinMac_Sync': Input/output error

---

### Post by steeldriver on 2013-09-02
Those passport drives are kind of funny - unless you completely wiped and formatted it before use, it probably still has the original Windows-only 'unlocker' on it - which makes it look like a virtual CD initially when you boot

If you have access to a Windows box, see if you can access it from there, at least to run / disable the lock feature

---

