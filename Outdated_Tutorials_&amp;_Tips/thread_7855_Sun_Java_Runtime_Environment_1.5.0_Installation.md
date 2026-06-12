---
title: "Sun Java Runtime Environment 1.5.0 Installation"
date: 2004-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by gecko on 2004-12-11
Hello,
  
After review by the super moderator , I have removed these instructions and will hopefully return with a java-package solution.
 
 Regards
  
 Gecko

---

### Post by jdong on 2004-12-11
I do NOT recommend installing Java this way. Use java-package, which will build debian-specific extensions to Java (like /etc/alternatives symlinks and such), plus you get to use the wonderful dpkg system!

---

### Post by asimon on 2004-12-25
[QUOTE=jdong]java-package, which will build debian-specific extensions to Java (like /etc/alternatives symlinks and such), plus you get to use the wonderful dpkg system![/QUOTE]

Ubuntu's java-package 0.14 doesn't support java 1.5 from sun.

---

### Post by |Syrius| on 2004-12-29
well... I tryed this: [http://serios.net/content/debian/java.php#downloadjava](http://serios.net/content/debian/java.php#downloadjava)
and all worked well. I had to download java-package 0.17 but all went ok.

Hope to help others

---

### Post by jerome bettis on 2005-01-20
```
wget [http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb](http://davyd.ucc.asn.au/projects/misc/sun-j2sdk1.5_1.5.0_i386.deb)
sudo apt-get install java-package
sudo apt-get install sun-j2sdk1.5debian
sudo dpkg -i su*.deb

```

done.

---

### Post by Davepet on 2005-01-28
Warning to dial up users: that's a 60 MB download. The file from Sun may take more effort, but it's only 16 MB.

Dave

---

### Post by rapala61 on 2005-01-29
Wait a second.. so is there a problem with the manual way, y is this better, should i go back and undo all i did to install it and reinstall it this way??? thx

---

### Post by Davepet on 2005-01-29
I doubt there is a problem doing it manually, although the files may not be put where a debian system likes to put them. Tha't probably only an issue if you later try to update with apt. 

I just successfully installed it manually tonight myself.

Dave

---

### Post by rapala61 on 2005-01-29
aight.. if i do it this way...  how do i update java???

```
wget http://davyd.ucc.asn.au/projects/mi..._1.5.0_i386.deb
sudo apt-get install java-package
sudo apt-get install sun-j2sdk1.5debian
sudo dpkg -i su*.deb
```

---

### Post by wietse_nieuwland on 2006-05-02
I did all what you said with sudo etc but I got after entering the third line (sudo apt-get sun etc) the folowing message:
Instellen van java-package (0.26) ...
wietse@ubuntu:~$ sudo apt-get install sun-j2sdk1.5debian
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd... Klaar
E: Kon pakket sun-j2sdk1.5debian niet vinden

What should I do?

---

