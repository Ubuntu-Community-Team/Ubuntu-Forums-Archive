---
title: "Locked myself out of admin account"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by bedpotato on 2012-04-08
Please help and be kind to a clueless noob! 

I had just one user account on Ubuntu and it was set to be the admin one. I remembered reading that it wasn't a good idea to be always logged in as admin, so I decided I would change that account to "Standard." Fine. I also changed the password on it to something more secure.

Next, I decided I would create a new admin account which I would log into whenever I needed to do anything that required admin permissions. Right? So I made one, and gave it a username, and it now exists. THere are now two accounts. Mine, the standard one, which I've made a new password for, and the new admnin one, which I haven't made a password for yet. But here's the problem: 

I'm now still logged in as "me" (formerly admin but now suddenly Standard) and trying to give the Admin account a password, but in order to do that, it's _asking_ me for a password before it will let me proceed! How can that be, seeing as I haven't even MADE a password for it yet?

I'm rather frustrated and confused. Did I just somehow lock myself out of my own computer? IS there a standard default password for Admin accounts? If so, please can somebody tell me what it is?

---

### Post by roelforg on 2012-04-08
You could use the init=/bin/bash trick.
Forum rules say that this is all i'm allowed to say.

---

### Post by bedpotato on 2012-04-08
Thank you very much, but I don't know what you mean.

Edit: I googled what you said and it says it relates to a lost root password. How can the root password be "lost" if I have not yet created it?

Please can somebody tell me how there can be a password for the new account if I haven't MADE a password yet? :confused:

Did the computer make a password all by itself?

Did I do something stupid somehow?

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> Please help and be kind to a clueless noob! 

I had just one user account on Ubuntu and it was set to be the admin one. I remembered reading that it wasn't a good idea to be always logged in as admin, so I decided I would change that account to "Standard." Fine. I also changed the password on it to something more secure.

Next, I decided I would create a new admin account which I would log into whenever I needed to do anything that required admin permissions. Right? So I made one, and gave it a username, and it now exists. THere are now two accounts. Mine, the standard one, which I've made a new password for, and the new admnin one, which I haven't made a password for yet. But here's the problem: 

I'm now still logged in as "me" (formerly admin but now suddenly Standard) and trying to give the Admin account a password, but in order to do that, it's _asking_ me for a password before it will let me proceed! How can that be, seeing as I haven't even MADE a password for it yet?

I'm rather frustrated and confused. Did I just somehow lock myself out of my own computer? IS there a standard default password for Admin accounts? If so, please can somebody tell me what it is?


well admin and root are different things.  The root account is locked by default and has no password unless you gave it one.

The first user on the system is given admin access via the use of sudo and sudo group membership making it a admin user.

To repair sudo

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

to recover password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The advice for not logging in as admin, means dont login as root, logging in under a admin account is fine as we use sudo to perform any admin action under that account

read [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

---

### Post by roelforg on 2012-04-08
> **bedpotato said:**
> Thank you very much, but I don't know what you mean.

Edit: I googled what you said and it says it relates to a lost root password. How can the root password be "lost" if I have not yet created it?

Please can somebody tell me how there can be a password for the new account if I haven't MADE a password yet? :confused:

Did the computer make a password all by itself?

Did I do something stupid somehow?

Root can do anything, including resetting passwords, the init trick boots to a root shell

---

### Post by Gone fishing on 2012-04-08
The /bin/bash trick - I think we can do this without breaking the rules! You will need to edit the grub recovery mode. To edit the recovery mode go to the grub screen select recovery mode and lick e to edit and change the line that reads 

ro recovery modeset

to read
Code:

rw init=/bin/bash

Then allow the system to boot (cantrol x) and it will drop you down to a root shell. At the # prompt you can set the admin password

passwd admin_user and then add the password twice and reboot and you will be able to login as admin_user. Obviously change admin_user to the right user name

I think you can safely make your account an admin account as long as you don't randomly use the sudo command.

---

### Post by winh8r on 2012-04-08
process broken down and explained via PM at OP's request.

basically the same same solution as supplied by others , just in smaller steps.

---

### Post by bedpotato on 2012-04-08
Oh dear...

Thank you all very much for trying to help, but please would somebody mind dumbing it down for me? I do not have any expert knowledge at all. 

e.g. I have absolutely no idea what you mean when you say "go to the grub screen." To save me accidentally messing up my computer even more, it would be safer if somebody gave me jargon-free instructions rather than me having to google everything in the instructions to see what I'm supposed to do, and perhaps getting it wrong.

 Thank you for trying to help, though. I'm very grateful. :)

Edit: oh thank you for helping Winh8r! :)

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> Oh dear...

