---
title: "Custom Application Launcher"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by zeththedarkmage on 2008-07-22
I have a program that is located in my documents and I want to make an application launcher for it, but when I browse and find the file and put gksudo in front of it and try to get it to come up it asks for my password but doesn't open the program after. (the program is weird and requires me to run sudo for it to work) So what am I doing wrong?

---

### Post by stoneybroke on 2008-07-22
On the desktop right click and then select Create Launcher the new window will ask for a description enter something then click Browse to go to the application that you wish to launch once that's done there will be a small icon on the desktop normally looks like a spring with a board on it clicking this will launch the application.

Hope that helps...

---

### Post by zeththedarkmage on 2008-07-22
I've tried that, and thats where the problem comes in, when I click it for it to launch the program the program does not launch.

---

### Post by zeththedarkmage on 2008-07-22
bump

---

### Post by Oldsoldier2003 on 2008-07-22
What is the program you are trying to launch? it may be a path issue or you may need additional parameters.

---

### Post by Tim Sharitt on 2008-07-22
I'm just throwing this out there. Is the command something like
```
gksudo ~/Documents/program
```
If so it needs to be 
```
gksu /home/*USERNAME*/Documents/program
```

---

### Post by seuzy13 on 2008-07-22
You might try moving into your system path. If you cp the file to /usr/bin, you could just type in the command "gksudo" + application name.

---

### Post by ktrnka on 2008-07-22
Is the program set as executable?

```
chmod +x program
```

---

### Post by zeththedarkmage on 2008-07-22
the program is stepmania, a DDR simulator for the computer.

I have a whole folder for it but I just put it into the documents folder. There is an executable but the only way I get it to run normally is sudo ./stepmania through terminal when I'm in the folder.

EDIT: Problem solved there was spaces in one of the folder names and it was causing it to not read properly so when I changed the name of the folder it is working now. Thanks all.

---

### Post by Tim Sharitt on 2008-07-22
Are you giving the full path in the launcher?

---

### Post by ktrnka on 2008-07-22
If you're not giving it the full path name then you could just create a symlink in /bin to the folder.

eg.

```
sudo ln -s /fullpath/to/executable /bin/stepmainia
```

---

