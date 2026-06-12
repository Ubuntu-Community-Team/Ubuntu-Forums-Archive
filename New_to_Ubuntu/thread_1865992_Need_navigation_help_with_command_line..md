---
title: "Need navigation help with command line."
date: 2011-10-20
forum: New to Ubuntu
---

### Post by mikebravo on 2011-10-20
[SIZE=4][SIZE=3][COLOR=black]Why does CD not always CD? I am in the Absolute Beginners thread for a reason. All I want to do is navigate to /home/mikebravo/Downloads and command the file there    hplip-3.11.10.run        I can get to mikebravo@linux:/home$ at which point   ls -a    says mikebravo exists and is a directory (it is blue) but I can not change to it for love or money. 
How am I going to run my printer plug in??
[/COLOR][/SIZE][/SIZE]


[SIZE="4"]Thank you to all responders. Lets mark this one SOLVED.  This is what worked for me: It just happens that after my original post I installed and booted into the Gnome Classic desktop. From there I decided to give it another try. There was NO problem, navigation on the command line went exactly as expected. Everything I did before, that did not work before, worked in the terminal under the Gnome Desktop!!  Go figure.  I would like someone to explain this. My  opinion is not worth one cent more than the next guy but it is my opinion that someone should get Shuttleworth by the short hair and slap him around until he quit screwing things up every six months. Classic Gnome is now so crippled that I will have to use Unity whether I like it or not, and I don't. PS my printer is working again.[/SIZE]

---

### Post by papibe on 2011-10-20
Use ls to list what is in the actual directory:
```
ls
```
to see where you are run:
```
pwd
```
to cd to directory without making spelling mistakes use the tab key for completion. For example:
```
ls
Downloads/ Documents/

cd Dow<tab>
```
The last command will convert in:
```
cd Downloads/
```
In order to execute that script you need to see it with the 'ls' command. Then run it like this:
```
bash ./hplip-3.11.10.run
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by AlphaLexman on 2011-10-20
Although Papibe's advice is good, it will **ONLY** work if your are in your $HOME directory...

Use:
```
cd ~/Downloads
```
to get there from **ANY** directory. The difference is between *absolute* and *relative* paths.

---

### Post by dcsoldschool53 on 2011-10-20
> **mikebravo said:**
> [SIZE=4][SIZE=3][COLOR=black]Why does CD not always CD? I am in the Absolute Beginners thread for a reason. All I want to do is navigate to /home/mikebravo/Downloads and command the file there    hplip-3.11.10.run        I can get to mikebravo@linux:/home$ at which point   ls -a    says mikebravo exists and is a directory (it is blue) but I can not change to it for love or money. 
How am I going to run my printer plug in??
[/COLOR][/SIZE][/SIZE]

First, when you tried to ```
cd /home/mikebrava/Downloads
```I hope you used lower case letters for cd. Second, go back to way you said that you can see the folder, and type this in a terminal```
ls -l
``` to check your file permission. If you don't have permission, it will have to be changed, so that you can change into that directory.

I hope this helps you.

---

