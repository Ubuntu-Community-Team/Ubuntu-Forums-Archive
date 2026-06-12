---
title: "how do i install from a terminal?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Peterfc on 2008-05-04
HI all

From a recent post i was able to install using the termninal. I needed Google Earth for research. That's now ok. I have on screen a message for a to install missing plugin. I downloaded Java and tried to run from the terminal. I keep getting the message below. Can anybody help.

Thanks  



peter@peter:~$ cd Desktop
peter@peter:~/Desktop$ jre-6u5-linux-i586-rpm.bin
bash: jre-6u5-linux-i586-rpm.bin: command not found
peter@peter:~/Desktop$ 





jre-6u5-linux-i586-rpm.bin

Dell Dimention 2400, 200gb drive, 1gb ram

---

### Post by Joeb454 on 2008-05-04
It's because it's an rpm file, you need to look for the .deb :)

---

### Post by adityakavoor on 2008-05-04
```
sudo apt-get install alien
```

then

```
sudo alien package_name.rpm
```

this will convert rpm to deb

---

### Post by Joeb454 on 2008-05-04
But from what it looks like, the OP is trying to install Java, which is available as a .deb anyway, so why install alien to convert it when you can get a deb anyway.

And I believe java is available in the repositories anyway, so you may want to open up synaptic (System > Administration > Synaptic Package Manager) and search for Java

---

### Post by Biggy on 2008-05-04
1- Put downloaded file (jre-6u5-linux-i586-rpm.bin) in Home folder.
2- Open Terminal and type : sh jre-6u5-linux-i586-rpm.bin

---

### Post by iswa on 2008-05-04
Installing Java on Ubuntu is (relatively) painless, and there is an excellent howto in the Ubuntu Community docs here:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Note too that Google Earth is available from the Medibuntu repositories. To enable these repositories, see here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then its just a simple 'sudo apt-get install googleearth', and you are sorted.

Hope this helps.

---