Thank you all very much for trying to help, but please would somebody mind dumbing it down for me? I do not have any expert knowledge at all. 

e.g. I have absolutely no idea what you mean when you say "go to the grub screen." To save me accidentally messing up my computer even more, it would be safer if somebody gave me jargon-free instructions rather than me having to google everything in the instructions to see what I'm supposed to do, and perhaps getting it wrong.

 Thank you for trying to help, though. I'm very grateful. :)

Edit: oh thank you for helping Winh8r! :)

Follow the links in my post above, its as dumbed down as it gets.

Peace

---

### Post by bedpotato on 2012-04-08
> **winh8r said:**
> edited

Oh Winh8r I don't know why you've edited it away, but when I did what you said first it said: PCI (sysfs)  and then it paused and then came up with pages and pages of funny text :confused:

haqking, I did briefly look at your links and they seemed a bit daunting to me. I will try looking at them again. Edit: oh dear, see, it talks about fixing broken sudo. I don't know what a sudo is or how or why I've broken it. That article tells me to boot into recovery mode, but I'm currently still logged in. Wouldn't it be a bad idea to log out and lose access to my computer? :confused:

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> Oh Winh8r I don't know why you've edited it away, but when I did what you said first it said: PCI (sysfs)  and then it paused and then came up with pages and pages of funny text :confused:

haqking, I did briefly look at your links and they seemed a bit daunting to me. I will try looking at them again

if you only look briefly at answers people give you then you wont get the results you want ;-)

the resetpassword link is simple and will help you reset any passwords you are having issues with.

and remember sudo/admin is different to root

---

### Post by roelforg on 2012-04-08
> **haqking said:**
> if you only look briefly at answers people give you then you wont get the results you want ;-)

the resetpassword link is simple and will help you reset any passwords you are having issues with.

and remember sudo/admin is different to root

+1

root is the most powerfull user on linux, whenever passwd stuff pops up i boot to root shell and use passwd to change the pass

---

### Post by bedpotato on 2012-04-08
> **haqking said:**
> if you only look briefly at answers people give you then you wont get the results you want ;-)

the resetpassword link is simple and will help you reset any passwords you are having issues with.

and remember sudo/admin is different to root

I don't think you quite understand what I am trying to say.

What I am trying to say is that, because I am a newbie and the people on this thread appear to be of the knowledgable, geeky variety, I don't understand the words you're using. 

Since I am English, if you sent me a link to a page in Greek or Russian, a brief look would be enough to establish that it will leave me none the wiser. 

Likewise, since I don't understood all the jargon in the links you've sent me, a brief look is enough to know that it will leave me none the wiser. :( Do you see what I am trying to say? 

I am not trying to sound ungrateful because I am grateful that you are trying to help me. Thank you. :) But I am a newbie. That's why I am posting in the newbie section.

Perhaps it would help if you could think back in your mind to the time before you knew anything about Linux or computers, and didn't know any of those words yourself yet. Then you will understand why I cannot follow your instructions. :(

"remember sudo/admin is different to root" 

sounds to my mind like: 

"remember ???????/>>>>>>>> is different to @@@."

---

### Post by roelforg on 2012-04-08
> **bedpotato said:**
> I don't think you quite understand what I am trying to say.

What I am trying to say is that, because I am a newbie and the people on this thread appear to be of the knowledgable, geeky variety, I don't understand the words you're using. 

Since I am English, if you sent me a link to a page in Greek or Russian, a brief look would be enough to establish that it will leave me none the wiser. 

