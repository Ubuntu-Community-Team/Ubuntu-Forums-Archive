---
title: "gns3 on ubuntu"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by kiedis on 2011-11-19
I try to configure GNS3 on ubuntu. i installed all necessary packages, have IOS binary file but when i try to play the router i get error** ''209 unable to start instance''**. i did some research and learned that [B]''dynagen expects the correct IOS file specified  within the generel router section of the net-file. Therefore you have to  edit the "image ="-line''

[/B]Code example:[B] image = /opt/7200-images/c3640-jk9o3s-mz.124-5a.bin

[/B]My question is - where should i go in order to make these changes? i heard many times that linux is cool because you can modify, patch some application code, but how exactly should i do it? open python and write some code there? or do some other thing? where can i find GNS3 (or any other installed application's) source code?

---

### Post by gordintoronto on 2011-11-19
The GNS3 web site does not offer a Linux version. Where did you get the program from?

---

