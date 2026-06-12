---
title: "Ubuntu name"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Badoxide on 2008-08-19
Hello.To all

I was just wondering because a friend of mine installed ubuntu after seeing it on my laptop. He had all types of problems, so I had a look at his laptop I could not find a thing other then.

When he had done the install of ubuntu he used lets say Jerry as root name which he also used as a user name I reinstalled ubuntu and all problems were gone, so does anyone think that using his name, for both Root and User name may of had anything to do with all the problems he may have been having. ???

Thank you

Badoxide

---

### Post by ggaaron on 2008-08-19
Certainly renaming root user to Jerry could have had an impact on confused GNU system.

Seriously: no.

---

### Post by coffeecat on 2008-08-19
> **Badoxide said:**
> When he had done the install of ubuntu he used lets say Jerry as root name which he also used as a user name

I think you must be misunderstanding something here. You can't even set a root password during an Ubuntu install let alone call root something else. Is it even possible to give root the name Jerry, anyone? :-s

Do you mean that he set the hostname the same as his username? Or the password the same as his username? Whatever - I think you need to look for other reasons for the problems.

---

### Post by LowSky on 2008-08-19
> **Badoxide said:**
> Hello.To all

I was just wondering because a friend of mine installed ubuntu after seeing it on my laptop. He had all types of problems, so I had a look at his laptop I could not find a thing other then.

When he had done the install of ubuntu he used lets say Jerry as root name which he also used as a user name I reinstalled ubuntu and all problems were gone, so does anyone think that using his name, for both Root and User name may of had anything to do with all the problems he may have been having. ???

Thank you

Badoxide

Ok I have no idea what you are saying?

What problems did he have? Please explain...

Ubuntu does not give you an option to Set up a Root name when installing. It only has an option to set up the first account wich will have sudo access.

---

### Post by Badoxide on 2008-08-19
Hey.To all

Hm OK let me try this way when you do sudo whatever password what pops up on the Terminal @ say root@name.

Thank you

Badoxide

---

### Post by hotstovejer on 2008-08-19
It's username@computername

So what did his say?

---

### Post by Badoxide on 2008-08-19
Hi.hotstovejer

It was jerry@jerry were mine is say me@badoxide

Thank you

Badoxide

---

### Post by ggaaron on 2008-08-19
> **coffeecat said:**
> Is it even possible to give root the name Jerry, anyone? :-s

I don't think that this is possible, I've expressed it in my previous post=)

---

### Post by Badoxide on 2008-08-19
Hey.Guys

OK its true I am king of the Moron's I had not seen it before on my own ubuntu but mine is username@computername but the good thing is now I know where the would newbie comes from its, for people like myself.

But I had to ask to make sure, so I would not go and do the same thing sometime down the road. Sorry for taking up your time.

Thank you

King of the Moron's

---

### Post by zzHanks on 2008-08-19
Root is always root@computer_name, so I think you're misunderstanding something.

It is not recommended to use the root account as the main account.

---

### Post by Badoxide on 2008-08-19
Hi.zzHanks

OK I am lost, Yet again so are you saying that it should be root@Jerry or Jerry@Jerry I don't get it. This is why I asked in the first place.

NOTE: 

Just to be clear here I mean when you use the Terminal what should he have had is it root@Jerry or again Jerry@Jerry. ?
 
Thank you

Badoxide

---

### Post by t0p on 2008-08-19
> **Badoxide said:**
> Hi.zzHanks

OK I am lost, Yet again so are you saying that it should be root@Jerry or Jerry@Jerry I don't get it. This is why I asked in the first place.

NOTE: 

Just to be clear here I mean when you use the Terminal what should he have had is it root@Jerry or again Jerry@Jerry. ?
 
Thank you

Badoxide

*You're* lost?!  We're all confused cos we don't know what you are asking/saying!

Let me try to cut through the chaff:

If jerry's command prompt says

```
jerry@jerry
```

this means his **username** (the name he logs in with) and the **host name** (the name of the computer) are both jerry.  There is no reason why that would cause a problem.

When he uses the sudo command, the command prompt will not change.  It will remain jerry@jerry.

The exception to that is if he uses the command **sudo -s**, because that command invokes a root shell.  Then the command prompt *will* change to **root@jerry**, just as mine changes in this example below:

```
t0p@ubunty:~$ sudo -s
[sudo] password for t0p: 
root@ubunty:~# 

```

To sum up: having the username and hostname the same will not cause problems.  So that isn't what caused jerry's issues.

In Ubuntu, you never "change the root name".  Root's name is root.  And anyway, in a default Ubuntu set-up you never get to directly use the root account.  The closest you'll get is a root shell if you invoke the command **sudo -s**.

