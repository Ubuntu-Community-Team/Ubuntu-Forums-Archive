---
title: "Simple bash program"
date: 2007-07-15
forum: Programming Talk
---

### Post by Carleton91 on 2007-07-15
Hi, I'm pretty new to programming, but I have a need to automate 5 Terminal command lines that use sudo in order to connect to my wireless network. (I have issues connecting automatically so until I resolve those I would like to just be able to run a program that does these lines for me.)

They are:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid (My essid here)
sudo iwconfig wlan0 key (My key here)
sudo ifconfig wlan0 up
sudo dhclient

I made it a txt file on my desktop and then made a launcher out of it but then it said permission denied

---

### Post by max.diems on 2007-07-15
Create a file called get-online in your home directory and put these lines in it:
```

#!/bin/bash
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid (My essid here)
sudo iwconfig wlan0 key (My key here)
sudo ifconfig wlan0 up
sudo dhclient

```
Go to terminal and type
```
chmod 700 ./get-online
```
to make it executable. Now it can be run.

---

### Post by mattze on 2007-07-15
another very easy way to do this is to edit you .bashrc (in your home-dir)

just put:

function chose_your_command_name {
sudo ifconfig wlan0 down
sudo iwconfig wlan0 essid (My essid here)
sudo iwconfig wlan0 key (My key here)
sudo ifconfig wlan0 up
sudo dhclient
}

in there and restart the bash.
the effect is the same but i find it easier to keep track of your commands like this.
however some might see a securtiy risk in that.

---

### Post by max.diems on 2007-07-16
Or, if you want to use a compiled executable, you can compile this as a C++ program:
```

#include<cstdio>
#include<cstdlib>
#include<iostream>

using namespace std;

int main(int argc, char *argv[]);

int main(int argc, char *argv[]){
    system("sudo ifconfig wlan0 down");
    system("sudo iwconfig wlan0 essid INSERT_ESSID");
    system("sudo iwconfig wlan0 key INSERT_KEY");
    system("sudo ifconfig wlan0 up");
    system("sudo dhclient");
    return 0;
}


```

(Yes, it is EXACTLY the same as just putting in in a script. And, yes, using the system function is a cheat. What's your point?)

---

### Post by po0f on 2007-07-16
Carleton91,

Or you could just put that series of commands in /etc/rc.local.  Make sure to put them **before** the `exit 0` line in there by default.  IIRC, rc.local is run after all other startup scripts have executed, which is probably what you want if you are having wireless troubles.

Oh and full paths to commands help (I'm not quite sure how gimped startup script environments are).  Just type `which <command>` in a terminal to get the full path to the executable.

[EDIT]

And if you do go this route, you can drop the `sudo`; all startup scripts are run as root.

---

