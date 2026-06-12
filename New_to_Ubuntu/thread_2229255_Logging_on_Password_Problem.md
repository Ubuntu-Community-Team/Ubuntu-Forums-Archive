---
title: "Logging on Password Problem"
date: 2014-06-12
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-12
I have been using Ubuntu 14.04 for about 3 weeks or so, dual booting with Windows 7. Yesterday evening, while using Ubuntu OS, I found I could not get onto BBC Homepage. The screen went grey and I was given the option of waiting or forcing  a halt to the download attempt. I did one and then the other. Later I logged off and logged back on, this time to Windows 7 which configured the OS after having downloaded some updates earlier in the day. As a matter of fact the Windows configuration did not go as normal. It had about three goes at completing the configuration having to re-start itself about three times and ending up by starting itself in what looked to be 'safe mode'.

Anyway, most of of the above might be irrelevant to the problem I now have which is that Ubuntu does not seem to be recognising my logging in password. I can get in only as a 'guest'. Can anyone please tell me how I can restore things to normal in Ubuntu? I have, by the way, tried a start up using the Ubuntu 'Advanced' option but the has not solved the problem.

---

### Post by Impavidus on 2014-06-12
Does it say: "Incorrect password" or does it accept your password and bounce back to the login screen immediately?

In the first case, it's a password problem. You can try resetting your password using this link: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

In the second case, it's the graphical session that crashes as soon as it starts, taking you back to the login screen. The usual suspect would be the file **.Xauthority** in your home directory, which, through incorrect usage of sudo, may have become root-owned. **.ICEauthority** sometimes causes the same problem. Both must be owned by you and have permissions -rw------- (octal 0600). If you login in the console (ctrl-alt-F2) or from a root shell (recovery mode), you can check and fix if needed.

Windows updates might interfere with grub, but as you get to the login screen that's not your problem.

---

### Post by gordon99 on 2014-06-12
It does not say "incorrect password". I am using the same password that I used when installing of Ubuntu. It accepts the password but after a delay of, maybe 45 seconds, it bounces back to the password screen. I don't think I've used sudo. Not yesterday anyway when it wet wrong. I am relieved to know Windows updates did not cause the problem though they did seem to upset Windows itself for a time.
I am not sure what I have to look for, or do, when I press ctrl-alt-F2 (or get to root shell) but I will investigate. By the way, I seem to get a choice of two or three recovery options plus generic options, all titled linux xxxxxx. Does it matter which recovery option I choose for Ubuntu 14.04?

---

### Post by Bucky Ball on 2014-06-12
Oddly, I had this same endless login loop and fixed it just today. Perhaps it will work for you, too. 

* Boot from a LiveDVD/USB and get to a desktop (or boot from another install on the machine if you have one, which is what I did);
* Navigate to the /home/user folder;
* Hit CTL+h to reveal hidden files/folders;
* Look for 'ICEauthority' and 'Xauthority';
* Delete them and reboot - both files will be regenerated on reboot.

Any luck?

PS: If you're confident, you could hit F2 at the endless login screen and delete those files using the tty ... Good luck either way.

---

### Post by gordon99 on 2014-06-12
I am getting into deeper water I fear. I got onto terminal via ctrl-alt-f2 and after putting in my user name and password I inserted the command rm ~/.Xauthority which I believe to be the file removal command. The reply was something like "Cannot remove xxxxxx Permission Denied".  I then tried the same for .ICEauthority and again permission was denied.  I think I still have the USB with which I did the original Ubuntu install. If I plug that in and switch on where will it get me to?

---

### Post by steeldriver on 2014-06-12
Don't panic yet

First of all can you post the results of these commands from the Ctrl-Alt-F2 virtual terminal:

```

ls -ld ~

ls -l ~/.{ICE,X}authority

```

---

### Post by Bucky Ball on 2014-06-12
Easy. You need:
```

sudo rm ~/.Xauthority 
sudo rm ~/.ICEauthority
```

That simple. You need to do it as root, that's all. You're fine. ;)

---

### Post by steeldriver on 2014-06-12
^^^ yes but if a user can't rm files (even root owned ones) from their own directory, it possibly indicates the home directory ownership itself or permissions are messed up

---

### Post by Bucky Ball on 2014-06-13
OP gives no indication they've run the commands as root. Probably why they're getting "Cannot remove xxxxxx Permission Denied". Should probably try with sudo first, then move on if it doesn't work.

Worked for me in virtually the same situation yesterday (after five hours of trying to figure it out) as I mentioned earlier. I changed from GDM to XDM login manager and wound up with an endless login loop; right password, back to login screen ad infinitum, which looks the same or similar to OP's problem. Deleting those two files and rebooting fixed it. Worth a try. ;)

If they won't delete running with sudo, well, that gives us some new clues. :-k

---

### Post by gordon99 on 2014-06-13
Thanks steeldriver and Bucky Ball. Firstly I tried "ls -d~" and received the reply "/home/gordon". Then I tried "ls -l ~/.{ICE,X}authority" and the reply was "/home/gordon/.Xauthority".

I then put in "sudo rm ~/.Xauthority"  and reply came back "[sudo] passsword for gordon:" I inserted my password and the terminal input for me, which is "gordon@Gordon-HP:~$" came back. I then inserted "sudo rm~/.ICEauthority" and the reply was the terminal input again.
 
