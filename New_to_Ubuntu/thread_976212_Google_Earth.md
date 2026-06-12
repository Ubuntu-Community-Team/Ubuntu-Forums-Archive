---
title: "Google Earth"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by beswatcher on 2008-11-09
What am I doing wrong using terminal? I have downloaded Google Earth for Linux to the desktop, and have tried to use the instructions from Google.

"Open a terminal window/console and navigate to your default downloads directory. Enter the following command in the directory: > sh GoogleEarthLinux.bin"

When I try using terminal, this is what I get

rick@rick-desktop:~$ > sh GoogleEarthLinux.bin
bash: GoogleEarthLinux.bin: command not found
rick@rick-desktop:~$ 

 I've got to be doing something wrong.

---

### Post by Tom--d on 2008-11-09
Right click the file > properties > permission etcetc > Tick allow file to be excuated (something like that) now do it.

---

### Post by beswatcher on 2008-11-09
Just tried it, Tom. Same thing from terminal.:confused:

---

### Post by Tom--d on 2008-11-09
Ah.. sorry, silly me. Do this as well,
```
sudo sh GoogleEarthLinux.bin
```

---

### Post by Ryadt on 2008-11-09
The code is ```
sh GoogleEarthLinux.bin
```
without the **>**

---

### Post by beswatcher on 2008-11-09
Iv'e tried both codes, but all I get is

rick@rick-desktop:~$ sudo sh GoogleEarthLinux.bin
sh: Can't open GoogleEarthLinux.bin

At least now terminal realizes that a file is there!

---

### Post by natirips on 2008-11-09
Try this in the terminal if you plan on installing somewhere in your home folder:```
./GoogleEarthLinux.bin
```

Try this in the terminal if you plan on installing it into something like /usr/... or /opt/...:```
sudo ./GoogleEarthLinux.bin
```

---

### Post by Ryadt on 2008-11-09
You must have the medibuntu repos for google earth.```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

and you can install if you want with ```
sudo apt-get install googleearth
```

---

### Post by gmanuel on 2008-11-09
I just opened a terminal then drag the Google Earth.bin icon into the terminal and pressed enter.  It is installing now

---

### Post by natirips on 2008-11-09
> **Ryadt said:**
> You must have the medibuntu repos for google earth.```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
``````
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

and you can install if you want with ```
sudo apt-get install googleearth
```
I have google earth without the medibuntu repos. (Installed from the binary with "sudo ./GoogleEarthLinux.bin".)
Although the repos are generally a better way.

---

### Post by beswatcher on 2008-11-09
> **gmanuel said:**
> I just opened a terminal then drag the Google Earth.bin icon into the terminal and pressed enter.  It is installing now

The simplest things work best! Except I had to hit enter twice. Google earth is running now.

Thanks everyone!!

---

