---
title: "Raspberry Pi 3 install ssh putty access denied"
date: 2017-01-29
forum: New to Ubuntu
---

### Post by jaxxwalker on 2017-01-29
Hi there,
 
i hope someone can help,  I'm new to Linux and decided to install ubuntu on my raspberry pi 3 as a good way to start learning the system.  I'm at the point of first boot and going through the configuration setting.  I've set up a ssh key using Putty on a win10 laptop and imported this into my Ubuntu One account.  

The next part of the configuration says.........
congratulations this is now register to [EMAIL="xxxxxxx@xxxxxxx.com"]xxxxxxx@xxxxxxx.com[/EMAIL]. The next step is to log into the device via SHH. 

So I go back to putty on the win10 laptop and and try log on.  I enter my username but when prompt for my password is says access denied even when the IP address is correct,  the password is correct and both GSSAPI boxes are unchecked.  I've spent most of the  day reaseaching on the net how to solve this and have tried and tried again.   This thread is my last hope of getting it up and running and would be greatfull for some guildance.

---

### Post by cariboo on 2017-01-30
Have you got openssh-server running on your raspberry pi?

---

### Post by jaxxwalker on 2017-01-30
Hi Carliboo,  the fact that I have no idea what that is,  is a good chance it's not running on the rasp pi.  How do you get it running?

---

### Post by The Cog on 2017-01-30
I assume you have a TV connected to the pi, and can use a keyboard locally? 
If so, can you open a command prompt and enter the command 
```
netstat -lt
```
which will list all the TCP ports listening for incoming connections. You should see ssh mentioned. If not, this command should install and start the openssh server:
```
sudo apt-get intstall openssh-server
```

---

### Post by kevdog on 2017-01-30
Just an FYI -- you in no way need an UbuntuOne account to use ssh on your RasberryPi.  The two are mutually exclusive.

---

### Post by mastablasta on 2017-01-30
you need to: create keys on the Pi.

move private key to Windows 10
import the key into Putty (putty uses a different key format as i remember)

then you can try to connect.

you might want to change the shell after loging in.

ssh with keys:
[SIZE=2]https://help.ubuntu.com/community/SSH/OpenSSH/Keys
[/SIZE]
on pi with raspbian
[SIZE=2]https://www.raspberrypi.org/documentation/remote-access/ssh/windows.md
[/SIZE]

---

