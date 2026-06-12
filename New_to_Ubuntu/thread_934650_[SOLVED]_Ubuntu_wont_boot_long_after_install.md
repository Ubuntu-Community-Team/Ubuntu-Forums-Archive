---
title: "[SOLVED] Ubuntu wont boot long after install"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-09-30
Ive had ubuntu hardy installed on my pc since its been out and all of the sudden It wont boot. It gets to a screen where it tells me what its dong and says starting up blue tooth. Which A. I have no blue tooth devices or anything in the pc to detect blue tooth and B. thats as far as it gets. 
And help is MUCH MUCH appreciated because Im stuck with winblows until then

---

### Post by Zzl1xndd on 2008-09-30
When did this start happening? after an Kernel update perhaps?

---

### Post by SpenceMakesSense on 2008-09-30
no...it happened yesterday. And I think the reason is is because instead of letting it shut down correctly i held the button down to force shut it down.

---

### Post by SpenceMakesSense on 2008-10-01
bump

---

### Post by shifty_powers on 2008-10-01
have you tried going into the grub menu and using the recovery mode?

---

### Post by SpenceMakesSense on 2008-10-01
yes...still not much help there still hanging when starting bluetooth

---

### Post by karlr42 on 2008-10-01
If you can access your ubuntu files from windows, find /etc/modprobe.d/blacklist , edit it with notepad and add 
```

blacklist hci_usb

```
to the end. That disables bluetooth. Then try booting ubuntu again.

---

### Post by SpenceMakesSense on 2008-10-01
well after 4 failed attempts to fix it with a live cd I went back and it ended up booting so I'm not sure what it did..I wouldnt be amazed if it fixed itself

---

