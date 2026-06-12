---
title: "PSP manager installation help"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Dalston on 2008-05-26
Hello im trying to set up qpspmanager-2.0.2 on 8.04 using this guide [https://help.ubuntu.com/community/PSP#head-fa4de8668dea93576d79f6c243f505e79b880f6e-2]("https://help.ubuntu.com/community/PSP#head-fa4de8668dea93576d79f6c243f505e79b880f6e-2") it says "*Unfortunetly the last step doesn't work for everyone (make install). Instead a QPSPManager executable file is made in the bin directory. You can then copy this to /usr/local/bin yourself.*"  But I dont seem to be able to do the last 2 steps..
```
make

```
```
sudo make install

```

After I type make into the terminal i get this error..
```
make: *** No targets specified and no makefile found. Stop.
```
Can someone help me work out where im going wrong please?

---

### Post by Dalston on 2008-05-26
Do I have to put anything in with ```
make
```?

---

### Post by zeronothing on 2008-05-26
I helped someone with this same exact problem. check out the old post on how to get the qpspmanager running 

[http://ubuntuforums.org/showthread.php?t=747725](http://ubuntuforums.org/showthread.php?t=747725)

---

### Post by Dalston on 2008-05-26
Thanks for your help, i've got stuck on this part "next we need to compile the program. open up terminal and change directory into the root of the qpspmanager folder."  I dont understand how to change directory into root.

---

### Post by cariboo on 2008-05-26
In a terminal:

```
cd qpspmanager
```

Thats assuming that the qpspmanager directory in in your home directory.

Once you are in the qpspmanager you want to type:

```
./configure
```

Once that has run it's course. Type

```
sudo make && make install
```

Once that has finished with no erros you should be able to use your program. It more then likely won't add an entry into your menu so you'll have to do it maually.

Good Luck

Jim

---

### Post by Dalston on 2008-05-26
When I put in

```
./configure
```

I get this

```
bash: ./configure: No such file or directory
```

---

### Post by zeronothing on 2008-05-26
> **Dalston said:**
> Thanks for your help, i've got stuck on this part "next we need to compile the program. open up terminal and change directory into the root of the qpspmanager folder."  I dont understand how to change directory into root.

When I say change into the root of the directory, you need to use the "cd" command which stands for "change directory." when I say change into the "root of the qpspmanager folder" you need to change directory into the Qpspmanager folder wherever that my be.

you had to first download the file and save it somewhere (most likely your desktop). then you had to extract what was in the tar.gz file to somewhere (possibly to your desktop). that folder that you extracted from the tar.gz would be the qpspmanager folder. Now if you would happen to click on that folder that was extracted from the tar.gz file you would be technically be at the root of the qpspmanager folder. this is what I'm talking about in the instructions. so using termainal just "cd" into the main directory. hope this helps

---

### Post by Dalston on 2008-05-26
This is all confusing me for some reason,  i've never had this trouble installing something before.  After I enter ```
cd qpspmanager
``` i get this ```
username:~/qpspmanager/src$
``` which I presume means im in the root,  but then when I enter ```
./configure
``` it still says ```
bash: ./configure: No such file or directory
``` The folder has been extracted but its saying no such file.

---

### Post by Dalston on 2008-05-26
Ok I think im nearly there i've got to the stage where in the terminal it says.. 
```
[COLOR="Lime"]QPSPManager[/COLOR]
usernameGhost:~/qpspmanager/bin$
```
But I cant move the executable to /usr/bin because when I execute
```
 sudo cp QPSPmanager /usr/bin/
```
It says..
```
cp: cannot stat `QPSPmanager': No such file or directory
```
Thanks for your help so far, theres just this last step to work out.

---

### Post by zeronothing on 2008-05-27
I hope this helps, attached to this post is a howto document. this should take you step by step through the process of installing Qpspmanager.

---

### Post by Dalston on 2008-05-27
Thanks I got it going late last night,  only thing is I cant move files to my psp, I think its because of file permissions.  When i try to change them it says its read only.

---

### Post by zeronothing on 2008-05-27
The fix for that problem is to load Qpspmanager as root and you shouldn't have any problems. this will allow you to convert .iso images to .ciso. if you do this it will take the .iso image and create the .ciso image and dump it to the Root of the file system. I hope the program gets updated to dump the image into your home directory.

---

### Post by Dalston on 2008-05-27
Ok i tried loading pspmanager through the root using ```
gksudo nautilus
``` but I get this error in pspmanger  "error copying file.iso"

---

### Post by zeronothing on 2008-05-27
try this, if you use the keyboard shotcut "Alt + F2" this will bring up the run application window. from their type "gksu QPSPManager" this will load QPSPManager with root privileges

---

### Post by Dalston on 2008-05-27
Tried that and got the same error.

---

### Post by Dalston on 2008-05-28
I think its more to do with the file permissions on the PSP rather than the file permissions of PSPManager,  because I can copy stuff from my PSP to the folder PSPMsnager sets up in the options, just not the other way.

---

### Post by lunarcloud on 2009-05-06
I've fixed the help page, [https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)
and I got video conversion to work, but only after linking to the pspvc version of ffmpeg.

---

