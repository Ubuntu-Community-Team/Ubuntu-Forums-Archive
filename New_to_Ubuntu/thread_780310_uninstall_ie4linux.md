---
title: "uninstall ie4linux"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by grewolf on 2008-05-03
Hello I have installed wine and ie4linux and now want to remove it all as I have found a way to surf the site I need through firefox. I use Gutsy Gibbon.  I went to this web page [http://yourubuntulinux.blogspot.com/2007/12/how-to-install-ie4linux-on-ubuntu-710.html](http://yourubuntulinux.blogspot.com/2007/12/how-to-install-ie4linux-on-ubuntu-710.html)

and followed these instructions 

```
1. Make sure you login your Ubuntu Linux with normal user. Don't login as root. Sometime IE4Linux won't come out or launching when you login as root after install.

2. Open your terminal

3. Open /etc/apt/sources.list with command. For this case I use gedit. Please use your favorite editor for easy editing. For example Vi editor, Nano editor etc.

sudo gedit /etc/apt/sources.list

4. Uncomment (or add) following lines:

deb http://us.archive.ubuntu.com/ubuntu gutsy universe

5. Add this line:

deb http://wine.budgetdedicated.com/apt gutsy main

6. Close gedit. Update and install wine and cabextract:

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wine cabextract

7. Download IEs 4 Linux and install

wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
```

I have looked through web pages and on the forum and all I have found is how to uninstall wine.

---

### Post by SunnyRabbiera on 2008-05-03
I think it has a folder inside your home folder, i dont use it but there is a start for you at least.

---

### Post by macaholic on 2008-05-03
I'm pretty sure it just has things in it's fodler in your home folder, but other than that I think it only isntalls stuf on your wine drive. Uninstalling it through wine amd removign the fodler should work.

---

### Post by lswest on 2008-05-03
if you still have the script, try running ```
./ies4linux uninstall
``` after cd'ing to the directory.

---

### Post by forestpixie on 2008-05-03
There are a couple of folders in your /home that it installs

ies4linux
bin - check inside that there is only and ie file

in .wine check in /drive_c/Program Files for Internet Explorer

if you can't uninstall with uninstall script - delete the folders

---

### Post by msghaleb on 2008-09-12
Hi 

If you were a normal user during installation everything should be under:

/home/user/.ies4linux

and here one file just to start ie6, you need to delete that too:
/home/user/bin/ie6

please replace user above with your user name


if you used root to install it then it should be under:

/root/.ies4linux

and here one file just to start ie6, you need to delete that too:
/root/bin/ie6

Thank you

MG

---

