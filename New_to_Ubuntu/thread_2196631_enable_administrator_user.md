---
title: "enable administrator user"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by matteucci-samuele on 2013-12-30
Hi

I have a big problem I cannot solve. I have mistakenly disabled the administrator account. When I rebooted my PC I couldn't access it, it wouldn't recognize the password. I managed to change the root password and now, although it seems to accept the new password, the computer would not load the admin info but it would return to the main log-in page asking again for the password. it would go on in a loop. Is there anything I can do to solve this problem? Any suggestions welcomed;)

---

### Post by ian-weisser on 2013-12-30
How did you disable the administrator account?
Please be specific. That phrase could mean several different kinds of disablement.

Enabling a root password is discouraged in this forum. Ubuntu is intended to work with the root account disabled.
The root account is generally different from the user account with admin (sudo) priveleges.

All can be fixed if you use the recovery console.
Access the recovery console from the GRUB prompt at boot.

---

### Post by matteucci-samuele on 2013-12-31
hi, 

thanks for replying. I have disabled my account (administrator) from the account users window on settings. It was not my intention. I have realized my mistake when I tried to log in again and my password was refused by Ubuntu. I have searched for this problem in many a chat rooms such as this for Linux/Ubuntu and I have wrongly supposed (from what I understood reading your post) that the problem was the root password. I managed to change it, I hope it is not a big deal, but the result is that the access to the admin user is still denied.

What string of command do I need to write to solve this in the GRUB prompt?

---

### Post by Iowan on 2013-12-31
From the recovery console, **passwd -S <username>** will show the status of <username>
**man passwd** gives details of the fields

---

### Post by ian-weisser on 2013-12-31
You seem to have two or three problems now:
1) Your account, which happens to have your administrator privileges, is disabled.
2) You have enabled the root account.
3) If you have a GRUB prompt (instead of a list of kernels to boot from), then you have a big third problem.

Do you really have problem #3?
If not, select and boot into Recovery Mode. It's just a command line.

