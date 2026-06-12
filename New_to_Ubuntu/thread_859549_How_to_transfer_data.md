---
title: "How to transfer data"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Majorix on 2008-07-14
I warn you, I am very new to this, hence the Absolute Beginner section.

Anyways, I have a Hardy & Vista dual-boot. My sister; usually connecting to the internet on the same network (actually via wired for a little while nowadays) on her Vista and I want to exchange files.

However I don't know nothing regarding this. Best idea I could come up with is a USB HDD but that doesn't always work as we are not always in the same place.

So what I am asking is:
- How to transfer data between Hardy&Vista or Vista&Vista on the same network.
- How to do the same but not on the same lan.
- An answer to what on earth a Workgroup Windows keeps asking during the initial setup is and if it is related to this at all.

Thanks for helping.

---

### Post by silkstone on 2008-07-14
I'm sorry this is going to be no help at all, but I spent ages trying to work out how to get my Ubuntu and XP machines to talk to each other over the network, and ended up deciding that a USB stick was by far the easiest way. :)

---

### Post by The Cog on 2008-07-14
In my opinion, installing an SSH server on the Ubuntu machine (install package openssh-server) and installing Filezilla on the Windows machine is the easiest way. Provided you have strong passwords, you can expose the SSH server to the internet for when she is away.

---

### Post by Barrucadu on 2008-07-14
Install SAMBA, I can't remember off the top of my head how to set it up, but I remember that I was sharing files and a printer with all the Windows machines in the house within hours.

---

### Post by Xerp on 2008-07-14
+1 for The Cog's answer. Either Filezilla or WinSCP on the Windows computer. Secure, quick and easy.

---

### Post by bodhi.zazen on 2008-07-14
samba works out of the box.

On the windows, vista box create a shared folder

On Ubuntu go to Places -> Network -> navigate to the share -> enter user name and password (vista user name password).

---

### Post by cariboo on 2008-07-14
You don't need anything to transfer between Vista and Hardy. If you sisters computer is set up for file sharing you should see it in Places-->Network just double click on Windows Network-->MSHOME and you should have access to her shared files.

To view Ubuntu shares in Vista you will need to install Samba it is in the repositories and you can install it using Add/Remove Programs or Synaptic Package Manger. here is a link to a samba howto:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Jim

---

### Post by whitethorn on 2008-07-14
Hi, there are two good options depending on what you plan on doing.  With samba you can setup window share folders for specific users.  This is especially useful when ur inside a private network, but not so much when you're trying to connect from outside.  Installing a SSH server is actually a better idea.  You can then connect to it from outside and you can use WINSCP to connect to your ubuntu computer from windows.

---

### Post by LowSky on 2008-07-14
Samba works for me really well and it can work both ways if you use it correctly.

---