I then escaped from the terminal, shut down and re-booted. The log-in page appeared but when I put in my password the log-in page re-appeared. The only difference was, instead of having to wait half a minute or so for the log-in page to re-appear, it came back almost immediately. Progress of some sort I guess.

Sorry to be such a pain. Any other suggestions other than a complete re-install? Am willing to try anything within my limited competence.

---

### Post by Impavidus on 2014-06-13
That shouldn't be the complete output of those commands. Maybe you forgot the l (lower case L)? The correct commands are```
ls -ld ~
ls -l .{X,ICE}authority
```In my case the output is```
egroot@Elektra:~$ ls -ld ~
drwxr-xr-x 56 egroot egroot 12288 jun 13 12:02 /home/egroot
egroot@Elektra:~$ ls -l .{X,ICE}authority
-rw------- 1 egroot egroot 1610 jun 13 12:02 .ICEauthority
-rw------- 1 egroot egroot   52 jun 13 12:02 .Xauthority
```
Even if .Xauthority and .ICEautority are owned by root, you don't need sudo to delete them as long as your home directory is owned by you. So maybe your home directory (/home/gordon) is not owned by you. In which case login fails as those files cannot be recreated as you don't have write permission in your own home directory.

---

### Post by steeldriver on 2014-06-13
Thanks Impavidus that's **exactly** where I was going with this! 

gordon99 please re-run the first command including the "minus ell" (we don't really care about the second one now since you used sudo to remove the files anyway)

---

### Post by gordon99 on 2014-06-13
Have just tried going to terminal and, after putting in user name and password to get to 'gordon@Gordon-HP:~$' I put in 'sudo rm ~/.Xauthority' and the reply came back to the effect that '/home/gordon/.Xauthority' could not be removed as there is no such file or directory. I then did the same for 'sudo rm ~/.ICEauthority' and the reply was 
again to say there was no such file or directory. I suppose this just confirms that both files were removed when I first used the sudo commands just prior to my earlier reply.

---

### Post by steeldriver on 2014-06-13
**Yes, we know both files were removed.** However that has not fixed the problem, has it? So we need to know

```

ls [B]-ld ~
[/B]
```

to see if the problem is the ownership or permissions on your **home directory**.

---

### Post by gordon99 on 2014-06-13
Just to say I have re-visited terminal and after giving my user name 'gordon' and my password i tried the two sudo commands again. in each case the reply was of the form ' cannot remove '/home/gordon/.Xauthority' no such file or directory'. I guess this indicates that my earlier removal attempt of these files was successful even if it didn't solve my log-in password problem. Terminal still seems to recognize my log-in password which may,or may not, be significant. By the way, if a similar message from me is also posted it is because I signed in to Ubuntu as a guest and logged on to the forum to post this message. However, when I went back to Windows and logged in to forum again my first attempt at sending this did not seem to have been posted.

---

### Post by Bucky Ball on 2014-06-13
Forget about removing .ICEauthority and .Xauthority. You have successful achieved removing them. Time to move on. They will be re-created when you manage to login. Please post the result of this, as requested by steeldriver. 

> **steeldriver said:**
> 
```

ls [B]-ld ~
[/B]
```

---

### Post by gordon99 on 2014-06-13
From 'ls -ld ~' I get the response 'dr-xrwr-x  24 gordon gordon 4096 Jun 13 10:27 /home/gordon'

---

### Post by Bucky Ball on 2014-06-13
> **gordon99 said:**
> From 'ls -ld ~' I get the response 'dr-xrwr-x  24 gordon gordon 4096 Jun 13 10:27 /home/gordon'

Different permissions to this:

[QUOTE= Impavidus]drwxr-xr-x 56 egroot egroot 12288 jun 13 12:02 /home/egroot[/QUOTE]

How about the output of the other command:

```
ls -l .{X,ICE}authority
```

---

### Post by gordon99 on 2014-06-13
For 'ls -l .{X,ICE}authority' the response is 'ls: cannot access .xauthority:No such file or directory'.
                                                          'ls: cannot access .ICEauthority: No such file or directory'.
Hope this sheds some light on where the problem is.
Thanks for your continued interest.
H

---

### Post by steeldriver on 2014-06-13
Please run

```

sudo chmod u+w /home/gordon

```

in the Ctrl-Alt-Fx terminal and then press Ctrl-Alt-F7 and try again to log in via the GUI

---

### Post by gordon99 on 2014-06-13
steeldriver, I am very pleased to report that, having typed the commands as you suggested, i am now able to log in as normal. Needless to say I am very grateful to you, Bucky Ball and Impavidus for the trouble you have taken to assist me. I would not have had a clue what to do without your guidance. I find there is another problem that had first occurred immediately before the log-in problem reared its head. I may have referred to in in my original posting. I am finding that when I click onto Firefox, which results in google bringing up a page containing BBC Homepage, the computer stops responding and a notice comes up asking if I want to wait or do a forced shutdown. At the same time I notice that the hard drive is running extremely fast. If you think this requires a new thread I will open one.
Anyway, my thanks once again.
gordon99.

---

### Post by steeldriver on 2014-06-13
Glad we got you logged back in, yes please start a new thread for the firefox lockup issue

---

### Post by Bucky Ball on 2014-06-14
> **steeldriver said:**
> Glad we got you logged back in, yes please start a new thread for the firefox lockup issue

+1. New thread with a descriptive title for the Firefox issue. The title of this thread has nothing to do with it so reduces your chances of support posting here. Also, please mark the thread as 'Solved' to help future travelers. Thanks. ;)

---

