---
title: "Can't Install Skype on 14.04 LTS"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by etep513 on 2014-07-20
I just downloaded and installed 14.04 LTS from a USB stick last night.  I am trying to install skype (since a version wasn't available for 14.04, I selected the 12.04 multiarch versin) but I am having absolutely no luck at all.  I did the install through the software center.  However, when I click skype to try to start it up, nothing happens.  How do I install it?  Remember, I'm fresh off the boat so if it's complicated I need step by step instructions.

---

### Post by mooreted on 2014-07-20
First off, it's not a good idea to mix 12.04 and 14.04 software, you're going to break something.

Skype should be already in the software center, it is in mine. Skype has never worked well in Linux and now that it's owned by Microsoft it probably never will.

First, remove the Skype version you just installed. Then open "Software and Updates" from the Dash. Under "Other Software" make sure that "Canonical Partners" is enabled. Then install "Client for Skype VOIP and instant messaging service" by using the keyword "skype" in the software center search.

---

### Post by samosaara on 2014-07-20
Ha! Had the same problem too, you did installed, it does works, I use it, but the 'Skype' button of the ... (don't know how is it called) "Start Menu", you know the menu, is broken. Simply CTRL + ALT + T and type:
```
$ skype
``` And that's it. Ah, and a tip. I have and quite large contact list and message history, it crashed for me the 1st time, it infinitly BEEP's over and over again, wait some time like 5 to 10 minutes it isn't gonna work but after that, CTRL + C the terminal window u used to open skype and it *should* close (if it doesn't  open another terminal, type "xkill" and click the skype window) and open skype again same way and it will work. Good luck! let me know if u have any trouble.;)
ANd yeah, skype should also be on the repo if it isn't and you preffer try the upper guy soluction don't forget to type:
```
$ sudo apt-get update
``` To get the latest program version list.

---

### Post by mooreted on 2014-07-20
Found some more information about the new Skype 4.3 that might help:

[http://askubuntu.com/questions/488053/how-to-install-skype-4-3](http://askubuntu.com/questions/488053/how-to-install-skype-4-3)

---

### Post by etep513 on 2014-07-20
> **mooreted said:**
> First off, it's not a good idea to mix 12.04 and 14.04 software, you're going to break something.

Skype should be already in the software center, it is in mine. Skype has never worked well in Linux and now that it's owned by Microsoft it probably never will.

First, remove the Skype version you just installed. Then open "Software and Updates" from the Dash. Under "Other Software" make sure that "Canonical Partners" is enabled. Then install "Client for Skype VOIP and instant messaging service" by using the keyword "skype" in the software center search.

How do I remove it?  I was right clicking it to see if I could uninstall it, but I could not find any such feature?  Will this version of skype you are talking about through Canonical Partners work fine?

> **samosaara said:**
> Ha! Had the same problem too, you did installed, it does works, I use it, but the 'Skype' button of the ... (don't know how is it called) "Start Menu", you know the menu, is broken. Simply CTRL + ALT + T and type:
```
$ skype
``` And that's it. Ah, and a tip. I have and quite large contact list and message history, it crashed for me the 1st time, it infinitly BEEP's over and over again, wait some time like 5 to 10 minutes it isn't gonna work but after that, CTRL + C the terminal window u used to open skype and it *should* close (if it doesn't  open another terminal, type "xkill" and click the skype window) and open skype again same way and it will work. Good luck! let me know if u have any trouble.;)
ANd yeah, skype should also be on the repo if it isn't and you preffer try the upper guy soluction don't forget to type:
```
$ sudo apt-get update
``` To get the latest program version list.

Is there any way I can fix it permanently so I don't have to play with command lines every time?  I was trying to do some stuff with command lines that I saw online but it was asking me for a password.  When I typed in the password I created, it kept telling me that it was incorrect and would not let me change anything.  I'm getting pretty frustrated with linux already.

---

### Post by Bucky Ball on 2014-07-20
Skype is in the Software Centre (repositories). ALWAYS check there first. Much better to install from there as it will get regular updates.

I have Skype in 14.04 and it works faultlessly, as it did in 12.04, 10.10, 10.04, 8.04. Have no idea where the idea that Skype has never run well in Linux comes from. Maybe not for some folks, but perhaps that's a hardware thing. Never had an issue personally. ;)

---

### Post by mooreted on 2014-07-20
For me the audio setup was murder. After spending hours finally getting it to work, it would continue to work for a few days, then quit working for no discernible reason. The same for video: though it was easier to setup than the audio, it would also quit working for no apparent reason. Maybe it is better now, but I got burned out with it.

---

### Post by etep513 on 2014-07-20
I was able to start up the 12.04 multiarch version of skype by going into the terminal and doing $ skype

However, I don't want to have to do that every time.  I want the desktop to be more user friendly.  How do I make it so that the icon works?

---

### Post by silex89 on 2014-07-20
> **Bucky Ball said:**
> Skype is in the Software Centre (repositories). ALWAYS check there first. Much better to install from there as it will get regular updates.

I have Skype in 14.04 and it works faultlessly, as it did in 12.04, 10.10, 10.04, 8.04. Have no idea where the idea that Skype has never run well in Linux comes from. Maybe not for some folks, but perhaps that's a hardware thing. Never had an issue personally. ;)

