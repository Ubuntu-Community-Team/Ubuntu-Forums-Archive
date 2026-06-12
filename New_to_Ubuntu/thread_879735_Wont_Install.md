---
title: "Wont Install"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by Kurasu1415 on 2008-08-04
After booting to the dvd, it loads to the ubuntu startup where I select elnglish as my language and select "install ubuntu" after that the loading screen starts. Then it goes to a screen where it lists errors like something about a read buffer error FD0. I dont know what is going on. I checked and the download was ok. Anyone have a solution?

---

### Post by hyper_ch on 2008-08-04
what's your videocard?

---

### Post by AdamWood on 2008-08-04
When you say you checked the download was OK, did you also check the DVD was burned correctly?

---

### Post by ET! on 2008-08-04
it says read buffer error so probablythe problem is in your dvd...

---

### Post by Kurasu1415 on 2008-08-04
I burned it 3 times, using infrarecord. Anyone have a suggested software to use?

---

### Post by Kurasu1415 on 2008-08-04
> **hyper_ch said:**
> what's your videocard?

My videocard is an nvidia 7300.

---

### Post by AdamWood on 2008-08-04
With the CD in the drive you can open a terminal by pressing ALT+F2 and typing gnome-terminal, then click run. In the window that appears you should type.
```

md5sum /dev/cdrom

```
This will take quite a long time. You can then check the long list of numbers and letters that is eventually displayed against the MD5SUMS file that can be downloaded from the Ubuntu site. Maybe someone else can post a link if they have the address handy.

---

### Post by fiddledd on 2008-08-04
I seem to remember a bug that caused this error on certain hardware if there was no floppy drive. But it was in feisty or gutsy, so I would imagine it was fixed by hardy. I think the workaround was to use the Alternate Dvd. But like I said, I'm not 100% sure on this.

---

### Post by Kurasu1415 on 2008-08-04
that would make sense, because I don't have a floppy drive installed. Ill try to alternate install.

---

