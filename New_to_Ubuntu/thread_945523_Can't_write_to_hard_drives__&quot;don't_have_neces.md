---
title: "Can't write to hard drives  &quot;don't have necessary permission&quot;&gt;"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Big Pimp Daddy on 2008-10-12
Hi, hope somebody can help, new to Ubuntu and Linux generally, got it all installed fine. The hard drive with ubuntu on is fine, the other ntfs drives from my old windows system are fine, but any new hard drives I format in ubuntu I am not able to write to, the paste and create new folder options are greyed out, and the only folder there ("lost + found") I am not able to access as I apparently don't have permission.
I created another user and gave them all the permissions available, same problem, and I don't seem to be able to log in as root. Not sure what options are left. Any help greatly appreciated. Thanks in advance.

(Edit- Am using the latest ubuntu fully updated on AMD X2 3800+, 1.5gb ram, ATI 3450, bunch of random hard drives from old windows server.)

---

### Post by Gutt on 2008-10-12
You'd have to get into Nautilus as root.

Open up a terminal and type

```
Sudo Nautilus
```

Then just watch out, cuz any wrong move could do a lot of damage to your system.
Hope that works.

---

### Post by thomasyen on 2008-10-12
Maybe you'd like to try changing permissions using the chmod command:
```
sudo chmod -R 766 *(your drive mountpoint here)*
```
Explanation:
sudo --- superuser privileges
chmod --- change mode (permissions)
-R --- recursive processing (changes mode for every child directory)
766 --- owner readable/writeable/executable, group readable/writeable, other users readable/writeable

Hope this is of help!

p.s. As a side note, the default for Ubuntu is to disable logging in as root for security reasons.
Also, if the above doesn't work, try changing owner, then change mode:
```
sudo chown -R *(your username here) (your drive mountpoint here)*
```
Explanation:
sudo --- superuser privileges
chown --- change owner
-R --- recursive processing (changes owner for every child directory)

---

### Post by Big Pimp Daddy on 2008-10-12
Awesome! Thanks Gutt, that's exactly what I wanted. I'm sure thomasyen's answer would have worked too, but tried yours first. Can't thank you both enough.

---

### Post by simtaalo on 2008-10-12
```
gksudo nautilus
```

is a little more correct to gain root priviledges on nautilus.

---

