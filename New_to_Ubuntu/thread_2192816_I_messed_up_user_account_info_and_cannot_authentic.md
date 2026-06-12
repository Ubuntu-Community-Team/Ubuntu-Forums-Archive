---
title: "I messed up user account info and cannot authenticate anything!!"
date: 2013-12-09
forum: New to Ubuntu
---

### Post by taylor.allison on 2013-12-09
:oops: 			

 		
 	
Someone please help!! I was preparing to sell my computer with Ubuntu 13.10 installed, and I wiped out Windows 8 which was on the computer before it. When trying to remove my account information for Ubuntu, I changed User Account settings, deleted the name that was there, "Allison Taylor", by backspacing and changing it to "Me" (thinking the new buyer can change it to whatever name she wanted once she owned the machine). I also chose not to be asked for a password for login.

When trying to demontstrate how to install a Ubuntu file (Skype), I was asked to authenticate. And I keep getting told the password is wrong, when I am pretty sure I was entering the correct one.

I am totally unable to do ANYTHING from the terminal because it asks for my password, and I had tried changing passwords, thought I had done so successfully, but nothing I enter is accepted. It mentions the "root password", and without that, I have been totally unable to carry out any of the dozens sites I have visited for help! I am in an endless loop of needing to authenticate, authentication failing without the root password, and any command prompts asking for my password and then being rejected. Of course after 3 times , I read "This has been reported".

I am desperate now, because I feel I have not only made a mammoth mistake in deleting my Windows OS (totally unintentional and happened by inadvertently touching my mouse when I didn't mean to!!), but now in messing up this "root" stuff. 

:confused:

---

### Post by Iowan on 2013-12-09
[This]("http://www.psychocats.net/ubuntu/resetpassword") might be helpful...

---

### Post by taylor.allison on 2013-12-09
Well that enabled me to change my password, but I still cannot authenticate when trying to install Skype. I get the following message :

[B]An application is attempting to perform an action that requires privileges. Authentication as the super user is required to perform this action.
Password for root:___________

Your authentication attempt was unsuccessful. Please try again.
[/B]

---

### Post by deadflowr on 2013-12-09
You can boot into the system, right?
then post the output of this from the "terminal" program:
```
id username
```
change username with the username you have on the machine.
My guess is whatever you did, the user has only normal user rights, 
but this will help confirm it.

---

### Post by taylor.allison on 2013-12-09
allison@allison-Aspire-V5-531P:~$ id allison
uid=1000(allison) gid=1000(allison) groups=1000(allison),4(adm),24(cdrom),30(dip),46(plugdev),112(lpadmin),118(nopasswdlogin),124(sambashare)
allison@allison-Aspire-V5-531P:~$

---

### Post by deadflowr on 2013-12-09
You seem to not be in the admin rights groups anymore.
If you log back into the recovery mode again and run the same mount command as before you should be able to add the user back into the admin rights group.
to do so, try
```
adduser username sudo
```
Which should add the user to the sudo group, giving the user admin rights.
Change the user to your username, of course.
then exit as before and try logging in and see what happens.

---

### Post by taylor.allison on 2013-12-10
Ok, as before when I typed **mount -0 rw,remount /** I received a long string of information, and then was told to type **man 8 mount**  
More strings of information, as before, and after several times clicking "help" to continue, I finally arrive to where I can enter **passwd allison**
But now it is not allowing me to change the password. So I manage somehow to get to where I can enter **adduser allison sudo** and am told [B]allison@allison-Aspire-V5-531P:~$ adduser allison sudo
adduser: Only root may add a user or group to the system.
allison@allison-Aspire-V5-531P:~$ 

[/B]

---

### Post by taylor.allison on 2013-12-10
Following the instructions on how to reset my password as per the link provided by lowan, the screen shot shows an example of a "Susan" as the user, but the text says root@susanbuntu:~=
I can see now that mine does not say root at all

---

### Post by deadflowr on 2013-12-10
Did you do this in the recovery mode or in a terminal?
You have to actually reboot the system to get into the recovery mode.
And the option in the recovery mode will be root, as the input console/terminal is a root shell.
But the reason to run the mount -o rw,remount / command is because in the root shell it is mounted as read-only and that command re-mounts it read-write, which is what you want.
And notice that it is the letter o in the command and not the number zero. -o.
And letter case is also important. big O can do different things than little o in a command.

If you have problems getting the recovery mode when you boot up, press the shift? key(I think it's what it is) when the BIOS screen exits(that's the first screen you should see when you start the computer).
Then let go when see the word grub loading appear.
You should then get an option to boot into some entries, if it only says Ubuntu and an option for advanced options, click on theadvanced options and look for an option that has (recovery mode) or something similar, then let it boot, and from there look for the root shell listing and run the commands.

---

### Post by taylor.allison on 2013-12-10
Are there any spaces in the command   **mount -o rw,remount / **? And Yes, I may have either entered a zero or a capital O, so I will once again try this. I am afraid, because I cannot even go back to Windows!

---

### Post by taylor.allison on 2013-12-10
:guitar:=D>:biggrin:\\:D/Thank you, thank you, thank you!!!!!!!!!!!!!!!!!!!! deadflowr, you have made me a very happy ubuntu user!!!! there was a space after mount, and a space before the / symbol!  And, yesssss, using that lower case letter o also made a huuuuuge difference!! Completed in about a minute!!!! ):P

---

### Post by deadflowr on 2013-12-10
So, now are you able to install stuff?
And yes, I was going to state that there are spaces between the mount and the -o and the rw,remount and the /.

If everything seems to be working, somewhat as it should, then good.
Here's a little extra on ubuntu and root users
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by taylor.allison on 2013-12-10
I installed Skype!!! Now I need to try and install a free antivirus!  Bless you, I am thrilled to bits now.  I will copy and bookmark that link you provided. Thanks a million.

---

### Post by deadflowr on 2013-12-10
Here are two links about security and av in ubuntu
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

and a personal favorite
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Have fun.
'Cause that's what matters in the long run.

---

### Post by taylor.allison on 2013-12-10
Awesome! I believe I am loving Ubuntu now!!!  :D Thanks bunches.

---

### Post by taylor.allison on 2013-12-10
So do I assume antivirus software is really not vital? I do have my firewall installed and active. I don't have "Wine" yet, but have it ready to install. Lots to learn, but I love learning, and that is why I wanted to dive into this new world of Linux.  lol

---

### Post by deadflowr on 2013-12-10
Security should always be considered an on-going fight.
Little more [here]("https://wiki.ubuntu.com/BasicSecurity")

As far as how-tos and what-nots with using ubuntu
[New Docs]("https://help.ubuntu.com/community/NewDocs") is a nice little place to look at.

And of course, asking questions in the forums is always, okay.
(If a question is out of character with the [forums rules]("http://ubuntuforums.org/misc.php?do=showrules") then that will come when it comes)

This though, feels off topic with the thread at hand, and if you feel that the Original problem has been solved, mark the thread as "solved"
You should be able to find a solved in your "thread tools" at the top of the thread page area.

good Luck in learning more.
The adventure awaits...

---

