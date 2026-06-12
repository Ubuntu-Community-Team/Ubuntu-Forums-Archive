---
title: "what is this"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by westentertainer on 2008-07-20
can anyone tell me what this means  and how to rectify it please/home/tony/Desktop/Screenshot-synaptic.png

---

### Post by Saint Angeles on 2008-07-20
it means what it says... the last time you tried to upgrade it got interuppted...


run the command it says in a terminal and you'll be fine

---

### Post by hyper_ch on 2008-07-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Joeb454 on 2008-07-20
> **Saint Angeles said:**
> it means what it says... the last time you tried to upgrade it got interuppted...


run the command it says in a terminal and you'll be fine

Actually not quite. You have to run it as root, so you would run ```
sudo dpkg --configure -a
```

---

### Post by asmoore82 on 2008-07-20
Open a Terminal "Applications -> Accessories -> Terminal"
and run this command
```
sudo dpkg --configure -a
```
you will have to enter your password and
you will not see any visual feedback as you type; this is normal.

---

### Post by westentertainer on 2008-07-20
> **hyper_ch said:**
> It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

SORRY im new to this

---

### Post by westentertainer on 2008-07-20
ah tied typing in terminal  only i cannot enter my password now!!! nothing prints after sudo password    
1!!!!

---

### Post by asmoore82 on 2008-07-20
no terminal command will give any visual feedback while typing a password; this is normal
just type the password and hit enter

"Everybody falls the first time"

---

### Post by Shazaam on 2008-07-20
Don't worry, your password is there. Keeps shoulder snoops from seeing the length of the password. Type in the password and hit enter.

---

### Post by westentertainer on 2008-07-20
password will not write in!!

---

### Post by asmoore82 on 2008-07-20
> **westentertainer said:**
> password will not write in!!

This is normal;
**It is There, but no one can see it!**

---

### Post by MunkyJunky on 2008-07-20
when you type your password, nothing will show - this is normal. It's still there, just type it in when asked and hit enter, even though you can't see it.

---

### Post by arpanaut on 2008-07-20
That is SOP, don't expect ********
Trust us.... :biggrin:It's being acknowledged 
Just type in and hit enter, the command will be executed.

---

### Post by pastalavista on 2008-07-20
The password does not show on the screen but it is being entered. If it is entered incorrectly (the root password for the original user) it will say 'incorrect password' or some such. You have been explained this once already. You don't explain exactly what errors you're having. Any time you make a change to your system, you'll need to use the 'sudo' command in terminal and the password will not be evident as you type it (in terminal only). GUI configurators may display the password dots but teminal does not unless you have configured it to. 
```
sudu gconfig-editor
```Be sure you use the root password and hit enter and you should be OK.

---

### Post by westentertainer on 2008-07-21
this is what i gettony@tony-desktop:~$ sudo dpkg --configure -achloe7
[sudo] password for tony: 
dpkg: conflicting actions -c (--contents) and -

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
tony@tony-desktop:~$

---

### Post by oldos2er on 2008-07-21
Copy and paste "sudo dpkg --configure -a"

---

### Post by westentertainer on 2008-07-21
thanks tried that nothing happens

---

### Post by terry_gardener on 2008-07-21
Copy and paste "sudo dpkg --configure -a

to paste into terminal using keyboard press shift+ctrl+v

then it will ask for password: type the password it will not show it as * and appear blank then press the enter key.

---

### Post by oldos2er on 2008-07-22
> **westentertainer said:**
> thanks tried that nothing happens

 Will you help us to help you? Please paste the output of "sudo dpkg --configure -a" here.

---

