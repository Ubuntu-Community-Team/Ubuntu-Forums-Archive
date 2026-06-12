---
title: "[SOLVED] Help: &amp;quot;Can't open file to write&amp;quot;"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by imjscn on 2008-06-30
I installed Samba, now I need to add these lines in smb.conf
[sandbox]
path = /home/russ/sandbox
valid users = sandbox
read only = No
create mask = 0777
directory mask = 0777

After editing, when save, it says "can't open file to write".

what can I do now?

---

### Post by Inxsible on 2008-06-30
Use gksudo in front of the command to open the file. Put in your password when asked

---

### Post by PinkFloyd102489 on 2008-06-30
Then restart the samba daemon.

```
sudo /etc/init.d/samba restart
```

---

### Post by imjscn on 2008-06-30
do you mean opening the smb.conf in Terminal? How? If edit it in Terminal, how to save it?
(I openned it via mousepad)

---

### Post by sisco311 on 2008-06-30
Applications --> Accessories --> Terminal
```
gksu mousepad /etc/samba/smb.conf
```

or Alt+F2 and copy paste the command.

---

### Post by imjscn on 2008-06-30
amazing...it works! I love these magic words!!!

Thanks!

---

### Post by imjscn on 2008-07-03
Hello again...this time I got a Tiger report in HTML formate, how can I open and read it?

---

### Post by Inxsible on 2008-07-03
> **imjscn said:**
> Hello again...this time I got a Tiger report in HTML formate, how can I open and read it?HTML can be opened by any browser that you have. Right click and select Open with and then select your favorite browser.

---

### Post by imjscn on 2008-07-03
it's var/log/rkhunter.log , with a red cross on it, it says can't open without permission.

---

### Post by ChameleonDave on 2008-07-03
> **imjscn said:**
> it's var/log/rkhunter.log , with a red cross on it, it says can't open without permission.

You can view any text-based file with the command "cat".  For larger files, use "more" or "less" instead.  If there is a permission problem, put "sudo" before the command.  For example:

```

sudo less /var/log/rkhunter.log

```

---

