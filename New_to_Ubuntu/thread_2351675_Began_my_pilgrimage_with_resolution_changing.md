---
title: "Began my pilgrimage with resolution changing"
date: 2017-02-05
forum: New to Ubuntu
---

### Post by dryw on 2017-02-05
Hi all, 

very sorry to waste your time but I seem not to be able to solve this.

I draw on [this ]("https://ubuntuforums.org/showthread.php?t=2269309")existing post and on your [wiki]("https://help.ubuntu.com/community/Lubuntu/Monitor_or_Screens#Sometimes_it_takes_real_tweaking_to_solve_the_problem"). Let's stick on the so called "quick fix".

> Another easy (and cheaper) solution, that often works, is to 'uncomment' (that is remove the # character from) the line

**#GRUB_TERMINAL=console**

in the file **/etc/default/grub**

Too easy to grasp for me I guess. 
I opened and modified grub both with notepad and through console. The first gave me "can't open file to write" the moment I attempted to save it, the second didn't seem it should be saved or at least it is not mentioned is the thread. Next instruction is run the command ```
sudo update-grub
``` and restart

 Running this instruction either through console or ctrl+alt+t so far looks it should be the same. Better the second since it give you some feedback.

No change after restarting. I reopened grub. Everything was unmodified. 
Thanks for you understanding and patience.

---

### Post by Autodave on 2017-02-06
You will have to modify the file using the terminal. Once you modify it, click on the top left corner "FILE" and then choose to save it. Exit the terminal. Reboot and report back.

---

### Post by Impavidus on 2017-02-06
To modify the file you need root privileges. The easiest way is to open a terminal (ctrl-alt-t will be fine, console and terminal are loosely used for the same thing, although there really is a small difference). Then run this command:```
sudo nano /etc/default/grub
```sudo will give you root privileges, nano is a simple text editor and /etc/default/grub is the file you want to change. Sudo will ask for your password and it will show nothing while you type it. There are other text editors, like vim, but nano is the simplest to use.

Then use the arrow keys and what other keys you need to modify the file. Then save it and exit the editor. The keyboard shortcuts are listed at the bottom of the screen, ^ means the control key, so ^X means ctrl-x. Then run```
sudo update-grub
```to activate the changes.

---

### Post by dryw on 2017-02-06
> You will have to modify the file using the terminal. Once you modify it,  click on the top left corner "FILE" and then choose to save it. Exit  the terminal. Reboot and report back.

I do not see any "save" option in the left corner File menu.
  [ATTACH=CONFIG]273555[/ATTACH]

Is it that "File" you all are talking about? Wow I'm feeling a Neanderthal. I wasn't even able to take a screenshot.

Assuming I will be able to save, in the near future, ```
sudo update-grub
``` has to be run on a separate window/tab (or console) which I can comfortably open from "File", right?

Ignore the sarcasm please and thanks for your help.

---

### Post by howefield on 2017-02-06
> **dryw said:**
> I do not see any "save" option in the left corner File menu.

That looks like the nano text editor that you are using.. Ctrl + O, press enter and then Ctrl + X to save and exit the file.

The commands are at the bottom of the terminal windows, with "^" meaning the Ctrl key - as per the post by Impavidus.

---

### Post by dryw on 2017-02-06
So "write out" means "save". I wouldn't have guessed it in a hundred years.
Never struggled so much to save something.
It worked anyway. 
Thanks a lot!!

---

### Post by oldrocker99 on 2017-02-06
Great! Nano is one fine little editor, and once you get used to the commands, I find it my go-to editor,

Please mark your thread as [SOLVED] with the Thread Tools at the top of this thread, to help other users.

---

### Post by howefield on 2017-02-06
> **dryw said:**
> Never struggled so much to save something.

Nano is my text editor of choice but if you prefer a more GUI way of editing text files, Lubuntu comes with the leafpad text editor. To edit the grub file you would use the terminal to open leafpad with elevated privileges..

```
sudo -H leafpad /etc/default/grub
```

---

### Post by dryw on 2017-02-07
Noting wrong with the GUI, that was more a problem with semantic. Guess we can call it a first impact for a naive Windows user..

---

