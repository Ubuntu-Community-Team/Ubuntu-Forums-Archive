---
title: "How to get through internet proxy"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by jerryheavyarms on 2008-06-10
Hello!

Our network has an internet proxy. So every time I connect to the internet, I am being asked of my username and password.

Now, every time I would Add a program, I would get an error message saying I need authentication first to the proxy.

I have done doing this on a terminal:

export http_proxy=http://username:password@<ip of proxy>:<port>

I also added it to rc.local.

Still I get the error message..

What to do now? 

Thanks in advance!

---

### Post by spiderbatdad on 2008-06-10
That might work better in .bashrc of your /home/user directory...

---

### Post by jerryheavyarms on 2008-06-10
Thanks Spider for the reply..Appreciated.

But being new to Linux, how will I do that?

Thanks!:)

---

### Post by auitman on 2008-06-25
> **jerryheavyarms said:**
> Thanks Spider for the reply..Appreciated.

But being new to Linux, how will I do that?

Thanks!:)

[LIST=1]
[*]Easily go to Ubuntu command line by choosing "Application > Accessories > Terminal" from Ubuntu main menu.
[*]In order to open the .bashrc file for editing, type in "sudo vim /home/*_user_*/.bashrc" (remember to replace *_user_* with your own username). You may be required to enter your administrator password.
[*]Press "I" to start editing; you can do whatever you normally do in any other editor (add, delete, new line, etc). In your case, you need to add "export http_proxy=http://usernameassword@<ip of proxy>:<port>" somewhere in the script.
[*]When you are finished editing, press "ESC".
[*]Type in ":wq"
[*]You are now back to command line, now type in "exit"
[*]Restart Ubuntu.
[/LIST]
All Done!

Good Luck.

---

### Post by jerryheavyarms on 2008-06-29
Hey Auitman!

Thank you buddy! It solved my problems!:)



Thanks to you too, Spider!

---

