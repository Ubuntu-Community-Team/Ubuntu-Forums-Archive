---
title: "A problem with the tarballs (I don't know what i'm doing wrong)"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by nintendude7cubed on 2008-11-27
Whenever i use the commands in ubuntu's help to install a tarball, it can never find the tarball when i try to extract/cd the directory. I used windows to put the tarball onto my external harddrive if that helps. I type in EXACTLY what i am told. For example, i tried installing the tarball for the specified ralink 2860 driver tarball. I went step by step using this tutorial where i found it: [http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink]("http://ubuntuforums.org/showthread.php?t=966185&highlight=ralink") ... I used every command EXACTLY as written and after successfully removing the network manager and attemting to extract the tarball, it says the tarball doesn't exist. Is there anything that i'm possibly doing wrong here or missing? please help.

---

### Post by nothingspecial on 2008-11-27
Dose the file on your computer look exactly like this.

2008_0918_RT2860_Linux_STA_v1.8.0.0

If not, change all relevant commands.

---

### Post by Michael.Godawski on 2008-11-27
If the output of the tar command says the tarball does not exist you might be executing it in the wrong directory. Make sure you navigate in terminal into the exact location of the tarball. You can list all files of a directory with the command

```
ls -a
```

It helps me to navigate. Also you the TAB-Button to auto-complete long file names.

---

### Post by nintendude7cubed on 2008-11-27
> **nothingspecial said:**
> Dose the file on your computer look exactly like this.

2008_0918_RT2860_Linux_STA_v1.8.0.0

If not, change all relevant commands.

yeah it is the same.. im gonna try the other guy's idea ill get back on whether it works sooner or later cuz i need to restart... if anything ill comment sooner if it does work if i get it to work cuz the ill actually have internets on ubuntu :popcorn:

---

### Post by Keen101 on 2008-11-27
you could try copying the tar file to your desktop, and then use the 

> cd ~/Desktop command in the terminal. 

also make sure you have the same name archive as the tutorial. if not, just make sure you type in the right numbers.

---

### Post by Paqman on 2008-11-27
By far the easiest way to extract a tarball: right click > extract here.

---

### Post by nintendude7cubed on 2008-11-29
> **Keen101 said:**
> you could try copying the tar file to your desktop, and then use the 

 command in the terminal. 

also make sure you have the same name archive as the tutorial. if not, just make sure you type in the right numbers.

i understand now... you type cd then the exact location of the folder (after i extracted it by right clicking) and it changes it to that so it knows what folder you're modifying.. sweet. So i did that and made all the modifications i need for the ralink 2860 tutorial and guess what.. no luck! i need to make sure everything i put in that it told me to is correct and accurate before i give up, but ill do that once i've cooled off the frustration!

---

### Post by oldos2er on 2008-11-29
Can you please copy and paste the commands you typed, and their output?

---

