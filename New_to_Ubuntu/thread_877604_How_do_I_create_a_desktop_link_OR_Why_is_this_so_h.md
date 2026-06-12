---
title: "How do I create a desktop link? OR Why is this so hard to do?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by VitaminBB on 2008-08-01
Judging from the title im sure u think this is an even newbier then usual question but hear me out ...


I have created links with the launcher on my desktop BUT ...

**1.** the first link I created pointed to ***/usr/bin/iPodder*** it turns out that I was pointing at a text file for iPodder (?) but double clicking on this file brought up a window asking me if i wanted to run the file, selecting run made the program launch.

This wasent so bad but I was sick of having to select run each time, so I searched for a way to make it run automatically and just hit a wall, after reading several sites I realize I had infact made a mistake in what I was pointing the launcher at, trying to fix this mistake I came to the second problem ...


**2.** I then created a shortcut with launcher that points at ***/home/arghmonkey/icepodder/*** then I got an error saying I didnt have permission to run that file, so I went into permissions and change it to read and write and "allow executing file as program" but when I double click I still get the same old message **"Failed to execute child process "/home/arghmonkey/icepodder/" (Permission denied)"**


So right now I still dont know how to properly create something as seemingly simple as a desktop shortcut to a program ...



I came here because I hate microsoft but this is a steep learning curve ...

If you can help its appreciated ...

---

### Post by collinp on 2008-08-01
on that last error, navigate to your Desktop "cd Desktop" with terminal, then run "sudo ./(filename)". That should allow you to execute the file, but the problem is that only stays for as long as the program is open.

---

### Post by VitaminBB on 2008-08-02
Ok but is there no way for me to have a link that opens whenever I click it ?!?!

Am I losing my mind here?

What about all the other programs like firefox etc? I dont have to type anything every time I want to open those ...

This really is starting to more then suck, its like im back at computer grade school when I was really good at windows os ...

Anyone with other ideas?

---

### Post by kk0sse54 on 2008-08-02
type ```
sudo chmod 700 <filename>
``` in order to change the file permission obviously replacing filename by the path to the file. One question is this program installed and can be accessed by the run dialog or application menu?

---

### Post by phidia on 2008-08-02
How did you install these two packages? 
You shouldn't need to change permissions on your executables and it could even be a security risk. 
Open the terminal app Applications> Acessories> Terminal and type "icepodder" (without the quotes press enter and copy/paste the output.

---

### Post by bks on 2008-08-02
> **VitaminBB said:**
> So right now I still dont know how to properly create something as seemingly simple as a desktop shortcut to a program ...

When creating a launcher, in the Command text box, just include *gksudo* before the rest of the command. That will prompt you for your password and then load the program as root.

---

### Post by VitaminBB on 2008-08-02
> **C!oud said:**
> type ```
sudo chmod 700 <filename>
``` in order to change the file permission obviously replacing filename by the path to the file. One question is this program installed and can be accessed by the run dialog or application menu?

Just tried your suggestion, I notice the icon is now a blue diamond with the picture of gears inside (if that means anything to you) but I get the same permission window response as before.

This program "icepodder" was put together through another surfers suggestions since it doesnt install regularly, thats probably the problem right there.

Is there anyway I can get the text file to run automatically? maybe ill just go back to that, it worked at least.

---

### Post by BGFG on 2008-08-02
Does icepodder not appear in the applications menu ? If so then right click and>>Add this launcher to desktop.

---

### Post by VitaminBB on 2008-08-02
You know what, like most noob mistakes I realize what I did wrong here, the txt file is a shell script, thats why I was linking to it.

I let someone else set this up for me and thats the mistake.

Thanks for the tips everyone.

---

