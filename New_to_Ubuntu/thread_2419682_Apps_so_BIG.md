---
title: "Apps so BIG"
date: 2019-05-24
forum: New to Ubuntu
---

### Post by mraamohamed on 2019-05-24
Hello, I am new to Linux but I am LOVIN it.  I have just one complaint why are the apps so large in file size, I have looked around and find that a lot of apps that are small on Windows are large here, it is just weird to me maybe.  

Thanks

Abdulah Mohamed

---

### Post by richard378 on 2019-05-24
The apps on Ubuntu are SNAPS a lot of the time.  They bundle the depedencies with the apps making them larger.  There are three package managers that do this SNAPS, Flatpacks, and AppImages.  Do a google search for more info on these.

---

### Post by mraamohamed on 2019-05-24
OK #richard378 thanks for the info, I am off to Big Brother Google.

---

### Post by Impavidus on 2019-05-25
I don't know how big applications on Windows are these days. Traditionally, they are smaller on Linux because Linux makes more use of shared libraries. Most applications here are a few tens of kilobytes, only a few tens of applications are larger than a megabyte, measured by the size of the executable, for what that's worth. I don't have any snaps.

---

### Post by PaulW2U on 2019-05-25
> **richard378 said:**
> The apps on Ubuntu are SNAPS a lot of the time.
In the current development version, and probably also in Ubuntu 19.04, only **calculator**, **characters**, **logs** and **system monitor** are pre-installed as snaps. Any other snap that is unintentionally installed might be due to misreading the information being displayed when installing new applications using the 'Software' application, commonly referred to as the 'Software Center'.
> **mraamohamed said:**
> I have just one complaint why are the apps so large in file size,
Can you give us some examples of these large applications?

---

### Post by oldos2er on 2019-05-25
Which apps? Exactly how large? Hard disk (or SSD) space is relatively cheap these day.

---

### Post by SeijiSensei on 2019-05-25
All of libreoffice is stored in /usr/lib/libreoffice/program on my 19.04 machine.  It totals only 221M in size. 

All of Kubuntu 19.04 occupies just 9.4 GB of the 20 GB partition I allocated to it at installation.  My /home is mounted as a separate partition. 

I never think of Ubuntu or its applications as "big."  Most Windows programs are statically-compiled meaning they duplicate libraries used in other statically-compiled programs.  Unix uses a common set of libraries so individual programs are much smaller.

---

### Post by ajgreeny on 2019-05-25
Just to give us more information can you please show us the output of ```
snap list
``` in terminal, which will show how many of your applications are snaps, and give us a clue about how much of your disk space is being used in this way.

Like impavidus, I do not have any snaps on my system, though I do run an appimage of musescore, which considering what it can do, is not too large at just 144MB, though it does also need a soundfont, and depending on which one you use, that can be huge.

On 18.04 I think all repository applications are available as normal .deb packages; I can't say if that is also true of later versions as I have not yet used anything later than 18.04 for much, preferring to use LTS versions only.

---

### Post by SeijiSensei on 2019-05-26
All the packages I normally use are available as deb's in the repository for 19.04.  I have no snaps on my system.

---

