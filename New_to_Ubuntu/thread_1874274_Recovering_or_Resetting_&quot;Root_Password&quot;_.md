---
title: "Recovering or Resetting &quot;Root Password&quot; on Ubuntu 10.04 (LTS, 32 Bit)"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by kerimatasoy on 2011-11-02
Hello people...
I've forgotten my Ubuntu 10.04 System Administrator (Root) password and I need it now to gain access for setting up Xampp package...
Could you give me some idea about how to recover or reset that password...?
Thank you in advance...

---

### Post by LowSky on 2011-11-02
there is no ROOT password. All you have is your user password that can be used with Sudo

start the application from a terminal using sudo

ex:

sudo xampp

---

### Post by Paddy Landau on 2011-11-02
LowSky is correct, unless you manually created a password for root (which you should not have done).

As LowSky said, use sudo when using a non-GUI program, e.g.
```
sudo xampp
```But when using a GUI program, you must use gksudo, e.g.
```
gksudo gedit
```Most of the time you won't notice a difference between sudo and gksudo, but there are some occasions where using sudo for a GUI will cause you problems.

---

### Post by kerimatasoy on 2011-11-02
I've just used "Terminal" (Command Line Interface) and entered this code:

user@user-laptop:~$ sudo xampp (My machine asked me for my user password and I entered it...)

Then, the machine said this:

[sudo] password for user: 
sudo: xampp: command not found

