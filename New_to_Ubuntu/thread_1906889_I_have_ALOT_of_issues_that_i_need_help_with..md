---
title: "I have ALOT of issues that i need help with."
date: 2012-01-10
forum: New to Ubuntu
---

### Post by DarkReaperZer0 on 2012-01-10
I'll just list the first five I'm having.


[LIST=1]
[*]I don't know how to authenticate my pc for the update manager.
[*]I can't install moonlight onto firefox.
[*]None of my system  preferences are saving.
[*]I can't find out how to use Sudo
[*]i can't update firefox
[/LIST]

---

### Post by overdrank on 2012-01-10
Hi and welcome, Moved to Absolute Beginner Talk :)

---

### Post by DarkReaperZer0 on 2012-01-10
Hello, thank you for the welcome, but I really do need help. My computer is practically useless now...

---

### Post by androssofer on 2012-01-10
> **DarkReaperZer0 said:**
> I'll just list the first five I'm having.


[LIST=1]
[*]I don't know how to authenticate my pc for the update manager.
[*]I can't install moonlight onto firefox.
[*]None of my system  preferences are saving.
[*]I can't find out how to use Sudo
[*]i can't update firefox
[/LIST]

welcome to the forums. 1st thinks 1.. background!

when you try to update what happens? 

is moonlight a firefox add-on?

when you say ur system preferences dont save, what do u mean?

sudo is used in the terminal.. what where you trying to use it for?

the firefox update is proably related to point 1...

---

### Post by satanselbow on 2012-01-10
Shall we start at the top with #1?

What version Ubuntu are you using? 
Exactly what error message are you getting?

---

### Post by DarkReaperZer0 on 2012-01-10
> 

When I go to update form the update manager, a pop-up appears asking my to "authenticate", at first i though it meant entering my password, but that doesnt seem to work at all.

yes moonlight is an add-on

whenever i go to the system settings and change something, like brightness or volume, it keeps getting reset every once and in a while.

from what i've seen sudo is like the "run command" from windows, and nothing else has been working for me.

---

### Post by DarkReaperZer0 on 2012-01-10
> Shall we start at the top with #1?

What version Ubuntu are you using? 
Exactly what error message are you getting?ubuntu 11.10, it seems like whenever i try to authenticate, it doesnt let me, for example it says "authentication failed" but not much more.

---

### Post by nothingspecial on 2012-01-10
You sure you have your password right? It is the same one you log on with.

---

### Post by androssofer on 2012-01-10
> **DarkReaperZer0 said:**
> When I go to update form the update manager, a pop-up appears asking my to "authenticate", at first i though it meant entering my password, but that doesnt seem to work at all.

yes moonlight is an add-on

whenever i go to the system settings and change something, like brightness or volume, it keeps getting reset every once and in a while.

from what i've seen sudo is like the "run command" from windows, and nothing else has been working for me.

Humm, the authenticate password is the password you use to login with. 

moonlight might install fine if we get your firefox updating

not sure about the other 2.. my brightness is always full unless my power cable comes out. and volume is always full.. so dont know if this is a normal problem...

sudo isnt quite that. sudo is an abbreviation of 'super user do' (i think so anyway, thats what i think of it as anyway) and is used when you need super user rights. Its a hard concept to explain, as there is nothing like it in windows... but basicly all the important stuff in your computer is protected against accidental changes. so to change it you use 'sudo' which basicly lets the computer know, you know wot your doing.. (not always the case for me :P) 

what where you trying to run using it? and why.. we might be able to help :-)

---

### Post by satanselbow on 2012-01-10
> **DarkReaperZer0 said:**
> When I go to update form the update manager, a pop-up appears asking my to "authenticate", at first i though it meant entering my password, but that doesnt seem to work at all.


Yep the "authenticate" prompt is after your login password.

> **DarkReaperZer0 said:**
> 
yes moonlight is an add-on


We'll come to that in a bit ;)

> **DarkReaperZer0 said:**
> 
whenever i go to the system settings and change something, like brightness or volume, it keeps getting reset every once and in a while.


Let's get the updates installed - as there may be a fix in there already. If it persists we can dig deeper.


