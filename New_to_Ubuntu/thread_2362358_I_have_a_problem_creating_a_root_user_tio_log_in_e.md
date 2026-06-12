---
title: "I have a problem creating a root user tio log in each time i enter to my ubuntu"
date: 2017-05-27
forum: New to Ubuntu
---

### Post by elreydelaswasas1 on 2017-05-27
[INDENT]Firstable i run the command sudo passwd root at the terminal then i wrote my user password after that i wrote the same new asked password 2 times then i run the command su and wrote the same password as the password i talked about in this message then i executed the cd command thenfore i executed the gedit /etc/lightdm/lightdm.conf then after i executed that command there appeared a text dcument there i replaced what there said with [SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
greeter-show-manual-login=true y replaced it with the copy paste method then i saved the document text and then i executed two times the exit command after that i rebooted the pc and there at login appeared an option that said begin session i wrote root and pressed enter after that i enter the pasword i entered twice between the part i entered the sudo passwd root comman finally the su command and there appeared the next problem There appeared an error uploading <</root/.profile>> mesg: ttyname there failed: ioctl non appropiate Function for the device 
As result the session misconfigured Correct the issue as soon as possible  
[/INDENT]

---

### Post by oldos2er on 2017-05-27
Thread moved to New to Ubuntu. The Resolution Centre is for[COLOR=#000000] problems with your forum account, to appeal moderator action, to request a thread be moved from the jail, or to file a complaint about forum harrassment or abuse. [/COLOR]

---

### Post by QIII on 2017-05-27
Hello!

Why do you think you need to log in as root each time?  What do you mean by "your root account"?

For the benefit of our English speaking members, would you please translate the error?  This is an English-speaking area of the Forums.

Thanks!

---

### Post by SeijiSensei on 2017-05-27
Why is this marked [SOLVED]?

OP, start by reading this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