Likewise, since I don't understood all the jargon in the links you've sent me, a brief look is enough to know that it will leave me none the wiser. :( Do you see what I am trying to say? 

I am not trying to sound ungrateful because I am grateful that you are trying to help me. Thank you. :) But I am a newbie. That's why I am posting in the newbie section.

Perhaps it would help if you could think back in your mind to the time before you knew anything about Linux or computers, and didn't know any of those words yourself yet. Then you will understand why I cannot follow your instructions. :(

"remember sudo/admin is different to root" 

sounds to my mind like: 

"remember ???????/>>>>>>>> is different to @@@."
me thinks you're a new arrival from windows.
So let me put it like this:
your normal user is like Administrator in win.
root's authority/power 1-ups that... by about 100 times.

---

### Post by Gone fishing on 2012-04-08
Haqking there is something I don't understand on my box dropping down to the root shell needs the admin password (hence the /bin/bash trick) and it has on other boxes I've used, but my sons doesn't. 

Do you know why?

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> I don't think you quite understand what I am trying to say.

What I am trying to say is that, because I am a newbie and the people on this thread appear to be of the knowledgable, geeky variety, I don't understand the words you're using. 

Since I am English, if you sent me a link to a page in Greek or Russian, a brief look would be enough to establish that it will leave me none the wiser. 

Likewise, since I don't understood all the jargon in the links you've sent me, a brief look is enough to know that it will leave me none the wiser. :( Do you see what I am trying to say? 

I am not trying to sound ungrateful because I am grateful that you are trying to help me. Thank you. :) But I am a newbie. That's why I am posting in the newbie section.

Perhaps it would help if you could think back in your mind to the time before you knew anything about Linux or computers, and didn't know any of those words yourself yet. Then you will understand why I cannot follow your instructions. :(

"remember sudo/admin is different to root" 

sounds to my mind like: 

"remember ???????/>>>>>>>> is different to @@@."

which words in the directions in the links dont you understand ? The guide is for newbies, it is step by step, just follow it.

And i explained the difference between sudo/admin and root in my first post

---

### Post by haqking on 2012-04-08
> **roelforg said:**
> me thinks you're a new arrival from windows.
So let me put it like this:
your normal user is like Administrator in win.
root's authority/power 1-ups that... by about 100 times.

mmmm yes and no.

on a windows box a administrator account is all powerful and there can be more than one.

on Linux there can be more than one admin but only one root, but the power difference between the root on linux and admin in windows are the same as they are equally powerful on there given system.

Root on linux cannot do anything more on a linux system than a administrator can on a windows system.

Peace

---

### Post by haqking on 2012-04-08
> **Gone fishing said:**
> Haqking there is something I don't understand on my box dropping down to the root shell needs the admin password (hence the /bin/bash trick) and it has on other boxes I've used, but my sons doesn't. 

Do you know why?

Ubuntu ? or other distro

and did you enable the root password at some point ?

---

### Post by roelforg on 2012-04-08
> **Gone fishing said:**
> Haqking there is something I don't understand on my box dropping down to the root shell needs the admin password (hence the /bin/bash trick) and it has on other boxes I've used, but my sons doesn't. 

Do you know why?

easy, the /bin/bash trick tells the kernel not to run init, instead run bash as init.
And since init is always ran as root, you bypass the auth.
That was the beginner version.
I also have a more technical one if you wanna hear it.

---

### Post by jps2012 on 2012-04-08
Bedpotato: There's a reasonably simple explanation of the password recovery command here (by A.P. Lawrence, a Unix/Linux consultant): 