> **DarkReaperZer0 said:**
> 
from what i've seen sudo is like the "run command" from windows, and nothing else has been working for me.

Sudo is more akin to "UAC" on windows and grants you temporary elevated privleges so you can perform software installations and administer your system. Sudo is most commonly typed at the terminal before a command although the "authentication" box you are seeing is effectively a gui request for sudo elevation ;)

---

### Post by DarkReaperZer0 on 2012-01-10
> **nothingspecial said:**
> You sure you have your password right? It is the same one you log on with.
Yes I'm sure, but when I enter my user password it doesn't accept it, is their a default password?

---

### Post by DarkReaperZer0 on 2012-01-10
> **androssofer said:**
> Humm, the authenticate password is the password you use to login with. 

moonlight might install fine if we get your firefox updating

not sure about the other 2.. my brightness is always full unless my power cable comes out. and volume is always full.. so dont know if this is a normal problem...

sudo isnt quite that. sudo is an abbreviation of 'super user do' (i think so anyway, thats what i think of it as anyway) and is used when you need super user rights. Its a hard concept to explain, as there is nothing like it in windows... but basicly all the important stuff in your computer is protected against accidental changes. so to change it you use 'sudo' which basicly lets the computer know, you know wot your doing.. (not always the case for me :P) 

what where you trying to run using it? and why.. we might be able to help :-)
Well, I think I shold get my system updated first.

---

### Post by DarkReaperZer0 on 2012-01-10
I guess that means i need to update my pc, but that's proving troblesome

---

### Post by satanselbow on 2012-01-10
Are you sure you have not knocked CAPS LOCK on? Passwords are case sensitive. My other personal, regular, clumsy, fat-fingered fail is turning NUM LOCK off by mistake ;)

If you have managed to log in to Ubuntu - there really is no other reason for the updater authentication to fail other than a wrong password :(

---

### Post by satanselbow on 2012-01-10
Erm... just a thought but have you run the Ubuntu installer or are you running off a liveCD?

---

### Post by DarkReaperZer0 on 2012-01-10
> **satanselbow said:**
> Are you sure you have not knocked CAPS LOCK on? Passwords are case sensitive. My other personal, regular, clumsy, fat-fingered fail is turning NUM LOCK off by mistake ;)

