---
title: "[SOLVED] Removal of some boot options lost my audio and wireless"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Berean on 2008-05-17
Hi,

I think I've been silly and lost audio and wireless after removal of some boot options!  I had to download modules for Virtual Box and following this ended up with additional boot options - 386, Virtual, Server, Open v3, generic, but don't remember which was already there - and so had a full screen of boot options.  Deleting those I didn't think I needed (virtual, server, open v3, generic) but when I booted I no longer have wireless or any audio.  I attempted to reinstall these from Synaptic, but still have no wireless or audio.  What do I need, and what do I need to get rid of before I can start to get wireless and audio working again?  Your advice is appreciated.  Regards,

---

### Post by philinux on 2008-05-17
Have a look in /boot/grub for you old menu.lst file when you made the changes it should have created a backup named menu.lst~

Check the date stamps by viewing in list mode. All you need to do is copy the file back from either cli or gksudo nautilus

---

### Post by Berean on 2008-05-17
philinux,

thank you.  However, I'm a relative newb so where do I find this information?  I appreciate your advice, cheers.

---

### Post by philinux on 2008-05-17
Use 

```
gksudo nautilus
```

In a terminal - applications>accesories>terminal.

Be careful you have full admin rights with this.

Use the nautilus browser to navigate to the file system then to the directories.
boot then grub. select view as list then look for menu.lst~

The ~ is important it signifies a backup file.

---

