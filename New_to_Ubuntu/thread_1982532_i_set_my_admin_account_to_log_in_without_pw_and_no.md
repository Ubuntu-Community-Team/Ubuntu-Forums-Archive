---
title: "i set my admin account to log in without pw and now ubuntu won't let me have a pw"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by nemespheric on 2012-05-18
okay, so i set my admin account to login without password and now it won't let me change my password or enable it so i have one, i basically wanted to disable annoying password prompts for like everytime i wanted to install something, or login etc

now as things are i can log in without a pw, however it still prompts me for my password when i try to install stuff, plus it won't accept my old password or let me change or reenable my password, how do i fix this ?

---

### Post by wilee-nilee on 2012-05-18
> **nemespheric said:**
> okay, so i set my admin account to login without password and now it won't let me change my password or enable it so i have one, i basically wanted to disable annoying password prompts for like everytime i wanted to install something, or login etc

now as things are i can log in without a pw, however it still prompts me for my password when i try to install stuff, plus it won't accept my old password or let me change or reenable my password, how do i fix this ?

Login is fine, disabling password for everything defeats the safety you have with Ubuntu, there are open source releases that run in root stock, you might want to check them out.

You wont get advice on how to do this on the forum it is against the forum policy. :)

Your password is the one you login with.

---

### Post by Lisiano on 2012-05-18
@wilee-nilee he can't use his password as his account is considered disabled, but he is still able to login without a password (Like using -d with passwd on his account). This is a option inside the users settings.

@nemespheric Do you have a 2nd admin account, if you do, just change the settings from that account? If you don't, you will have to get dirty with a console, so before proceeding, be VERY sure about what you write in the console.
For now, please remember or find the username you have. You can easily see it by opening a terminal (Ctrl+Alt+T) and looking at the line you see. It is formatted by default in this way
```
username@hostname:current directory$
```
So whatever is before the @, is your username, write it down. Now you will have to reboot your PC into a recovery mode. To do that, reboot your PC and hold Shift while booting to get a Grub menu (If you also have Windows installed, then you won't need to hold Shift), now press the Down key once so the line looks like that (The numbers don't matter)
```
Ubuntu, with Linux 3.2.0-24-generic (recovery mode)
```
then press Enter, wait for a while and you will be greeted by a greyish box on a blue background, select Root Prompt using the arrow keys and press Space as "Enter". Now be careful not to mistype the command.
```
passwd username
```
Where username is your actual username, so if it is the same as here, you will have to type in
```
passwd nemespheric
```
You will now be asked to enter the password you want. Note that you will not see any kind of visual indication that you are typing, just keep on typing and once done, press enter, type the new password again and if everything is cool, you will see this
```
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```
Now just type in ```
reboot
``` and your PC will reboot.

---

### Post by wilee-nilee on 2012-05-18
> **Lisiano said:**
> @wilee-nilee he can't use his password as his account is considered disabled, but he is still able to login without a password (Like using -d with passwd on his account). This is a option inside the users settings.

To be honest the OP's description could mean that the auto login is on, we never really know from descriptions. it is at the least a convoluted description.

As well if the admin account is disabled, the fix from the recovery will not work.

---

### Post by Lisiano on 2012-05-18
Recovery will work as he didn't touch root. I had a similar situation, if you set your account as passwordless ([http://ubuntuone.com/1JzUit93Kjfe7Z77oTlAWB](http://ubuntuone.com/1JzUit93Kjfe7Z77oTlAWB)), you can't use anything related to administration until you get a password, which the recovery will do.

Or maybe he is typing it on a wrong layout.

---

### Post by pablo180 on 2012-05-18
> **wilee-nilee said:**
> 
You wont get advice on how to do this on the forum it is against the forum policy. :)

You sure? I can't find anything about that in the Code of Conduct or FAQ? Maybe it should be though. 

@nemespheric not really a good idea to try and disable all password prompts as wilee-nilee said, if you don't need a password, nor does anyone/anything else. 

I thought they were annoying too when I first used Ubuntu but you get used to the prompts after a while and don't really notice them as much.

