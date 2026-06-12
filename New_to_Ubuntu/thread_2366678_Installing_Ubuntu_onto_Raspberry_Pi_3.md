---
title: "Installing Ubuntu onto Raspberry Pi 3"
date: 2017-07-20
forum: New to Ubuntu
---

### Post by austiner on 2017-07-20
Hello,

I am trying to install Ubuntu onto a a Raspberry Pi 3 and am stuck at the screen as shown in the attachment. I entered my info into Putty and now it is asking for a password. I am not sure what password it is asking for. On a side note, when the RPi3 is booting up, it says no ethernet connected. The ethernet has been checked and is working properly. I am currently on restricted wifi, in case that may have something to do with it. 

Any help is greatly appreciated.

---

### Post by austiner on 2017-07-20
Updated post.

---

### Post by vocx on 2017-07-20
> **austiner said:**
> Hello,

I am trying to install Ubuntu onto a a Raspberry Pi 3 and am stuck at the screen as shown in the attachment. I am not sure what to do with this information and have tried entering the info into the command prompt of my laptop and desktop and am getting nothing. On a side note, when the RPi3 is booting up, it says no ethernet connected. The ethernet has been checked and is working properly. I am currently on restricted wifi, in case that may have something to do with it but I also tried on an open network and got stuck on the same screen. 

Any help is greatly appreciated.
I have a Raspberry Pi 3 with Raspbian, so I don't have experience with installing Ubuntu Core.

However, that screen says, "to login...". Did you try that?
```

ssh austiner@172.20.176.32

```

This is a command used to remotely connect to another machine. It uses secure shell (ssh) followed by the username and IP address of the machine, "ssh username@ipaddress".

If you have the Pi connected in a local area network, with another computer you may run that command and it will let you log in. Did you try that already?

If you are using a laptop which is also in the local network, the process should look like this
```

**user@Laptop:~$** ssh austiner@172.20.176.32
The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Thu Jul 20 11:29:21 2017 from 172.20.1.10
**austiner@raspberry:~ $** 

```
If you see that the prompt changed, then you successfully logged in, and means Ubuntu is installed. But that does not mean that you will get a graphical user interface. Maybe afterwards you need to install the user interface with "sudo apt install xubuntu-desktop" or similar.

To be honest, installation questions on the Raspberry Pi are better handled on the Raspberry Pi forums, as they are more familiar with installing all sorts of Linux distributions on the particular Pi hardware. I strongly suggest you check guides and info there.

Also, did you see the information here? [https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3](https://developer.ubuntu.com/core/get-started/raspberry-pi-2-3)
It seems to me that an Ubuntu desktop is not installed by default, and you need to use the "snap" command to install "snap" packages to get the graphical user interface and applications. It is different from using a normal Ubuntu desktop, so I suggest you read a bit about it.

---

### Post by Bucky Ball on 2017-07-20
Open a terminal and

```
ssh austiner@172.20.176.32
```

User: pi
Password: raspberry

They are the default credentials for RPi-s I have owned. Give that a try. You can also use those credentials when logging in with Putty (if they work, of course).

---

