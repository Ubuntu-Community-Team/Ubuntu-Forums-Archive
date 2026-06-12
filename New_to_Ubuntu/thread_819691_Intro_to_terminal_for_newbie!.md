---
title: "Intro to terminal for newbie!"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by navic101 on 2008-06-05
Could you kindly suggest any "newbie intros" to terminal or any copy and paste lines that i could try that might give me system info without altering anything..to try! I dabbled with MSDOS in XP and was amused to see the route my IP took to get to my server..

thanks

---

### Post by cardinals_fan on 2008-06-05
For basic system info, enter ```
uname -a
``````
sudo lspci
``` and ```
sudo lsusb
``` list the hardware attached through pci/usb on your system.

For a basic terminal guide, visit [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by st33med on 2008-06-05
Here is a good one:
[http://linuxcommand.org/learning_the_shell.php]("http://linuxcommand.org/learning_the_shell.php")

---

### Post by deltaprime on 2008-06-05
> iwconfig for information on wireless devices =)
> sudo to become administrator mode (you will have to enter your password) 
> apt-get install firefox to install firefox with shell (shell=command prompt)
to start a feature:
> sudo /etc/init.d/vsftpd start in this example i start the vsftpd deamon with shell. you will have to change the path to start whatever program you want to start.
Play sudoku in shell:
> sudo apt-get install sudoku
then it will ask you y or n for yes or no in the installation process. Select > y
Then start the programm after the installation by typing > sudoku 

have fun

DELTA

---

### Post by msidhard on 2008-06-05
hey u can search for "Beginning Ubuntu Linux - From Novice To Professional (2006).pdf". in google. u can find there are three books related to ubuntu and its application. if u want to know more about bash shell just visit [http://www.tldp.org/LDP/Bash-Beginne...ners-Guide.pdf](http://www.tldp.org/LDP/Bash-Beginne...ners-Guide.pdf) then [http://www.tldp.org/LDP/abs/abs-guide.pdf](http://www.tldp.org/LDP/abs/abs-guide.pdf) and [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) also [http://www.linuxcommand.org](http://www.linuxcommand.org) 
And a short overview on bash commands here's a pdf on that page:

[http://fosswire.com/2007/08/02/unixl...d-cheat-sheet/](http://fosswire.com/2007/08/02/unixl...d-cheat-sheet/)

There's an excellent guide, called Advanced Bash Scripting, at tldp.org/LDP/abs/abs-guide.pdf
(PDF). There's also an HTML version, tldp.org/LDP/abs/html/. those things relates to bash and terminal and introduction to ubuntu

---