---

### Post by wilee-nilee on 2012-05-18
> **pablo180 said:**
> You sure? I can't find anything about that in the Code of Conduct or FAQ? Maybe it should be though. 


Quite sure pm the mods and ask, running not in a stock setup with Ubuntu is not ever advised as far as super user access. whether in root or without a password. Ubuntu is designed to be run in a specific way, when you do not you set your self up for programs running as root when not supposed to, and being exposed to security problems.

Really this is in the area of common sense, there are open source setups that run in root and are designed to be that way Ubuntu is not, or without a password.

The COC conduct only covers so much, since this is common sense it is not there. As well this is a site that supports OS's that are known to run in root like backtrack, puppylinux..ect so having this in the COC makes no sense.

---

### Post by nemesephric on 2012-05-18
okay, thank you huys for your replies, okay right so basically my first install opf ubuntu has gone completely forked on me, i have tried to fix through the boot loader recovery console, but i could not seem to find a way to get it out of read only mode so anytime i tried to use the password reset commands, i think it said something like password authentification token error, passwords do not match

sooo basically i have no idea what to do lol, all i wanted was the darn lauch menu at the bottom of the screen and i have somehow managed to wreck my linux installtion lol

ahhh

soo anyways, i er am guessing that as i have idabled my account i can;t even log into it now, there is no pw prompt i cna only sign in as a guest, i can;t get the the  recoveyr console out of mode out of read only mode


oohh but i think figured out why i could not do this, i didn't realse that i had to extract in the home folfer i extratced somehwer else then copied the file, it seems that extacting in the home folder gives me a different file, which i guessing would work lol if i could still log in, perhaps a reinstall is a good ideA?

i have no files that need backing up as i only just installed linux, i am dual booting though, would that complicate things?

maybe if i could still get the thing out of read only i coiuld fix the issue with my pw, but hooO00000000OOoooW? i have tried everything i could find on the net, aahh (sigh)

---

### Post by wilee-nilee on 2012-05-18
> **pablo180 said:**
> You sure? I can't find anything about that in the Code of Conduct or FAQ? Maybe it should be though. 


Found the link hope this helps. :)

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

OP this might help as well for understanding how we can help you as well.

---

### Post by wilee-nilee on 2012-05-18
> **nemesephric said:**
> okay, thank you huys for your replies, okay right so basically my first install opf ubuntu has gone completely forked on me, i have tried to fix through the boot loader recovery console, but i could not seem to find a way to get it out of read only mode so anytime i tried to use the password reset commands, i think it said something like password authentification token error, passwords do not match

sooo basically i have no idea what to do lol, all i wanted was the darn lauch menu at the bottom of the screen and i have somehow managed to wreck my linux installtion lol

ahhh

soo anyways, i er am guessing that as i have idabled my account i can;t even log into it now, there is no pw prompt i cna only sign in as a guest, i can;t get the the  recoveyr console out of mode out of read only mode


oohh but i think figured out why i could not do this, i didn't realse that i had to extract in the home folfer i extratced somehwer else then copied the file, it seems that extacting in the home folder gives me a different file, which i guessing would work lol if i could still log in, perhaps a reinstall is a good ideA?

i have no files that need backing up as i only just installed linux, i am dual booting though, would that complicate things?

maybe if i could still get the thing out of read only i coiuld fix the issue with my pw, but hooO00000000OOoooW? i have tried everything i could find on the net, aahh (sigh)

If you have completely disabled the admin account as in making it a standard or in some way not described, and have nothing to get out of it I would reinstall it in the same place, using the something option in the install gui.

I suggest this as even if someone could get you back in, personally I would not advise you to do that as we don't really know what you have done, and just getting back in does not mean you are safe or setup correctly.

Reinstall and get used to passwords. If you have been using windows without a password in a admin account especially that is about the worse thing that can be done unless you really know what you are doing. No competent IT person would advise a no password set up in any place not designed for one at the least in windows admin.

If you want to be able to learn about some root access in Ubuntu look at this link.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2012-05-18
> **wilee-nilee said:**
> Found the link hope this helps. :)

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

