---
title: "Recover password, manuals didn't work"
date: 2013-11-15
forum: New to Ubuntu
---

### Post by daniel-prokop on 2013-11-15
hello everyone,

i am using ubuntu 12.04 LTS on an acer aspire e1-531

i have the following problems: since some ubuntu updates i suddenly have two ubuntu accounts, one as "username" and one es guest session. my username account is locked, when i want to unlock it, i get asked the root password and unfortunately i cant remember it.

so i read some manuals here how to recover the root password but none of it worked. what i tried so far:

i booted by pressing shift to enter the gnu / grub menua (it says gnu grub version 1.99-21ubuntu3.10)

then i selected ubuntu, with linux 3.2.0-56-generic-pae (recovery mode) and pressed enter

then the following selection appears from the recovery menu (filesystem state: read only) resume; clean; dpkg; failsafex; fsck; grub; network; root; system-summary. so i selected root and pushed enter.

then i typed mount -rw -o remount /

then i typed the command: passwd username

then "Enter new UNIX password: came up and i wrote and confirmed a new password, it says password successfully updated.

when i go into the user settings then and unlock the account i am asked to type the root password, when i type in the new password which i just set, it doesnt work. so what is wrong, why does it not work?

Then i tried this here: 

[SIZE=1][I]"If [Jorge's method]("http://askubuntu.com/a/24024/156684") didn't work for you, as it didn't for me, here is another method. I had to try something different because:
[/I][/SIZE]
[SIZE=1][/SIZE]
[LIST=1]
[*][SIZE=1]*My USB keyboard did not work at the root prompt &#8943; probably  hardware either keyboard or mainboard. To fix I used an old PS/2  keyboard (the little round plug) and use that.*[/SIZE]

[*][SIZE=1]*When I used passwd username to change my password, it failed because of a bad token or such. This called for drastic measures.*[/SIZE]
[/LIST]
[SIZE=1][/SIZE][h=2][SIZE=1]*The Drastic Measures*[/SIZE][/h][SIZE=1][/SIZE][SIZE=1]***This is a very dangerous thing to do!** [Jorge's method]("http://askubuntu.com/a/24024/156684") should be used; only do this in case that method doesn't work.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]***Do this at your own risk**. It did work for me on my 11.10 system.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*The idea is to set the user's password to blank (or null) - this allows you to just press Enter at the Password: prompt.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Still at the root prompt from [Jorge's method]("http://askubuntu.com/a/24024/156684"), first remount the root file system as read-write by using this command:*[/SIZE]
[SIZE=1][/SIZE][SIZE=4][/SIZE][SIZE=1][I]mount -o remount,rw /
[/I][/SIZE][SIZE=1][/SIZE]
[LIST]
[*][SIZE=1]*Now you are a super-user on this system. Tread lightly.*[/SIZE]
[/LIST]
[SIZE=1][/SIZE][SIZE=1]*Then edit the password shadow file to remove the encrypted password for your username. Type in:*[/SIZE]
[SIZE=1][/SIZE][SIZE=4][/SIZE][SIZE=1][I]nano -B /etc/shadow
[/I][/SIZE][SIZE=1][/SIZE][SIZE=1]*The nano editor will display the contents of the file. Each line will have the form name:&#8943;:&#8943;:&#8943;&#8230;  where &#8943; is a string or null (empty). One of the lines will start with  your username. The first &#8943; after your username is your encrypted  password. As an example:*[/SIZE]
[SIZE=1][/SIZE][SIZE=4][/SIZE][SIZE=1][I]username:$1$amFeNcjp$PprjCKEVk3UtzKwWfEMOY0:14920:0:99999:7:::
[/I][/SIZE][SIZE=1][/SIZE][SIZE=1]*where $1$amFeNcjp$PprjCKEVk3UtzKwWfEMOY0 is the encrypted password.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Carefully delete the encrypted password leaving the all the ":"s, so it looks like this:*[/SIZE]
[SIZE=1][/SIZE][SIZE=4][/SIZE][SIZE=1][I]username::14920:0:99999:7:::
[/I][/SIZE][SIZE=1][/SIZE][SIZE=1]*Then type Ctrl+O, press the Enter key to save, then Ctrl+X to close **nano**.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Reboot and you will have an empty (or null) password.  Be sure to use passwd username in a terminal to set  or reset your user password.*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Source for PS/2 workaround was [here]("http://en.wikipedia.org/wiki/PS/2_connector").*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Sources for the drastic measures were [here]("http://www.debuntu.org/recover-root-password-single-user-mode-and-grub") and [here]("http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-change-the-filesystem-from-read-only-to-read-write-185821/").*[/SIZE]
[SIZE=1][/SIZE][SIZE=1]*Note on nano &#8213; the -B option makes a backup of the original edited file, same name with a "~" appended."*[/SIZE]

