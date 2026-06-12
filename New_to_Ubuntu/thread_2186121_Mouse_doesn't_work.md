---
title: "Mouse doesn't work"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by enocifer on 2013-11-05
Hi, i just installed Ubuntu, downloaded from the official site yesterday, alongside Windows XP Pro, and when I boot to Ubuntu, the mouse does not work at all. I can do some stuff with the keyboard, but can't move the mouse cursor at all. Mouse still works on Windows. My Windows claims it's not genuine and I want to get away from Microsoft completely. What do I do to get it to work?   Please help! Thank you.

---

### Post by oldrocker99 on 2013-11-05
I personally have used many mice with Ubuntu with no issues. The drivers for 98+% of computer hardware are already in the kernel.

What's your output from

lsusb | grep ouse     [grep just filters the output, 'ouse' is to find a Mouse or mouse]

Post your result.

---

### Post by enocifer on 2013-11-05
I'm sorry, i'm completely new to this. I don't know what that means. Do I enter that text somewhere?

---

### Post by elliotn on 2013-11-05
I had the same problem with the native Ubuntu kernel thus I ended up installing Liquorix kernel and it worked.....

Google liquorix kernel

---

### Post by mastablasta on 2013-11-06
> **enocifer said:**
> I'm sorry, i'm completely new to this. I don't know what that means. Do I enter that text somewhere?

alt+T will open terminal windows where you can type this command (if you had a mouse you could go to browser and copy it more easilly).

this command should identify the mouse. 

otherwise a very good cheapest logitech or genius mouse will work very well in linux and they are usually well made. so if you are willing to spend a little money for new mouse get one of those.

i also have a small generic made in china mouse i bought for 5 EUR. works nicely as well. in short it is unusual that mouse doesn't work.

---

### Post by varunendra on 2013-11-06
> **mastablasta said:**
> alt+T will open terminal windows where you can type this command

Erm.. you mean **Ctrl**+Alt+T, don't you? :P

I'd be interested in seeing the outputs of -
```
xinput
lsmod
```
You can redirect the outputs to a plain text file by adding a "> textfile.txt" after the commands. Like this -
```
xinput > myoutput.txt
lsmod >> myoutput.txt
```
(the double ">>" appends the output instead of overwriting the file)
This will create a "myoutput.txt" file in your home directory from which you can easily copy-paste later, or attach the files itself here in your next post.

Please use 'Code' tags while posting the outputs to preserve the formatting of the outputs. Follow the "Using Code Tags" link in my signature to see how to use that.

---

### Post by buzzingrobot on 2013-11-06
If you can borrow someone else's mouse, try using that to determine if the issue is specific to your current mouse or is a broader issue.

What version of Ubuntu are you using?  What brand and version is the mouse?  Your hardware?

---

### Post by urapain on 2013-11-06
to  see what mouse the system sees, in terminal enter on one line:  
dmesg 
followed by a vertical bar called  pipe
followed by tee
followed by another pipe
folowd by grep -i
followed by mouse
followed by \
followed by a single space
should llok like this  $ dmesg|tee|grep -i mouse\

---

### Post by Mark Phelps on 2013-11-06
> alongside Windows XP Pro

Back in the early XP days, it was not uncommon for Mouse to use ps/2 adapters, not USB.  

So, we need to know if this is a USB mouse (wireless will be USB, most likely).
'
If it is USB, you need to go into your BI=OS settings and confirm that "legacy USB" is enabled.

---

