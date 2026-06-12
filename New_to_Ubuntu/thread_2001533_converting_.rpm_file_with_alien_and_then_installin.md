---
title: "converting .rpm file with alien and then installing"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-11
Hi all

I wanting to install serna-free, which is an XML editor.
They only had .rpm packages, so I downloaded that file. I have already downloaded alien for another .rpm file in the past. So I ran this:
```

glenn@design:~/Downloads$ sudo alien --scripts serna-free-4.4-4.4.0-20111103.i686.rpm

```It had told me that I need to have the --scripts option, so I included it. It ran with no errors and exited.
Then, I chown to glenn:glenn and chmod a+x the file.
After this, I install the package:
```

glenn@design:~/Downloads$ sudo dpkg -i serna-free-4.4_4.4.0-20111104_i386.deb
(Reading database ... 265655 files and directories currently installed.)
Preparing to replace serna-free-4.4 4.4.0-20111104 (using serna-free-4.4_4.4.0-20111104_i386.deb) ...
Unpacking replacement serna-free-4.4 ...
Setting up serna-free-4.4 (4.4.0-20111104) ...
glenn@design:~/Downloads$ 

```but when I attempt to run the program from terminal:
```

glenn@design:~/Downloads$ serna-free
serna-free: command not found
glenn@design:~/Downloads$ serna
No command 'serna' found, did you mean:
 Command 'sirna' from package 'emboss' (universe)
serna: command not found
glenn@design:~/Downloads$ 

```Where have I gone wrong?

---

### Post by sanderj on 2012-06-11
sudo updatedb

locate -i serna

---

### Post by Senior_Buckethead on 2012-06-11
Thanks for that.

ok, had to pipe output to a file because hundreds and hundreds of lines. (6680 in all). It's all in the /Opt directory.
Found the shell file serna.sh and ran it. Now the difficulty is in making a shortcut for it on the desktop

---

### Post by sanderj on 2012-06-11
locate serna.bin

---

### Post by Senior_Buckethead on 2012-06-11
Done!
Made a file on the Desktop called Serna.desktop

And in it:
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Serna Free
Exec=sh /opt/serna-free-4.4/bin/serna.sh

```

then:
```

sudo chown glenn:glenn Serna.desktop
sudo chmod a+x Serna.desktop

```

Do you know how I can change the icon from the default sh. icon?

---

### Post by sanderj on 2012-06-11
> **Senior_Buckethead said:**
> Done!


So ... it works? What do you say then ... ?

---

### Post by Senior_Buckethead on 2012-06-11
Thank you.

[Solved]

---

