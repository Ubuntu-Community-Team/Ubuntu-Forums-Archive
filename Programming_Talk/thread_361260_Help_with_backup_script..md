---
title: "Help with backup script."
date: 2007-02-14
forum: Programming Talk
---

### Post by apan on 2007-02-14
I need som help.
Can someone help me with a script that asks if i whant to backup my /home/. If i answer "y" should all files in /home/ zip to an .tar.gz-file that will be saved in /backup/ with the name "date"backup.tar.gz. This script should run everytime on startup.
The script should be able to handle with linux startup-script: rc-update in gentoo (is it same for ubuntu?).

I also whant a script that backups all the files in /Home/data to /Home/my_backup everytime i login to the system from bash.

---

### Post by rekahsoft on 2007-02-14
ok...so u want to script to run when u open up your terminal? and simply ask you if you would like to backup? then if 'y' then it tars your home dir?

The way i would go about it is to create the script like so:```
#!/usr/sh
echo "Would you like to backup?"
read input
if [ "$input" == "y" ]; then
     tar --recursive -cf ~/Backup.tar ~/*
else
     echo "No back-up done"
fi
```Then edit ~/.bashrc and make the script run when the terminal is opened by adding the following to the end of the file:```
sh ~/.backup
```Note that this assumes that you save the script as .backup in your home dir

---

### Post by apan on 2007-02-14
> **rekahsoft said:**
> ok...so u want to script to run when u open up your terminal? and simply ask you if you would like to backup? then if 'y' then it tars your home dir?


Hi rekahsoft and thanks for your replay!
I want the script to run when i login to the system. So it should be a startup-script that askes me everytime when i login if i want to backup my /Home/. If i choose "Y" it should back it up.  
And yes it should tar my home dir and place the tar att /backup.

The other script im intrested in are almost the same but it should automatic copy, without asking, my /home/data files to /home/backup when i login to ubuntu. 

I will also try your script and se what happens! 
Thanks again!

---

### Post by rekahsoft on 2007-02-14
ok...in that case...hmm...have u tried any of the backup utilities? I could simply write you a script to do the backup but why when there are already tools available. I recommend you try out sbackup (simple backup) get it like so:```
sudo apt-get install sbackup
```

---

### Post by apan on 2007-02-15
> **rekahsoft said:**
> ok...in that case...hmm...have u tried any of the backup utilities? I could simply write you a script to do the backup but why when there are already tools available. I recommend you try out sbackup (simple backup) get it like so:```
sudo apt-get install sbackup
```

Hi rekahsoft!
I know, the reason why i need a script is that we are working with linux the "hard way" in school and we thought we could write this script but relised that we dont have a clue how to do it, so we was about to give it up but then we came up with the idé of trying this forum for an answer. :)

I understand u think it was wierd that we dont just use an simpel program but now u know why. :)

---

### Post by rekahsoft on 2007-02-15
ok in that case use the original script i gave you (as follows):```
#!/usr/sh
echo "Would you like to backup?"
read input
if [ "$input" == "y" ]; then
     if [ ! -d ~/Backup ]; then
          mkdir ~/Backup
     fi
     tar --recursive -cf ~/Backup/$(date +%s)-Backup.tar ~/*
else
     echo "No back-up done"
fi
```Now you have to go to System>Prefrences>Session and add the script to the run on start up programs.

Note: The only think i am not sure of is if terminal will open to read the input. I am going to write a nicer script for you and get back ASAP :D

---

### Post by rekahsoft on 2007-02-15
ok..i wrote a python front end so that you can have some buttons :D...to use do this:
1. extract the archive attached to this post to where ever you wish
2. go to System>Preferences>Session and add the backup.py to startup programs
:) it will run every start up :)

---

