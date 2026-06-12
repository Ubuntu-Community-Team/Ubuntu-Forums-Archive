---
title: "how to install software on a computer that do not have Internet connection?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-07-09
at home i've ubuntu with Internet connection, but at school i don't have internet connection. so i've difficulties to install new program to the computer at school. for e.g if i've downloaded ccsm or any other program at home, is there a way for me to copy the program package and install it to the computer at school? In windows we can copy the setup file and thus are able to install it on other computers. in fact with ubuntu i don't even know where the downloaded package are being stored. i just go to add/remove application, click on apply changes to download the selected software and click on install to install the software(it's true that it's very easy). 
please help.

---

### Post by mikewhatever on 2008-07-09
You can either use aptoncd. The problem is, you'll somehow need to install aptoncd on both computers first. There used to be a handy site called nonetdebs.net, but it's been down for some time.

---

### Post by techwrekfix on 2008-07-09
I have kind of the same problem. At home and work I have Ubuntu setup but at school they won't install anything other than windows. I got around this by installing Ubuntu on a USB thumb drive. The trick is to get one big enough to store the OS and files so you don't lose anything. I found this website a big help. [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by RajaAjmal on 2008-07-09
thanks techwrekfix
i've gone to the website. it's really helpful. again thanks.

---

### Post by sea_monkey987 on 2008-07-09
you can use the -d switch on apt-get in the command line.  Then, browse, to /var/cache/apt/archives to find the .deb file.  This is your "setup" file.  Run this on the computer at school to install the program.  Don't forget any files for the dependencies as well.

You can do "sudo apt-get clean" to empty out the archives folder.

---

