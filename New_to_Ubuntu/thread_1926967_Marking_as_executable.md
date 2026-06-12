---
title: "Marking as executable"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Spik31 on 2012-02-17
Hi,

I want to install some windows based software and wine is constantly complaining about the file not being "marked as executable" is there a way I can mark all of my files as executable?

If this causes a problem for ubuntu can I select a directory that I want to change?

---

### Post by winh8r on 2012-02-17
Right click on the file


click on permissions


select the box that says


allow executing file as program

---

### Post by themusicalduck on 2012-02-17
If you have a directory with .exe files that you want to change all to executable, the best way would be to do it with the command line.

Navigate to the directory using cd. So if it is on your desktop: ```
cd ~/Desktop/nameoffolder
```Then use the command: ```
chmod +x *.exe
``` chmod +x changes the permissions to allow executing (or chmod -x to change it back) and *.exe applies it to all files with .exe on the end.

If you have exe files in directories within that directory too, I think this would work: ```
chmod +x -R *.exe
``` but I'm not entirely sure if that's right. Someone else might be able to confirm.

Edit: just tested it, seems to work fine.

I don't think there is an easy way to do this with the GUI. Or to make all files executable by default.

---

### Post by Spik31 on 2012-02-17
> **themusicalduck said:**
> If you have a directory with .exe files that you want to change all to executable, the best way would be to do it with the command line.

Navigate to the directory using cd. So if it is on your desktop: ```
cd ~/Desktop/nameoffolder
```Then use the command: ```
chmod +x *.exe
``` chmod +x changes the permissions to allow executing (or chmod -x to change it back) and *.exe applies it to all files with .exe on the end.

If you have exe files in directories within that directory too, I think this would work: ```
chmod +x -R *.exe
``` but I'm not entirely sure if that's right. Someone else might be able to confirm.

Edit: just tested it, seems to work fine.

I don't think there is an easy way to do this with the GUI. Or to make all files executable by default.


Awesome! (/solved)

---

