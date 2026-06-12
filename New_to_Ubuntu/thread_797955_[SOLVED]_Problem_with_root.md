---
title: "[SOLVED] Problem with root"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Sheneron on 2008-05-17
I have had to install some programs using root because it said I had to.  Now I am trying to add some finals into the folder of the program I installed and it said I don't have permission.  It says the root has permission but I do not.  How can I get on root to fix this?  Or what can I do to fix this?

---

### Post by forestpixie on 2008-05-17
Start the command with sudo eg.

sudo apt-get 
sudo dpkg

---

### Post by nowshining on 2008-05-17
or if u don't fill like sudo all the time use

sudo /bin/bash

then input ur pw, it won't show as u type - this is normal - when done with root and to go back to a user prompt just use the command exit.

---

### Post by zouzou0 on 2008-05-17
you can try ```
su 
```and wirte down the password

---

### Post by fmartinez on 2008-05-17
Depending on the folders your trying to modify determine who has permissions to them. In a terminal look at the out put of the command "ls -la /path/to/the/directory" this will show you the permissions of the directories below. At that point depending on what you need look at the man page for the command "chmod" and make any necessary permission changes. 
Also if you need to make changes or add files to the directory as root. You can always use sudo. try this command 
#sudo cp /youfile /path/to/root/owned/folder
The command above is only an example. 
The sudo command gives you temporary root privilages and allows you make changes as root for that one instance.

---

### Post by spiderbatdad on 2008-05-17
Use ```
sudo -s
or
sudo -i
```
You can have graphical root file permission with ```
gksu nautilus
```

---

### Post by Sheneron on 2008-05-17
Thanks everyone so far.  Is there anyway to do it without using the terminal?

---

### Post by grannyw on 2008-05-17
it is not so complicated as it seems just get the basis and go with it

---

### Post by amingv on 2008-05-17
> **Sheneron said:**
> Thanks everyone so far.  Is there anyway to do it without using the terminal?

> **spiderbatdad said:**
> 
You can have **graphical** root file permission with
```
gksu nautilus
```

Just be careful of what you do in there, and always make backups.

---

### Post by grannyw on 2008-05-17
Dont be obsessive about the backups just alway think about what exactly you are doing and how you can revert.

---

### Post by Oldsoldier2003 on 2008-05-17
> **Sheneron said:**
> Thanks everyone so far.  Is there anyway to do it without using the terminal?

The reason that you get mostly command line answers here in the forums is because its faster and more efficient than trying to talk someone through layers of menus and windows. Since you can copy/paste the commands directly into the terminal it make it more likely that there will be no misunderstandings, and also gives us a way of getting exact feedback when a command fails.

With that said, there is nothing wrong with using the gui when its available, its just easier on the forums to provide the help via terminal commands. It also gives you a taste of the power and flexibility of the command line :)

---

### Post by fmartinez on 2008-05-17
> **Oldsoldier2003 said:**
> 

With that said, there is nothing wrong with using the gui when its available, its just easier on the forums to provide the help via terminal commands. It also gives you a taste of the power and flexibility of the command line :)

Well said Oldsoldier2003! :)

---

### Post by Charlie708 on 2008-05-17
I would make backups before modifying files.  It isn't uncommon to make a small change to a huge file/script, and seemingly irreversibly break it.

There are ways around the command line, but it is by far more flexible than any GUI.  The command line isn't as hard to use as you may think, you just need to learn the commands.  Stick to it, and you'll be a pro in no time :)

---

### Post by nowshining on 2008-05-17
yeah a lot of people think it's this huge scary thing that if they input a wrong command their computer will blow all up. :D

---

### Post by Sheneron on 2008-05-18
Thank you all.

---

### Post by nowshining on 2008-05-18
ur welcome.

---

