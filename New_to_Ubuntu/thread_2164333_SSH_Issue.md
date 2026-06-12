---
title: "SSH Issue"
date: 2013-07-31
forum: New to Ubuntu
---

### Post by 3eLtehF on 2013-07-31
Hi All,

I have a windows environment and a VMWare workstation on it where i have installed ubuntu 12 server.

is it possible that i can run VMWare in background and ssh through Putty from Windows environment.

sshserver is installed on ubuntu.

Help would be appreciated.

-- Shani

---

### Post by Chris of Arabia on 2013-07-31
Unfortunately, I can't answer the question, but I'd be interested in seeing what sort of replies you get back. Out of curiosity though, how would you want to use a set-up like this?

---

### Post by 3eLtehF on 2013-07-31
I just did not want to replace my windows environment and i can not have both the OS on same PC as my drives are full of files.

so i thought of installing Ubuntu over the VMWare ... 

for SSHing from Windows would make it more easily accessible as right now on VMWare i cannot copy or paste any thing in CLI.

---

### Post by Cheesemill on 2013-07-31
Yes it's possible, I do it all of the time.

Make sure that the SSH server is installed on your Ubuntu VM...
```
sudo apt-get install openssh-server
```

Then just run PuTTY and use the IP address of your Ubuntu machine as the host to connect to.

---

### Post by DGINSD on 2013-07-31
> **3eLtehF said:**
> I just did not want to replace my windows environment and i can not have both the OS on same PC as my drives are full of files.

so i thought of installing Ubuntu over the VMWare ... 

for SSHing from Windows would make it more easily accessible as right now **on VMWare i cannot copy or paste any thing in CLI.**


Just thought I'd mention this I believe I read somewhere virtualbox supports this, cant remember where so youd need to double check

---

### Post by sharadchhetri on 2013-07-31
Which VMware edition you are using, I used ACE edition and now I only use Virtual Box. In Vmware ACE edition after running the machine when we click on close button it shows some options and one of the option is Run in background.

---

### Post by 3eLtehF on 2013-07-31
i am running VMWare workstation 9.
tried run in background.
installed ssh server.
host as IP address on putty.
putty shows a blank screen.
no good :(

---