[http://www.securitypronews.com/it/operatingsystems/spn-22-20040209LostRootPasswordLinux.html](http://www.securitypronews.com/it/operatingsystems/spn-22-20040209LostRootPasswordLinux.html)

I'm very new to the command line (and Ubuntu), and I know what you mean about being lost. Good luck.

---

### Post by Gone fishing on 2012-04-08
Sudo means superuser do - it gives the user, superuser or root privileges for a short period, when you need that authority (for example installing software). Root or superuser has that authority all the time and so it is a bad idea to run as root as you can break things accidentally. In Ubuntu the root account is not used, but admin users can use sudo - this is fine and safe just remember if you sudo or gksudo you have superuser privileges. In Ubuntu non admin users can't sudo and so they can't change the system.

haqking no I didn't give root a password and I'm using Ubuntu. Sorry roelforg you missed the point I know why init=/bin/bash works I don't understand why my box in recovery mode wont let you drop down to root without providing an admin password

---

### Post by roelforg on 2012-04-08
> **Gone fishing said:**
> Sudo means superuser do - it gives the user, superuser or root privileges for a short period, when you need that authority (for example installing software). Root or superuser has that authority all the time and so it is a bad idea to run as root as you can break things accidentally. In Ubuntu the root account is not used, but admin users can use sudo - this is fine and safe just remember if you sudo or gksudo you have superuser privileges. In Ubuntu non admin users can't sudo and so they can't change the system.

Technically root isn't disabled.
Cause that's not possible.
init is the first and only program the kernel starts on it's own after leaving the initrd (just ignore that last part if you don't know what the initrd is).
init is started as root (root has the same level of authority as the kernel) and init is expected to handle further launching of stuff and configuring the system.
The init= bootopt overrides the /sbin/init default and with the bash trick launches bash.
You are now seeing a root-shell.
gone fishing, you probably already know this, but it's to clarify for others and your post is a nice starting point.

---

### Post by bedpotato on 2012-04-08
Oh dear

*bangs head off wall*

I didn't mean "*please define all the jargon you use*"

I meant "*please do not use jargon at all*." 

This thread is about trying to regain access to my computer. Not a place for using strange words and then telling me what they mean. Learning new words will not fix my problem.

Thank you.

This is an "Absolute Beginner Talk" thread, so people please understand that I am an Absolute Beginner and word replies accordingly. Thank you. :)

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> Oh dear

*bangs head off wall*

I didn't mean "*please define all the jargon you use*"

I meant "*please do not use jargon at all*." 

This thread is about trying to regain access to my computer. Not a place for using strange words and then telling me what they mean. Learning new words will not fix my problem.

Thank you.

This is an "Absolute Beginner Talk" thread, so people please understand that I am an Absolute Beginner and word replies accordingly. Thank you. :)

Look no offence but you are not helping yourself here.

The fact is if you want to use Linux and you are new to it, you will need to learn it and that includes jargon.

Everything has a word/meaning and maybe something new to you.

BY your own admission you are new to Linux, that means you need to learn it, if you want to be given advice, or told how to do things or in words than you are not familiar with and dont want to learn then you wont get far learning your new system.

I again ask which part of the step by step process linked to is confusing and which words as you stated you didnt understand the words used.

Follow the guides and post back when you get stuck on a step/process or word/jargon.  

Thanks

---

### Post by Gone fishing on 2012-04-08
bedpotato do what Haqking said in his first post  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) and it will fix the problem. If for some strange reason it doesn't follow what I said in my first post and that will fix the problem.

---

### Post by roelforg on 2012-04-08
> **haqking said:**
> Look no offence but you are not helping yourself here.

The fact is if you want to use Linux and you are new to it, you will need to learn it and that includes jargon.

Everything has a word/meaning and maybe something new to you.

I again ask which part of the step by step process linked to is confusing and which words as you stated you didnt understand the words used.

Thanks
Haqking has a point,
whenever a beginner has a problem, i try to give them a solution and educate them in the process.
This entire page is filled with people explaing stuff to teach you something.

---

### Post by bedpotato on 2012-04-08
> **haqking said:**
> 

I again ask which part of the step by step process linked to is confusing and which words as you stated you didnt understand the words used.

Thanks

All of the Linux-related ones. 

As I already said in another way, if I don't speak Greek and you send me something in Greek, the words I don't understand will be "all the Greek ones."

