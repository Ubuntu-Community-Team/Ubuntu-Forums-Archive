---
title: "Pogoplug"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by jfbooth on 2013-02-05
Rookie here with some pretty dumb questions.

Uhm .. running Xubuntu 12.04 .. XFCE.

Thought I would try to access my POGOPLUG drives with my Linux box.  Searching, I found this:

> 
1) Download and unpack pogoplug utility to a directory
2) cd to download directory
3) sudo usermod -a -G fuse $(id -u -n)
4) sudo mkdir /media/pogoplug
5) sudo chown root:fuse /media/pogoplug
6) sudo chmod 0777 /media/pogoplug/
7) sudo chmod +r /etc/fuse/config

I was then able to successfuly run the pogoplufs application and access my data.  I think step 6 could have used 0775 if I would have added myself to the fuse group, but this works.

Question #1:
Sooo I unpacked a file named pogoplugfs (an executable) to DESKTOP.  I don't think that is a good place to put it .. but don't actually KNOW a good place to put it.

Question #2:
Step #4 ... /media/pogoplug seems to me a folder which will appear in the C: ROOT directory (pardon the MicrosoftSpeak).  [COLOR="Red"]Uhm .. not actually Root .. there is a protected folder named Root .. I am talking about the top level of the file system ... Uh .. well .. you know what I mean ... right?[/COLOR]  If that is true, I prefer the folder be named Pogoplug.  If that is OK, I will modify the instruction.

Question #3:
Step #3 is something I can handle, .. I think ... once Question #1 is resolved.

All references to /media/pogoplug will become /pogoplug.

I have determined 'fuse' is already installed.

So .. if working folder can be Desktop, and 'install' folder can be /pogoplug, then it seems I am 'good to go' ..BUT ...what do I EXECUTE from an APPLICATION standpoint?  Filename pogoplugfs?  If that is the case, it is sitting on Desktop ... forever.  Hence, Desktop it not a good place for it ... so .. again where to put it?

Once it is where it belongs ... how do I then 'run it' without opening a file manager or terminal first?

I am not sure, but once I do this 'procedure' I THINK the pogoplug drive mounts automatically .. so I may not need to 'run' anything.  Dunno ... so confused.

Sorry to be so 'freshman'.  Thank you in advance.

---

### Post by omeomi on 2013-02-05
Q #1: You can put it everywhere you like. I typically put things like this in a directory inside my home folder, e.g. /home/omeomi/pogoplug.

Q #2: /media is the location where removable media like USB flash driver or CD/DVD are normally mounted by the system. Therefore have your directory inside /media would be sensible. Although it is not at all similar in your example /media is inside the toplevel folder (and it already is because it is a system folder) and the instructions tell you to create a subfolder called 'pogoplug'.

As far as the name of the directory, you can in theory use any folder name you want for it, so /media/Pogoplug is possible. However, I don't know if the utility expects it to be a lowercase name so for safety I would stick to that.

Q #3: You type the command exactly like that and press enter. That's all!

To start the application you first need to make it executable which you can do either using the GUI (right click -> Properties -> Permissions) or by the following command:
```
chmod +x /path/to/file/pogoplugfs
```

---

### Post by jfbooth on 2013-02-05
Thank you SO much for your kind reply and good advice.  Will mark this thread solved soon as I apply your instructions.  thank you again.

---

### Post by jfbooth on 2013-03-07
Between your advice and these instructions:

> 1) Download and unpack pogoplug utility to a directory
2) cd to download directory
3) sudo usermod -a -G fuse $(id -u -n)
4) sudo mkdir /media/pogoplug
5) sudo chown root:fuse /media/pogoplug
6) sudo chmod 0777 /media/pogoplug/
7) sudo chmod +r /etc/fuse/config

I was then able to successfuly run the pogoplufs application and access my data. I think step 6 could have used 0775 if I would have added myself to the fuse group, but this works.

I followed the instructions TO THE LETTER.  When I got to #3, I was informed that

> The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo

so I installed it with apt-get.  Then, at #7, I get:

> jb@Compaq-PC:~/pogoplug$ udo chmod +r /etc/fuse/config
Error:  0: couldn't open source file </etc/fuse/config.ui>
/etc/fuse/config.ui: No such file or directory

Help .. please.:confused:

---

### Post by Cheesemill on 2013-03-07
Look at your typos. The command is sudo not udo, your missing the s off the front :)

---

### Post by jfbooth on 2013-03-07
> **Cheesemill said:**
> Look at your typos. The command is sudo not udo, your missing the s off the front :)

You are obviously and absolutely right.  Thing is .. when I **sudo apt-get install udo** SOMETHING installed!!!  What .. I do not know ... and guess I never will.  Isn't there some kind of log where I can find out?

Anyway .. moving on, here is what I tried and now get:

jb@Compaq-PC:~$ cd pogoplug
jb@Compaq-PC:~/pogoplug$ ls
pogoplugfs
jb@Compaq-PC:~/pogoplug$ sudo usermod -a -G fuse $(id -u -n)
**4) sudo mkdir /media/pogoplug**  [COLOR="#FF0000"]already exists[/COLOR]
jb@Compaq-PC:~/pogoplug$ sudo chown root:fuse /media/pogoplug
jb@Compaq-PC:~/pogoplug$ sudo chmod 0777 /media/pogoplug/
jb@Compaq-PC:~/pogoplug$ sudo chmod +r /etc/fuse/config
chmod: cannot access `/etc/fuse/config': No such file or directory

/etc/fuse does not exist ... but Synaptic Package Mgr says FUSE is installed.


Thank you for your help.

---

### Post by tgalati4 on 2013-03-07
tgalati4@Mint14-Extensa ~/Desktop $ apt-cache search udo universal document
udo - universal document - text processing utility
udo-doc-de - universal document - German documentation
udo-doc-en - universal document - English documentatio

```
sudo apt-get remove udo
```

---

### Post by jfbooth on 2013-03-07
tgalati4 ... you are the best.  thank you.

---

### Post by jfbooth on 2013-03-13
Any Pluggers out there to help me?  Please??

---

