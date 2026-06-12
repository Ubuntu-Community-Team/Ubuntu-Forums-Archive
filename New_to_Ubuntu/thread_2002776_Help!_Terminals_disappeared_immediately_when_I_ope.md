---
title: "Help! Terminals disappeared immediately when I opened them in Ubuntu 11.10"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by qiushuichangtian on 2012-06-13
Hello everyone! Today,I can not open my terminals in Ubuntu 11.10. It disappeared immediately,when I opened it. I have tried to open the terminal both in "Ctrl + T" and in "win + A + terminal".The result is the same.If I opened several terminals at the same time,all of them will disappear one by one.
Why? I am confused by the [FONT=Arial]phenomenon.How can I know why this happened and what should I do to solve this problem?[/FONT]
[FONT=Arial]Thank you very much!:KS[/FONT]

---

### Post by howefield on 2012-06-13
> **qiushuichangtian said:**
> Hello everyone! Today,I can not open my terminals in Ubuntu 11.10. It disappeared immediately,when I opened it. I have tried to open the terminal both in "Ctrl + T" and in "win + A + terminal".

Try Ctrl + Alt + T

---

### Post by qiushuichangtian on 2012-06-13
I am so apology to tell you that I have made a mistake,I have tried the key "Ctrl + alt + t" instead of "Ctrl + t",but the result is the same.It is necessary to describe it with more detail.When I press "Ctrl + alt + t" together,I can see the terminal being opened,but it is closed immediately. So the problem is about "disappearing" not "opening".
What can I do to solve the problem?Reinstall  the system may be the last way for me to solve the problem. :confused:
Thank you all the same!:p

---

### Post by philinux on 2012-06-13
> **qiushuichangtian said:**
> I am so apology to tell you that I have made a mistake,I have tried the key "Ctrl + alt + t" instead of "Ctrl + t",but the result is the same.It is necessary to describe it with more detail.When I press "Ctrl + alt + t" together,I can see the terminal being opened,but it is closed immediately. So the problem is about "disappearing" not "opening".
What can I do to solve the problem?Reinstall  the system may be the last way for me to solve the problem. :confused:
Thank you all the same!:p

Open Dash and type term. Choose uxterm and then enter into it gnome-terminal press enter
and report back any errors shown.

---

### Post by qiushuichangtian on 2012-06-13
> **philinux said:**
> Open Dash and type term. Choose uxterm and then enter into it gnome-terminal press enter
and report back any errors shown.
I have opened Dash and typed term ,then chosed uxterm.However nothing happened,just like you have not chosed it.Everything is so calm,nothing has happened!
How strange it is!I also tried to choose xterm and terminal in the Dash,I can not entered into them too.The results are the same,and nothing happened.I tried to choose firefox web brower in the Dash,the firefox web brower can be opened and worked normally!Why?Thank you for telling me the way to analysis this problem.:confused:

---

### Post by philinux on 2012-06-13
Try this. [http://askubuntu.com/questions/127235/gnome-terminal-doesnt-start](http://askubuntu.com/questions/127235/gnome-terminal-doesnt-start) Scroll down to last bit te fonts.

---

### Post by qiushuichangtian on 2012-06-14
> **philinux said:**
> Try this. [http://askubuntu.com/questions/127235/gnome-terminal-doesnt-start](http://askubuntu.com/questions/127235/gnome-terminal-doesnt-start) Scroll down to last bit te fonts.
Hello! I am glad to tell you that I know more about my problem, but I find I can not work as root in my machine although I have the password!  When I pressed "ctrl + alt + F1" and put in user name logging in and the right password, it gave me some error messages like this:
 
qq-ThinkPad-Edge login:root
Password:
Last login:Fri Jun15 02:07:41 CST 2012 on tty1
welcome to Ubuntu 11:10 (GNU/Linux 3.0.0-12-generic i686)
     *Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
30 packages can be updated.
[COLOR=red]-bash:error while loading shared libraries:libncurses.so.5:cannot open shared object file : No such file or directory.[/COLOR]
Ubuntu 11:10 qq-Thinkpad-Edge tty1
qq-Thinkpad-Edge login:
 
[COLOR=black]It required me to login again and again and again![/COLOR]
What's more insteresting is I can write an bash shell script to install myunity in my home,but it is source code. I can not using "make" command to make it!
Now I am confused by that. How can I solve this problem when I can not work on my machine as root or even can not use a terminal?
Incidentally,libncurses.so.5 is downloaded from the Internet to help me build gdb-7.2
which should be used to work in another machine whose architecture is arm.I have installed libncurses.so.5 as root.:confused:

---

