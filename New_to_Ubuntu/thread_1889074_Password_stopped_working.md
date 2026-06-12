---
title: "Password stopped working"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Tazzers on 2011-11-30
Hello. My name is Phil. I am a new Ubuntu and Linux user and also new to this forum so hello and HELP!

I have been happily beavering away on Ubuntu for a week and so far I am very happy with it. Still can't find a driver for my 35mm film scanner but I can work around that by switching to windows whenever I am scanning. Hopefully I will find one eventually.

The real problem I have is more profound and I think I might be staring a re-install in the face.

All of a sudden my password doesn't work. My desktop logs on automatically, that's okay but I cannot install anything. Every time I am asked for authentication, the password that I have been using successfully for a week is no longer accepted.

I didn't change it and I don't know what to do next. Please, if you can help me, help.

Thank you

Phil :confused:

---

### Post by miasmablk on 2011-11-30
try ```
sudo passwd
```
enter your desired password (three times i believe it will require)

then you should be set. also when you are typing in your password it will appear that you aren't typing anything but you really are.

---

### Post by Tazzers on 2011-11-30
Thanks for the quick reply.

I just tried that and after typing in my password three times it says:

sudo: 3 incorrect password attempts

Back to square one I'm afraid. Thanks for trying.

Phil

---

### Post by ajgreeny on 2011-11-30
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)  should help you to set a new password using recovery mode from the grub menu.

If you don't see a grub menu at boot time, hold shift as you boot up and it should appear.  Second entry in the list will be recovery mode.

For your film scanner try installing xsane and you may find that the scanner is already detected.

---

### Post by miasmablk on 2011-11-30
this is the only info i found related to this particular issue when "sudo passwd" doesn't work.


[B]
"Probably you are using modified ubuntu server image, xen vm, etc..    You must add this line at the bottom of the /etc/sudoers file:    #includedir /etc/sudoers.d"
[/B]
it was confirmed to fix the problem[B].
[/B]

---

### Post by Tazzers on 2011-11-30
Hello

My name is Phil. I have put this in another section but I thought it might be worth putting it in here too.

My problem is that my password has stopped working. It is as though it has been changed but as far as I know, nobody has done any such thing.

I am the password holder on this computer and only I know what the password was/is.

So if the password has been changed, I simply do not know what it is and I am screwed if I need to do anything that requires password authentication. I cannot create a new account, I cannot install anything and I can only count myself lucky that my computer logs in automatically.

Is there anything I can do besides a re-install, to sort it out? Even if I re-install it, what is to say it is not a glitch and that it is simply going to happen again?

I'm stumped. Please help.

Cheers

Phil :confused:

---

### Post by Paqman on 2011-11-30
It's easy enough to [reset your password]("http://www.psychocats.net/ubuntu/resetpassword"). Do you have any idea when/why it stopped working?

---

### Post by Tazzers on 2011-11-30
Hello folks. Thanks for your help but so far no joy.

I have tried to change the password and I am getting this message:

"authentication token manipulation error password unchanged"

Still in the same boat I'm afraid.

miasmablk, Sorry I am a bit confused about your last reply, I don;t know where to input it, it is confusing me I'm afraid, I think I need an idiots guide.

