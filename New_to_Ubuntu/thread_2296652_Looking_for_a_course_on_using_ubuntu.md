---
title: "Looking for a course on using ubuntu"
date: 2015-09-27
forum: New to Ubuntu
---

### Post by noob5 on 2015-09-27
Hi,
I am a complete noob regarding computers but from what I have read I feel Ubuntu is the way I would like to go regarding what OS I would like to use.
I am currently in Ljubljana and should be here for about a year and will have time on my hands and would like to put that time to use by getting some computer experience.
I have tried setting up an account on the Slovenian forum but not getting any joy so I have decided to post on here,maybe someone can point me in the right direction.
I would like to know if there is any kind of a course that i could do on Ubuntu or if there was anybody willing to help me with the basics,someone patient as I am not the brightest around a computer but am willing to learn,Any help would be greatly appreciated,):P

---

### Post by tgalati4 on 2015-09-27
Welcome to the forums.  Your English is excellent, so why not ask your questions here.  Click on [Popular Pages]("http://https://help.ubuntu.com/community/PopularPages") and glance at the topics--read, do, and ask questions.  What are your computer interests?

If you have Ubuntu installed on a computer, open a terminal and post the following:

```
cat /etc/issue
lsb_release -a
uname -a
```

After 10,000 posts, you will be an expert.

---

### Post by ajgreeny on 2015-09-27
I do not know of any training courses personally, but the best way to learn is just to use Ubuntu and keep trying to do things.

If you want a written guide there is a good one at [http://ubuntuguide.org/wiki/Ubuntu:Trusty](http://ubuntuguide.org/wiki/Ubuntu:Trusty) (assumes you are using 14.04 with the unity desktop; the one with a launchbar on the left side of the screen).

---

### Post by PaulW2U on 2015-09-27
Hi noob5, welcome to the Ubuntu Forums.

I can't help with Ubuntu courses but I'm sure that a web search will bring up a large number although whether they are suitable is another matter.

Personally I would recommend first downloading [Getting Started with Ubuntu 14.04e2]("http://ubuntu-manual.org/?lang=en_GB"). It's free, quite detailed and includes many illustrations and screenshots. It's written specifically for users that are new to Ubuntu.

You could also search YouTube for whatever you need. There are many demonstrations and tutorials available. I just searched for "install ubuntu software" and found almost 600,000 results. Searching for "How to install Ubuntu 14.04" gave me over 6,000 results. I'm sure many of those would be of use to you and be the next best thing to a course.

I hope that's given you some ideas.

---

### Post by J_R._Bahena on 2015-09-27
When I first started to use Ubuntu I kept a notes file of commands I used over the course of having Ubuntu. Here are some commands I have in my notes:
To update and upgrade system, respectfully:
```
 sudo apt-get update && sudo apt-get upgrade
```

To install a program (if you get used to using the command line everything will make more sense, try to stay away from ubuntu software center and use it unless all fails.)
```
 sudo apt-get install <name-of-program> 
```

To add a ppa
```
 sudo add-apt-repository ppa:<name-of-ppa> 
```

Most of all, read the documentation and google any question to find your answer.

---

### Post by Geoffrey_Arndt on 2015-09-28
Another way to learn Ubuntu is all the online video tutorials:

To start, watch a few of these on youtube:   [https://www.youtube.com/results?search_query=learn+ubuntu+for+beginners](https://www.youtube.com/results?search_query=learn+ubuntu+for+beginners)

---

### Post by Bucky Ball on 2015-09-28
> **J_R._Bahena said:**
> 
To update and upgrade system, respectfully:
```
 sudo apt-get update && sudo apt-get upgrade
```

Do you mean respectively? :)

You should also include:

```
sudo apt-get dist-upgrade
```

> **J_R._Bahena said:**
> ... try to stay away from ubuntu software center and use it unless all fails.

Why? It is nothing but a pretty front end GUI for apt. It works exactly the same as 'apt-get install' in a terminal. So does Synaptics.

> **J_R._Bahena said:**
> To add a ppa
```
 sudo add-apt-repository ppa:<name-of-ppa> 
```

Rather than avoiding Software Centre (which I don't use myself, incidentally, but not for any reason given here) you should try and avoid installing third-party PPAs and stick to what's in the repositories. 

Installing unknown, untested, unsupported PPAs is a major cause of self-inflicted breakage and can be diabolical if not disabled or removed prior to upgrading the OS to a newer version online. Avoid unless you've done some research and know the PPA you're about to install is to some degree reliable (popular, well-known, lots of people using it). Despite all reassurances, a PPA server can die at any time, the PPA can stop being maintained at any time (and you generally won't know this until you try to update and get an error which many new comers then spend an hour to a couple of days trying to figure out).

As for learning Ubuntu: install, use, research, ask questions if you're unsure or when you hit a brickwall. It is best if you have project in mind, something you want to do with the machine, then go about working out how to do it. 

Good luck, enjoy the learning curve, the forums and the OS. :)

---

### Post by noob5 on 2015-09-28
Hi,
Thx for the reply,
I am Irish,guess that is why my English is good lol.
Only joking but thx for your imput.
Bye
):P

---

### Post by noob5 on 2015-09-28
Thx for reply
):P

---

### Post by tgalati4 on 2015-09-28
My ignorance in geography.  I thought Ljubljana was in Kazakhstan or some other *stan. It is the capital of Slovenia.  I didn't know that Slovenians spoke Irish. ):P  Anyway, good luck on your journey.  You have plenty to study now.

---

### Post by ra7411 on 2015-09-28
There are a number of good youtube vids on using Ubuntu.
Start with Joe Collins and Jay LaCroix.

---

