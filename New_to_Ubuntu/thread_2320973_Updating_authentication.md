---
title: "Updating authentication"
date: 2016-04-19
forum: New to Ubuntu
---

### Post by oleandra on 2016-04-19
I have the Software Updater appearing & can't update anything as my password "fails".
Since I joined I've been trying to post for help & have lately got a mail saying that I might have signed in to Ubuntu One (which is the case) & that I was to post to the Resolution Center for the password problem.

Now you'll understand my level of expertise LoL.
I signed in to Ubuntu One because I saw that it was the right place to sign in to everything with the same password. And I have used exactly the same one. Also I only have one mail address.
I finally managed to post my SOS - and - it was received by the Admin Team ... and it's from the link they provided that I've managed to get back in here.

The other problem is that videos in Facebook don't work - nor in the Orange News Page (Orange is my provider [I live in France]). I get various messages either telling me to change browser or I get a link to download Flash Player. I've tried many times to download Flash - I even found it in the Download file to install it - but videos still won't work - so I have to go to the W7 side for that. 
But not only - the main reason being my WikMail which I don't want to lose - I've made many backgrounds in there & want to keep them. I finally came across the Ubuntu Manual & saw that Windows apps can work with Wine just that the last time I typed codes was way back when GML was used ... and that was under OS/2 - way before Windows ... 

I'm just a good user once I've got the hang of things & though retired now - I still like to make my own tags & cards. And this time it's not just an upgrade to learn ... so my brains get confused between Ubuntu, Mozilla & Thunderbird - in English in here - & in French in W7 ... I finally did go to get a glass of wine - but to get in WikMail in W7 where it works ... LoL

Once I've got everything working in Ubuntu - I want to uninstall Windows - so I'll have more room on the hard drive - but for now it's a lot of brainstorming ! :confused:

Thanks for the info/help/tips you can give me

Oleandra

---

### Post by grahammechanical on 2016-04-19
Please. One problem at a time. A thread can get very confusing if we are expected to offer advice of more than one issue. Right now, I see at least 4 subjects and I am, not sure which ones have been solved, which are pending or which are information only requests.

Are you still having problems updating the OS? Most times Software Updater - Update manager will run without us needing to authenticate. Upgrades to certain packages that change the OS do prompt a Dialog asking us to authenticate the action. I notice that this happens if the upgrade involves a kernel upgrade or an upgrade to the Grub boot loader. But most of the time my update/upgrades run without me needing to authenticate the action. And my user password is sufficient when I do need to authenticate.

Ubuntu One or Single Sign On is something different. Having one of these Ubuntu One accounts will allow us to easily register and log in to certain Ubuntu web sites such as the Ubuntu forums, AskUbuntu, Launchpad (were we can report bugs), the Ubuntu Online Summit. Those who use a Ubuntu phone or tablet will also use their Ubuntu One account to access the phone/tablet app store.

I do not think it is a good idea to have the same user name & password for our Ubuntu One account as for our OS login. I certainly keep these things different.

Flash? I have installed Google Chrome. Most of the time I use Firefox. But I decided a while back to no longer use the flashpluging installer and use Chrome for those times I want to access online video playback. Such as BBC iplayer or ITV iplayer (TV channels to all you in the rest of the world) or Ubuntu On Air which I will be watching in a couple of hours because there is a Ubuntu Community Q&A taking place. We can ask questions.

Oh. Ubuntu is the Linux distribution we are using. Mozilla is the software foundation that develops the Firefox web browser. Thunderbird is an email client which is also developed by Mozilla. 

Regards.

---

### Post by oleandra on 2016-04-19
Well I still have the Software Updater in the vertical bar highlighted  because I didn't open it till my password problem is sorted out. I'll change passwords when I'll have access - but I've not noticed when I sign in for OS - (Operating System) ? Yes, I have to learn a new language.

I've always used the Family/students version of Windows & the Office - my technical knowledge is limited to the use of that.

I  went to Launchpad to try to close my account down - but I don't have  access to that - but when I signed on in there I thought I was in Ubuntu  One ...
So my problem is still at the same point - plus I'm confused  now because I thought when that button showed up I had to action it & it's showed up very regularly - just I didn't have any info for the first steps in Ubuntu so I must have made many mistakes clicking everywhere trying to work things out ...

OK - I've taken note that I have to install Chrome - so the videos should work.

And I'll open another thread for my Wine/WikMail problem.

Sorry for having mixed everything up - what I should have specified is that I need to know what to do/where to go for each problem.

So the problems for [COLOR=#0000cd]this thread[/COLOR] are linked because I can't validate the update (I'm asked to do it) because I was told to use the link that brought in me here to fix the password one before.

I hope I've got it right this time.

Thanks for your patience - as you see I'm quite lost for the time being.

---

### Post by Bucky Ball on 2016-04-19
Welcome. Could you open a terminal please and paste these commands, one at a time, hitting enter after each.
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Please post any errors you receive here between code tags (see the green link in my signature below for how to use them).

PS: And yes, one issue per thread and thread titles describing the problem, please. This will greatly improve your chances of support. Good luck. ;)

---

### Post by oleandra on 2016-04-19
I messed it up on the very 1st screen & didn't see it - "sudi" instead of "sudo"... then on the 3rd "upgrade" instead of "dist-upgrade".  I was asked for my password that obviously wasn't accepted.
```
[IMG]sudo autoremove 1 2016-04-19 20:58.png[/IMG]
[IMG]Sudo update 1 2016-04-19 21:01.png[/IMG]
[IMG]sudo upgrade 1 2016-04-19 21:04:00.png[/IMG]
```

