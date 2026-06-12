---
title: "Saving to DVD+R"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by johnwill on 2013-11-25
Hello.
I have letters written by my father whilst in M.E.F from 1940-44 and wish to scan and save to a DVD+R.
I Have Scanned with Simple Scan "Saved as"a file which comes up as saved in Gimp.
I then try and save file to the DVD to be told that there is no application to allow this.
Sadly I am unable to Scan via my printer without using Simple Scan   "Canon MP 610" 
What am I doing wrong? any help would be most appreciated.
Thank you.
JohnWill.
Ubuntu 12.04LTS

---

### Post by Lars Noodén on 2013-11-25
You generally have to gather all the files you want to save into one directory or a hierarchy under one directory, then make an ISO 9660 disc image.  Then it is that image which gets burned to the DVD.  

It should be possible to do that drag-and-drop in a graphical interface using a tool like K3b or whatever the disc burning package you have.  Try looking there.  

DVD RW is good to have for practice.

---

### Post by Dennis N on 2013-11-25
Once you have the files saved from the scanning in some image format such as .jpg, you have to burn them to the dvd, not save them.

Use a burning tool such as **xfburn** or **brasero** to do this and create a data DVD.

With DVD-R you get one shot per blank disk, so be sure you have all the files you want to burn assembled first. As you select them in the burning software window, you will be informed of the space being used on the DVD.

---

### Post by johnwill on 2013-11-25
Thank you both for your help.
Foolish of me! as when on Windows I needed a burning tool,and had forgotten this,is there any difference in the two programmes you mentioned?
Johnwill

---

### Post by Lars Noodén on 2013-11-25
They are about the same in capabilities, but different varieties (Lubuntu for example) has different pre-installed apps.  So, if you have xfburn on your system, you can use that.  If you have Brasero already, then use that.

---

### Post by johnwill on 2013-11-25
Thank you both

---

### Post by johnwill on 2013-11-26
Hello again.
Have downloaded Brasero as suggested: sudo apt-get brasero install.
Download continues,when finished cannot find download,have tried ls  -l brasero not shown also tried ls  -la also not shown.
How do I continue now-I am assuming download has been successful?
Thank you 
johnwill

---

### Post by Lars Noodén on 2013-11-26
Which distro are you running?  You installed via the Software Center, Synaptic or apt-get, right?

---

### Post by johnwill on 2013-11-26
Hello Lars.
Ubuntu 12.04LTS 64 bit Lenovo Desktop.
Used apt-get install.
john

---

### Post by VMC on 2013-11-26
> **johnwill said:**
> Hello again.
Have downloaded Brasero as suggested: sudo apt-get brasero install.
Download continues,when finished cannot find download,have tried ls  -l brasero not shown also tried ls  -la also not shown.
How do I continue now-I am assuming download has been successful?
Thank you 
johnwill
You actually installed it as opposed to downloading it. So just type ***brasero ***from a terminal [I](Ctrl+Alt+L). 
[/I][Installed programs, end up inside the  "/var/cache/apt" folder ]

---

### Post by johnwill on 2013-11-27
Hello

---

### Post by johnwill on 2013-11-27
Hello VMC 

Thank you solved typed brasero in terminal all ok.
Johnwill

---

### Post by VMC on 2013-11-27
@john,

Actually what ends up in "/var/cache/apt/archives" is the "deb" files. Most installed programs end up in "/usr/bin", but not all. Google is one exception.
You can use the terminal to find installed programs - "whereis brasero" finds binary files,  or "locate brasero" finds files based on databses, as an example.

[COLOR=#000000]If this topic is solved you can mark it so yourself.[/COLOR]

---

### Post by jimmyh1972 on 2013-12-05
try - sudo apt-get install xfburn
(its much more friendly use than braser)
the application should be on the "sound & video" tag on your desktop menu 
if you are using unity desktop click the ubuntu icon on the top of the unity laucher and type "xfburn" - it will pop-up

---