No offence to you either, but I do not think you are putting yourself in the shoes of a "Complete Beginner" and this is a Complete Beginner sub-forum. I also have a mental disability so before lecturing me on learning new words please bear in mind my brain is, for some functions, about 8 years old and I have a low IQ. Even if that were not the case, as I already said, this is a forum for beginners. Harsh non-compassionate people need not reply to my thread, please. :(

---

### Post by roelforg on 2012-04-08
> **bedpotato said:**
> All of the Linux-related ones. 

As I already said in another way, if I don't speak Greek and you send me something in Greek, the words I don't understand will be "all the Greek ones."

No offence to you either, but I do not think you are putting yourself in the shoes of a "Complete Beginner" and this is a Complete Beginner sub-forum. I also have a mental disability so before lecturing me on learning new words please bear in mind my brain is, for some functions, about 8 years old and I have a low IQ. Even if that were not the case, as I already said, this is a forum for beginners. Harsh non-compassionate people need not reply to my thread, please. :(

The beginner forum serves as a place for linux newb's to ask questions, get answers, learn something new about their linux sys and ultimately grow to be advanced linux users.
If we don't teach, nobody would outgrow beginnerness. And if you want to be one, fine, but let us at least educate future visitors of this thread.

---

### Post by Gone fishing on 2012-04-08
click this link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) follow what it says if you have a problem post back

---

### Post by roelforg on 2012-04-08
> **Gone fishing said:**
> click this link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) follow what it says if you have a problem post back

i think that link has been posted like 3 times in this thread by now.

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> All of the Linux-related ones. 

As I already said in another way, if I don't speak Greek and you send me something in Greek, the words I don't understand will be "all the Greek ones."