and repeated the steps above, with the same result. 

when i now try to go into the terminal and when i am asked a password there, it says username is not in the sudoers file. This incident will be reported.

 


i didnt really understand other manuals, as the adviced steps lead me to interfaces not showing what is been written in the tutorials i read. could anyone please help me?

cheers, dan.

---

### Post by deadflowr on 2013-11-15
It seems your mount command was wrong.:confused:

Try
```
mount -o rw,remount /
```
Or follow this
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Another method is to select the option networking first, which then sets up networking and then when networking is set bring you back to the option screen and the root session  will be reset as read/write.

---

### Post by daniel-prokop on 2013-11-16
thanx, i am in the network screen now and idk how to get back to the menue screen from there. i know that a quite noobish question but could you please tell me which i command have to prompt from there?

---

### Post by steeldriver on 2013-11-16
If you are in the root shell (#) of recovery mode, you can usually exit back to the main menu by typing 'exit' at the prompt

```
# exit
```

HOWEVER if it really is asking for your **root** password then the problem is unlikely to be anything to do with your **user** password (in fact if it had failed to reset your user password because the filesystem was read-only, you would have got a message to that effect 'authentication token manipulation error').

Can you describe exactly what you mean by "my username account is locked, when i want to unlock it, i get asked the root password" - what application is "asking"?

---

### Post by heir4c on 2013-11-16
Normally you have no root password in Ubuntu. Just the user who installed the system have rootrights with his/her password. So if you will change the password following this howto:
[https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Forgotten-password:-what-to-do](https://sites.google.com/site/easylinuxtipsproject/tips#TOC-Forgotten-password:-what-to-do)
If ask to type: passwd your_own_username it means not that you type this literal but that you type after 'passwd' your own username, so if your username is daniel you type:
passwd daniel 
than following the instructions.
If you don't remember your username type: ls /home 

So, you can't change the root password because there is not a root password in the first place.

FYI (for the sudoers file): [http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/](http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/)

---

### Post by deadflowr on 2013-11-16
> **daniel-prokop said:**
> thanx, i am in the network screen now and idk how to get back to the menue screen from there. i know that a quite noobish question but could you please tell me which i command have to prompt from there?

Yeah, I probably should have stated that if networking can't be resolved, which can happen, then it can hang indefinitely.
Normally when entering into networking it resolves the network connections you have and then exits back to the recovery screen.
If it hangs with no option to type, you can try ctrl + C, or maybe ESC or q for quit.

If it can't resolve the network connection then just enter the remount command manually.
The network option is just a nifty way of doing that and establishing a network connection as well.
Basically though what you're trying to do is remount the file system as read/write, instead of the default read-only.

---

### Post by daniel-prokop on 2013-11-17
thank you very much, i solved the problem thanks to all you guys' help

---

### Post by daniel-prokop on 2013-11-17
thanks :)

---

### Post by daniel-prokop on 2013-11-17
ah thanks, i put the username into the sudo group, reset the password and now it works. since i did that the userpassword works again when i am asked to prompt it in the terminal and the user settings.

about the lock/unlock issue: i cant take screenshots right now so im trying to explain. when i enter the user menue i see the username as locked. that means whenever i want to shutdown or restart the system i am asked to type in a password and the notebook still wont shut down or restart. when i tried to click on the lock button at the user name that was locked i was asked for a password with root access maybe? i dont know and dont see the screen anymore because now that i followed the steps there i was simply able to unlock the user account by using my password. so thanks alot :)

---

### Post by heir4c on 2013-11-17
Always welcome.

(Mark your thread as [SOLVED] - this can be done from Thread Tools of threads you start)

---

