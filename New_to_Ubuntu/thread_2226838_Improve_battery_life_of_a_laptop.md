---
title: "Improve battery life of a laptop"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by don62 on 2014-05-29
I am running ubuntu 12.04 LTS on a Compaq Presario CQ61.
A very reputable computer magazine has given a tip to improve battery life.
The command lines are as follows:-

                        sudo add-apt-repository ppa:linrunner/tlp 
                     sudo apt-get update

These lines seemed to work OK, but the final command
sudo tlp start 

produced the line
sudo: tlp: command not found 

Can anybody give me some advice please.

---

### Post by plucky on 2014-05-29
> **don62 said:**
> I am running ubuntu 12.04 LTS on a Compaq Presario CQ61.
A very reputable computer magazine has given a tip to improve battery life.
The command lines are as follows:-

                        sudo add-apt-repository ppa:linrunner/tlp 
                     sudo apt-get update

These lines seemed to work OK, but the final command
sudo tlp start 

produced the line
sudo: tlp: command not found 

Can anybody give me some advice please.


Try the [Developers Website](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html) for TLP. A lot of useful information.


Good Luck

---

### Post by Toz on 2014-05-29
> **don62 said:**
> I am running ubuntu 12.04 LTS on a Compaq Presario CQ61.
A very reputable computer magazine has given a tip to improve battery life.
The command lines are as follows:-

                        sudo add-apt-repository ppa:linrunner/tlp 
                     sudo apt-get update

These lines seemed to work OK, but the final command
sudo tlp start 

produced the line
sudo: tlp: command not found 

Can anybody give me some advice please.

After "sudo apt-get update", you need to install the tlp package:
```
sudo apt-get install tlp
```

If it doesn't automatically start with the install, you can manually start it up via:
```
sudo service tlp start
```
...or:
```
sudo /etc/init.d/tlp start
```

---

### Post by don62 on 2014-05-29
Thanks a lot Plucky & Toz for your input.
Spot on Toz, after adding the line you suggest, it worked.
I just hope that tlp improves my battery life.
I have emailed the editor of the magazine to advise him of the omission.
Once again, many thanks.
Don.

---

### Post by su:bhatta on 2014-05-29
TLP does good work.
If you are using AMD processor you can try [Dynamic Power Management.]("http://webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html")

---

### Post by don62 on 2014-05-30
Thanks fot that tip bhatta.

---

