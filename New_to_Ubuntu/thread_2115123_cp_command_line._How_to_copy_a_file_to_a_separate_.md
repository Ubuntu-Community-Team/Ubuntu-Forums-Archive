---
title: "cp command line. How to copy a file to a separate folder"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by terradax on 2013-02-12
Me@Me:~$ ls
Desktop    Downloads         Music     Public     Ubuntu One
Documents  examples.desktop  Pictures  Templates  Videos
Me@Me:~$ cd ./Documents
Me@Me:~/Documents$ ls
Documentation  en-US           malware         Win_Documents
Drive          Me_Documents  Untitled 1.doc
Me@Me:~/Documents$ cd ./Documentation
Me@Me:~/Documents/Documentation$ ls
Advanced_Bash_Scripting.pdf   LinuxFromScratch.pdf
Easiest_Linux_guide_ever.pdf  Linux_hard_disk_layout.pdf
GNU-LinuxAdvanced.pdf         Unix_Linux_SysAdmin_Shell_Prog.pdf
LInux_Command_Line.pdf
Me@Me:~/Documents/Documentation$ cp LInux_Command_Line.pdf malware
Me@Me:~/Documents/Documentation$ 

This is what I did. I am trying to copy LInux_Command_Line.pdf into the folder malware. Can anyone tell me what i did wrong. 
After running this, I end up with a copy of the file LInux_Command_Line named malware.

---

### Post by omeomi on 2013-02-12
The problem is that the 'malware' folder is not inside the current directory.

So you need to run it like this:
```
$ cp LInux_Command_Line.pdf ../malware
```

the '../' command means 'go one level up' from the current folder, so it refers to the Documents folder.

---

### Post by wlraider70 on 2013-02-12
If you get lost in the file structure go to the destination and type "pwd" it will print working directory. You can then copy and paste that. This way you can tell it

cp LInux_Command_Line.pdf /home/me/Documents/malware

---

