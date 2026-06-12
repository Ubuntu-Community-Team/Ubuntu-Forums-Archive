---
title: "Help with booting Ubuntu"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by Anabelle Estrada on 2011-11-28
Hello, well I'm new. & this said beginner talk, well i am a beginner& i need help. my computer is having problems. so whenever i turn on my computer it starts up normally until something purple pops up (well the background pops up) this is what happens: 
:confused:
ok so here are the following things that pop up

GNU GRUB version 1.99-12ubuntu5

Ubuntu, with Linuz 3.0.0-13-generic
Ubuntu, with Linux 3.0.0-13-generic (recovery mode)
Previous Linux versions 
Memory test (memtest86+)
Memory test (memtest 86+ , serial console 115200)

&at the very bottom 
Use the up&down arrow keys to select which entry is highlighted 
Please enter to boot the selected OS, 'e' to edit commands before booting or c for a command line


if you need a picture please let me know.

---

### Post by shortpaw on 2011-11-28
Hi, Annabelle,
What you're looking at is your "bootloader," and that's normal. Assuming you want to "log into" your Ubuntu OS, simply use the arrows to highlight
"Ubuntu, with Linux 3.0.0-13-generic" (if it isn't already highlighted), and press "enter"; your computer should boot you into your Ubuntu OS. (The other entries are for troubleshooting tools, and eventually you'll need to know about those. At this point, they wouldn't make any sense to you.)
I hope this helps.
All best,
~shortpaw

---

### Post by nothingspecial on 2011-11-29
Hi Anabelle, welcome to the forums :)

When you have a question, rather than putting it in a thread that has nothing to do with your problem, make a thread of your own with a descriptive title. That way someone who kinows the answer has a good chance of seeing it.

---

### Post by lolpenguin on 2011-11-29
> **Anabelle Estrada said:**
> Hello, well I'm new. & this said beginner talk, well i am a beginner& i need help. my computer is having problems. so whenever i turn on my computer it starts up normally until something purple pops up (well the background pops up) this is what happens: 
:confused:
ok so here are the following things that pop up

GNU GRUB version 1.99-12ubuntu5

Ubuntu, with Linuz 3.0.0-13-generic
Ubuntu, with Linux 3.0.0-13-generic (recovery mode)
Previous Linux versions 
Memory test (memtest86+)
Memory test (memtest 86+ , serial console 115200)

&at the very bottom 
Use the up&down arrow keys to select which entry is highlighted 
Please enter to boot the selected OS, 'e' to edit commands before booting or c for a command line


if you need a picture please let me know.

+1 shortpaw. This is absolutely normal, though on my computer this step is skipped because there is no alternate OS to boot into. Here's a rundown of the individual options:
Ubuntu, with Linux 3.0.0-13-generic
This is your main OS and kernel. This is usually the latest version of Linux on your computer.
Ubuntu, with Linux 3.0.0-13-generic (recovery mode)
This is your main OS and kernel, but it boots into, well, recovery mode. This is similar to safe mode in MS Windows.
Previous Linux Versions.
If you have older versions of Linux installed (in your case I think it is 3.0.0-12-generic, use this to bring up another menu to boot into them, if your current one does not work.
Memory test (memtest86+)
This is a utility for testing your RAM for errors. It does not provide a functional operation environment.
Memory test (memtest 86+ , serial console 115200)
I don't know what the serial console bit is about, but it should do the same job as above.
You should not need to enter the other options just yet, you may need them if you computer breaks down.

---

### Post by mastablasta on 2011-11-29
But she shouldn't see this on startup (it's not set like that by default i believe) unless she has another OS installed.

---

### Post by Anabelle Estrada on 2011-11-29
thank you all for responding. I'm sorry i did not start a new thread, i have no idea how,i will find out how& next time i will. & i do click the first option but when i do, first there is just a blinking line then something pops up saying: 

BusyBox v1.18.4 (Ubuntu 1:1.18. 4-2ubuntu2) built in shell (ash) 
Enter 'help' for alist of built in commands 

(initframs) 


if you would like to know what the commands are please tell me.

---

