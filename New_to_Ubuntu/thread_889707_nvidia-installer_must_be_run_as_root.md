---
title: "nvidia-installer must be run as root"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by poscomp on 2008-08-14
I am trying to load new Nvidia video drivers. I go to the root directory, run the command and it starts then I get this error message.
       nvidia-installer must be run as root
I try to login as root with no success. What am I doing wrong?

Thanks in advance.

---

### Post by nothingspecial on 2008-08-14
sudo it.

---

### Post by halitech on 2008-08-14
the root account is disabled so you can't log in as root. just take the command and put sudo in front of it

example  sudo nvidia-installer.sh

it will then ask for your password, enter it and it should install and run

---

### Post by Riffer on 2008-08-14
Why don't you try Envy?

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by poscomp on 2008-08-14
Now I get this error:


 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

What now?

---

### Post by TheMaxzilla on 2008-08-14
You don't login as root from the login screen, silly goose.

Open up a terminal, (Applications > Accessories > Terminal) and type in
```
sudo [command]
```
Also, you can do this in your home directory, no need to navigate to Root directory.
sudo means Super User DO, and gives you the privileges of root. That way, you can run any command, and make system wide changes. When you type in "sudo [command]" in the terminal, you will be prompted for a password. Type in the password for your account (i.e., the one you login with) and you will run it as root.

If you are going to be running many commands with sudo privileges, you can alternatively type in 
```
sudo su -
```
and get a root terminal. That means, you will run every command you type in as root, or Super User. Be careful, and don't run commands blindly. If you are unsure of what a command does, google a cheat sheet for yourself on the internet. or, you can (befre you run it) type in:
```
man [command]
```
"man" means Maunal, and it will explain to you what the command does. "man man" for more information on the manual pages.

Hope this helps!

---

### Post by LowSky on 2008-08-14
Why not use EnvyNg to install your drivers

```
sudo apt-get install envyng
```
its under Applications>System>EnvyNG

---

### Post by vikramaditya on 2008-08-14
> **poscomp said:**
> nvidia-installer must be run as root
yes, this is so.

---

### Post by nothingspecial on 2008-08-14
> **TheMaxzilla said:**
> 

If you are going to be running many commands with sudo privileges, you can alternatively type in 
```
sudo su -
```
and get a root terminal. 

Not a good idea unless you know exactly what your doing.

---

### Post by halitech on 2008-08-14
ok, lets back up here a bit. What video card do you have that you are trying to install drivers for?

---

