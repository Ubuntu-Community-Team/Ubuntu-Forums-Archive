---
title: "How to save Boot Messages shown at booting into a file"
date: 2020-07-22
forum: New to Ubuntu
---

### Post by rahul_bhise on 2020-07-22
I am using ubuntu 20.04.
I want to store all the messages shown at the time of booting into a file.
they must be same to same as shown while booting. with same sequence.
can somebody help me in this.

---

### Post by ActionParsnip on 2020-07-22
```

dmesg > ~/Desktop/Boot\ Messages.txt

```

---

### Post by CatKiller on 2020-07-22
Minor addendum: I think you need sudo for dmesg now.

---

### Post by Impavidus on 2020-07-22
You can already find those in a file: /var/log/dmesg

---

### Post by deadflowr on 2020-07-22
> **CatKiller said:**
> Minor addendum: I think you need sudo for dmesg now.

The change only currently applies to 20.10 and newer.
20.04 and older still have all access to dmesg.
Reference article: [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.10-dmesg-Needs-Root]("https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.10-dmesg-Needs-Root")

---

### Post by &amp;wP*!) on 2020-07-23
**journalctl** already stores all boot messages in /var/log/journal directory. **journalctl --dmesg** shows what you need. It offers many more things. Look at its manual.

---

### Post by rahul_bhise on 2020-07-25
> **ActionParsnip said:**
> ```

dmesg > ~/Desktop/Boot\ Messages.txt

```

thankyou.

---

