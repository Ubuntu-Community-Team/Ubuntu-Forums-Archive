---
title: "listing many lines before startup begine with green [ok]"
date: 2021-12-09
forum: New to Ubuntu
---

### Post by esso10 on 2021-12-09
I asked help before for my laptop's keyboard doesn't respond when I close the lid, so I googled and found some line which I don't remember and I copy pasted it in terminal, now when booting it takes too long time to start, listing so many lines start with green [OK].

---

### Post by tea for one on 2021-12-09
> **esso10 said:**
> I googled and found some line which I don't remember and I copy pasted it in terminal,

Open a terminal and enter
```
history
```
You may recognise the command you entered?

---

### Post by esso10 on 2021-12-10
I found 1999 commands, not one of them. :/

---

### Post by ActionParsnip on 2021-12-10
Did you run it as the user you are using now? Did you sudo up to root, as an example?
Try your browser history for the web page you used

---

### Post by esso10 on 2021-12-28
I guess I found it:

In a terminal open GRUB:  sudo nano /etc/default/grub
  Now find the line that starts with GRUB_CMDLINE_LINUX_DEFAULT="
  and replace it with
  GRUB_CMDLINE_LINUX_DEFAULT="atkbd.reset i8042.reset i8042.nomux quiet splash"
  Save and exit Ctrl+O and Ctrl+X then update GRUB.
  sudo update-grub "

I reversed it but nothing happened.

---

### Post by schragge on 2021-12-28
Did you run
```
sudo update-grub
```
again?

---

### Post by esso10 on 2021-12-29
Actually I did. Is there anything not in its place here?

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUBCMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

---

### Post by schragge on 2021-12-29
It's the other way round. To get rid of a screenwall of diagnostic messages, you have to add **quiet splash**:
```
GRUBCMDLINE_LINUX_DEFAULT="quiet splash"
```
then sudo **update-grub**

---

### Post by esso10 on 2021-12-29
Well, I don't like to say it, but it doesn't work.

---

### Post by esso10 on 2021-12-29
Well, I scanned the script again, and when I looked closely I found this:

 GRUBCMDLINE_LINUX_DEFAULT="quiet splash"   instead of   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

When I added the underscore I found out you're the man ... Thanks a lot, man!

---

### Post by schragge on 2021-12-29
Ah, thanks. I amended my post above.

---