Phil :(

---

### Post by Tazzers on 2011-11-30
Hello. Thankyou for responding but I have tried this and I get the following:

"authentication token manipulation error"

password unchanged...................

..................and when I log back in, same problem :(.

Thanks all the same.

Phil

---

### Post by lisati on 2011-11-30
Threads merged. Please do not start multiple threads for the same problem, it dilutes the community's efforts to help.

---

### Post by Tazzers on 2011-11-30
Sorry. I am getting desperate.

Phil

---

### Post by ajgreeny on 2011-11-30
I am beginning to think this is a problem with your /etc/sudoers file, so you can copy this default file into gedit in your /home folder and call it **sudoers**
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
```Now compare this with your **/etc/sudoers** file which you will probably have to view using recovery mode, or a live CD if necessary.   If they are not the same, edit yours with ```
visudo
```from recovery mode.  visudo ensures that no syntax errors creep into the file if you edit it.

I wonder if your problem has followed on from you using **sudo <command>** for a gui application instead of **gksu <command>** or **gksudo <command>**  as sudo is only to be used for command line apps, not gnome or kde aps;  some apps will work OK with sudo, but others can cause the problem you have seen.

---

### Post by fdrake on 2011-11-30
from "man passwd"
> 
EXIT VALUES
       The passwd command exits with the following values:
       0 success
       1 permission denied
       2 invalid combination of options
       3 unexpected failure, nothing done
       4 unexpected failure, passwd file missing
       5 passwd file busy, try again
       6 invalid argument to option

I don't think the error is related to the lost/wrong password, but the application itself. can you use "passwd" in the recovery section (as root) and right after the error msg type and post here the result of:
```

echo $?

```

also check this link :[http://www.ideaexcursion.com/2009/09/11/fixing-authentication-token-manipulation-error-when-changing-passwords-with-passwd/](http://www.ideaexcursion.com/2009/09/11/fixing-authentication-token-manipulation-error-when-changing-passwords-with-passwd/)

---

### Post by Tazzers on 2011-11-30
Food for thought there, I shall have at it tomorrow, the wife is kicking me off the computer now, I'll try not to lose too much sleep over it but I'd hate to have to re-install and the idea of switching back to Windows for everyday tasks is not my favoured option either.

I'll let you know how I get on and once again, thanks for your help so far.

Phil

---

### Post by Tazzers on 2011-11-30
> **ajgreeny said:**
> I am beginning to think this is a problem with your /etc/sudoers file, so you can copy this default file into gedit in your /home folder and call it **sudoers**
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d
```Now compare this with your **/etc/sudoers** file which you will probably have to view using recovery mode, or a live CD if necessary.   If they are not the same, edit yours with ```
visudo
```from recovery mode.  visudo ensures that no syntax errors creep into the file if you edit it.

I wonder if your problem has followed on from you using **sudo <command>** for a gui application instead of **gksu <command>** or **gksudo <command>**  as sudo is only to be used for command line apps, not gnome or kde aps;  some apps will work OK with sudo, but others can cause the problem you have seen.

AJ thanks. Firstly though, I don't know where to find this folder I truly am an absolute beginner. Also I do use sudo at the beginning of command lines in terminal because I don't know where and when to use anything else. Did I mention I was an absolute beginner?

I would copy and paste this into a folder but when I open up my home folder I don't see a geddit folder and when I look inside the folders that are there I still don't see a geddit folder, in fact I don't see anything at all. So I assume that I need to invoke all this in a terminal but if that is the case I need to know what to do from start to finish otherwise I am stuck. Also, everytime I try to copy and paste anything into the terminal, precisely nothing happens. :confused: 

Cheers

Phil :)

---

### Post by Tazzers on 2011-11-30
Okay this is getting very strange indeed. Now I can't shut the computer down. It is acting like it has a virus or something. I try to shut down and it logs me out instead. I try to shut down from the log in screen and nothing happens at all.

Can anybody explain this bizarre behaviour?

Cheers

Phil :confused::confused:

---

### Post by miasmablk on 2011-11-30
hmm when did you install? did you run an Md5 checksum of the .iso you used to install your OS with? sounds like your install may be corrupted.. you haven't been using the "computer janitor" utility have you? you may have to back up important file and do a fresh install.

---

### Post by ianma on 2011-12-23
Did you ever get this solved as I have the same problem, when I try to change the password with the instructions at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) I also get the error

"authentication token manipulation error"

My problem appeared after I had switched the password off to save me keep typing it everytime I went to use the pc after the screen had powered down. Now I cant change any settings as I a am unable to authenticate myself.

If anyone has any ideas that would be great.

Many thanks

Quick edit I forgot to mention I am using Ubuntu 11.10

---

### Post by Ron May on 2012-01-21
> **ianma said:**
> Did you ever get this solved as I have the same problem, when I try to change the password with the instructions at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) I also get the error

"authentication token manipulation error"

My problem appeared after I had switched the password off to save me keep typing it everytime I went to use the pc after the screen had powered down. Now I cant change any settings as I a am unable to authenticate myself.

If anyone has any ideas that would be great.

Many thanks

Quick edit I forgot to mention I am using Ubuntu 11.10

I also have the exact same problem with a dual boot setup.  Autologon enabled.  System comes on and autoconnects to local WIFI.  Message comes up to unlock keyring and <my password> works.  Fine up to that point and I am ablr to do anything not requiring a password.  Any SUBSEQUENT need (sudo, etc.) will NOT recognize <my password>.  Worked fine until tonight.  Only thing different is that Ubuntu ran a disk check on boot.  After trying the psychocats.net link suggested above my compiz config icon size reverted back to original size from 32.  Very frustrating.

---

### Post by Ron May on 2012-01-21
> **Ron May said:**
> I also have the exact same problem with a dual boot setup.  Autologon enabled.  System comes on and autoconnects to local WIFI.  Message comes up to unlock keyring and <my password> works.  Fine up to that point and I am ablr to do anything not requiring a password.  Any SUBSEQUENT need (sudo, etc.) will NOT recognize <my password>.  Worked fine until tonight.  Only thing different is that Ubuntu ran a disk check on boot.  After trying the psychocats.net link suggested above my compiz config icon size reverted back to original size from 32.  Very frustrating.

Launcher icons back to 32 now on their own.  Ubuntu (11.10) still will not authenticate on <my password>, either GUI or command line after login and WIFI established.  None of the options in this thread allow me to modify password, with or without sudo/gksudo and cannot change even as root.

---