^This!. Just make sure that you have the "Partners of Canonical" source enabled in the Software Sources window. Then you update and voilà.

Best of luck!

---

### Post by etep513 on 2014-07-21
So is there any way I can make the current icon functional?

---

### Post by samosaara on 2014-07-22
YEs! Is dumbly easy. Search for skype and use THAT icon (yes is a different one) will work, well at least it did for me.

---

### Post by etep513 on 2014-07-23
> **samosaara said:**
> YEs! Is dumbly easy. Search for skype and use THAT icon (yes is a different one) will work, well at least it did for me.

There are two skype icons when I clicked the blue swirly button and went under applications.  One of the icons is a marginally darker blue.  That's the one that works.  The lighter one is the one that does not work.  How do I remove the non-working icon?  There is no "Right-click > Delete" options like in Windows XP.

---

### Post by samosaara on 2014-07-23
Ha I think you can't pal, what I did was opening lots of different's apps until the wrong skype go out of recent's list but I know there is a command to clear the recent's list maybe a more advanced user can help us here -- Anyone??

---

### Post by kurt18947 on 2014-07-23
I use Ubuntu-gnome, not the 'default' Ubuntu w/ Unity.  Gnome-shell with an add-on or two can create app launching icons just like Win98, Win2K, WinXP ad nauseum.  I'm not sure how to do that with Unity, or even if it can be done.  Google might have a clue.

  (OT)The reason for occasional password frustration is that Ubuntu often requires you to perform operations that impact more than just your account from an account with sudo privileges.  Sudo is sort of like having limited time administrator privileges.  Many programs will prompt you for a sudo user password in a non-sudo account.  When you enter a password you'll get a message that the password is incorrect or not authorized.  You need to switch to an account with sudo privileges to perform at operation.

  Linux is much more strict about who can do what to the common system than Windows, certainly XP and earlier.  The idea seems to be if you want to foul your own account up beyond all recognition, go ahead.  If you want to do something that can impact other users, you need higher privileges.  I use a (limited) desktop user account 98% of the time even though I'm the only person to use this machine.  Smart Windows users do the same.

---

### Post by etep513 on 2014-07-23
Lol so many people posting replies about simple solutions, yet I don't see anything simple about them.  There is too much tinkering required with ubuntu for us to see any mass adoption anytime soon.  I have built computers before and I know windows pretty well.  I would consider myself to be decently geeky with windows and computers in general, but linux is very much a new front.  For the average non-geek who checks emails but doesn't have much technical knowledge, ubuntu is too hard and still too much like a science experiment for most people to handle.  If the goal is to have an os for geeks, then ubuntu has accomplished that goal ok.  But if more widespread adoption is the goal, then the community isn't even close to hitting the mark, with the main version at least.

---

### Post by Bucky Ball on 2014-07-24
> **etep513 said:**
> Lol so many people posting replies about simple solutions, yet I don't see anything simple about them.  There is too much tinkering required with ubuntu for us to see any mass adoption anytime soon.  I have built computers before and I know windows pretty well.  I would consider myself to be decently geeky with windows and computers in general, but linux is very much a new front.  For the average non-geek who checks emails but doesn't have much technical knowledge, ubuntu is too hard and still too much like a science experiment for most people to handle.  If the goal is to have an os for geeks, then ubuntu has accomplished that goal ok.  But if more widespread adoption is the goal, then the community isn't even close to hitting the mark, with the main version at least.

Thanks for sharing, but off-topic and belongs in the Cafe or a non-support section. Have you got Skype installed and running? If so, please mark the thread as solved and post a new thread for any further topics of discussion/support requests. Thanks.

---

### Post by etep513 on 2014-07-24
> **Bucky Ball said:**
> Thanks for sharing, but off-topic and belongs in the Cafe or a non-support section. Have you got Skype installed and running? If so, please mark the thread as solved and post a new thread for any further topics of discussion/support requests. Thanks.

Skype is installed but I want to know how to have only one functional copy and get rid of the other non-functional one.  Clearly, the issue is not over.  Nobody has given me clearcut, step by step instructions on how to do this yet.

---

### Post by Bucky Ball on 2014-07-24
How did you install the non-functional one? That will give a clue how to uninstall it.

---

### Post by etep513 on 2014-07-24
> **Bucky Ball said:**
> How did you install the non-functional one? That will give a clue how to uninstall it.

I already stated how I downloaded it.  I went to the skype website and I downloaded the 12.04 multiarch version they had.

---

### Post by Bucky Ball on 2014-07-24
How did you install it I mean. What instructions did you use? Was there a 'read me' file in the download? Was it a .deb file?

---

### Post by Votlon on 2014-07-24
Skype works perfectly for me in xubuntu 14.04 and all I did was
```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update  
sudo apt-get install skype
```

So idk why u guys are having so many issues ;)

---

### Post by Bucky Ball on 2014-07-24
I don't know why not installing from Software Centre. If there is a problem with the one in there it should be reported. Works perfectly for me and has since it's been there.

---

### Post by etep513 on 2014-07-26
> **Bucky Ball said:**
> How did you install it I mean. What instructions did you use? Was there a 'read me' file in the download? Was it a .deb file?

That I do not remember.  I'm too much of an absolute beginner in this department to know.

---

