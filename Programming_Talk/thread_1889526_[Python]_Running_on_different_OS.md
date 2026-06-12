---
title: "[Python] Running on different OS"
date: 2011-12-01
forum: Programming Talk
---

### Post by jmg158 on 2011-12-01
Hi all,

Sorry for the vague title, it's more confusing than informative but I wanted to keep it short. 

Anyway, I've written a nice python script that can go through and organize my music to a certain extent. I can run it easily on my computer with Ubuntu. 

However, I wanted to share it with a friend of mine, so it could help him as well, however, he runs windows. What kind of process would I have to use to send it to him? I've never really tried to program something on one OS and run it on another, so I'm not even sure what would be involved. 

Any help would be appreciated, Thanks!

John

---

### Post by karlson on 2011-12-01
> **jmg158 said:**
> Hi all,

Sorry for the vague title, it's more confusing than informative but I wanted to keep it short. 

Anyway, I've written a nice python script that can go through and organize my music to a certain extent. I can run it easily on my computer with Ubuntu. 

However, I wanted to share it with a friend of mine, so it could help him as well, however, he runs windows. What kind of process would I have to use to send it to him? I've never really tried to program something on one OS and run it on another, so I'm not even sure what would be involved. 

Any help would be appreciated, Thanks!

John

Unless you want your friend to do the testing for you.  I'd suggest installing a VirtualMachine of some sort (VirtualBox, VMWare) running Windows and testing your script there.  

Once you know it works you can zip the source files up using zip or 7z and send them to your friend via email.

One thing that he will have to do is download Python interpreter for Windows for example from [http://www.python.org/download/](http://www.python.org/download/)

---

### Post by Petrolea on 2011-12-01
If you're not using any OS specific code or libraries then porting the code shouldn't be a problem. But your friend will have to install interpreter, as the above post mentioned.

---

### Post by jmg158 on 2011-12-01
okay. I'm thinking about it now, and I may see a possible issue...

i'm using some commands that move and rename files (mostly from the os module). an example of this might be os.renames(music library folder + "/" + artist name folder + "/"... )

anyway, I'm assuming this will be a problem due to the slashes in the different direction.

I did some googling though, and came across something called py2exe... does anyone know if this would be of use?

---

### Post by Bachstelze on 2011-12-01
> **jmg158 said:**
> 
i'm using some commands that move and rename files (mostly from the os module). an example of this might be os.renames(music library folder + "/" + artist name folder + "/"... )


Use os.path.join() for that. :)

---

### Post by deonis on 2011-12-01
Hi, py2exe is a nice tool and very easy to use, so yes you can use it. I would suggest to create a platform independent code. So make sure that you do not use any specific paths (use sys.path). Also if you are dealing with txt files make sure you take in account end of line in windows and in linux. If you batch rename your files make sure that you use appropriate symbols etc. Overall script created for linux will work on windows with python installed.

---

### Post by lykwydchykyn on 2011-12-01
> **jmg158 said:**
> 
I did some googling though, and came across something called py2exe... does anyone know if this would be of use?

py2exe works great, I use it at work for this purpose.  Be aware that you'll need a windows installation with python and all applicable libraries installed before you can use it, though.  You can't create exe's in Linux with it.

There are some alternatives that might work too, such as cx_freeze or pyInstaller.

---

