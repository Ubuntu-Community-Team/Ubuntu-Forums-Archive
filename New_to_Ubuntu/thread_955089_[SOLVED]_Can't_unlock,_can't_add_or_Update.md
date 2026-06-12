---
title: "[SOLVED] Can't unlock, can't add or Update"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by maninsitu on 2008-10-21
I have tried numerous times to provide a password when trying to add users or even use Update Manager, Ubuntu can not authenticate. I orginally posted this with a question on how to update my profile to allow me to add users etc. The above is clarification.

Only able to add a user in Sudo at restart. Earlier thread describes my attempts. :(

I have tried a number of suggestions for using Terminal and Sudo to no avail.

---

### Post by eternalnewbee on 2008-10-21
Hi there.
By profile, do you mean Main > System > Preferences > About Me?

---

### Post by Nxion on 2008-10-21
> **maninsitu said:**
> How can I unlock my profile so that "administer" Ubuntu?

Only able to add a user in Sudo at restart. Earlier thread describes my attempts. :(

I have tried a number of suggestions for using Terminal and Sudo to no avail.

What is it you are trying to do exactly? Are you trying to update your system?

---

### Post by eternalnewbee on 2008-10-21
Btw, it would be handy if you added a link here to your earlier thread, so we might be able to help you more.

---

### Post by maninsitu on 2008-10-21
> **eternalnewbee said:**
> Hi there.
By profile, do you mean Main > System > Preferences > About Me?

Sorry, no what I meant is that as a user I am unable despite attempts to provide a password to add users or even use the Update Manager. Profile is not a good word to describe the problem.

I just can't seem to have Ubuntu to authenticate any attempts to add users, use the update manager nor add plug-ins in Firefox.

I can provide a password in Sudo during the boot process by hitting the escape key and selecting recovery mode and drop to the root. I was able to add a user this way. But unable to find a way to deal with those things I would like to do at the desktop level.

I hope this helps! I am a real newbie and all the switches, variables etc are really confusing. I am slowly starting to get used to some of the terminology!

---

### Post by maninsitu on 2008-10-21
> **Nxion said:**
> What is it you are trying to do exactly? Are you trying to update your system?

Yes and I can not use the graphical Update Manager on the desktop. It won't authenticate my password. Nor even Add Users in Administration. 

I have tried apt-get -d and there are multiple error messages. I just would like to have access to the desktop Update Manager and not use Sudo...

I really like Ubuntu, it's so stable and darn quick in booting! :) Something XP could never do!

---

### Post by eternalnewbee on 2008-10-21
As for using the update manager, should be able to do that, simply by clicking on Update Manager in Main Menu > System > Administration and type your password. That's all

---

### Post by eternalnewbee on 2008-10-21
As for using the update manager, should be able to do that, simply by clicking on Update Manager in Main Menu > System > Administration and type your password. That's all.
The same goes for adding users. Main Menu > System > Administration > Users And Groups.
If you are not experienced with with terminal, don't drop into a shell to try to solve your problems from there, instead come and ask your questions here. 99% satisfaction guaranteed.

---

### Post by maninsitu on 2008-10-21
> **eternalnewbee said:**
> As for using the update manager, should be able to do that, simply by clicking on Update Manager in Main Menu > System > Administration and type your password. That's all

I have tried numerous times and I get a message stating that Ubuntu is unable to authenticate my password. I have tried my user password, I have tried the password that works when I can drop to the root when booting in recovery mode - both are not accepted.

I have even tried a number of sudo commands in Terminal and at the root as described above.

---

### Post by Nxion on 2008-10-21
> **maninsitu said:**
> Yes and I can not use the graphical Update Manager on the desktop. It won't authenticate my password. Nor even Add Users in Administration. 

I have tried apt-get -d and there are multiple error messages. I just would like to have access to the desktop Update Manager and not use Sudo...

I really like Ubuntu, it's so stable and darn quick in booting! :) Something XP could never do!

Has it always done this? Has this password problem just come up? Have you changed the password recently? Are you logging with one of the accounts you created in recovery mode?

Can you post the errors you are getting when you run "apt-get -d"

---

### Post by eternalnewbee on 2008-10-21
Should'nt you just have one password?

---

### Post by Nxion on 2008-10-21
Also for reference here are some links that can help you understand Ubuntu more.
[URL="https://help.ubuntu.com/"]
https://help.ubuntu.com/[/URL]
[URL="https://help.ubuntu.com/community/RootSudo"]
https://help.ubuntu.com/community/RootSudo[/URL]
[URL="https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows"]
https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows[/URL]

---

### Post by maninsitu on 2008-10-21
> **Nxion said:**
> Has it always done this? Has this password problem just come up? Have you changed the password recently? Are you logging with one of the accounts you created in recovery mode?

Can you post the errors you are getting when you run "apt-get -d"

I just installed Hardy this week. I did though change the user password, and I can't recall trying to add a user prior to or after the password change.

I have tried to change back to the original and it won't let me as it apparently is too small (6 characters). I am not sure why it let me use it in the first place during installation.

I don't have to log in at recovery mode it is a choice that Grub provides during boot and when you hit the escape key before it loads the kernel (i think?). Is there a way to capture the error messages in this non graphical mode? Thank you for your help so far!

---

### Post by maninsitu on 2008-10-21
> **eternalnewbee said:**
> Should'nt you just have one password?

I don't know, I am a newbie :confused: lol

---

### Post by Nxion on 2008-10-21
Sorry, I forgot you don't have a GUI. 

Well what if you went into recovery mode and did this

```
passwd username
```

replace "username" with your user name you used. After that try to run this from a terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by maninsitu on 2008-10-21
> **Nxion said:**
> Sorry, I forgot you don't have a GUI. 

Well what if you went into recovery mode and did this

```
passwd username
```

replace "username" with your user name you used. After that try to run this from a terminal

```
sudo apt-get update && sudo apt-get upgrade
```

I was able to change the passwd as per above but when I tried the code in Terminal after a normal boot this is what I got (also, the password didn't stick I have to use the old one in recovery mode)

sudo apt-get update && sudo apt-get upgrade
[sudo] password for mark: 
mark is not in the sudoers file.  This incident will be reported.
mark@ubuntu:~$

---

### Post by Yashiro on 2008-10-21
It sounds like your user account is not in the admin subgroup.

---

### Post by maninsitu on 2008-10-21
Here is the screen shot when I try to use the graphical Update Manager

---

### Post by Nxion on 2008-10-21
Well I guess the next step is try this:

open a terminal and type this

```
su
```

And when it prompts you for a password enter it.

if that does NOT work try this:

Go back to recovery mode, login and run this:


```
sudo adduser matt admin
```

And reboot and login to your regular session and try to update again. Did that help?

Here is more info on users and groups for Ubuntu
[URL="https://help.ubuntu.com/community/AddUsersHowto"]
https://help.ubuntu.com/community/AddUsersHowto[/URL]

---

### Post by maninsitu on 2008-10-21
> **Nxion said:**
> Well I guess the next step is try this:

open a terminal and type this

```
su
```

And when it prompts you for a password enter it.

if that does NOT work try this:

Go back to recovery mode, login and run this:


```
sudo adduser matt admin
```

And reboot and login to your regular session and try to update again. Did that help?

Here is more info on users and groups for Ubuntu
[URL="https://help.ubuntu.com/community/AddUsersHowto"]
https://help.ubuntu.com/community/AddUsersHowto[/URL]

[SIZE="3"][COLOR="Green"]**Success!**[/COLOR] I was able to use Terminal with the su command. I then was able to use "apt-get dist-upgrade" That worked as well. I still can't use the graphical interfaces, but the adduser using su in terminal works too. 

So I guess I will use sudo in Terminal. I just have to figure out which command to use in Sudo for downloading plugins for Firefox...

Thanks Nxion!!!:popcorn: :)[/SIZE]

---

### Post by maninsitu on 2008-10-22
> **eternalnewbee said:**
> As for using the update manager, should be able to do that, simply by clicking on Update Manager in Main Menu > System > Administration and type your password. That's all.
The same goes for adding users. Main Menu > System > Administration > Users And Groups.
If you are not experienced with with terminal, don't drop into a shell to try to solve your problems from there, instead come and ask your questions here. 99% satisfaction guaranteed.

You are right! I had spent more time trying to solve this by myself than the time that I posted the thread until I got resolution.

I guess the distribution of this Linux Ubuntu (community) is appropriate as evident in the help that I received from you and Nxion...thanks folks!

---

### Post by eternalnewbee on 2008-10-22
You're welcome. Btw, if your problems are solved, you should mark this thread as solved at the top of the page, under Thread Tools.
Good luck to you, and welcome to Ubuntu.

---

### Post by Nxion on 2008-10-22
> **maninsitu said:**
> You are right! I had spent more time trying to solve this by myself than the time that I posted the thread until I got resolution.

I guess the distribution of this Linux Ubuntu (community) is appropriate as evident in the help that I received from you and Nxion...thanks folks!


Glad I could help. The community is here for you when you need help :)

---

