---
title: "Installing Software, why so caveman?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by AaronCW on 2008-04-27
Good morning.

My question is... why is Installing Software still so "out of date" as compared to Windows or even Mac Leopard? 

I really like the Add / Remove Programs manager that is included with Ubuntu. I used it to install Thunderbird and it was flawless. However, I also want to install Seamonkey and Lightning and now I'm lost in the README file. This is a quote of what it says to do:

>  o install SeaMonkey by downloading the tar.gz or tar.bz2 file:

Note: if you're using a tar.bz2 file, replace all ocurrences of .gz in the following instructions with .bz2

1. Create a directory named "seamonkey" (mkdir seamonkey) and change to that directory (cd seamonkey).

2. Click the link on the site you're downloading SeaMonkey from to download the non-installer (seamonkey*.tar.gz) file into the seamonkey directory.

3. Change to the seamonkey directory (cd seamonkey) and decompress the file with the following command:

  tar zxvf sea*.tar.gz
	
This creates a "seamonkey" directory under your seamonkey directory. 

4. Change to the seamonkey directory (cd seamonkey). 

5. Run SeaMonkey with the following run script: 

  ./seamonkey 

... it pretty much lost me at Step 2!! Any help? What does it mean to do a "./" ?? I kind of figured out that a .tar file is like a .zip file, right?? 

Any advice is greatly appreciated.

---

### Post by Joeb454 on 2008-04-27
Yes a .tar file is similar to a .zip file :)

And it wants you to do it from a terminal. Find it under Applications>Accessories.

And I wouldn't say installing software is caveman, I prefer it this way - I don't have to insert CD's and reboot after it's installed :) What's so caveman about that?

---

### Post by FredB on 2008-04-27
Indeed. And even if sometimes version are old, it is simple to install them with add-remove or synaptic

---

### Post by Joeb454 on 2008-04-27
I forgot to mention - most programs that come in .tar files are the source code, which you need to compile yourself.

This may seem caveman as well, however it can be very useful, because it will be optimised for your PC, and it allows you to include extra options in the program sometimes :)

---

### Post by Chilli Bob on 2008-04-27
Firstly, seamonkey is available in the repositories, If it isn't showing in add/remove, try "synaptic" under system - administration.  This is a more powerful version of what add/remove does, but a little less freindly.

Secondly you can do most of this from the GUI file manger if that is what you are used to.  Make and change directories as you would in windows.  Double clicking the tar file should bring up an archive manager, a bit like winzip works. You can then extract the files.

Any file that is normally hidden from view in the file manager starts with a dot. So

./seamonkey
 
is a hidden file. Select view hidden files in your file manager to see it. Double click the file to run it.

---

### Post by finer recliner on 2008-04-27
from those instructions, it doesnt sound like you have to "install" anything. you simply unpacked a tarball which contained a stand-alone executable. this should be a simple process. just type the commands as descibed in the parentheses above. what are you having trouble with exactly?

---

### Post by Joeb454 on 2008-04-27
> **Chilli Bob said:**
> Any file that is normally hidden from view in the file manager starts with a dot. So

./seamonkey
 
is a hidden file. Select view hidden files in your file manager to see it. Double click the file to run it.

Not quite

In a terminal ```
./
``` means the current directory. For example . is a current directory and .. is the parent directory.

Files prefixed with a . for example /home/joe/.bashrc are hidden files :) If seamonkey was a hidden file, it would say to execute ```
./.seamonkey
```

Hope that clears things up a little :)

---

### Post by lswest on 2008-04-27
> **Chilli Bob said:**
> 
Any file that is normally hidden from view in the file manager starts with a dot. So

./seamonkey
 
is a hidden file. Select view hidden files in your file manager to see it. Double click the file to run it.

Actually, the "./" means in the current directory, and "seamonkey" is the folder, so taken together it means "in the seamonkey folder within the current directory", and a hidden folder would be ".seamonkey"

*EDIT* Ah, too slow :P

---

### Post by Michael.Godawski on 2008-04-27
First make sure your application cannot be installed with Synaptic or you do not find a deb package. Installing from source should be the last attempt, but it is not a caveman approach, it is the "real" way. :)

---

### Post by Chilli Bob on 2008-04-27
D'OH! Quite correct.  I didn't think that through, did I?

---

### Post by Joeb454 on 2008-04-27
> **lswest said:**
> 
*EDIT* Ah, too slow :P

Sorry :D

> **Chilli Bob said:**
> D'OH! Quite correct.  I didn't think that through, did I?

And it is a little confusing at first, I had trouble grasping it at one time.

---

### Post by Sef on 2008-04-27
> Firstly, seamonkey is available in the repositories,....

To download Seamonkey from Add/Remove, be sure and set the box in the upper right corner to either 'All Open Source Applications' or 'All Available Applications'.  

'All Open Source Applications' is also known as universe, which contains only open source applications that are not included in the main Ubuntu repositories.

'All Available Applications' is also known as multiverse, which contains proprietary applications.  Also universe is available.

---

### Post by finer recliner on 2008-04-27
> **Chilli Bob said:**
> 

Any file that is normally hidden from view in the file manager starts with a dot. So

./seamonkey
 
is a hidden file. Select view hidden files in your file manager to see it. Double click the file to run it.

this is true, except in two cases: the single dot (.) (which is this case) and the double dot (..)



if the application you want to run is not in your default $PATH, you need to type the full path of the application (otherwise how will the shell know where it is?)

the dot in a path represents the current directory you are in. the double dot represents the directory one above where you currently are.

by typing "./seakmonkey" you are telling the shell, "i want to run an application. its located in the current directory i am in, and its called seakmoneky"

---

### Post by WoodyMahan on 2008-04-27
Aaron, some of the guys on here got lost in the geek speak, but fear not.  There were a few replies on here that addressed the issue in a manner that will probably work better for you.  Be assured that nearly every software item you are interested in finding is available in Synaptic OR Add/Remove.  These 2 programs have a small learning curve but once you get them figured out, I believe that you will readily agree that installing software in Linux is not only not caveman but truly far more advanced than the alternatives.

Don't get frustrated and try to understand that you will sometimes get replies that are the most complicated way of doing things on these boards.  With time you will figure out which responders and or responses to "tune out" and which ones will provide truly beneficial information.  Occasionally guys get on here and just cannot resist the temptation to show off their "uber-geek" status.

---

### Post by AaronCW on 2008-04-27
Thanks for all the replies. Most were over my head though. I never did find out how to install Seamonkey from the tar.gz file I downloaded. 

But I discovered something wonderful while trying... I just typed in the word "seamonkey" and the system told me that the application was not installed and exactly how to install it using the "sudo" command. I typed in what it told me, and now I have Seamonkey! 

What was the add-on or whatever that told me how to get it? It was in Terminal... 

Thanks!! Hopefully someday I will know as much as you guys!

---