No offence to you either, but I do not think you are putting yourself in the shoes of a "Complete Beginner" and this is a Complete Beginner sub-forum. I also have a mental disability so before lecturing me on learning new words please bear in mind my brain is, for some functions, about 8 years old and I have a low IQ. Even if that were not the case, as I already said, this is a forum for beginners. Harsh non-compassionate people need not reply to my thread, please. :(

well according to this thread where you posted

[http://ubuntuforums.org/showthread.php?t=1935163](http://ubuntuforums.org/showthread.php?t=1935163)

The words, Grub, Recovery mode, Sudo were all used by you so i still dont understand your difficulty.

I appreciate your learning difficulties.

But you need to follow the instructions and post back which part is not working or you dont understand rather than just repeating yourself about not understanding something you havent defined yet.

Cheers

---

### Post by winh8r on 2012-04-08
Okay guys, the OP has PM'ed me and the original problem is being resolved , 

Thanks to all who offered assistance.

---

### Post by coffeecat on 2012-04-08
@people, can you all give bedpotato some breathing space, please. You are all being very helpful and giving good advice, but there is too much detail for bedpotato and the cross-chat is simply providing background noise.

@bedpotato, the instructions you need are in the two links that haqking posted, but let me try to break this down to the essentials for you. As far as I can see, you&#8217;ve:

1 &#8211; removed your account from the admin group.

2 &#8211; Cannot assign a password to the new account.

Boot into recovery mode as described in the first link. Drop to a root shell as also described there. You will now be presented with  a &#8216;#&#8217; prompt which means that you have complete superuser (root) privileges. Be very careful not to make a typo. Run this command and press enter:

```
adduser bedpotato admin
```

I&#8217;m assuming that your main first account in Ubuntu is &#8220;bedpotato&#8221;. If it is not, substitute your username for bedpotato. That command will restore you to the admin group. You can now reboot into the GUI and use your first account to set the password on the second account. Or (from the second link):

```
passwd username
```

Substitute the username of the second account for &#8220;username&#8221; in that command. You will be required to enter the password twice and you will not see it being typed in, which can be disconcerting, but it is going in. Once you have finished in the recovery console you will want to reboot. Simply use this command (followed by enter):

```
reboot
```

**EDIT**: OK I see that this is being resolved. Thanks, winh8r, for posting that.

---

### Post by roelforg on 2012-04-08
> **coffeecat said:**
> @people, can you all give bedpotato some breathing space, please. You are all being very helpful and giving good advice, but there is too much detail for bedpotato and the cross-chat is simply providing background noise.

@bedpotato, the instructions you need are in the two links that haqking posted, but let me try to break this down to the essentials for you. As far as I can see, you’ve:

1 – removed your account from the admin group.

2 – Cannot assign a password to the new account.

Boot into recovery mode as described in the first link. Drop to a root shell as also described there. You will now be presented with  a ‘#’ prompt which means that you have complete superuser (root) privileges. Be very careful not to make a typo. Run this command and press enter:

```
adduser bedpotato admin
```

I’m assuming that your main first account in Ubuntu is “bedpotato”. If it is not, substitute your username for bedpotato. That command will restore you to the admin group. You can now reboot into the GUI and use your first account to set the password on the second account. Or (from the second link):

```
passwd username
```

Substitute the username of the second account for “username” in that command. You will be required to enter the password twice and you will not see it being typed in, which can be disconcerting, but it is going in. Once you have finished in the recovery console you will want to reboot. Simply use this command (followed by enter):

```
reboot
```

**EDIT**: OK I see that this is being resolved. Thanks, winh8r, for posting that.

Dude, you forgot the append flag for adduser, without it you get locked out of groups admin isn't member of and this can result in a hard time getting stuff to work again...

---

### Post by bedpotato on 2012-04-08
> **haqking said:**
> well according to this thread where you posted

[http://ubuntuforums.org/showthread.php?t=1935163](http://ubuntuforums.org/showthread.php?t=1935163)

The words, Grub, Recovery mode, Sudo were all used by you so i still dont understand your difficulty.

I appreciate your learning difficulties.

But you need to follow the instructions and post back which part is not working or you dont understand rather than just repeating yourself about not understanding something you havent defined yet.

Cheers

Do you always waste time looking through innocent people's posts to see if you can catch them out somehow? 

If you read the thread properly you will notice I was posting some instructions *sent to me by somebody else* (Winh8r) via PM. I made that perfectly clear and the instructions were quoted and all credit given to Winh8r. I did not write the instructions, and although I was able to carry them out, I still have no idea what those words mean. I just followed them blindly.

P.S. I did *not* say I had learning difficulties. I said I had a mental disability. If you do not know the difference you should not make wrong assumptions about terms you do not understand. That is never a good idea. Thank you. :)

Edit: thank you, Coffeecat! I can see you've posted some more helpful instructions too, so between you and Winh8r's ones maybe I can fix it, but I don't think I can handle reading any more for just now. I think my brain needs a rest or I might start to cry. Maybe I will try and fix it later. But, apart from helping me fix my problem, can somebody try to answer my question for me? I'm really perplexed and curious. While I don't want to learn all the new words, I would like to understand this one baffling thing: *how did the computer make up a password all by itself*? That is the funny question. I don't understand how this happened at all!

---

### Post by roelforg on 2012-04-08
> **bedpotato said:**
> Do you always waste time looking through innocent people's posts to see if you can catch them out somehow? 

If you read the thread properly you will notice I was posting some instructions *sent to me by somebody else* (Winh8r) via PM. I made that perfectly clear and the instructions were quoted and all credit given to Winh8r. I did not write the instructions, and although I was able to carry them out, I still have no idea what those words mean. I just followed them blindly.

P.S. I did *not* say I had learning difficulties. I said I had a mental disability. If you do not know the difference you should not make wrong assumptions about terms you do not understand. That is never a good idea. Thank you. :)

Edit: thank you, Coffeecat! I can see you've posted some more helpful instructions too, so between you and Winh8r's ones maybe I can fix it, but I don't think I can handle reading any more for just now. I think my brain needs a rest or I might start to cry. Maybe I will try and fix it later. But, apart from helping me fix my problem, can somebody try to answer my question for me? I'm really perplexed and curious. While I don't want to learn all the new words, I would like to understand this one baffling thing: *how did the computer make up a password all by itself*?
I'm confused, where did you post on winh8's behalf?
If it ain't here, i'm even more confused by your posts.

---

### Post by haqking on 2012-04-08
> **roelforg said:**
> I'm confused, where did you post on winh8's behalf?
If it ain't here, i'm even more confused by your posts.

he was referring to the link i posted about another thread.

Looks like this is getting resolved now so im out.

Peace

---

### Post by roelforg on 2012-04-08
> **haqking said:**
> he was referring to the link i posted about another thread.

Looks like this is getting resolved now so im out.

Peace

K, see you around!

---

### Post by bedpotato on 2012-04-08
> **roelforg said:**
> I'm confused, where did you post on winh8's behalf?
If it ain't here, i'm even more confused by your posts.

The thread that Haqking linked to. :)

