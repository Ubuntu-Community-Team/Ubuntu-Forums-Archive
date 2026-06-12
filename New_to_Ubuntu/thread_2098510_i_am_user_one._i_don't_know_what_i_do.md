---
title: "i am user one. i don't know what i do"
date: 2012-12-26
forum: New to Ubuntu
---

### Post by geooilhunter on 2012-12-26
well i have some challenges. I installed ubuntu alongside windows xp but i couldn't access to latter one e.g. windows xp. What sould i do?

---

### Post by audiomick on 2012-12-26
Look at this
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

You could try the boot repair function yourself, but it might be better to generate the boot info and post it so that people can give you advice based on the actual state of your machine.

---

### Post by Ichido on 2012-12-27
Look here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Then follow this:
**2nd option : install Boot-Repair in Ubuntu**

- boot your computer on a Ubuntu live-CD or live-USB.

- choose "Try Ubuntu"

- connect internet

- open a new Terminal, then type:

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

- Press Enter.

- Then type:

sudo apt-get install -y boot-repair && boot-repair

- Press Enter 

This worked great for me!

---

