---
title: "[SOLVED] Changing GRUB Config?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by UnknownFear on 2008-05-09
I ma having problems changing my GRUB configuration. I am trying to make it so I dont have a timeout on the boot screen in menu.lst, but I cant change it cause i dont have the permisisons. I keep running into this with everything! It keeps saying that I am not the owner in all the permissions tabs. Any help with this? How can I make it so I am the owner and STAY the owner??

---

### Post by Six_Digits on 2008-05-09
Are you familiar with sudo? Or is that not what you're asking...
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by newbuntuxx on 2008-05-09
hey

you need to use the terminal.

so, if you want to edit system files, you have to use sudo in terminal like this:

sudo gedit "Path to file"

as for grub, to edit the time out run this in terminal:

sudo gedit /boot/grub/menu.lst

and I think you can edit the time in that file.

---

### Post by forrestcupp on 2008-05-09
you can also install Startup Manager, which is a GUI to set all of that stuff.
```
sudo apt-get install startupmanager
```

---

### Post by Six_Digits on 2008-05-09
> **newbuntuxx said:**
> hey

you need to use the terminal.

so, if you want to edit system files, you have to use sudo in terminal like this:

sudo gedit "Path to file"

as for grub, to edit the time out run this in terminal:

sudo gedit /boot/grub/menu.lst

and I think you can edit the time in that file.

That will do :)

UnknownFear - I still advise you to take a look around that site I linked to you. Tons of useful information to get started.

---

### Post by Six_Digits on 2008-05-09
> **forrestcupp said:**
> you can also install Startup Manager, which is a GUI to set all of that stuff.
```
sudo apt-get install startupmanager
```

Totally forgot about that, but he should still know how to become root.

---

### Post by UnknownFear on 2008-05-09
> **Six_Digits said:**
> That will do :)

UnknownFear - I still advise you to take a look around that site I linked to you. Tons of useful information to get started.
I will deffinitly look at that site. Sorry, I'm just still fairly new to the Terminal. I'm getting somewhat better, though. Thanks for the help

---

### Post by kwacka on 2008-05-10
> **newbuntuxx said:**
> hey

you need to use the terminal.

so, if you want to edit system files, you have to use sudo in terminal like this:

sudo gedit "Path to file"



Most of the time 'sudo' is fine for graphical applications, **but** not always.

Therefore it is preferable to develop the habit of using (for example):```
gksudo gedit /boot/grub/menu.lst
```

The example I read (sadly I can't remember where, but thanks to whoever it was) was 'sudo firefox' opens firefox with root's configuration files, whilst 'gksudo firefox' opens it with user's config files.

---

### Post by forrestcupp on 2008-05-10
> **kwacka said:**
> 
The example I read (sadly I can't remember where, but thanks to whoever it was) was 'sudo firefox' opens firefox with root's configuration files, whilst 'gksudo firefox' opens it with user's config files.

You're right about the fact that you should always use **gksudo** or **gksu** for graphical apps.  But using gksudo with firefox still opens it with root configuration.  And why would you need firefox to be running as root anyway?

---

