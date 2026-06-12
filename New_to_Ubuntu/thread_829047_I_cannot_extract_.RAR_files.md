---
title: "I cannot extract .RAR files"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by ahmed_nasr on 2008-06-14
hi all ,

i cannot extract rar files on buntu .... i installed rar compression/uncompression tool and when i try to extract a file usin it i get this :

[IMG]http://b.imagehost.org/0064/Screenshot-file-roller.png[/IMG]


so can anybody help me plz ?

---

### Post by dkruidhof on 2008-06-14
What tool did you install?

I have unrar (package in synaptic or apt-get) installed and it's worked fine for me.

edit: just noticed your error message said you don't have permission to extract it. If you are using the terminal, start the command with "sudo" w/o the quotes. If you want to use a gui, then hit alt+F2 and type in "gksudo nautilus" w/o quotes then enter your password. That will open up a window with root access, so be careful what you do, but it should allow you to extract that file.

---

### Post by dacorr on 2008-06-14
check the file permissions for the destination, its telling you it cannot write to the place you are extracting to.

Dac

---

### Post by aktiwers on 2008-06-14
If you have permition to extract it in your download folder, chech if the rar files permitions. 
Then change it if you dont have permition to extract it.

Open terminal and type:
```
sudo chmod 777 <Drag/drop rar file here>
```

---

### Post by ahmed_nasr on 2008-06-14
dkruidhof : i used nautilus but still got no permission

Dac : how to get permission to right on this location ?

---

### Post by SunnyRabbiera on 2008-06-14
> **dkruidhof said:**
> What tool did you install?

I have unrar (package in synaptic or apt-get) installed and it's worked fine for me.

edit: just noticed your error message said you don't have permission to extract it. If you are using the terminal, start the command with "sudo" w/o the quotes. If you want to use a gui, then hit alt+F2 and type in "gksudo nautilus" w/o quotes then enter your password. That will open up a window with root access, so be careful what you do, but it should allow you to extract that file.

but unrar does help, at least for extracting them in a normal install.

---

### Post by ahmed_nasr on 2008-06-14
> **aktiwers said:**
> If you have permition to extract it in your download folder, chech if the rar files permitions. 
Then change it if you dont have permition to extract it.

Open terminal and type:
```
sudo chmod 777 <Drag/drop rar file here>
```

i do this but still have no permission to extract

---

### Post by aktiwers on 2008-06-14
You need a space after the 777
```
sudo chmod 777 /media/sda5/Downloads/Al_Okzoba.rar
```

---

### Post by ahmed_nasr on 2008-06-15
hey .. guys i need help here

---

### Post by bumanie on 2008-06-15
Normally > sudo apt-get install rar unrar will usually allow you to do anything you need with .rar files.

---

### Post by subaruwrc01 on 2008-06-15
They have answered your question.  Make sure you have the correct path to the file and are typing the command right into the terminal.

If you are still having problems post your code and more help can be given.

---

### Post by aktiwers on 2008-06-15
What if you copy the rar file to your Desktop and extract it there?

---

### Post by aktiwers on 2008-06-15
If this is the case, I guess you for some reason don't have permission over your hard drive.
To give yourself permission run this command:
```
sudo chown -R USERNAME:USERNAME /media/sda5
```Where USERNAME is your Ubuntu username.
Then try unrar it again

---