OP this might help as well for understanding how we can help you as well.

We do not have a specific policy for this sort of thing, but this link give you insight to our mentality.

We would not encourage disabling security features.

If someone wishes to configure sudo or such, our preference is that you give them the proper warnings and education. This is most easily accomplished by giving a link to a wiki page.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Otherwise I do not have a problem with the discussion in this thread. I do not have a solution for the OP as I am wayyyy to paranoid to enable auto login.

---

### Post by pablo180 on 2012-05-19
> **wilee-nilee said:**
> Found the link hope this helps. :)

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

OP this might help as well for understanding how we can help you as well.

Very interesting and helpful thanks. Helps clear up a lot of things and it seems even I was a bit blurry when it comes to root and an admin user. Must be a nightmare as a new user coming from Windows.

---

### Post by Lisiano on 2012-05-19
> **nemesephric said:**
> password authentification token error, passwords do not match Am I the only one that noticed that?...
```
Enter new UNIX password: orange
Retype new UNIX password: apple
Sorry, passwords do not match
passwd: Authentication token manipulation error
passwd: password unchanged
```
You entered the password wrong, use a simple one to reset it, like "apple", or simpler. The letter "A"

> **nemesephric said:**
> oohh but i think figured out why i could not do this, i didn't realse that i had to extract in the home folfer i extratced somehwer else then copied the file, it seems that extacting in the home folder gives me a different file, which i guessing would work lol if i could still log in
Question, what are you talking about? What file?

> **nemesephric said:**
> perhaps a reinstall is a good ideA?

i have no files that need backing up as i only just installed linux, i am dual booting though, would that complicate things? Nope, if you made a /home partition then it would be a breeze.
> **nemesephric said:**
> maybe if i could still get the thing out of read only i coiuld fix the issue with my pw, but hooO00000000OOoooW? i have tried everything i could find on the net, aahh (sigh)Are you sure it is running in Read-Only? If it is, very easy to get out of it. Just type ```
mount -o remount,rw /
```What have you tried that you found on the net?

@pablo180 and other windows users, you can think of your Ubuntu Admin account as a Admin account on Win7, except you need to type in your password if you want to do admin stuff, not just click "OK". You can consider the Root user as SYSTEM NT, It's the one your system is running as, the thing you want if you want full control.

---

### Post by ronaldsims on 2012-08-26
I did the procedure outlined in your post, but when I entered the UNIX password once, then again, I still got the message that some sort of error had occurred.  I am quite sure I entered the password exactly the same both times.  I am wondering if I should somehow get Ubuntu off my computer, then start over again with Ubuntu?

---

### Post by bodhi.zazen on 2012-08-26
> **ronaldsims said:**
> I did the procedure outlined in your post, but when I entered the UNIX password once, then again, I still got the message that some sort of error had occurred.  I am quite sure I entered the password exactly the same both times.  I am wondering if I should somehow get Ubuntu off my computer, then start over again with Ubuntu?

You can always do a fresh install

---

### Post by yenic on 2013-02-25
Not to bump an old thread but this just happened to me tonight. I enabled autologin from user accounts and now when I try to install something it asks for my password.. but it does not accept my old one, it also doesn't accept a blank one.

I know what my old password was for sure. I'm not typing it wrong, it types out just fine in any program. 

When I go back into my user account to reenable or change the password it doesn't accept anything as my old password.. not the password or just no password.  Same thing running sudo passwd root.

It's looking like a reinstall, which isn't right. I'm on 12.04.2 LTS 32bit.

---

### Post by westie457 on 2013-02-25
If the information in this link does not help you, then you will need to re-install. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by yenic on 2013-02-26
> **westie457 said:**
> If the information in this link does not help you, then you will need to re-install. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

This fixed it for me, thanks. I reset it to my old password, I tried similar instructions before but not in recovery mode, which did the trick.

---

### Post by gdmt on 2013-08-29
I am running Ubuntu 13.04. I did the same thing as you. I went to settings, user accounts, clicked new password, typed in a new password twice, and viola! Fixed! I hope this helps.

---