After that I did a restart before trying again & though I was sure of my "sudo" spelling the password was refused from the start
```
[IMG]autoremove 2016-04-19 23:00:50.png[/IMG]
[IMG]update 2016-04-19 23:04:49.png[/IMG]
[IMG]dist-upgrade 2016-04-19 23:08:14.png[/IMG]
```

I hope this coded send has worked - it's my first try at this ... 

I'll be back tomorrow to see what you suggest to "repair" these errors of mine.
Looks like I'm learning the hard way ... but learning just the same.

I'll send the other threads when I've finished with this one - I don't want  to mix things up & make it difficult for everyone.

Thanks for your help

---

### Post by oldos2er on 2016-04-19
You need to just copy and paste the terminal output from those commands into a post here, rather than trying to capture an image.

---

### Post by oleandra on 2016-04-20
This is what I get when I try copy/paste from the terminal - I can't paste anything in there either.


[COLOR=#0000ff]```
[/COLOR][COLOR=#0000ff]sudo apt-get autoremove[/COLOR][COLOR=#0000ff]
```[/COLOR]

I can crop the captures to isolate the terminal if that can help. Anyway - when I click enter after the command I'm asked for my password that is refused systematically. If I retry - I'm warned that I've already tried twice ...

---

### Post by Impavidus on 2016-04-20
To copy from the terminal to the web browser: Select the text with your mouse, right click, click "copy". Go to the web browser and paste in whathever way you're used to. To copy from the browser to the terminal: Select the text in the browser, copy in whatever way you're used to, go to the terminal, right click, click "paste" (or whatever it says in your language). Copy and paste in the terminal doesn't work with ctrl-X, ctrl-C, ctrl-V.

---

### Post by oleandra on 2016-04-20
Hmmm - I was using my bad habits ... Now it works - thanks for the info. Here is what I get :

[COLOR=#0000cd]```
[/COLOR]oleandra@oleandra-K70AF:~$ sudo apt-get autoremove
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
sudo: 3 incorrect password attempts
oleandra@oleandra-K70AF:~$[COLOR=#0000cd]

[/COLOR]oleandra@oleandra-K70AF:~$ sudo apt-get update
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
sudo: 3 incorrect password attempts
oleandra@oleandra-K70AF:~$[COLOR=#0000cd]
[/COLOR]
 oleandra@oleandra-K70AF:~$ sudo apt-get dist-upgrade
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
[sudo] password for oleandra: 
Sorry, try again.
sudo: 3 incorrect password attempts
oleandra@oleandra-K70AF:~$[COLOR=#0000cd]
```[/COLOR]

---

### Post by oleandra on 2016-04-20
I've been thinking about what [COLOR=#0000cd]grahammechanical[/COLOR] told me about passwords.
 Actually even my email address is the same for all the email systems I have. 
That always baffled me (but it was easier & I had no problems) - maybe it is this causing all the trouble now ?
It's Orange & Thunderbird (in French) and Wikmail in W7 - and Thunderbird in here till (if I can) get WikMail in. Orange I can use in here too (it stays in French).

Also when I open Facebook in here - & later in W7 - I have Facebook asking me to confirm if it was me in the other domain - & it does it for every logon.
 
I thought this info could help ...

---

### Post by oleandra on 2016-04-21
Seeing everyone thinks that I must have used a different address or password for Ubuntu One - and I'm not saying you are wrong - just that it can't be that because the addresses and passwords are all identical.
The  only thing I can think of is that somewhere in the "program" it was  another email client that was chosen compared to the one used before.  This really baffled me as before we were told that the name was already  in use & each email client had it's own name after @. 

This crossed my mind while I was writing in the Resolution Centre so they could direct me where to go to get this password problem fixed.

Hope it's helpful in here. I'd so much love to be operational ...

---

### Post by Impavidus on 2016-04-21
I see a lot of password confusion...

Whatever you've set your passwords to, it is clear from the error message from sudo that the password for your account in Ubuntu on your own computer (not on Ubuntu One) is not what you think it is. [Here is a tutorial]("http://www.psychocats.net/ubuntu/resetpassword") to reset the password on your computer. This will reset the password you use to login to your desktop and for sudo. You may have configured your computer for automatic logic (I think you did), in which case you don't need a password to login to your desktop, but that password still exists. Resetting your password using this tutorial will not affect any other passwords, like Ubuntu One. You will still be able to login here on the forum using the same password you used yesterday. Then sudo should work again.

Your email has nothing to do with this. The password you use for sudo is completely unrelated to anything having to do with email or Ubuntu One. You may have set it to the same thing, but they are independent.

=====

You can use the same password and usernames for different accounts. It has one advantage: it's easier to memorise so you're less tempted to use a password that's too easy. But, maybe apart from accounts that are really unimportant, it's better to use different passwords for everything.

Consider this: Some website where you have an account, facebook or Ubuntu One for example, has a security breach. A hacker has stolen the file with the hashed passwords. If that website used an outdated, unsafe hash function, the hacker can crack your password. If your password is weak, he can brute-force it in an off-line attack, which is far more likely to succeed in a reasonable time than using an on-line attack. In any case, the hacker may get your password. Hackers know that some people use the same password for everything, so the hacker will try this and suddenly hack all your accounts at once.

---

### Post by oleandra on 2016-04-21
Thank you so much for this info I'll be reading the "how to" very carefully & hopefully get things right.

I bought this desktop 6 years ago & honestly I can't remember what I did - as I wasn't really happy with W7 being so different to XP. I'm a good user when I get the hang of things - but out of email & Office - I'm like on a raft in the middle of nowhere. I think that my reasoning on the subject showed my level in this art ... 

I'll let you know what happened.

Thanks again 

Oleandra

---

