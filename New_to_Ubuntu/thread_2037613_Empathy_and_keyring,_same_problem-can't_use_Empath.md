---
title: "Empathy and keyring, same problem-can't use Empathy"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by goodbye-windows(tm) on 2012-08-05
I decided to give Empathy a try, it is the default IM program for Unity and have run into a problem. Empathy needs to use the keyring. I  have never set up the key ring and it does not accept any of the  passwords I try. 

To make matters even worse, it prevents me from accessing other programs while the keyring dialog is on the screen.

And, just when I thought it couldn't get any worse, the keyring dialog box prevents me from even registering and testing the software and if I choose 'skip' it still won't let me register my chat accounts. 

And finally, the process repeats itself, each time Empathy is opened, I have to reenter the log in info again!!!

I tried skipping it as suggested in this forum and other technical emporiums (reported by google). No one seems to have an answer yet.

The developer is unavailable, there is no website or contact info in the software center.

I find posts on this topic back to 2010, and yet the problem isn't fixed yet.

I'm trying to run it on a 64 bit Dell laptop that is certified compatible for Linux.  Using Unity, 11.10.

I would like to contact the developer or to have information on how to fix the problem.

TY.

Art

---

### Post by mcduck on 2012-08-05
The keyring is set up automatically for you when you install Ubuntu, and it will by default sue the same password you set as your login apssword during the install.

As long as the passwords remain same, and you use a normal login screen with password confirmation, the keyring will get unlocked automatically for you. If you change your login apssword, you need to change the keyring password as well to keep the automatic unlocking working.

...and if you use automatic login, you will either have to unlock the keyring with password, or set it to use empty password (wich will allow automatic unlocking, but of course looses the security aspect of the keyring).

So, the short answer is to try using the password you set up when you installed Ubuntu. (and these forums are not the way to approach any developers, they very, very rarely hang around here. If you ever run into an actual bug, a properly files bug report in Launchpad is the way to go).

---

### Post by goodbye-windows(tm) on 2012-08-06
> **mcduck said:**
> The keyring is set up automatically for you when you install Ubuntu, and it will by default sue the same password you set as your login password during the install.

As long as the passwords remain same, and you use a normal login screen with password confirmation, the keyring will get unlocked automatically for you.** If you change your login password, you need to change the keyring password as well to keep the automatic unlocking working.**


Thanks so much mduck.

I did in fact change my password (user's account password, administrative) recently, to a much stronger but easier to enter password. I have also changed the super users password recently. I know both old and new passwords for both accounts. But, when I enter the new password into the keyring error window, it is rejected.

You mentioned that the keyring is set to the original password of the super user at installation time. Do I need to change the super users keyring or my own accounts keyring value?

I have tried the original super users password and my accounts password, neither satisfy the keyring error dialog window.

I'll start a search for info on how to change the keyring value. But, some of the sources I found on the net advocated deleting some file related to this issue instead. It's not an option for me as I have multiple users on my system, and the other users passwords would be trashed by deleting the file.

**Which keyring password do I have to change to enable the automatic unlocking of the keyring???? **

Regards,

Art

PS:I hope there is a terminal command for making the keyring change::>

---

### Post by mcduck on 2012-08-07
The keyring is different one for each user, so of course the password is always that user's keyring password, and users don't have access to any others than their own keyrings. Pretty much the same as with any other non-admin application.

So if youa re not using the account created during Ubuntu install, the keyring password should be the one you set when you created the user account you are now using.

The main point here is that the keyring password is set to same as the login password at the time the user is created, but after that changin the login password will not automatically change the keyring password so you'll have to do that manually if you wish to benefit from the automatic unlocking feature.

Anyway, if the original password of that suer account doesn't work, and you are absolutely sure you haven't ver stored any important and information in the keyring, you *can* just delete the current keyring and a new one will be created automatically, giving you a chance to set a new password for it. To do that just remove the *~/.gnome2/keyrings/default.keyring* file.

---

### Post by goodbye-windows(tm) on 2012-08-07
Thanks again!!

I was able to find instructions for editing the keyring value, so that the current password and the keyring values are equal.

I didn't want to delete the file, and eventually I found the MIA passwords and encryption folder (which was not in "settings").

The vast majority of the keyring problems (as listed on this forum) happen with those users who log in automatically and those users who only have keyring issues using the wireless setup. 

I hope users change passwords periodically, despite the fact that ubuntu is pretty secure. I think it's still good practice to change passwords even though it seems that doing so will create the keyring problem and will require manual editing of the keyring value.

So, I'm going to mark this one as solved. Once again, the forum and users who share their technical knowledge via the forum deserve a big "thank you". Ditto those who run and administer this forum-Ubuntu would no be viable without the forum provides insight.

GO LINUX!!!

Art

---

