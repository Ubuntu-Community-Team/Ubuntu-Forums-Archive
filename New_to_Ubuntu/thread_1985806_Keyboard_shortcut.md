---
title: "Keyboard shortcut"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by bob brazie on 2012-05-23
Ubuntu 12.04

I am trying to create a keyboard shortcut to "simple scan". I enter a new custom shortcut and name it simple scan and use the same name as the command. I give it the key combo of ctrl+s.

It does not work.

I tried opening it in a terminal using the same command and it does not open that way either.

The app is installed as I just used it. <g>

What am I doing wrong.

Thanks in advance. Bob.

---

### Post by garvinrick4 on 2012-05-23
Any time you are adding a shortcut. You have to hit add then under command use the 
script to run it with your key command. Like open a Terminal "gnome-terminal" without quotes.

---

### Post by garvinrick4 on 2012-05-23
click on screenshot.

---

### Post by bob brazie on 2012-05-23
I used the command: gnome-simple scan" as instructed but the simple scan app still does not open. ?
Bob.

---

### Post by garvinrick4 on 2012-05-24
How about "simple-scan" without quotes.

If you run this in a terminal below, copy and paste it in a termial you will get a text file
with all your installed with the correct correct command in your Home.
```
sudo dpkg --get-selections > installedsoftware 
```You can also look in Ubuntu software center and hit "more info" and will give you correct command for any software (under version.)

---

### Post by bob brazie on 2012-05-24
Version: simple-scan 3.4.1-0ubuntu1, From the Sofware center.

Still does not work.

---

### Post by bob brazie on 2012-05-24
Copied and pasted "sudo dpkg --get-selections > installedsoftware" into a terminal and all it did was return me to a prompt.

---

### Post by bob brazie on 2012-05-24
This is what I get when I use your command:
And just simple-scan worked!

---

### Post by garvinrick4 on 2012-05-24
> Copied and pasted "sudo dpkg --get-selections > installedsoftware" into a terminal and all it did was return me to a prompt.
That is what it is suppose to do, now look in your Home and there will be the text file with all your software in alphabetical order. 

> And just simple-scan worked! 
glad you got the hang of it.

---

### Post by bob brazie on 2012-05-25
Thanks for the help!

Bob.

---

