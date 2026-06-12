---
title: "can't change the directory in the terminal"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by Jake_Handwork on 2014-02-04
I have been a Windows user all my life. I just switched to Ubuntu 13.10 (Saucy Salamander) on one of my laptops. It's neat and all, but I'm having difficulty with the terminal.
 
I am trying to install Komodo Edit, but I don't understand it. I'm using this site "http://docs.activestate.com/komodo/7.0/install.html#Installing_Komodo_on_Linux" the terminal will not let me change my directory.
 
I have the Komodo Edit file in Home/Downloads/KEEP/applications/Komodo Edit. Whenever I try to cd to anywhere besides home it says 'no such file or directory'.
 
That is my current problem, but I also barely understand the terminal, as well as how to download/install applications using ppa. Any help is greatly appreciated.

---

### Post by CharlesA on 2014-02-04
Linux is case senstive. Are you using tab completion when typing the directory names?

The download should be in /home/USER/Downloads/etc/etc/etc/

cd ~/Downloads/KEEP/applications/Komodo <tab>

Should get you to the right directory.

---

### Post by deadflowr on 2014-02-04
What's the command you are trying to change directories with?
By default you should open a terminal in your home folder
/home/username(it will be marked witha ~ symbol.
You can find out where you are with
```
pwd
```
If you want to change into the Downloads folder, then
```
cd Downloads
```
Capital and small letters are important.

If the folder is somewhere else then used the full path
```
cd /home/otherguysfolder/Downloads
```
If using the full path make sure the / symbol is at the front.
The / symbol is file system(or root)
home is inside root and the user's folder inside home and Downloads inside the user's folder, and etc,etc.

---

### Post by 3rdalbum on 2014-02-05
Just because it's a terminal, doesn't mean you have to type everything :-)

Type the letters "cd", press the spacebar, and then drag the desired folder to the terminal. (it will fill in the whole path of the folder). Click on the terminal again to bring it back to the front and hit Enter.

---

### Post by CharlesA on 2014-02-05
> **3rdalbum said:**
> Just because it's a terminal, doesn't mean you have to type everything :-)

Type the letters "cd", press the spacebar, and then drag the desired folder to the terminal. (it will fill in the whole path of the folder). Click on the terminal again to bring it back to the front and hit Enter.

Wow, I had totally forgotten about that. I guess I use SSH too much. :)

---

### Post by LinuXXuniL on 2014-02-05
Maybe this will help you regarding the ppa 
[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

---

### Post by Adam_GUI on 2014-02-05
So, the directory you want to change to is "/home/<Username>/Downloads/KEEP/applications/Komodo Edit" Including the space?
Terminals have a habit of stopping when they come to a space.  It's a classic end at a "location not found" message.

You'll have to put your end location in quotations.
Like so: > cd "/home/user/example/subdirectory/program/program edit"

---

