---
title: "Launcher to Bottom?"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by Citta on 2016-05-26
Hi, 
Just installed 16.04 in VM workstation and tried to move the launcher to the bottom, following that instruction, from [http://www.linuxandubuntu.com/home/10-things-to-do-after-installing-ubuntu-16-04-xenial-xerus](http://www.linuxandubuntu.com/home/10-things-to-do-after-installing-ubuntu-16-04-xenial-xerus). dconf-editor is installed, still "launcher position left", "Bottom" is not there. 
What might be the mistake? Thanks for your help!


 [LEFT] [h=3]3. Activate New Features Presented In Ubuntu 16.04[/h] [/LEFT]
 
  [LEFT] [Ubuntu 16.04]("http://www.linuxandubuntu.com/home/ubuntu-16-04-lts-is-now-available-to-download") has brought some new features so let's give them a try. Let's activate the new features. [/LEFT]
     [LEFT] [h=4](i). Move Unity Launcher To Bottom[/h] [/LEFT]
 
  [LEFT] You now have the ability to move unity launcher from left to bottom.  Although the option has not been implemented in universal settings  panel. You need to install a third party application called gconf-editor  to **move unity launcher to bottom**.  [/LEFT]
   [LEFT]  sudo apt-get install dconf-editor 
 [/LEFT]
 
  [LEFT] Open dconf-editor and go to com >> canonical >> unity  >> unity and change launcher position to bottom. And Voila! Your  unity launcher has moved to bottom.
[/LEFT]
   [CENTER] [[IMG]http://www.linuxandubuntu.com/uploads/2/1/1/5/21152474/6643326.png?588[/IMG]]("http://www.linuxandubuntu.com/uploads/2/1/1/5/21152474/6643326_orig.png?588")
[/CENTER]

---

### Post by howefield on 2016-05-26
Does it work with the terminal command..

```
gsettings set com.canonical.Unity.Launcher launcher-position Bottom
```

and to revert to the left..

```
gsettings set com.canonical.Unity.Launcher launcher-position Left
```

---

### Post by Citta on 2016-05-26
Thanks, meanwhile I continued searching the internet and found exactly the same code you posted-it was so simple and I will remove the stuff I just installed, must find out how...

---

### Post by howefield on 2016-05-26
> **Citta said:**
> ... I will remove the stuff I just installed, must find out how...

```
sudo apt remove dconf-editor
```

will do it.

---

