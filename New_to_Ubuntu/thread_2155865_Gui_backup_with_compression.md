---
title: "Gui backup with compression"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2013-06-19
Hi I have used defa-dup and backintime and want one of these to just backup data and compress it don't care if it encrypts it just want data backup and compressed. Going from one hard drive to another and need data compressed. I don't know much about backups so does any one have any ideas?

---

### Post by ahallubuntu on 2013-06-19
~

---

### Post by monkeybrain2012 on 2013-06-19
Do you just want to backup and compress your data or to clone the whole system?

For cloning I recommend fsarchiver, there is a gui version called qt4-fsarchiver which you can get from source forge. But I prefer the command line one, it is is really easy to use and has many more useful options like excluding folders that you don't want to back up. 

Never use Clonezilla but I know that Clonezilla cannot restore to partition smaller than the original one even if only a small part of it has data, this is kind of stupid if I want to restore to a different hard drive or repartition. Fsarchiver can do this and it also does live backup so you can use your computer while it clones the system (with some restrictions to what you can do, so that the image would be as consistent as possible) and you can choose your level of compression. Backing up and restoring are both done with a single command.

---

### Post by lance bermudez on 2013-06-19
my bad let me clarify I want to back up Ubuntu/windows files to another hard drive that is usb removable. No need for cloning just backing up files.

---