Haqking, I am not a he, I am a she. :)

---

### Post by roelforg on 2012-04-08
> **bedpotato said:**
> The thread that Haqking linked to. :)

Haqking, I am not a he, I am a she. :)

:oops:

Sorry, it's just that in general posting is done by men.
Not sexism, just statistics.

---

### Post by roelforg on 2012-04-08
@bedpotatoe
What i still don't get is why you keep getting all worked up when someone posts a more indepth explaination.

---

### Post by haqking on 2012-04-08
> **bedpotato said:**
> The thread that Haqking linked to. :)

Haqking, I am not a he, I am a she. :)

 i always use the masculine, not due to sexism but as stated statistically or i go gender agnostic with OP instead.

Peace

---

### Post by bedpotato on 2012-04-08
It's OK Haqking, you weren't to know my gender! I normally tend to assume people on here are male, too. :)

> **roelforg said:**
> @bedpotatoe
What i still don't get is why you keep getting all worked up when someone posts a more indepth explaination.


Well, because I am autistic so I am very literal and make literal requests and replies. It is very frustrating for me when people misunderstand my words and do not take them literally. It's hard for an autistic person to understand why non-autistic people do that. ;)

I ask for things to be dumbed down and people reply using (what is, to me) advanced jargon. :confused:

That doesn't seem to make any sense. It's like asking for red and being given blue. Asking for coffee, and being given a Coke. It would make anyone frustrated, right?

Either they're not reading my request at all, or 

they're reading it and deliberately ignoring it because they want to look down on me and show off their superior knowledge, or 

they're under the impression that they're dumbing down, when in fact they aren't. 

I don't know. :confused: I try to look for all the logical possibilities and there don't seem to be many more than that. 

I can't understand people responding to me like this, because I wouldn't do it myself. I take things literally and follow instructions, so if I were replying to a thread on *my *specialist subject in which someone asked me to dumb down, I *would *dumb down. So I can't understand why others aren't doing so here. It makes me frustrated. I feel like shouting: *can't people read*? That's all. :) But I understand people are doing their best to help me, and it's kind of them to want to help me at all, so thank you. :)

---

### Post by winh8r on 2012-04-08
Just an update on the original issue posted by the OP.

After trying unsuccessfully to get the machine to boot to the GRUB MENU , 

the best option was to use the LIVE CD and chroot into the partition and 

modify permissions that way.

---

### Post by CharlesA on 2012-04-08
> **roelforg said:**
> Dude, you forgot the append flag for adduser, without it you get locked out of groups admin isn't member of and this can result in a hard time getting stuff to work again...
Just for the record, adduser just adds a user to whatever group you specify. There is no "append" option to it. You might be thinking of *usermod* though. ;)

```
root@Atlantis:~# useradd someuser
root@Atlantis:~# adduser someuser admin
Adding user `someuser' to group `admin' ...
Adding user someuser to group admin
Done.
root@Atlantis:~# adduser someuser sudo
Adding user `someuser' to group `sudo' ...
Adding user someuser to group sudo
Done.
root@Atlantis:~# grep someuser /etc/group
sudo:x:27:someuser
admin:x:111:charles,someuser
someuser:x:1001:

```

> **winh8r said:**
> Just an update on the original issue posted by the OP.

After trying unsuccessfully to get the machine to boot to the GRUB MENU , 

the best option was to use the LIVE CD and chroot into the partition and 

modify permissions that way.

I would have to agree. It's more of a pain in the butt to do it that way, but if they are unable to get to the GRUB menu in order to access recovery mode, that's pretty much what they will need to do.

---

### Post by bedpotato on 2012-04-09
It's now solved!  

Special thanks to clever winh8r for helping me behind the scenes and getting my admin access back by his helpful patient instructions! 

Also thank you to everyone who took the time to reply to this thread and take the time to try and help me. I am very grateful to you for trying, even though I can't quite understand some of the more advanced instructions yet.

Thank you everyone!

Bedpotato xx

---

