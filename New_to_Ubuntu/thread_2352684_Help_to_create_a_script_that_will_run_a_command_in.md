---
title: "Help to create a script that will run a command in terminal at login"
date: 2017-02-14
forum: New to Ubuntu
---

### Post by fozziebear on 2017-02-14
I am using get_iplayer to download BBC radio and tv series. This has a web based PVR system which will automatically download new programs.

get_iplayer for Ubuntu requires the user to start the Pearl web server listening on the loopback address in order for the application to run the PVR in a browser window. This is achieved by running the command

```
get_iplayer_web_pvr
``` in terminal. 

In windows I could paste the command into a text file and change the extension to .bat and put it in the startup folder. With Ubuntu I have no idea where to start. I have read about Bash Scripts but these all appear to run applications rather than a terminal command. Is there a similar method of creating a terminal script that will run at login?
Again may thanks for your help and patience.
Fozzie

---

### Post by QIII on 2017-02-14
Hello!

Please use the default font, weight and color unless you want to draw special attention to a small part of your post.

Also, please post terminal commands and results between code tags.

To do that you may:

1.  Click the # sign in the toolbar above the text entry box, place your cursor between the code tags that will appear and type or paste your text.

2.  Type or paste your text, highlight it and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after it.  The square brackets are required.

---

### Post by fozziebear on 2017-02-14
> **QIII said:**
> Hello!

Please use the default font, weight and color unless you want to draw special attention to a small part of your post..

Apologies for not abiding by forum etiquette but I am having real problems with my posts. I have already reported one issue to the site Admin as I cannot remain logged in. 

Regarding the font it was not my intention to use bold font. I tried to remove it using the toolbar but whatever I did it remained bold. I even deleted the bold lines and re typed them but they became bold again.

I also take your point about code but was not aware that what I had typed was in fact "code" I just used it for information. I am new to Linux and clearly the forums here are much different to Windows forums where there is no necessity to put commands in any specific way.
I will try in future to comply
Fozzie

---

### Post by &amp;KyT$0P# on 2017-02-14
[This]("https://wiki.archlinux.org/index.php/Autostarting#Graphical") should point you in the right direction.

---

### Post by ajgreeny on 2017-02-14
Create a shell script called **pvr.sh** with content
```
#!/bin/bash
get_iplayer_web_pvr
```
put it in a folder that you will have to create called **bin** in your home and make it executable. That adds it to the system $PATH variable meaning it will execute simply by running command **pvr.sh**

Now add that command to the autostart programs list in Settings manager ->Session and Startup and it should run at every session start.

I do not know, however, how you make use of that in a web browser so will leave that to you as you appear already to know all about that.

---