( The file's complate name is "xampp-linux-1.7.7.tar.gz" )

Any idea, please...?

---

### Post by kerimatasoy on 2011-11-02
Confusing but, this link may help:

[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

I still couldn't solve this actually... When I tried apachefriend's instructions, the machine asks me for a password which is different from my current user password...

---

### Post by kerimatasoy on 2011-11-02
So far, I've tried these:

user@user-laptop:~$ cd &#304;ndirilenler  ("Downloads" in English)

user@user-laptop:~/&#304;ndirilenler$ ls
(...Current files have listed...)
xampp-linux-1.7.7.tar.gz (Here is the XAMPP's downloaded package...)

user@user-laptop:~/&#304;ndirilenler$ sudo xampp-linux-1.7.7.tar.gz
[sudo] password for user: 
sudo: xampp-linux-1.7.7.tar.gz: command not found
user@user-laptop:~/&#304;ndirilenler$ 

user@user-laptop:~/&#304;ndirilenler$ tar xvfz xampp-linux-1.7.7.tar.gz -C /opt
(The machine trys to execute the command but, returns some prints those indicates some errors: "... tar: lampp/etc/original: mkdir olanaks&#305;z: No such file or directory
lampp/etc/original/extra/ ...")

Still searching for it...

---

### Post by agillator on 2011-11-02
It looks to me as if you are trying to 'run' a compressed archive (tar.gz), not a program file. If the .....tar.gz file is what you were trying to run, it is probably the installation package. First, take a quick look at the man page for tar (man tar) to get an idea of what I am talking about. Then, go to the directory where you want the installation files to be temporarily (not the actual program files) and enter 'tar zxvf xampp-linux-1.7.7.tar.gz'. That will give you the installation files. There should be instructions there. If you are being asked for another password, are you sure you are not being asked to create a password for MySQL?

---

### Post by kerimatasoy on 2011-11-02
> **agillator said:**
> It looks to me as if you are trying to 'run' a compressed archive (tar.gz), not a program file. If the .....tar.gz file is what you were trying to run, it is probably the installation package. First, take a quick look at the man page for tar (man tar) to get an idea of what I am talking about. Then, go to the directory where you want the installation files to be temporarily (not the actual program files) and enter 'tar zxvf xampp-linux-1.7.7.tar.gz'. That will give you the installation files. There should be instructions there. If you are being asked for another password, are you sure you are not being asked to create a password for MySQL?

H&#305;mm... I've tried entering "man tar", read the manual solely, pressed "q" button, then, gone for a "man gzip"...
I guess, the file compressed two times: firstly, for "tar" and secondly gone for "gz", right...?
I think, the machine was asking me for a "super user password" when I typed "su" on command line interface...
When I tried for "sudo" then it asks me for my current user password which I've logged on with now...
So, what should I do now...? Should I extract the "tar" file first from the XAMPP's "gz" file...?

---

### Post by agillator on 2011-11-02
Ok, open a terminal. Creating a .tar.gz file is actually a two step process although tar appears to do it in one. To 'tar' a bunch of files is to create an archive, that is take a bunch of files and make it one file. That is the .tar part. The .gz part is the result of compressing that tar file using gzip - there are other compression schemes that can be used, also, but yours is the gzip scheme. Tar recovers the original files in a two step process - uncompressing and then unarchiving (if that is a word). It appears to do it in one step, smart program that it is. So, using tar, restore the original files and structure - tar zxvf whatever.tar.gz. Then look for a README or INSTALL file that will tell you how to proceed. You will probably NOT have to use sudo to initially untar the file, though you may. If you do, you do. In that case the password you will use is YOUR password. During the installation of the MySQL part of the package you will probably be asked for a 'root' password BY MYSQL. That is to create a root account for MySQL, not your system. It is part of the database system's authentication/authorization process. I have not used xampp so really cannot help you any further with the specifics of that package.

---

### Post by kerimatasoy on 2011-11-02
:) Thank you SO MUCH, everyone, it worked somehow... I've tried this as "agillator" instructed me:

" tar zxvf xampp-linux-1.7.7.tar.gz "

user@user-laptop:~/&#304;ndirilenler$ tar zxvf xampp-linux-1.7.7.tar.gz
(The command extracted the compressed files from XAMPP's downloaded file. :) Will share the results here with all later, now, I'd like to delve some more about XAMPP's installation and usage...

THANK YOU, GUYS... :)

---

### Post by kerimatasoy on 2011-11-03
Sorry but, although I was able to extract the files from XAMMP's "tar.gz" file, I couldn't install a "LAMPP" or "XAMPP" service package yet, because, the system still keeps for asking a root access... It took me all day and a brand new install though, I may try something different later...

---

### Post by agillator on 2011-11-04
If you have reached that point then you probably do need to use sudo. If sudo doesn't work, it may be that it really needs to be on a 'root' account, although that would be very rare. However, if that is the case, a couple of cautions, then . . . . Remember, when functioning as root there are two kinds of people: those who have and those who will - - - - destroy their system, that is. Back everything up and then proceed very carefully. Did I mention BACK EVERYTHING VALUABLE UP! Then, in a terminal, enter 'sudo passwd root'. sudo will ask for YOUR password to verify you are authorized, and then passwd will ask for the new root password and then ask for it again in confirmation. Now you have a 'root' account. su to switch to that account, then do the install of your program again. See if that accomplishes anything. Good luck.

---

### Post by illgetit on 2011-11-04
Couldn't he just```
 sudo su
```
That way he wouldn't have the security issues involved in actually setting a root password

---

### Post by illgetit on 2011-11-04
> **agillator said:**
> Ok, open a terminal. Creating a .tar.gz file is actually a two step process although tar appears to do it in one. To 'tar' a bunch of files is to create an archive, that is take a bunch of files and make it one file. That is the .tar part. The .gz part is the result of compressing that tar file using gzip - there are other compression schemes that can be used, also, but yours is the gzip scheme. Tar recovers the original files in a two step process - uncompressing and then unarchiving (if that is a word). It appears to do it in one step, smart program that it is. So, using tar, restore the original files and structure - tar zxvf whatever.tar.gz. Then look for a README or INSTALL file that will tell you how to proceed. You will probably NOT have to use sudo to initially untar the file, though you may. If you do, you do. In that case the password you will use is YOUR password. During the installation of the MySQL part of the package you will probably be asked for a 'root' password BY MYSQL. That is to create a root account for MySQL, not your system. It is part of the database system's authentication/authorization process. I have not used xampp so really cannot help you any further with the specifics of that package.



Superb explanation by the way

---

### Post by Paddy Landau on 2011-11-04
> **agillator said:**
> ... enter 'sudo passwd root'.
This explanation violates the code of conduct of these forums. Please do **not** create a root password.

Instead, use *sudo*; and for those very, very rare occasions when you need to stay on root for a while (I have never needed to do this), use *sudo su* (as [post=11423581]illgetit said[/post]).

---

### Post by agillator on 2011-11-04
illgetit: you are correct. For some reason it has never occurred to me to do it that way. In my mind sudo really doesn't go with su, but that is just my warped way of thinking, I guess, kind of like the phrase 'return back'. You obviously are correct that sudo su avoids the security problems of a root account.

To kermitasoy: is there a reason you specifically want xampp or are you just looking for a LAMP server? And why/for what specific purpose? The answer to those two questions may help us help you since there are several ways to LAMP if that is what you are really after.

---

### Post by kerimatasoy on 2011-11-04
STEPS DONE SO FAR:

1. [http://www.apachefriends.org/en/xampp-linux.html#374](http://www.apachefriends.org/en/xampp-linux.html#374)
I've downloaded the XAMPP's "tar.gz" file from the link which has given just as above...

2. [http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)
Then, tried to extract the file and done it, fortunately... :)

Some "infos" from "Terminal":
user@user-laptop:~$ cd /
user@user-laptop:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
user@user-laptop:/$ su 
Parola: 
su: Yetkilendirme hatas&#305; (Gives some error due to trying to gain a root access without any authorization but, we're not done yet...)
user@user-laptop:/$ sudo su
[sudo] password for user: 
root@user-laptop:/# (Here, it worked somehow... :) But, still, not done yet...)
root@user-laptop:/# cd home
root@user-laptop:/home# ls
user
root@user-laptop:/home# cd user
root@user-laptop:/home/user# ls
Belgeler  examples.desktop  Genel  &#304;ndirilenler  Masaüstü  Müzik  Resimler  &#350;ablonlar  Videolar
root@user-laptop:/home/user# cd &#304;ndirilenler
root@user-laptop:/home/user/&#304;ndirilenler# ls
xampp-linux-1.7.7.tar.gz (The file IS HERE...)
root@user-laptop:/home/user/&#304;ndirilenler# tar xvfz xampp-linux-1.7.7.tar.gz -C /opt (We're good so far... :) )
root@user-laptop:/home/user/&#304;ndirilenler# exit
exit
user@user-laptop:/$ ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old
user@user-laptop:/$ cd opt
user@user-laptop:/opt$ ls
lampp (Let's go and see a little bit deeper then...)
user@user-laptop:/opt$ ls lampp
bin  cgi-bin  error  etc  htdocs  icons  lampp  lib  libexec  licenses  logs  modules  phpmyadmin  RELEASENOTES  sbin  share  tmp  var
user@user-laptop:/opt$ (Now, we're almost sure that the files which were included in the XAMPP's compressed package before, have just been extracted already into the right place... :) )

3. [http://www.apachefriends.org/en/xampp-linux.html#378](http://www.apachefriends.org/en/xampp-linux.html#378)
I've tried to start the XAMPP services then...

user@user-laptop:/$ /opt/lampp/lampp start
You need to start XAMPP as root!
user@user-laptop:/$ sudo su
[sudo] password for user: 
root@user-laptop:/# /opt/lampp/lampp start
Starting XAMPP for Linux 1.7.7...
XAMPP: Starting Apache with SSL (and PHP5)...
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
root@user-laptop:/# (It's time to test the services then...) 

4. [http://www.apachefriends.org/en/xampp-linux.html#379](http://www.apachefriends.org/en/xampp-linux.html#379)
Just as instructed before, I'd go for a testing...

On Firefox, typed the "url" address to test the things if they were working well or not... --> "localhost" or "http://localhost", either would work fine... (Lucky me... :) Actually, thanks to YOU... :) )

"... Welcome to XAMPP for Linux 1.7.7 !
     Congratulations:
     You successfully installed XAMPP on this system! ..."

**THANKS** again...

---

### Post by kerimatasoy on 2011-11-04
> **agillator said:**
> illgetit: you are correct. For some reason it has never occurred to me to do it that way. In my mind sudo really doesn't go with su, but that is just my warped way of thinking, I guess, kind of like the phrase 'return back'. You obviously are correct that sudo su avoids the security problems of a root account.

To kermitasoy: is there a reason you specifically want xampp or are you just looking for a LAMP server? And why/for what specific purpose? The answer to those two questions may help us help you since there are several ways to LAMP if that is what you are really after.

Sure, gladly... I'd like to use or at least have experience those packages, like XAMPP, WAMP, EasyPHP and so on... Because, these packages have been claimed as "better" or "easier" for some developing purposes and actually, it mostly seems so for many areas... Also, fortunately, they make the things easier for us... But, many professionals have noticed us saying that for some production purposes, it wouldn't be the same... I'm not a "guru" yet, so...
I'm interested in PHP developing and programming, generally...
I'm also open for any different solution those may work for me...
Thank you for everything...

---

### Post by agillator on 2011-11-04
You are up and running - that is what we were all getting at. The other ways I might have suggested might not have been easier except for the problems you were having - there would at least have been different problems. But once you find a way that works for you, stick with it unless you find it isn't really doing what you wanted. Good luck! Glad we could all help.

---

