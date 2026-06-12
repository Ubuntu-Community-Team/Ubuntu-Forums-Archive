---
title: "How to autostart programs in virtual console?"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by navoye on 2013-03-09
Hello world!

I've got a little problem. I need 2 programs to start automatically in virtual consoles after I start the system.
Till now all my attepts have failed. I'll try to describe the process in few words and maybe someone could help me do it.
 

My enviroment builds like this: (I use compilation with kernel 3.2)
I do as follow:
Ubuntu server default installation with server ssh and next:
```

aptitude install xserver-xorg xserver-xorg-core  xserver-xorg-input-evdev xserver-xorg-video-ati lightdm unity-greeter  openbox roxterm
echo 'export DISPLAY=:0' >> ~/.bashrc
aptitude install build-essential dkms unzip
aptitude build-dep fglrx
```

  I add auto-login to /etc/lightdm/lightdm.conf

```
[SeatDefaults]
greeter-session=unity-greeter
user-session=openbox
autologin-user=my_username
autologin-user-timeout=0
```
and
```
usermod -a -G nopasswdlogin my_username
```
next I install Catalyst from AMD site
```
wget ADM_drivers
unzip AMD_drivers
sh AMD_drivers
amdconfig --adapter=all --initial -f
reboot
```

next openssh server configuration and everything works fine.
 
Programs I use work in terminal and now I do this:


After system starts I run roxterm and with


```
screen -S name


```



I  create virtual console and run first of my programs, next "CTRL+A+D".  After that I create second session and run second program, "CTRL+A+D"  and that"s it.
 Thanks to that I can login through ssh and use screen to check on  my programs. But I need those 2 programs run automatically in virtual  consoles after I start the system to make my server headness


Please let me know if you have any solution. Your help will be very apprecieated.

---

### Post by jaddi27 on 2013-03-10
I suggest you take a look at this thread: [http://ubuntuforums.org/showthread.php?t=953750](http://ubuntuforums.org/showthread.php?t=953750). 

The main think to know is to use ```
su - <username>
``` or ```
sudo -u <username>
``` to select which user to run the screen as, and then to start the screen.

---

### Post by navoye on 2013-03-11
Thank You for Your answer, but I dont have full desktop environment and i  can only run xterm in mine(i dont have possibilty to  System>Preferences>Sessions). Also my user is auto-login with  lightdm so i think i can run screen as this user, dont need to use  sudo(but mayby i'm wrong) - very important for me is NOT to run those  programs before my desktop will run - so i think the best way will be to  add it somewhere after auto-login(but where and how?)
could You tell me where (in which file) add those run commands or in which manual should i look for instructions?

---

### Post by jaddi27 on 2013-03-17
When a shell is started, there is a file that is run to set it up. This is usually called ```
.bash_profile
``` (or ```
.profile
``` or ```
.bash_login
```), and is placed in the user home directory. You could add the commands you want executed to the bottom of this file, or run a script from there also. If you put your commands in a bash script file, ensure you make it executable (```
chmod +x scriptname
```).

You could also look into using Upstart to run a script on startup (I haven't tried this before) - [http://upstart.ubuntu.com/cookbook/#what-is-upstart](http://upstart.ubuntu.com/cookbook/#what-is-upstart)

Taken from [http://askubuntu.com/questions/173941/proper-way-to-execute-a-script-on-system-startup](http://askubuntu.com/questions/173941/proper-way-to-execute-a-script-on-system-startup) and [http://askubuntu.com/questions/98433/run-a-script-on-login-using-bash-login](http://askubuntu.com/questions/98433/run-a-script-on-login-using-bash-login)

---

