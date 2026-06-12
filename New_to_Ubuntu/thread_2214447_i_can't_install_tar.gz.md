---
title: "i can't install tar.gz"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by albaniaguard on 2014-04-01
[COLOR=#000000]i try to install PCL_EMALB.tar.gz i do extraxt in desktop and i try to install with terminal the install.sh but i take a eror[/COLOR]
[COLOR=#000000]..................start install.................*** Check for root - failed[/COLOR]
[COLOR=#000000]*** Please retry as root user.[/COLOR]
[COLOR=#000000]press any key to exit.... [/COLOR]
[COLOR=#000000]what i can do ?[/COLOR]

---

### Post by apohal9 on 2014-04-01
It looks like this install-script is requiring root-rights. Open a terminal, change to the location where you've extracted the script to (If you've for example extracted to Downloads change by "cd Downloads/") and then do "sudo bash install.sh" on it.

---

### Post by albaniaguard on 2014-04-01
i have it in usb

---

### Post by Lars Noodén on 2014-04-01
Which package is it for?  If that package is already in the repository or in a PPA that would be the best way to install it.

---

### Post by albaniaguard on 2014-04-01
i have in a internet usb and i have like " PCL_EMALB.tar.gz" and i nead to install it to conect with the internet. in instructions is set extraxt this and leater run with the terminal the install.sh and i do it and is not installet but i take this eror 
[COLOR=#000000][COLOR=#000000].................start install.................*** Check for root - failed[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*** Please retry as root user.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]press any key to exit.... [/COLOR][/COLOR]

---

### Post by apohal9 on 2014-04-01
> **albaniaguard said:**
> i have it in usb

Same here. Check where the usb storage is mounted (should be in /media/) and do the same there.

---

### Post by albaniaguard on 2014-04-01
i try like this  sudo bash install.sh /media/Eagle Speed/Linux/PCL_EMALB.tar.gz  and is no work :(

---

### Post by Lars Noodén on 2014-04-01
As apohal9 mentioned, it is probably something like this:

```

sudo ./install.sh PCL_EMALB.tar.gz

```

or this

```

sudo sh ./install.sh PCL_EMALB.tar.gz

```

Can you paste exactly what you type and the exact resulting error message inside [****code] [/code] tags?

---

### Post by albaniaguard on 2014-04-01
i try the 2 comand and say cant open install.sh 
but here is the extraxt /home/ervis/Desktop/PCL_EMALB  and i try like this sudo bash install.sh/home/ervis/Desktop/PCL_EMALB and is not work i say bash: install.sh/home/ervis/Desktop/PCL_EMALB: No such file or directory

---

### Post by apohal9 on 2014-04-01
@Lars Noodén: I think the install.sh script is probably from within the tar, don't you think?

@albaniaguard: please open a terminal and put in there:

```

cd /home/ervis/Desktop/PCL_EMALB
sudo sh ./install.sh

```

---

### Post by albaniaguard on 2014-04-01
./install.sh: 31: ./install.sh: function: not found
Ubuntu
./install.sh: 46: ./install.sh: Syntax error: "}" unexpected
ervis@ervis-Aspire-5810T:~/Desktop/PCL_EMALB$ 
  i take this code from the terminal when i try this comand

---

### Post by steeldriver on 2014-04-01
... it looks like you are trying to execute install.sh in the wrong interpreter; please check what kind of file it is using the command

```
file install.sh
```

from the ~/Desktop/PCL_EMALB directory (where you are now)

---

### Post by albaniaguard on 2014-04-01
i have it in this place '/home/ervis/Desktop/PCL_EMALB/install.sh'

---

### Post by steeldriver on 2014-04-01
understood - and your terminal is currently **in** /home/ervis/Desktop/PCL_EMALB/ so you can do

```
file install.sh
```

It should tell us whether it is a bash script or a POSIX (dash) script or possibly a csh script

---

### Post by albaniaguard on 2014-04-01
when i try this comand i take this
 ervis@ervis-Aspire-5810T:~$ file install.shinstall.sh: ERROR: cannot open `install.sh' (No such file or directory)

---

### Post by steeldriver on 2014-04-01
I asked you to run the command **in the directory containing the install.sh file** (i.e. ervis@ervis-Aspire-5810T:[COLOR=#ff0000]~/Desktop/PCL_EMALB[/COLOR]$)

It seems you have tried to run it from your **home directory** (ervis@ervis-Aspire-5810T:[COLOR=#ff0000]**~**[/COLOR]$)  - this is not the same thing. 

If you find the directory structure difficult to navigate then you can just use the absolute file name

```
file /home/ervis/Desktop/PCL_EMALB/install.sh
```

---

### Post by monkeybrain20122 on 2014-04-01
> **albaniaguard said:**
> when i try this comand i take this
 ervis@ervis-Aspire-5810T:~$ file install.shinstall.sh: ERROR: cannot open `install.sh' (No such file or directory)

Is it in Desktop/PCL_EMALB/ ? Open the folder and have a look

if this is the case right click the file install.sh, from Properties > Permission check the box 'allow file to execute as a program..' (or something like that)

then open a terminal (If it is somewhere else, change 'Desktop/PCL_EMALB' to the path of wherever the file 'install.sh' is)
```
cd Desktop/PCL_EMALB/
sudo ./install.sh
```
if that doesn't work

```
cd Desktop/PCL_EMALB/
sudo sh install.sh
```

you either 'sh install.sh' or './install.sh' but not 'sh ./install.sh'! (post#10)

Edited: I don't know what this program is for, but you don't need sudo to run the install script if you just install the program in your /home. If you have to install for the system for it to work then you need sudo.

---

### Post by albaniaguard on 2014-04-01
thankyou vary much :)

---

