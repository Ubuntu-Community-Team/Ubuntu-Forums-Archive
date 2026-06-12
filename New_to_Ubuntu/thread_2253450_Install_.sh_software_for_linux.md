---
title: "Install .sh software for linux"
date: 2014-11-19
forum: New to Ubuntu
---

### Post by MrNewie on 2014-11-19
Hello I am struggling trying to install programs on linux.

I am running this program via wine but they released a linux version BUT I am stumpted::mad:

---

### Post by MrNewie on 2014-11-19
here is more info
thanks

---

### Post by monkeybrain20122 on 2014-11-19
Right click the .sh file, choose Properties > Permssions and check allow to execute.

Then run it by opening a terminal 

```
cd /path/to/.sh file
./ddpoker3.sh
```

/path/to/.sh file is the path to the file ddpoker3.sh. from your screenshot it would be Downloads/seamonkey (note the capital D)

---

### Post by MrNewie on 2014-11-19
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ ./ddpoker3.sh
bash: ./ddpoker3.sh: No such file or directory
eric@Eric:~$

---

### Post by monkeybrain20122 on 2014-11-19
No, I said you have to replace /path/to/.sh file by the actual path where ddpoker.sh is, in your screenshot it would be
```
cd Downloads/seamonkey
```

---

### Post by MrNewie on 2014-11-19
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ ./ddpoker3.sh
bash: ./ddpoker3.sh: No such file or directory
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ cd Downloads/seamonkey
eric@Eric:~/Downloads/seamonkey$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ 
eric@Eric:~/Downloads/seamonkey$ /path/to/.sh file is the path to the file ddpoker3.sh.
bash: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ /path/to/.sh
bash: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ ./ddpoker3.sh
bash: ./ddpoker3.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$

---

### Post by sandyd on 2014-11-19
> **MrNewie said:**
> eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ ./ddpoker3.sh
bash: ./ddpoker3.sh: No such file or directory
eric@Eric:~$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~$ cd Downloads/seamonkey
eric@Eric:~/Downloads/seamonkey$ cd /path/to/.sh file
bash: cd: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ 
eric@Eric:~/Downloads/seamonkey$ /path/to/.sh file is the path to the file ddpoker3.sh.
bash: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ /path/to/.sh
bash: /path/to/.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$ ./ddpoker3.sh
bash: ./ddpoker3.sh: No such file or directory
eric@Eric:~/Downloads/seamonkey$

Hi, you should replace /path/to/.sh file with the actual path to the file.

For example, the file you are looking to run, ddpoker3.sh is in the Downloads folder.
As a result, to run ddpoker3.sh, you would run
```

chmod u+x ~/Downloads/ddpoker3.sh
bash ~/Downloads/ddpoker3.sh
```
The first command adds executable permissions to the ddpoker3.sh file while the second runs ddpoker3.sh

---

### Post by MrNewie on 2014-11-19
eric@Eric:~/Downloads/seamonkey$ cd
eric@Eric:~$ chmod u+x ~/Downloads/ddpoker3.sh
eric@Eric:~$ bash ~/Downloads/ddpoker3.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:39: Failed to parse property value " GTK_SHADOW_NONE " for `GtkMenuBar::shadow-type'
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:42: Failed to parse property value " GTK_SHADOW_NONE " for `GtkToolbar::shadow-type'
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:66: error: lexical error or unexpected token, expected valid token

---

### Post by Ric_Helm on 2014-11-23
Installing Wine apps, I just used to repository to install "Winetricks", then I install with the WIndows application from Ubuntu desktop. Most work fine. A few don't. As I understand through *Cup of Linux*, I just don't have the dll's required. I never looked, what didn't work was unimportant to me.

Point is, why are you not just using Winetricks and the associated WINE files through the repository?

Did I miss something here???

---

### Post by monkeybrain20122 on 2014-11-23
> **Ric_Helm said:**
> 
Did I miss something here???

It is a linux program.

OP is having java error. Maybe he needs a different version or Oracle Java. Don't really know how to help with this. But it has nothing to do with wine.

---

### Post by GrouchyGaijin on 2014-11-23
Hmmmm I am running Ubuntu 14.04 and don't remember installing anything out of the ordinary for java.

I downloaded their script to ~/Downloads.
In a terminal I typed cd ~/Downloads (From your home folder cd Downloads will also work)
Then like their instructions say from the terminal I ran:
```
chmod 755 ddpoker3.sh 
```  This makes the file executable. (You can run it.)
Followed by:
```
sudo ./ddpoker3.sh
```
The sudo is to be able to install software.
Then the installer started.

I hit cancel because I don't really want a hold 'em poker game.

---

### Post by monkeybrain20122 on 2014-11-23
> **GrouchyGaijin said:**
> 
```
sudo ./ddpoker3.sh
```
The sudo is to be able to install software.
Then the installer started.

I hit cancel because I don't really want a hold 'em poker game.

Why do you need sudo? OP should be able to install it in $HOME. I can be wrong, but those errors appear to be java related rather than not having root permission to run the script.

---

### Post by GrouchyGaijin on 2014-11-23
I thought you need sudo to install anything.  Try running this program without sudo and see what happens. 

I just tried without sudo and the installer splash screen did appear, but I also got:

```

~/Downloads $ ./ddpoker3.sh
Unpacking JRE ...
Preparing JRE ...
Starting Installer ...
/usr/share/themes/Numix Daily/gtk-2.0/gtkrc:85: error: lexical error or unexpected token, expected valid token


```
which is an error I did not get when I ran the install command with sudo.

---

### Post by GrouchyGaijin on 2014-11-25
I wonder how this turned out for the OP?

---

