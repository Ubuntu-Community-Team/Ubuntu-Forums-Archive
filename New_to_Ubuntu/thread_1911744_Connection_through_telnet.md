---
title: "Connection through telnet"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by summisone on 2012-01-19
Hi. I have ubuntu installed in a system. I have to coonect 3 PCs to this system. Is it possible to connect these 3 windows systems as termals of ubuntu system through telnet. If so please tell me the settings that i have to do. I am an absolute beginner :(

---

### Post by Lars Noodén on 2012-01-19
Telnet is insecure and was [replaced by SSH](http://en.wikibooks.org/wiki/OpenSSH/Overview) nowadays.  

You can connect to your Ubuntu machine from the legacy systems by putting the package [openssh-server](http://packages.ubuntu.com/oneiric/openssh-server) onto your Ubuntu machine.  You can then connect from the legacy machines using [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/).  To connect from another Ubuntu machine you don't need anything else, the SSH client is already installed. 

Part and parcel of OpenSSH is support for SFTP.  FileZilla is a popular SFTP client.

---

