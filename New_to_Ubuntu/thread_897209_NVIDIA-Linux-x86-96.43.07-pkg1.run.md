---
title: "NVIDIA-Linux-x86-96.43.07-pkg1.run"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by mattcadu on 2008-08-21
How do i install this?

---

### Post by tuxxy on 2008-08-21
Open a terminal and navigate to the files directory

```
cd Desktop
```

Then type

```
chmod +x filename.run
```

Finally run the installer

```
./filename.run
```

---

### Post by mattcadu on 2008-08-21
This makes no sense to me.... so i open the terminal and type...... cd desktop then press enter?

---

### Post by tuxxy on 2008-08-21
Yes press enter after each command, change the filename to your NVIDIA-Linux-x86-96.43.07-pkg1.run

---

### Post by mattcadu on 2008-08-21
i type ....    cd desktop

it tells me 

cadieux@Riptidz:~$ cd desktop
bash: cd: desktop: No such file or directory

---

### Post by tuxxy on 2008-08-21
linux is case sensitive, you need to type it as Desktop not desktop, just copy and paste it in

---

### Post by jerome1232 on 2008-08-21
Okay, a few things

A) Linux is case sensitve, desktop and Desktop are treated differently

B) To install that driver your going to have to kill your x server (the gui)

C) Is there a particular reason your installing nvidia drivers this way?

you have easier options

1)System>>Administration>>Hardware Drivers - see if you can enable the driver there

2) maybe you need a newer driver, use envy-ng, it works great

```
sudo apt-get update
sudo apt-get install envyng-gtk
sudo envyng
```

Then follow the prompts

---

### Post by mattcadu on 2008-08-21
cadieux@Riptidz:~/Desktop$ chmod +x NVIDIA-Linux-x86-96.43.07-pkg1.run
cadieux@Riptidz:~/Desktop$ 


nothing happened did i do it wrong?

---

### Post by tuxxy on 2008-08-21
That fine it isnt meant to give you any ouput, now enter the last command to run the installer but I agree with jerome, you should try these methods to install the drivers first

> 1)System>>Administration>>Hardware Drivers - see if you can enable the driver there

2) maybe you need a newer driver, use envy-ng, it works great

To install envy just type in terminal

```
sudo apt-get install envy-gtk
```

---

### Post by mattcadu on 2008-08-21
cadieux@Riptidz:~$ sudo envy-ng
sudo: envy-ng: command not found
cadieux@Riptidz:~$ sudo apt-get install envy-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy-gtk
cadieux@Riptidz:~$

---

### Post by jerome1232 on 2008-08-21
make sure and do
```
sudo apt-get update
sudo apt-get install envyng-gtk
```

I'm not seeing just an envy package I was going to ask what the difference is but I think it's envyng

```

jeremy@desktop:~/.local/share/Trash/files$ apt-cache search envy
alsa-tools-gui - GUI based ALSA utilities for specific hardware
envyng-gtk - install the ATI or the NVIDIA driver
envyng-qt - install the ATI or the NVIDIA driver
envyng-core - install the ATI or the NVIDIA driver
fglrx-amdcccle-envy - Dummy package for easy transition
fglrx-control-envy - Control panel for the ATI graphics accelerators
fglrx-kernel-source-envy - ATI binary kernel module source
nvidia-glx-dev-envy - NVIDIA binary XFree86 4.x/X.Org driver development files
nvidia-glx-envy - NVIDIA binary XFree86 4.x/X.Org driver
nvidia-glx-legacy-dev-envy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver development files
nvidia-glx-legacy-envy - NVIDIA binary XFree86 4.x/X.Org 'legacy' driver
nvidia-glx-new-dev-envy - NVIDIA binary XFree86 4.x/X.Org 'new' driver development files
nvidia-glx-new-envy - NVIDIA binary XFree86 4.x/X.Org 'new' driver
nvidia-kernel-source-envy - NVIDIA binary kernel module source
nvidia-legacy-kernel-source-envy - NVIDIA binary 'legacy' kernel module source
nvidia-new-kernel-source-envy - NVIDIA binary 'new' kernel module source
xorg-driver-fglrx-dev-envy - Video driver for ATI graphics accelerators (devel files)
xorg-driver-fglrx-envy - Video driver for ATI graphics accelerators

```

---

### Post by tuxxy on 2008-08-21
Thats weird, try this

```
sudo apt get install envyng-gtk
```

Or just open system > admin > synaptic and search for envy

---

