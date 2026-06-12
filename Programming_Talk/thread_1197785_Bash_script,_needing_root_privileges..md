---
title: "Bash script, needing root privileges."
date: 2009-06-26
forum: Programming Talk
---

### Post by leech on 2009-06-26
This is driving me nuts.

I can't quite get the permissions to work properly on this one.

I'm running Debian, so the sudoers file isn't set up by default.

I want to be able to just double-click on this script, then ask the password once, then ask questions to set everything else up.

The problem I'm running into is that when you use usermod -a -G to add someone to the group, it doesn't update what group the user is in until logout / login.

I tried using a suggestion from [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

To add ```
su –preserve-environment –command “$(which $SHELL) –login -i” $(whoami)
```

But, while it did open up a new command prompt in the same terminal window, it didn't continue on in the script.

```
#!/bin/sh
# enable sudo.
set -x 
echo "Adding the 'username' user to the sudo group'"
# enable sudo
echo "Enabling sudo.
First we change the Sudoers file"
su -c 'echo %sudo ALL=NOPASSWD: ALL >> /etc/sudoers'
su -c 'sudo -u root usermod -a -G sudo username' 
su –preserve-environment –command “$(which $SHELL) –login -i” $(whoami)
# add username user from sudo group!

echo "Adding Debian's main repositories and removing DVDROM, and installing reuquired packages."
sudo sed -i -e 's/deb cdrom/#deb cdrom/g' /etc/apt/sources.list 
sudo echo "deb http://ftp.debian.org/debian lenny main contrib non-free" >> /etc/apt/sources.list 
sudo apt-get update 
sudo apt-get install rsync mysql-server-5.0 sun-java5-jdk sun-java5-jre libjdic-bin libjdic-java
```

This gives permission denied when adding the debian repositories, even though it runs the 'apt-get update'.

I've tried using sudo -u root as well, and didn't have much luck, and I don't exactly want to run su -c the entire time, since it always prompts for passwords.

Any suggestions?

---

### Post by master_kernel on 2009-06-26
The "answer" is here: [http://www.linuxquestions.org/questions/linux-general-1/is-it-possible-to-addremove-a-user-to-a-group-without-logging-out-and-in-again-707845/](http://www.linuxquestions.org/questions/linux-general-1/is-it-possible-to-addremove-a-user-to-a-group-without-logging-out-and-in-again-707845/)

As far as I know, there is no way the user can be added to the group (without logging in again) while the Window Manager is still running.

---

### Post by jpkotta on 2009-06-26
I also know of no way to do this.  However, if it is a major pain to log out, you can run commands from a new shell in a terminal with su
```
su $USER
```
or sudo
```
sudo -u $USER -s
```
I'm able to launch X apps from shells like this as well (i.e. it doesn't screw up XAuth or DISPLAY).

---

### Post by jpkotta on 2009-06-26
I also suggest that you add the Debian APT sources to their own file.  BTW, your bug in that is caused by the fact that the shell doesn't have root permissions, and that is what writes files with the redirect operator '>>'.  You need to give root permissions to the command that writes the file.  The most elegant way is probably with tee.
```
echo "deb http://ftp.debian.org/debian lenny main contrib non-free" | sudo tee -a /etc/apt/sources.list.d/debian.list >/dev/null
```

---

### Post by leech on 2009-06-26
I finally said 'screw it' and set it up so that you just have to run the script from the 'root terminal' that Debian puts in the menu, under Accessories.  

As long as the instructions are simple enough that anyone can follow them, so I'm not the only one who has to set up these boxes where I work.

By the way, I highly suggest people buy the qnap TS-439, they are cool as hell, by default, and you can install whatever OS you want on them.

Thanks for all the suggestions, guys.  It's weird that I couldn't even get gksu to work right.  If I had set it all up as a separate program, it probably would have.

I'll work on this solution later when I actually have more time.

Oh, and for the suggestion that I should put them in a different file for the debian Apt sources, I thought about that, but since they are the main ones (to tell the reason why I had to add them was because the qnap box that I installed debian on has a NIC that isn't recognized by the e1000e driver version that is in the debian 2.6.26 kernel (it's like 0.0.2 versions lower than the one in Ubuntu 9.04 that detects it properly)) I decided to put it in the sources.list file.

Leech

---

