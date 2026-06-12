---
title: "How to put files into root"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by chuckk2619 on 2008-05-02
Hi,

Am trying to upgrade my Nvidia drivers and need to get the latest driver into the root.   But Ubuntu won't let me, stating that only the user can do so.

How do I do I copy the file from the desktop to root?   I have saved the Nvidia file to my desktop.   Once it's in root I can then do the sh command to get it to run.

Thanks!

---

### Post by glennric on 2008-05-02
You don't need to copy the file into root, you need to run it as root.  To do this put "sudo" before whatever you are trying to run.

---

### Post by frup on 2008-05-02
Use terminal commands to make it easier such as sudo mv /home/user/Desktop/file /

or open nautilus as root with gksudo nautilus. 

With power comes responsibility.

EDIT:

and post above me is correct, I should have read more carefully.

---

### Post by Afkpuz on 2008-05-02
Well, to execute an sh file as root, you don't need to move that file to root.  Just add "sudo" before the sh command and run it from anywhere.  So the code would be,

```
sudo sh NVIDIA-something
```

---

### Post by chuckk2619 on 2008-05-02
I assume you have to run the sh command from inside terminal???

---

### Post by chuckk2619 on 2008-05-02
> **Afkpuz said:**
> Well, to execute an sh file as root, you don't need to move that file to root.  Just add "sudo" before the sh command and run it from anywhere.  So the code would be,

```
sudo sh NVIDIA-something
```

Okay got the file to run by using the sudo sh command in terminal.   However, the file then comes up with the following error:

 You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

Does this mean I have to run the sudo sh command in something other than terminal?

---

### Post by frup on 2008-05-02
No it means you should probably go CTRL ALT F1 and do it from the full terminal

Type CTRL ALT f7 to return to the GUI OR you may have to actually log out to GDM and select start session in terminal if it can't have x running at all.

Why are you fiddling with nvidia stuff though? If you are trying to install the proprietary nvidia driver have you tried the hardware drivers app in the system > administration menu?

---

### Post by chuckk2619 on 2008-05-03
> **frup said:**
> No it means you should probably go CTRL ALT F1 and do it from the full terminal

Type CTRL ALT f7 to return to the GUI OR you may have to actually log out to GDM and select start session in terminal if it can't have x running at all.

Why are you fiddling with nvidia stuff though? If you are trying to install the proprietary nvidia driver have you tried the hardware drivers app in the system > administration menu?

Hi Frup,

Thanks for the info...tried to instal via a safe terminal session but it still reckons I've got an X server open.   I'll try using the Envy installer instead.   Thanks for your help

---

### Post by Afkpuz on 2008-05-08
Just use the hardware manager.  System>Administration>Hardware Drivers

Check the box next to your video card and it should install for ya.

---

### Post by dtrot55 on 2008-05-08
Im just curious...what is the difference between these two lines of code?

sudo mv /home/user/Desktop/file /
sudo sh NVIDIA-something

What is the "mv" or "sh"

---

### Post by sam_delta on 2008-05-08
mv = move command,

example of mv

mv /file/to/move/path /destination/path

this will move the file on the first path into the file in the second path


and if im not wrong
sudo sh, = execute as super user in shell 

sam

---

### Post by Afkpuz on 2008-05-09
> **dtrot55 said:**
> Im just curious...what is the difference between these two lines of code?

sudo mv /home/user/Desktop/file /
sudo sh NVIDIA-something

What is the "mv" or "sh"



```
sudo mv /home/user/Desktop/file /
```
This command is a move command.  Thats what the "mv" part means.  Whatever follows the "mv" is the file that you want to move.  Then there's a space and then the place where you want to copy the file.  In the above case, it's "/".  That's your root folder, or your C: equivalent.
"sudo" means that you have root privileges when you execute any command.  So, you're moving a file on your desktop top called "file" to your root folder with root privileges



```
sudo sh NVIDIA-something
```
This is the "execute-a-shell-script" command.  That's what the "sh" means and then the file immediately following it is your .sh file.  In your case, it would be the NVIDIA .sh file.  I didn't know the exact name, which is why I wrote "NVIDIA-something".  Anyway, "sh" is the command you use to execute a .sh file.

---

