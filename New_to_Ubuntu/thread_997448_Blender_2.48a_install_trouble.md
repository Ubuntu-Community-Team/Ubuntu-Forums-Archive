---
title: "Blender 2.48a install trouble"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by tampablendie on 2008-11-29
I'm trying to install Blender 2.48a.  It's not available from synaptics or add/remove(only 2.46 is).  So I downloaded the tar.bz2 from Blender.org and extracted the file.

I then double click the Blender executable file and nothing happens.  No error no attempt by Ubuntu to do anything???  I've read somewhere that Ubuntu does not have the dependencies for Blender installed???

What does that mean?? How do I install it?

Keep in mind I am an Uber Noob, this is my first day on Ubuntu.  Looking forward to blending! ;-)

---

### Post by linuxguymarshall on 2008-11-29
If you give me 5 mins to get out of Fluxbox, load into KDE, get a can of Bawls and download it through my T1 line then I will help you. I need to do it as well

---

### Post by tampablendie on 2008-11-29
thanx man I would really appreciate it

---

### Post by bruce89 on 2008-11-29
The tarball (tar.bz2) is just a source archive. You'd have to compile the source. I'm sure someone will post how, as I don't do details.

Anyway, is there any reason why 2.36 won't suffice? People recently from Windows get version fever.

---

### Post by linuxguymarshall on 2008-11-29
Kde hung its self so im back in Fluxbox. downloading  the tarball now.


Which version did you get? I dowloaded Python 2.5

---

### Post by linuxguymarshall on 2008-11-29
I just ran it. Opened it up, double click Blender and BAM!

---

### Post by tampablendie on 2008-11-29
I downloaded both and had luck with neither.  It says on the blender site and the Ubuntu documentation that after extracting the tar file that you should be able to run blender straight from executable.

---

### Post by bruce89 on 2008-11-29
> **tampablendie said:**
> I downloaded both and had luck with neither.  It says on the blender site and the Ubuntu documentation that after extracting the tar file that you should be able to run blender straight from executable.

Ah, try executing it from the terminal, and post any output.

---

### Post by tampablendie on 2008-11-29
how do I run a file from the terminal that I downloaded??

Your patience with my noobisms are greatly appreciated

---

### Post by bruce89 on 2008-11-29
> **tampablendie said:**
> how do I run a file from the terminal that I downloaded??

Your patience with my noobisms are greatly appreciated

After "cd"ing to the directory where the file is, use ```
./file.name
``` to execute the file (assuming it is executable).

---

### Post by tampablendie on 2008-11-29
terminal says "program Blender is not yet installed you can get it by typing""sudo apt-get install blender""


But using that terminal command Downloads the 2.46 version which is missing some features that I have used on current projects I am working on

---

### Post by bruce89 on 2008-11-29
> **tampablendie said:**
> terminal says "program Blender is not yet installed you can get it by typing""sudo apt-get install blender""


But using that terminal command Downloads the 2.46 version which is missing some features that I have used on current projects I am working on

You are running the one in PATH. You need to extract the tarball, cd to it in the terminal, and then run the main script (probably blender) by using [FONT="Monospace"]./blender[/FONT].

---

### Post by linuxguymarshall on 2008-11-29
I think I know. Do you have Python installed? Open synaptic and install python 2.5.

---

### Post by tampablendie on 2008-11-29
Bruce what I typed in terminal

cd/home/mike/blender

blender

got the same error blender not installed

Marshall In synaptics it says I have Python 2.5.2 in stalled

---

### Post by tampablendie on 2008-11-29
WTF???? Just started working????  Thanks for your efforts guys I have no idea what I did It just started working all of a sudden!

Woot Woot

---

### Post by linuxguymarshall on 2008-11-29
Have fun. If you plan to make human or human like figures then I will recommend makeHuman. I use it extensively in my games and animations. Its free and open source

---

### Post by lavinog on 2008-12-19
> **tampablendie said:**
> Bruce what I typed in terminal

cd/home/mike/blender

blender

got the same error blender not installed

Marshall In synaptics it says I have Python 2.5.2 in stalled

For future reference:
to execute a program that is not in a folder like /usr/bin /usr/local/bin...etc
you need to execute the program with the folder name ie:
```

/home/mike/blender/blender
or 
cd/home/mike/blender
./blender

```
the ./ means current folder
typing blender (without ./) causes the system to search the folders in your $PATH variable for an executable named blender...this is why you are getting a blender not installed statement.
to see the folders in your $PATH variable you can type this in a terminal
```

echo $PATH

```

---

