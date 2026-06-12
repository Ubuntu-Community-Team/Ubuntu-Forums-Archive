---
title: "HOW TO: Change Computer Name"
date: 2009-10-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Jason Cook on 2009-10-12
I have received  help [here]("http://ubuntuforums.org/showthread.php?t=1280054") in doing this so I am going to try to sumarize this and show you how to trouble shoot. This is my first How To so any suggestions would be helpful.
    
Open nautilus and copy hosts and hostname to your desktop in case you make a mistake.
    Open a terminal and type
    ```
gksudo gedit /etc/hostname
```    Remove all of the text and enter the name you would like.
    Next type this into the terminal.
    ```
gksudo gedit /etc/hosts
```    It should have something like this:
```
127.0.0.1    NAME    localhost.localdomain    localhost
``` If there is another name in there make sure that is has a different IP adress eg. 127.0.0.2 other wise you will recieve an error when you use sudo. The name you choose can not hjave any spaces in it.
 Change name to what you enter in the first file.
    ```
127.0.0.1    NEWNAME    localhost.localdomain    localhost
```  Type
  ```
sudo
```  into the terminal and you should see something like this:
  ```

  usage: sudo -h | -K | -k | -L | -l | -V | -v
  usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
              {-i | -s | <command>}
  usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
```If gedit isn't working switch "gedit" with "vim".

Using Vim
Use the arrow keys to move you cursor the the beginning of the document. Press x to delete the charactors. Press i and type the text you want in. Press ":q!" to quit without saving and ":wq!" to save and quit.

Again any suggestions would be helpful.

---

### Post by Hated On Mostly on 2009-10-12
Good post. There is a tutorial forum where you should post this also.

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by Jason Cook on 2009-10-12
> **Hated On Mostly said:**
> Good post. There is a tutorial forum where you should post this also.

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)
Posted and waiting for moderation.

---

### Post by dlteach2 on 2009-10-12
Would like to change my computer name. am newbie on linux and wonder if I should just reinstall ubuntu 9.4. Would that be easier and more secure. I've already had to retrieve  my passwords and am concerned my security at this early point. Thanks for any advice.

---

### Post by Sef on 2009-10-12
Moved to T&T. 

Read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

It says in part:

> Graphical sudo
You should never use normal sudo to start graphical applications as root.

---

### Post by Jason Cook on 2009-10-13
> **Sef said:**
> Moved to T&T.
Someone told me about that forum in a previous post in this thread. I Already posted it and it is waiting for moderation. Hopefully someone catches it and it doesn't get posted again;)
> You should never use normal sudo to start graphical applications as root.
I did not know that. thanks for pointing this out.

---

### Post by Francewhoa on 2010-03-12
There is an **easier, safer and faster** way to do this at [http://ubuntuforums.org/showthread.php?p=8955992#post8955992](http://ubuntuforums.org/showthread.php?p=8955992#post8955992)

---

### Post by Samthorn on 2010-03-12
Perfect. Thanks for posting this.

~ Sam

---

