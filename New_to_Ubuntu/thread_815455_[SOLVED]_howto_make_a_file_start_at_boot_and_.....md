---
title: "[SOLVED] howto make a file start at boot and ...."
date: 2008-06-01
forum: New to Ubuntu
---

### Post by trigsenior on 2008-06-01
hello,

I have recently been making sh file which is great , howerever i want the to run at boot but am not sure which file i need to put the sh file in. 
I found a couple boot files but am scared of messing my system up. and also something unrelated is there a dictionary of linux comands as im finding it hard rembering them all heh .  And also a ebook describing how linux works behind the scenes , as i can only find old old ebooks .

many many thanxs as usual =)

---

### Post by bobnutfield on 2008-06-01
Hello, I am not on my Ubuntu box right now so I am answering from memory.  But, if you place your script in /etc/rc.d/rc.local it will be run at boot time.  I may be not be remembering the exact location, but rc.local is the directory you are looking for.

Hope this helps

Bob

---

### Post by sayakb on 2008-06-01
[Linux Commands]("http://ubuntuforums.org/linuxcommand.org/")
Refer to the Guides in my sig.

Dave

---

### Post by cariboo on 2008-06-01
Try this [http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz). This is what I started out with so many years ago. 

Jim

---

### Post by trigsenior on 2008-06-01
thanxs bob 

i found a couple files , 

/etc/rc0.d/
/etc/rc1.d/
/etc/rc2.d/
/etc/rc3.d/
/etc/rc4.d/
.....
.....
/etc/rc6.d/

i did not find rc.local but that dosn t matter does it ?

all the files are wifi , keyboard ect  all stuff which run on boot up does it matter which file i put my sh file in ?

---

### Post by sayakb on 2008-06-01
```
sudo gedit /etc/rc.local
```End up every command with an & so that the next command is executed.
[URL="http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/"]
[/URL]

---

### Post by bobnutfield on 2008-06-01
I have forgotten exactly where Ubuntu places this file, but I would say yes, you should try to place in the rc.local directory as this is where local scripts are run at boot time.  I am on a Slackware machine right now and the directory is /etc/rc.d/rc.local.  Look for /etc/rc.d  and you should find rc.local in that directory.

Hopefully, someone will post the exact location.

Bob

---

### Post by sayakb on 2008-06-01
This might also help: [http://ubuntu.wordpress.com/2005/09/...run-at-bootup/]("http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/")

---

### Post by bobnutfield on 2008-06-01
> **LinuxIsInnovation said:**
> ```
sudo gedit /etc/rc.local
```End up every command with an & so that the next command is executed.
[URL="http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/"]
[/URL]

Linuxisinnovation has given you the correct location to place your script. That link is also VERY helpful.

Bob

---

### Post by sam_delta on 2008-06-01
just add it under system>preferences>sessions, click on add and then type a name, and where it says "command", type the path to your script

also, about rc.local,,  /etc/rc.local is actually a file, which is executed each boot, that means, that any command typed inside that file, will be executed at boot time. so you may also open that file by typing ```
sudo gedit /etc/rc.local
``` and then, make it open your script at boot by typing ```
sh /home/user/your_script
``` so when rc.local is executed, it will automaticly call your script, so it will get exececuted too.

sam

---

### Post by trigsenior on 2008-06-01
thanxs for the help , i looked at the links and looks like just what i was looking for , i have just got to read them now =) 

also dave i found the file many thanxs il try my hand at some scripting later  :)

---

### Post by sayakb on 2008-06-01
No probs :) Glad I could help.

---