At the recovery mode command prompt (#), try the command **passwd -u** **<yourusername>**
That should unlock your account.
Reboot and try to login to your account.

Once your account is working, open a terminal.
At the command prompt ($), do the command **passwd -dl root** to delete and lock the root account.
That should fix root.
You don't need to reboot after that, since you are already using your own account.

---

### Post by matteucci-samuele on 2013-12-31
I will describe the process of what I do:

#Boot my PC holding SHIFT
#I have a window GNU GRUB with a list of 4 option to choose from: I go for Advance option for Ubuntu
#Another  window appears with different lines: I choose Ubuntu, with Linux 3.11.0-14-generic (recovery mode)
#After a series of commands that scrolled down my display, the system asks for the passphrase which I enter
#I have now a recovery menu (file system read only). I scroll down and choose "root" - drop to root shell prompt
#I entered the command you gave me at the bottom of the screen. I got this message: <cannot lock/etc/shadow; try later.

Where do I do wrong?

---

### Post by acebrain01 on 2013-12-31
reboot into GRUB
Choose recovery mode
boot into root shell
REMOUNT drive as RW
set password to enable account.

Brian

---

### Post by ian-weisser on 2013-12-31
(withdrawn - acebrain01 beat me to it!)

---

### Post by acebrain01 on 2013-12-31
Remount drive as RW

---

### Post by matteucci-samuele on 2013-12-31
sorry guys but I am pretty new to Ubuntu (I should have mentioned it earlier)

How do I remount the drive as rw?

---

### Post by matteucci-samuele on 2013-12-31
I did write this command: mount -o re,remount /

After that I wrote the command: passwd -u <Myusername>

and this is the message I got: passwd: password expire information changed

I tried to reboot and enter the password into the admin log in but it did not recognised the password

---

### Post by matteucci-samuele on 2014-01-01
Hi,

I need to remount my system as RW to do some changings (in fact I have disabled my administrator user account and I cannot log in anymore as such). I have been told that I can change it in the root shell prompt but I am not sure about the syntax of the command.

Can anyone help me please?

---

### Post by coffeecat on 2014-01-01
I have merged your new thread with your old one, as this is all part of the same problem you are trying to solve. You may bump a thread if you are not getting a reply, but only after 24 hours please.

To remount the system rw when you boot in recovery mode, the command is:

```
mount -o rw,remount 
```

Not the &#8220;mount -o re,remount /&#8221; you said you used.

Here is a useful howto for resetting your password:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

And from the same website, here is a howto that may help you with your original question:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by matteucci-samuele on 2014-01-01
Thanks for the instructions.

I have successfully changed the password from the safe mode.

When I reboot Ubuntu normally, I enter the new password in my user log in. Initially it seems to accept the password but the screen would go back to the log in page. I can enter the new password as many time I like, Ubuntu would go in a loop and would NOT let me access it. 

I think I need to re-enable <myuser> as administrator or create a new user administrator so to get access to all privileges.

I tried #passwd -u <user> but it didn't work before

---

### Post by matteucci-samuele on 2014-01-01
I am stuck. My computer is not responding to the commands I have been given. the only thing I can do is to log in as guest session

---

### Post by matteucci-samuele on 2014-01-01
is there a way to reboot the computer with old settings saved before that unfortunate day when I changed the configuration of the administrator?

---

### Post by matteucci-samuele on 2014-01-01
is there anyone that can give me suggestions how to solve this problem? I am pretty disperate

Ta

---

### Post by matteucci-samuele on 2014-01-01
is there anyone that can give me suggestions how to solve this problem? I am pretty disperate

 Ta

---

### Post by Dave_L on 2014-01-01
This might not solve your problem, but it may give more information until someone posts a solution.

After a normal boot, you can toggle between the GUI (Graphics User Interface) mode and non-GUI mode:

Control+Alt+F1 switches to non-GUI mode.
Control+Alt+F7 switches to GUI mode.

In non-GUI mode, can you log in to your admin user?

---

### Post by matteucci-samuele on 2014-01-01
Thanks Dave for answering.

I did as you suggested and, since I managed to remove the password, as I log in with my username (which is the administrator) I have the following:

[B][I]The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu come with absolutely no warranty, to the extent permitted by
 applicable law.

Signature not found in user keyring
perhaps try the interactive 'ecrypsfs-mount-private'

[/I][/B]This is what I have got.
Do you understand what this means?

I have no clue.

---

### Post by Iowan on 2014-01-01
Try the process again. If the system was not **rw**, the changes may not have been saved.

---

### Post by matteucci-samuele on 2014-01-01
I manage to set the system on RW. I can set password for the <username> or remove it alright. Still, with password or not, I cannot access the <username> account. It looks like I am locked out. 

Could it be that it is a bug? I know that possibly it is me who is doing or rather not doing things right. it is frustrating though.

---

### Post by Iowan on 2014-01-01
Have you tried changing the password?
(Next step might be to create another user.)

---

### Post by matteucci-samuele on 2014-01-01
Yes I tried. I have changed it twice but the result doesn't change.

How do I create another username with admin power? I need to do it from recovery mode

---

### Post by Iowan on 2014-01-01
You can add a user with the **adduser** command. 

[http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line](http://askubuntu.com/questions/7477/how-can-i-add-a-new-user-as-sudoer-using-the-command-line)
[http://askubuntu.com/questions/266986/authentication-failed-with-the-correct-password-and-now-i-cannot-use-sudo-anymor](http://askubuntu.com/questions/266986/authentication-failed-with-the-correct-password-and-now-i-cannot-use-sudo-anymor)
(Curiously, my 12.04 system uses **admin** group, rather than **sudo**)
**groups <username>** will show which groups <username> is a member.

---

### Post by Dave_L on 2014-01-01
> **matteucci-samuele said:**
> Thanks Dave for answering.

I did as you suggested and, since I managed to remove the password, as I log in with my username (which is the administrator) I have the following:

...

Signature not found in user keyring
perhaps try the interactive 'ecrypsfs-mount-private'

[/I][/B]This is what I have got.
Do you understand what this means?

I have no clue.

If you changed your password from the command line, it's possible that the password needs to be updated in the keyring. Here are some old posts on that. I'm not sure if they're applicable to your situation.

[http://ubuntuforums.org/showthread.php?t=1695764&p=10497521#post10497521](http://ubuntuforums.org/showthread.php?t=1695764&p=10497521#post10497521)
[http://ubuntuforums.org/showthread.php?t=1781787&p=10962324#post10962324](http://ubuntuforums.org/showthread.php?t=1781787&p=10962324#post10962324)

---

