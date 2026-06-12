---
title: "Can somebody plz assist me in installing Java"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by mattcadu on 2008-08-22
This is what is downloaded to my desktop

jre-6u7-linux-i586-rpm.bin

Now ... Heres the thing... How do i install this?

Can anyone please help me?

---

### Post by yabbadabbadont on 2008-08-22
Sun's Java packages are already in the Ubuntu repositories.  Just install them using Synaptic.  System->Administration->Synaptic Package Manager.

Edit: You'll need to have the multiverse repository enabled before they will show up.  See the following for details on how to do that:

[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by jakupl on 2008-08-22
this thread is the same.

[http://ubuntuforums.org/showthread.php?p=5645721#post5645721](http://ubuntuforums.org/showthread.php?p=5645721#post5645721)

---

### Post by jerome1232 on 2008-08-22
just a side note, anything that's a "rpm" is for red hat based distros (fedora, OpenSuse)

.deb are debian packages (Debian, Ubuntu)

---

### Post by mattcadu on 2008-08-22
This really doesnt help me... what do i do once i get there?

---

### Post by jakupl on 2008-08-22
get where?

have you tried to write this in the terminal?

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by aloshbennett on 2008-08-22
try this
> apt-cache search sun java

You'd see couple of packages like sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-fonts etc..

If you just need the jre, install the following
> sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

If you are a developer, select the packages you need and stick them to the end of 'sudo apt-get install' (There's sun-java6-jdk sun-java6-doc sun-java6-source sun-java6-javadb glassfishv2 etc)

If you dont see any of these packages when you do 'apt-cache search', try enabling multiverse repository from System -> Administration -> Software sources

---

### Post by Sef on 2008-08-22
Easy way to install Java:

Applications > Apply > Show: All Available Applications > Search: Sun Java 6 > click on Sun Java 6 Runtime > Apply Changes > Apply > Close.

> This is what is downloaded to my desktop

jre-6u7-linux-i586-rpm.bin

Now ... Heres the thing... How do i install this?

Can anyone please help me? 

1) Ubuntu uses .deb and not .rpm.

2) To get a .rpm to run on Ubuntu, you need to use alien to convert the .rpm to a .deb.

---

### Post by Bölvaður on 2008-08-22
the first place to download programs are from add/remove or synaptic package manager.

System -> Administration -> Synaptic Package Manager
(type your password)
Search - "Java"
Check the box next to "java-common"
(Press Apply)

whoolla it has been installed.

I think you dont need to add extra repositories for this.

---

### Post by Bölvaður on 2008-08-22
> **Sef said:**
> 
2) To get a .rpm to run on Ubuntu, you need to use alien to convert the .rpm to a .deb.

it actually was a binary (bin) file for redhat, which will most probably not work for you without changing things.

running/installing .bin files is simple :   ./executable.bin

---

### Post by Cheesehead on 2008-08-22
To install Sun Java6 JRE in Ubuntu:
(allow ~20 minutes or more, depending on the speed of your network connection)
[U]
THE EASY WAY:[/U]
1) Take the downloaded file, 'jre-6u7-linux-i586-rpm.bin', and throw it in the trash. You won't need it.

2) Open Applications --> Add/Remove
   Wait for it to finish updating the package list
   In the search box, enter 'Java' --> Select 'Sun Java 6 Runtime'
   Click 'Apply Changes'

_THE HARDER, GEEKY WAY_
1) Take the downloaded file, 'jre-6u7-linux-i586-rpm.bin', and throw it in the trash. You won't need it.

2) Open a terminal window and enter the following commands:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo update-java-alternatives -s java-6-sun
```

---

### Post by Bölvaður on 2008-08-22
> **Cheesehead said:**
> 
1) Take the downloaded file, 'jre-6u7-linux-i586-rpm.bin', and throw it in the trash. You won't need it.


Smart && Funny :)

---

### Post by alienexplorers on 2008-08-22
On my system the libjavaplugin_oji.so file is never placed in the right spot in the mozilla-addons/plugins directory.  I always have to do a symbolic link to get it there.

---

