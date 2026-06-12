---
title: "Installing sh file"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by mancroft on 2008-06-07
I just downloaded boinc_5.10.45_i686-pc-linux-gnu.sh for SETI to my downloads folder and don't know how to install it.

Any help appreciated.

---

### Post by ukripper on 2008-06-07
if it is a .sh that means it is a shell script. 
Warning: Make sure first what you are installing on your system. Check the shell script what it is doing only then install if you are satisfied.

go to the download directory where you have saved your file and then
here is the command to install any shell script:
```
sh filename.sh
```
 replace filename with your file's name

---

### Post by st33med on 2008-06-07
Well, no installation is required for an sh (that is, if it isn't the installer, which it probably is). To run it, you need to go to the file, right click it, select 'Properties' in the menu, go to the permissions tab, and there is a checkbox at the bottom that says "Allow executing file as a program". Click on that. Now, you can double click it and choose Run in Terminal box in the pop-up window.

---

### Post by rampageoberon on 2008-06-07
Try this

```

chmod 755 boinc_5.10.45_i686-pc-linux-gnu.sh
./boinc_5.10.45_i686-pc-linux-gnu.sh

```

It makes the file executable and then runs the script. (Make sure you read the script in a text editor and check what commands are being run)

---

### Post by mancroft on 2008-06-07
> **ukripper said:**
> if it is a .sh that means it is a shell script. 
Warning: Make sure first what you are installing on your system. Check the shell script what it is doing only then install if you are satisfied.

go to the download directory where you have saved your file and then
here is the command to install any shell script:
```
sh filename.sh
```
 replace filename with your file's name

Tried it. Doesn't work. Gives: > john@john-desktop:~$ sh boinc_5.10.45_i686-pc-linux-gnu.sh
sh: Can't open boinc_5.10.45_i686-pc-linux-gnu.sh
john@john-desktop:~$ 


---

### Post by mancroft on 2008-06-07
> **st33med said:**
> Well, no installation is required for an sh (that is, if it isn't the installer, which it probably is). To run it, you need to go to the file, right click it, select 'Properties' in the menu, go to the permissions tab, and there is a checkbox at the bottom that says "Allow executing file as a program". Click on that. Now, you can double click it and choose Run in Terminal box in the pop-up window.

Tried it. Just opens a box which closes immediately. The other to buttons... run and something else do not work either.

---

### Post by mancroft on 2008-06-07
> **rampageoberon said:**
> Try this

```

chmod 755 boinc_5.10.45_i686-pc-linux-gnu.sh
./boinc_5.10.45_i686-pc-linux-gnu.sh

```

It makes the file executable and then runs the script. (Make sure you read the script in a text editor and check what commands are being run)

Tried it and get:

> john@john-desktop:~$ chmod 755 boinc_5.10.45_i686-pc-linux-gnu.sh
chmod: cannot access `boinc_5.10.45_i686-pc-linux-gnu.sh': No such file or directory
john@john-desktop:~$ ./boinc_5.10.45_i686-pc-linux-gnu.sh
bash: ./boinc_5.10.45_i686-pc-linux-gnu.sh: No such file or directory
john@john-desktop:~$ 


---

### Post by st33med on 2008-06-07
You need to cd to the directory in order to change the permissions.
For example, if your file was in the desktop:
```
cd ./Desktop
chmod u+x boinc_5.10.45_i686-pc-linux-gnu.sh
./boinc_5.10.45_i686-pc-linux-gnu.sh

```

The 'cd ./[directory]' means to go to a folder in your current directory, which should be your home directory. A '~' in cd means to start from your home directory.

---

### Post by RATM_Owns on 2008-06-07
You have to be in the same directory as the file when using chmod.

---

### Post by rampageoberon on 2008-06-07
Well you are trying to do those operations to a file that doesn't exist. Where is the file saved? Desktop?

If so do

```
cd Desktop/
```

and then run the commands I said

---

### Post by mancroft on 2008-06-07
**[COLOR="Red"]BINGO![/COLOR]**

Thanks, guys, it worked when I changed directories. :guitar:

---

### Post by rampageoberon on 2008-06-07
In future try using tab complete, so type the first few letters of the filename and press tab. If it doesn't complete means the file is not there. Always useful that

---