To reiterate:  Jerry can use his name as both username and host name without problems.

---

### Post by Jordanwb on 2008-08-19
> **t0p said:**
> *You're* lost?!  We're all confused cos we don't know what you are asking/saying!

Ditto.

> **t0p said:**
> To reiterate:  Jerry can use his name as both username and host name without problems.

It's a good thing you knew what the dude was asking.

---

### Post by coffeecat on 2008-08-19
> **ggaaron said:**
> We're all confused cos we don't know what you are asking/saying!

How do you think Jerry is feeling? :shock:

:lol:

---

### Post by Tux.Ice on 2008-08-19
Ive seen linux IT Managers install ubuntu desktop from the live cd and set the username of the first account created to root. This causes PROBLEMS.

---

### Post by Tux.Ice on 2008-08-19
IM going to take the guess that he is jerry.

---

### Post by ggaaron on 2008-08-19
> **Tux.Ice said:**
> Ive seen linux IT Managers install ubuntu desktop from the live cd and set the username of the first account created to root. This causes PROBLEMS.

How come? Isn't having two users with the same name impossible?

---

### Post by zzHanks on 2008-08-19
[quote=Badoxide]...Just to be clear here I mean when you use the Terminal [/quote]
I thought you had allowed local system administrator login and Jerry was using that account only.

This misunderstanding was a bit funny though :)

---

### Post by Badoxide on 2008-08-19
Hey.All

Alright first I asked the question not, so much to say ubuntu had started the problem my buddy was having. I just need to make sure encase someone else may have asked about installing it, so if that had been the problem to look out for it when doing the install.

**No I am not Jerry**.

**Sorry the English language is not my natural spoken one**.

Again all I was trying to find out is if he had Jerry@Jerry could this had been the start of his problems. But thanks to **t0p** I now know there is no way that had started all the head pain. It had to be a bad install on his part. But who cares he is running ubuntu now, and like myself loving it.

And may I ask what is dude.

@ zzHank ;)

To all of you thanks

Badoxide

---

### Post by AClark on 2008-08-19
That was the most fun I've had reading a post in a long time  :)

---

### Post by aysiu on 2008-08-19
Please don't use *sudo -s*, as that gives you a root prompt but uses the user's environment.

```
sudo -i
``` gives you a root prompt with root's environment - much less likely to cause problems.

---

### Post by Badoxide on 2008-08-20
Hi.aysiu

Thanks for the help and information. To some of you I don't see what the big thing is all about I am sure not all of you roll out of bed as an ubuntu king.

Yes I may have asked a stupid question, but I was under the impression that this forum was, for learning how to use or not use ubuntu, and to ask when not sure that is all. 

Thank you

Badoxide

---

### Post by jerome1232 on 2008-08-20
> **aysiu said:**
> Please don't use *sudo -s*, as that gives you a root prompt but uses the user's environment.

```
sudo -i
``` gives you a root prompt with root's environment - much less likely to cause problems.

I was about to ask what the difference between sudo -s and sudo -i was, now I know.

---

### Post by t0p on 2008-08-20
> **Badoxide said:**
> Hi.aysiu

Thanks for the help and information. To some of you I don't see what the big thing is all about I am sure not all of you roll out of bed as an ubuntu king.

Yes I may have asked a stupid question, but I was under the impression that this forum was, for learning how to use or not use ubuntu, and to ask when not sure that is all. 

Thank you

Badoxide

I don't think anyone was laughing *at* you.  Well, not in a bad way.  The community of this forum is the nicest and most helpful I've come across on the web.  New users are always welcome.

---

### Post by aysiu on 2008-08-20
> **jerome1232 said:**
> I was about to ask what the difference between sudo -s and sudo -i was, now I know.
Here are some more details: ```
username@ubuntu:~$ $HOME
bash: /home/username: is a directory
username@ubuntu:~$ sudo -s
[sudo] password for username:
root@ubuntu:~# $HOME
bash: /home/username: is a directory
root@ubuntu:~# exit
exit
username@ubuntu:~$ sudo -i
root@ubuntu:~# $HOME
-bash: /root: is a directory
root@ubuntu:~# 
```

---

### Post by Badoxide on 2008-08-20
Hi.All

@ aysiu

Wow thanks for this info.

@ t0p

Its alright I just have a lot of friends, and family who have seen me running ubuntu, and had asked where they can download it to install. I just don't want any of them to feel like they shouldn't be asking any questions. Or their be made to look dumb.

As for myself I am bigger then that. ;)

Thank you

Badoxide

---

