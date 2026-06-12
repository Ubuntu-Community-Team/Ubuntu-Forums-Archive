---
title: "Ubuntu 12.04 Minimal LTS"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by heiko2 on 2014-01-29
Hello, 

ive just installed Ubuntu Minimal 12.04 LTS on my server and when im trying to install a program via sudo i get following error message: 

> E:Unable to locate Package

I tried it to install with following commands

apt-get install xrdp
sudo apt-get install xrdp

i also tried to to update and upgrade via apt-get update && upgrade. Both went fine but error for installing still shows up

Help pls :(

---

### Post by claracc on 2014-01-29
What repositories to get software have you enabled?,xrdp is in universe repositories.

 You can check your sources software in order to enable the " free open software mantained by community (universe)" in the ubuntu software tab.

See mine in the attached image:

---

### Post by mastablasta on 2014-01-29
server doesn't have ubuntu software tabs. so sources.list file i belive holds repositories. more here: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

