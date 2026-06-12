---
title: "[SOLVED] how to install tar.gz packages"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by grashdur on 2008-09-12
In Gutsy Gibbon, whenever I couldn't find a program anywhere as a .deb file package, I could just download a .tar.gz package -- the package would then be automatically converted and installed. 

But in Hardy Heron, I can only *download* a tar package. How do I install it now?

---

### Post by Bölvaður on 2008-09-12
I guess there are few programs that you cannot find in Synaptic...

What is the content of the compressed file? Is there any executable binary file you are supposed to run?

When I've got games that come in .tar.gz it is just a folder that I can decompress and put into ~/games and play it straight from there (no installation)

---

### Post by Locutus_of_Borg on 2008-09-12
```

tar -xvf NAME.tar.gz
cd NAME/
./configure
make
sudo make install
```

You need build essentials and linux headers from your live cd installed in order to compile it

---

### Post by handydan918 on 2008-09-12
Yeah, the real deal is that a tar.gz file is not an installation file, per se. All it really means is it is a compressed file. Not all tar.gz files have to be used with the "make yada-yada". The contents of the file could be nearly anything. First thing to do is uncompress the file and look for a README file, and well, READIT.

:)

---

### Post by grashdur on 2008-09-13
Thanks for the replies. 

To Bölvaður: I have several packages in mind. First, I want to revert to an older driver for my scanner, since the current one doesn't work. One of the things I'll have to install is a .tar.gz. I'm still trying to find out how to do some of the details of driver reinstallation. Thread: [http://ubuntuforums.org/showthread.php?t=783983](http://ubuntuforums.org/showthread.php?t=783983) I also want to install some financial software, other than GnuCash and other things in the Ubuntu reposities, which I'm dissatisfied with. (nice avatar and name, by the way)

To Locutus: When you say, "build essentials and linux headers from your live cd" do you mean that I won't be able to run those commands in Terminal until I get some utilities off the installation CD? How does that work? Are those utilities not downloadable from the repositories?

To handydan918: That's about all I knew so far: Download the tar package and open the README file. But I've never seen a README file in any of the tar packages that I've downloaded in recent months.

---

### Post by Sef on 2008-09-13
> To Locutus: When you say, "build essentials and linux headers from your live cd" do you mean that I won't be able to run those commands in Terminal until I get some utilities off the installation CD? How does that work? Are those utilities not downloadable from the repositories?


You used to have to use the CD to install build-essential; you should be able to download it from the repositories now.

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by grashdur on 2008-09-13
Thank you, Sef. I'll give this a try probably on Monday. What are Linux headers? Do you know if I need to find and install these too, in order to run those commands to install a tar.gz software package?

---

### Post by grashdur on 2008-09-15
Okay, I just tried to install a .tar.gz software package. First I just tried it right off, and it didn't work. Then I tried installing that build-essential, which was apparently successful. I then tried again to install my tar package (Moneydance). I got the same results:

> grashdur@grashdur-desktop:~/Desktop$ tar -xvf /home/grashdur/Desktop/Moneydance_linux_x86.tar.gz
Moneydance/
Moneydance/.install4j/
Moneydance/.install4j/i4jruntime.jar
Moneydance/Moneydance
Moneydance/.install4j/firstrun
Moneydance/.install4j/i4jparams.conf
Moneydance/.install4j/MessagesDefault
Moneydance/.install4j/user.jar
Moneydance/appsrc.jar
Moneydance/jcommon-1.0.12.jar
Moneydance/jfreechart-1.0.9.jar
Moneydance/license.txt
Moneydance/moneydance.jar
Moneydance/moneydance_icon32.png
grashdur@grashdur-desktop:~/Desktop$ cd /home/grashdur/Desktop/
grashdur@grashdur-desktop:~/Desktop$ ./configure
bash: ./configure: No such file or directory
grashdur@grashdur-desktop:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
grashdur@grashdur-desktop:~/Desktop$ sudo make install
make: *** No rule to make target `install'.  Stop.
grashdur@grashdur-desktop:~/Desktop$ 

Do I still need to find and install some kind of "Linux Header"? Or am I totally on the wrong track here?  :confused: :confused:

---

### Post by jemate18 on 2008-09-15
> **grashdur said:**
> Okay, I just tried to install a .tar.gz software package. First I just tried it right off, and it didn't work. Then I tried installing that build-essential, which was apparently successful. I then tried again to install my tar package (Moneydance). I got the same results:



Do I still need to find and install some kind of "Linux Header"? Or am I totally on the wrong track here?  :confused: :confused:

from the looks of the contents of your application, they are jar or java archive files...

Do you have a java installed?

---

### Post by gauntface on 2008-09-15
> grashdur@grashdur-desktop:~/Desktop$ ./configure
bash: ./configure: No such file or directory

Thats your error to start off with, but I think it is largely because u changed directory (cd) to your desktop folder but not into the moneydance directory.

Looking at the moneydance website you can download an installer but also just run moneydance by click on moneydance launcher in the folder.

I tend to just put all my programs like this in one folder and creater launchers in my menu

---

### Post by grashdur on 2008-09-16
Thanks, both of you, for the insightful suggestions you just gave. It turns out that I did *not* have Java installed on my main computer (I had just assumed it was part of the default installation of Ubuntu, so that it could run all the features of OpenOffice, etc.) 

After installing Java RE v6, I was able to simply click on that little quick-launch icon on the downloaded folder, and the program runs just fine!!

  \\:D/

---

### Post by jemate18 on 2008-09-16
> **grashdur said:**
> Thanks, both of you, for the insightful suggestions you just gave. It turns out that I did *not* have Java installed on my main computer (I had just assumed it was part of the default installation of Ubuntu, so that it could run all the features of OpenOffice, etc.) 

After installing Java RE v6, I was able to simply click on that little quick-launch icon on the downloaded folder, and the program runs just fine!!

  \\:D/

Please mark this THREAD as SOLVED

---

