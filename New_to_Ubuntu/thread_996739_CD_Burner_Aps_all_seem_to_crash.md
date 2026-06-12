---
title: "CD Burner Aps all seem to crash"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by carusoswi on 2008-11-29
I'm running 8.10 dual boot.  Have been using Brasero, uninstalled it and tried loading gnome baker - both behave similarly.  The application loads, I start a new audio cd project, navigate to my source files, add the first file to the lower pane, then, click to add the second at which point, the application just closes on me . . . no error messages, nothing.  Just closes as though I had clicked the 'x' box to close it out.

Both applications are behaving in exactly the same way.  I have used both previously without problems.

What could be causing this?

Thanks in advance for any advice.

Caruso

---

### Post by superprash2003 on 2008-11-29
try installing k3b

---

### Post by sujoy on 2008-11-29
you could try k3b as suggested or run the applications from terminal and check the output for what maybe causing the problem

---

### Post by carusoswi on 2008-11-29
> **sujoy said:**
> you could try k3b as suggested or run the applications from terminal and check the output for what maybe causing the problem

Thanks for the replies.  I did load up k3b, and it seems to be working fine.  How would I go about opening the other two aps from the terminal?

I opened a terminal, but have no idea where to look for the file or syntax that would invoke those aps.

Caruso

---

### Post by carusoswi on 2008-11-29
Nevermind.  Wasn't hard at all.  No searching necessary (or syntax, either).  Just typed brasero, and up she came.

Here is the log showing the crash:

caruso@caruso-desktop:~/Desktop$ brasero
I/O warning : failed to load external entity "/home/caruso/.config/brasero/brasero.session"
Segmentation fault
caruso@caruso-desktop:~/Desktop$ 


So, what looks to be wrong?

I've tried installing/uninstalling.  

Caruso...PS:

Here is the output following gnomebaker crash:

caruso@caruso-desktop:~/Desktop$ gnomebaker
Segmentation fault

---

### Post by ELMITWALLI on 2008-11-29
I have created an iso image to install ubuntu onto my laptop
it worked the first time but it did'nt work on the second time
is it the cd itself or is it the software used? I used nero to burn it?

---

### Post by sujoy on 2008-11-29
> **carusoswi said:**
> Nevermind.  Wasn't hard at all.  No searching necessary (or syntax, either).  Just typed brasero, and up she came.

Here is the log showing the crash:

caruso@caruso-desktop:~/Desktop$ brasero
I/O warning : failed to load external entity "/home/caruso/.config/brasero/brasero.session"
Segmentation fault
caruso@caruso-desktop:~/Desktop$ 


So, what looks to be wrong?

I've tried installing/uninstalling.  

Caruso...PS:

Here is the output following gnomebaker crash:

caruso@caruso-desktop:~/Desktop$ gnomebaker
Segmentation fault

segmentation fault!:confused: dont think i can help you much here.

---

### Post by davidshere on 2008-12-02
I am also experiencing this problem with Gnomebaker.  Running it from a terminal was a good idea.  I get a similar error:

```
david@raptor:~$ gnomebaker
vendor = HP, model = DVD Writer 1040d device =&#65533;&#65533;	&#65533;&#65533;
Segmentation fault
david@raptor:~$ 
```
 What we need here is (any Gnome) developer to give us more ideas on how to troubleshoot.

I load up Gnomebaker, choose "audio cd", and browse to the files I want to put in.  I can put in maybe one or two, and then Gnomebaker closes when I choose the next file.  The only way I was able to burn a CD was to add a song, save.  Add a song, save.  That way when it closed I could at least start from where I left off.  I probably had to restart it 8 times before I added all the songs I wanted.

Very frustrating when trying to make Christmas music compilation CDs....

One other thing:  This thread does not have "Gnomebaker" or "Brasero" in the title... made finding a little hard.

---

### Post by davidshere on 2008-12-02
I believe I've found a workaround.  I drag the file instead of using the add file button.  It seems to work for now.

---