If you have managed to log in to Ubuntu - there really is no other reason for the updater authentication to fail other than a wrong password :(
My password to get in has both lowercase and uppercase letters, so i make sure the caps lock is not on. It's kinda annoying how i can't update my pc with my own password, and i'm staring to think there is a deafult password, is that the case?

---

### Post by DarkReaperZer0 on 2012-01-10
> **satanselbow said:**
> Erm... just a thought but have you run the Ubuntu installer or are you running off a liveCD?
This pc was ahnded down to me, so i have no idea how ubuntu was installed, all i kow is that it was orignally a widows xp pc.

---

### Post by nothingspecial on 2012-01-10
Maybe you don't have an admin account. Did someone else set it up for you?

---

### Post by DarkReaperZer0 on 2012-01-10
> **nothingspecial said:**
> Maybe you don't have an admin account. Did someone else set it up for you?
Somebody did set it up for me, but this is the only account on my pc

---

### Post by satanselbow on 2012-01-10
> **DarkReaperZer0 said:**
> This pc was ahnded down to me, so i have no idea how ubuntu was installed, all i kow is that it was orignally a widows xp pc.

...OK...

It is possible that whoever set up your user account did not make you a member of the "Administrators" group - which means your password is not valid to perform system updates.

If that is the case then the only thing to do is to speak to however gave you the machine and ask them for the administrator account credentials - or reinstall.

You can check this by opening a terminal and typing:

```
id <username>
```

Replacing "<username>" with your own user name...


If the machine was originally a Windows XP box it may not have the hardware requirements to run the latest version of Ubuntu - which might explain your problems with setting changes fluctuating. You may want to try an older version of Ubuntu - although that will again involve a reinstall from scratch :(

*** nothingspecial types and possibly thinks faster thn me :( ***

---

### Post by nothingspecial on 2012-01-10
You need to reboot and enter recovery mode and drop to a root shell in the recovery mode menu.

Once there you need to type
```

adduser **[COLOR="Red"]username[/COLOR]** admin
```

where uaername is your actual username

Then ```
exit
``` and resume a normal boot.

---

### Post by DarkReaperZer0 on 2012-01-10
> **satanselbow said:**
> ...OK...

It is possible that whoever set up your user account did not make you a member of the "Administrators" group - which means your password is not valid to perform system updates.

If that is the case then the only thing to do is to speak to however gave you the machine and ask them for the administrator account credentials - or reinstall.

You can check this by opening a terminal and typing:

```
id <username>
```Replacing "<username>" with your own user name...


If the machine was originally a Windows XP box it may not have the hardware requirements to run the latest version of Ubuntu - which might explain your problems with setting changes fluctuating. You may want to try an older version of Ubuntu - although that will again involve a reinstall from scratch :(

*** nothingspecial types and possibly thinks faster thn me :( ***
iaustin@gold-mine:~$ id austin
uid=1000(austin) gid=1000(austin) groups=1000(austin),4(adm),20(dialout),24(cdrom),46(plugdev),109(nopasswdlogin),116(lpadmin),118(admin),124(sambashare)
austin@gold-mine:~$ 

that's what i got

---

### Post by nothingspecial on 2012-01-10
Well you do have an admin account (I hope that space is a typo). So the plot thickens. You also are set to login without a password. Are you absolutely sure you have your password correct?

You can reset it if not

---

### Post by satanselbow on 2012-01-10
> **nothingspecial said:**
> (I hope that space is a typo)

Confirmation of that would be good - it would certainly lock you out ;)

---

### Post by DarkReaperZer0 on 2012-01-10
> **nothingspecial said:**
> Well you do have an admin account (I hope that space is a typo). So the plot thickens. You also are set to login without a password. Are you absolutely sure you have your password correct?

You can reset it if not
It is a typo, sorry. Yes, i have checked with the previous owner and everything, i just attempted to reset the password but it gave me an error, and didnt change it at all

---

### Post by nothingspecial on 2012-01-10
You need to boot into recovery mode and drop to a root shell.

Then type

```
passwd [COLOR="Red"]**username**[/COLOR]
``` 

change your password then type 

```
exit
```

and resume a normal boot.

---

### Post by DarkReaperZer0 on 2012-01-10
> **nothingspecial said:**
> You need to boot into recovery mode and drop to a root shell.

Then type

```
passwd [COLOR=Red]**username**[/COLOR]
```change your password then type 

```
exit
```and resume a normal boot.
Yes, i did that to the letter, but it gave me and error, and didnt change the password

---

### Post by nothingspecial on 2012-01-10
What happens if you try it in a normal session.

---

### Post by DarkReaperZer0 on 2012-01-10
> **nothingspecial said:**
> What happens if you try it in a normal session.
explain how i can do that please.

---

### Post by DarkReaperZer0 on 2012-01-10
nevermind i just changed it, now what should i do?

---

### Post by DarkReaperZer0 on 2012-01-10
ok, the password has now been accepted, but now i'm getting a new error:

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

Details: Izma

---

### Post by grahammechanical on 2012-01-10
I am trying to find something that explains this. May I suggest that before telling Update Manager to run the update that you look through the lists of packages that are to be updated and remove the check mark against Izma? That may let you run the other updates.

See also this link on a possible solution:

[http://askubuntu.com/questions/15655/updates-dont-install-because-of-untrusted-packages]("http://askubuntu.com/questions/15655/updates-dont-install-because-of-untrusted-packages")

But what does the message mean? I think that I know but explaining it clearly is the problem that I am having.

Here is another solution and a little bit of explanation:

[http://www.tuxgarage.com/2011/02/requires-installation-of-untrusted.html]("http://www.tuxgarage.com/2011/02/requires-installation-of-untrusted.html")

Regards.

---

### Post by DarkReaperZer0 on 2012-01-10
I have finally updated everything, I got it working somehow... Now, that step 1 is done, can i get help with step 2?

---

### Post by nothingspecial on 2012-01-11
I would suggest starting one thread for each issue or this one is going to get messy.

---

### Post by DarkReaperZer0 on 2012-01-11
very well then

---

