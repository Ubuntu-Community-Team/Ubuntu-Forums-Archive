---
title: "ssh with X11 forwarding"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by daustinhjr on 2013-07-15
I've got Ubuntu Server 13.04 installed on a virtual machine.  I wish to be able to login remotely via ssh and have a remote gui without installing on the server, but I'm not quite sure the best way to go about it.  So let me tell you what I've done so far.

1.  Installed Ubuntu and setup user
2.  [LEFT][COLOR=#333333][FONT=UbuntuMono]sudo apt-get install xorg
3. [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]sudo apt-get install openbox
4. sudo reboot
5. logged in 
6. startx

On the local machine when I enter startx the screen goes black for a second then grey.  On the remote end when I ssh to the machine and try startx the following is the last line that appears and I see nothing like a desktop: [/FONT][/COLOR][/LEFT]Loading extension GLX.  Am I missing something or do I have to actually sudo apt-get install ubuntu-desktop to get this working the way I want.  I started trying to get this working following the guide [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI).

---

### Post by Cheesemill on 2013-07-15
> **daustinhjr said:**
> On the local machine when I enter startx the screen goes black for a second then grey.

That ***is*** the Openbox desktop. Right-click and you should get a menu.

> On the remote end when I ssh to the machine and try startx the following is the last line that appears and I see nothing like a desktop
Are you using the -X switch with SSH to enable X forwarding, for example...
```
ssh -X user@192.168.1.1
```

---

### Post by ajgreeny on 2013-07-15
Isn't it an upper case -X needed to enable X forwarding?

A lower case -x disables X forwarding, I believe.

---

### Post by Cheesemill on 2013-07-15
> **ajgreeny said:**
> Isn't it an upper case -X needed to enable X forwarding?

A lower case -x disables X forwarding, I believe.

You're right of course. I've edited my post.

---

### Post by daustinhjr on 2013-07-15
I am using ssh -X username@192.168.x.x

I forgot to mention that I edited the ssh files at [FONT=monospace]/etc/ssh/ssh_config and [/FONT][FONT=monospace]/etc/ssh/sshd_config to include 
[/FONT]ForwardAgent yes
ForwardX11 yes
ForwardX11Trusted yes

I've just never attempted this before and I really wasn't sure what all was required to make this work.  Is it normal for the screen to go black/grey if I try startx at the local machine (the ubuntu server)?  It is a vmware 9 virtual machine with default settings on the vm.  VMware tools is not currently installed; could this be the issue?  I'm connecting via ssh on osx 10.8.3 using XQuartz all I see on that end is a command prompt after I connect with a black background now.  I selected to launch xquartz in full screen so the background fills black. Is installing the tools necessary/favorable for a web server on a vm?  I really don't want to install anything that isn't absolutely necessary unless it dramatically increases performance/stability/security.  Thanks for the help.

---

### Post by daustinhjr on 2013-07-15
Well I just installed VMware tools after taking a snapshot, but still no difference in behavior.

---

