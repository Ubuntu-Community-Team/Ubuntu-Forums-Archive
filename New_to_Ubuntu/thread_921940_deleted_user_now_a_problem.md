---
title: "deleted user now a problem"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by Bobbi821@gmail.com on 2008-09-16
I am brand new to Ubuntu.  I had my son set up the user's for my computer, and of course I forgot one of the user's passwords.  So I got this bright idea to just delete the user and create a new one.  That was not the problem.  When attempting to log on the new user I received the following error message.

"User's $Home/dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned by user and not writeable by other users."

Can someone please tell me how to get this user up and running.  This user has never used this computer.  I didn't think I would destroy any files by deleting the original user.

Please help and most definitely in layman's terms!

Thanking you in advance for your help.

[email]Bobbi821@gmail.com[/email]  :(

---

### Post by iaculallad on 2008-09-16
Drop to the terminal and issue the following commands below, one at a time:

```
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
sudo chmod -R u+rwX,og-rwx /home/your_username
sudo chown your_username /home/your_username
```

---

### Post by Bobbi821@gmail.com on 2008-09-16
iaculallad,

I have finally found the terminal window (I think).  I am not sure whose password I am being asked for.  the administrator's or the new user?

it came back as follows: sudo chmod 644 ~/.dmrc
Password?

Also, what am I saving this as once I have typed in each line separately?

Bobbi821

---

### Post by kjohansen on 2008-09-16
you want the admin password for the sudo command

---

### Post by iaculallad on 2008-09-16
> **Bobbi821@gmail.com said:**
> iaculallad,

I have finally found the terminal window (I think).  I am not sure whose password I am being asked for.  the administrator's or the new user?

it came back as follows: sudo chmod 644 ~/.dmrc
Password?

Also, what am I saving this as once I have typed in each line separately?

Bobbi821

You are to input your own user password when using sudo, and, the terminal is found in Applications->Accessories->Terminal. You're not saving anything when issuing those terminal commands, what it does it change the folder permission.

---

### Post by Bobbi821@gmail.com on 2008-09-21
I am so sorry to bother you.  I suppose I should not be attempting to learn a new OS alone.

I finally had the time to sit down and do what I had to do to get the deleted user fixed.  What I did was went to the Terminal and typed in the first line you told me to:
Sudo chmod 644 ~/ .dmrc  then I was asked for my password.  I typed that in but there was no input on the screen(monitor) so I tried again.  Then out of frustration I found the reset on the terminal screen and low and behold now I can't log onto my own computer.  I really need someone's help and it has really got to be spelled out to me in laymen's terms step by step.  I can't understand why I was not successful in putting in my password to begin with.  Could there be another problem someplace else.

Thanking you in advance for your prompt attention and help concerning this matter.
[email]Bobbi821@gmail.com[/email]

---

### Post by freesitebuilder on 2008-09-21
When you enter your password on the terminal, it doesn't display - no asterisks etc to show that you've typed anything. Very confusing, I found at first!

---

### Post by bumanie on 2008-09-21
When typing your password in to terminal there is no visual output, but if you hit enter after putting in the password and have the password correct, your command will be executed.

---

### Post by Bobbi821@gmail.com on 2008-09-21
Thank you both for replying Dianne and Bumanie,

My problem now is not the sudo command or the password.  I accidentally reset the terminal window for my admin account and now I cannot log in.  I am using another users ID on the computer to log into Ubuntu Forums.  What I need now is to know how and understand how to get my administrator account back up and running.  The log in in not recoginzing my name or password since I had hit reset at the terminal window.

Please help!

[email]Bobbi821@gmail.com[/email]
Totally Frustrasted learning a new OS

---

### Post by bumanie on 2008-09-21
OK. Here is a [link]("http://www.psychocats.net/ubuntu/resetpassword") to a website that describes how to reset your password. You should be able to reset your password. Hope this helps

---

