---
title: "Howto Ubuntu Headless Virtual Box ! ^_^"
date: 2010-06-04
forum: Philippine Team
---

### Post by jmazaredo on 2010-06-04
VirtualBox Headless Configuration on Ubuntu 

Step 1. Install your Linux 
a. use a lightweight desktop manager if you have only 1 pc (fluxbox)

Step 2. Download VirtualBox package at VirtualBox.org

Step 3. Install VirtualBox ( install your virtual guest now! )

Step 4. Install rdesktop  (I have compiled the source since I think its not available on ubuntu repository. make sure you have compiler. Extract the package and
$   ./configure
$    make

(It will show errors if you don't have compilers installed like gcc etc. just download it using apt-get on ubuntu)


Step 5. Run VirtaulBox at console

VBoxHeadless --startvm XP --vrdp on --vrdpaddress 192.168.1.102 --width 512

Step 6. Run rdesktop 192.168.1.102

Full working Headless VirtualBox

* SO HOW CA YOU LEAVE THE SERVER (GUEST OS RUNNING IN BACKGROUND? USE SCREEN!

use the "screen" command

* I will be trying this on my production server hope it dont crash! :guitar:

---

### Post by umeshkamat on 2010-07-30
> **jmazaredo said:**
> VirtualBox Headless Configuration on Ubuntu 

Step 1. Install your Linux 
a. use a lightweight desktop manager if you have only 1 pc (fluxbox)

Step 2. Download VirtualBox package at VirtualBox.org

Step 3. Install VirtualBox ( install your virtual guest now! )

Step 4. Install rdesktop  (I have compiled the source since I think its not available on ubuntu repository. make sure you have compiler. Extract the package and
$   ./configure
$    make

(It will show errors if you don't have compilers installed like gcc etc. just download it using apt-get on ubuntu)


Step 5. Run VirtaulBox at console

VBoxHeadless --startvm XP --vrdp on --vrdpaddress 192.168.1.102 --width 512

Step 6. Run rdesktop 192.168.1.102

Full working Headless VirtualBox 

* SO HOW CA YOU LEAVE THE SERVER (GUEST OS RUNNING IN BACKGROUND? USE SCREEN!

use the "screen" command

* I will be trying this on my production server hope it dont crash! :guitar:

Can you tell me, if I am running the server in headless fashion and without anybody logging in, still I will be able to start the machine? Can you suggest where to write that script?

Also I want to know how to power off the machine, once started as headless server?

Umesh

---

### Post by jmazaredo on 2010-07-30
3.3 Starting A VM With VBoxHeadless

Regardless of if you create a new VM or import and old one, you can start it with the command:

VBoxHeadless -startvm "Ubuntu 8.04 Server"

(Replace Ubuntu 8.04 Server with the name of your VM.)

VBoxHeadless will start the VM and a VRDP (VirtualBox Remote Desktop Protocol) server which allows you to see the VM's output remotely on another machine.

To learn more about VBoxHeadless, take a look at

VBoxHeadless --help

This is from [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)

---

### Post by umeshkamat on 2010-07-30
I could run my virtual machine from command line. Thanks. 
But I could not stop it from command line nor from RDP. I press ^C in command line. Then state of the VM was aborted not Poweroff.

Is is some problem?

Umesh

---

