---
title: "stuck with CLI editing instructions (sudoers file)"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by deembee on 2008-09-23
Hi I'm trying as i might to learn about ubuntu and linux but most of the tutes i find are either so basic, such as how to install software with synaptic or assume a level of knowledge that i don't have. i need something in the middle. The more i use ubuntu the more frustrated i become. Don't get me wrong its a great OS and easy to use for a newbie if all you want to do is use stock applications that come in synaptic but if you want to change functions that are easy to do in XP or add software not in synaptic or .deb its a nightmare for me in ubuntu. 

ok enough of the rant, my problem is i want to add a line to my sudoers file to allow a plugin for my squeezebox (music streamer)to turn off my computer. Now i've read about visudo and can open the sudoers file in terminal but how do i change it? I've trawled for info and found all sorts of list for comands etc but as i said i'm in the middle; they assume i already know how to make the edit and add the command. I did find a post that said i need to use i to add to the file and :x to save it. i allowed me to insert it but i was unable to save it.
can someone please help with this and maybe point me somewhere where i cam learn this skills on the net

most appreciated

---

### Post by Tatty on 2008-09-23
You sound like you are struggling with using vi.  vi is an amazing text editor which can massively speed up your production if you know how to use it.  However if you dont know how to use it, it can be quite scary.

Like you, I do not really understand vi at all, and prefer to use nano for CLI text editing, as it is closer in functionality to a standard text editor.  According to this:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

It is possible to change the default editor for visudo.  Follow those instructions and change it to nano (make sure you back up any files you change first).

Then when in nano use ctrl+x to exit and save the file.

Alternatively you could always try to read a tutorial on how to use vi :)

---

### Post by nowshining on 2008-09-23
> **deembee said:**
> Hi I'm trying as i might to learn about ubuntu and linux but most of the tutes i find are either so basic, such as how to install software with synaptic or assume a level of knowledge that i don't have. i need something in the middle. The more i use ubuntu the more frustrated i become. Don't get me wrong its a great OS and easy to use for a newbie if all you want to do is use stock applications that come in synaptic but if you want to change functions that are easy to do in XP or add software not in synaptic or .deb its a nightmare for me in ubuntu. 

ok enough of the rant, my problem is i want to add a line to my sudoers file to allow a plugin for my squeezebox (music streamer)to turn off my computer. Now i've read about visudo and can open the sudoers file in terminal but how do i change it? I've trawled for info and found all sorts of list for comands etc but as i said i'm in the middle; they assume i already know how to make the edit and add the command. I did find a post that said i need to use i to add to the file and :x to save it. i allowed me to insert it but i was unable to save it.
can someone please help with this and maybe point me somewhere where i cam learn this skills on the net

most appreciated


Did you maybe think that the middle means you think in ur brain :) if you just thought a lil more and analyzed the situation ur problems would get solved quicker... again the middle is where one uses their brain to figure things out..

---

