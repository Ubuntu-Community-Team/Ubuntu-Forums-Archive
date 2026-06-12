---
title: "In the beginning..."
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Dbugger on 2008-06-21
I know this must be a complete newbie question, but I've spent all day gathering courage to let it go.... Here I come:

What are those letters that make no sense that I can be seen between the moment I press "Ubuntu" in the GRUB and the moment the X Windows open?

I'd like to take a closer look at them. Is there a way to store all that info in a file?

You can flame me now :D Just kidding.

---

### Post by kk0sse54 on 2008-06-21
What would you like to take a closer look at? It's just loading your Kernel and I don't think Ubuntu goes into Verbose Mode to show the rest of it booting up.

---

### Post by Dbugger on 2008-06-21
> **C!oud said:**
> What would you like to take a closer look at? It's just loading your Kernel and I don't think Ubuntu goes into Verbose Mode to show the rest of it booting up.

It's kinda just for the hell of it. I'd really like to UNDERSTAND linux, and I'd like to comprehend what all that stuff is. Besides, when I log off I see some very ugly messages telling me some stuff is wrong which I'd like to take a closer.

Can someone help me with it, please?

---

### Post by rbc on 2008-06-21
Open a terminal and type: dmesg
I think that's what you're after. If you want to make a file to look at it, again in terminal, type: dmesg > dmesgfile.txt (or call it whatever you want). That command will create that document in your home directory

---

### Post by Dbugger on 2008-06-21
> **rbc said:**
> Open a terminal and type: dmesg
I think that's what you're after. If you want to make a file to look at it, again in terminal, type: dmesg > dmesgfile.txt (or call it whatever you want). That command will create that document in your home directory

Well.. kinda... even though I see much more stuff that I usually see when I boot up! But thank you. The only problem is that im seeing the stuff that gets printed at boot time, and I was more interested in the ones that appear at "halt" time.

Any ideas?

---

### Post by avtolle on 2008-06-21
The stuff you are seeing when you log off is, as I understand it, something to do with debugging, and not for mere mortals like us to be concerned about. I see a screen-full of text when I shut down, stuff about network manager, etc., but to date, no problems of which I am aware.

---

### Post by cariboo on 2008-06-21
That text you see about nm and net manager is a bug that nobody has been able to correct yet. Depending on your installation, you might or might not see it. On my hardy installation I see the errors, yet on intrepid which is just barely in the testing phase, all I see is the normal Ubuntu throbber.

Jim

---

### Post by Dbugger on 2008-06-22
You already have intrepid ibex?!?!?! Where did you get it?!

---

### Post by sayakb on 2008-06-22
[http://cdimage.ubuntu.com/daily/20080622/](http://cdimage.ubuntu.com/daily/20080622/)
 
Intrepid Ibex is still in it's testing stage. It may be dangerous to try it.
Also, to reveal text during boot, press Ctrl+Alt+F1(to F6) to show the text.

---

### Post by bodhi.zazen on 2008-06-22
If you would like to look at the boot logs :

[http://ubuntuforums.org/showthread.php?t=253890](http://ubuntuforums.org/showthread.php?t=253890)

[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

