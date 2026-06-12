---
title: "Voodoo free JAVA"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by LazyTom on 2008-10-09
I have been going bats trying to get JRE on my system and hooked into Firefox. Every kind of method, procedure, or hint I have retrieved either doesn't work, points to missing pages, or has typos. The Firefox plugin finder dosen't.

I am an absolute Linux beginner who came here because Winbag is becoming a hopeless mess. I have worked on real operating systems and know one when I see one. I go clear back to BSD Unix 4.2. When I have time I will tweak and twunk like eveybody else. Right now I need certain things up NOW! My lame work PC is so bogged down that it takes 5 minutes to do anything. The Linux box runs rings around it(no surprise).

The machines I work with put food on my table and pay the rent. I can fool around later but not today.

I miss my old Berkley Vax (sigh)

---

### Post by ahsile on 2008-10-09
You should be able to get everything working correctly using these two commands. The sun-java6-bin package is the JRE, and the plugin package is for your browser.

You will be prompted to choose which java VM you would like to use by default after the update alternatives command. Just pick the number associated with the VM you would like to use by default (in my case I have Sun JRE5 and Sun JRE6... JRE6 (option 2) is my default.

```

sudo apt-get install sun-java6-bin sun-java6-plugin
sudo update-alternatives --config=java

```

---

### Post by LazyTom on 2008-10-09
hopk1954@hopkcpu-a:~$ sudo apt-get install sun-java6-bin sun-java6-plugin
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-bin
hopk1954@hopkcpu-a:~$

Here we go...again.

---

### Post by LowSky on 2008-10-09
```
sudo apt-get install ubuntu-restricted-extras
```

it installs java, flash, mstcorefonts and mp3 support all at once...enjoy

Oh I just forgot make sure you have all the repos enabled especially the multivers and universe repos.
here how to add them, its very easy
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by LazyTom on 2008-10-09
hopk1954@hopkcpu-a:~$ sudo apt-get install ubuntu-restricted-extras
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ubuntu-restricted-extras
hopk1954@hopkcpu-a:~$

---

### Post by Nepherte on 2008-10-09
> **LazyTom said:**
> hopk1954@hopkcpu-a:~$ sudo apt-get install sun-java6-bin sun-java6-plugin
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java6-bin
hopk1954@hopkcpu-a:~$

Here we go...again.
Be sure that you have enabled the multiverse repository (system > adminstration > software repositories). Then try this again:
```
sudo apt-get install sun-java6-bin sun-java6-plugin
sudo update-alternatives --config java
```

---

### Post by Therion on 2008-10-09
> **Nepherte said:**
> Be sure that you have enabled the multiverse repository (system > adminstration > software repositories). 
Definitely.  The errors you are receiving are clear indications you don't have all the repositories enabled.

[Graphical Guide](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html) to enabling Uni and Multi-verse repos in Hardy.

Bonus Edit: Might as well enable the [medibuntu repository](https://help.ubuntu.com/community/Medibuntu) as well!

---

### Post by LazyTom on 2008-10-09
OK, now we are getting somewhere. After enabling the repositories, before the apt-get would behave, I had to take a little side trip by the Synaptics Package Manager (discovered in another context), I installed the jdk, then did the apt-get which picked up the plugin. After that the update alternatives pointed out the correct Java, once I figured out there had been a minor syntax change. I figured I might as well put in all the Java stuff for future "debungling". Anyway Firefox and the apps are happy now.

The whole start of this thing was needing to run some router and network switch manager applications. It seems that everybody and his dog writes these in Java now.

From what I have read and seen, Linux is starting to get that "attic full of dusty trunks" air. At least I got here with less than a day of rummaging.

Guess I'll have to register my rattle, beads, and pig bladders now!

---

### Post by Therion on 2008-10-09
> **LazyTom said:**
> OK, now we are getting somewhere.
I've often thought what we need around here is a **Ten Things to do Immediately After Installing Ubuntu** that would be required reading for new install-ees.  The article would cover just such things as this: Things that 99% of your typical computer users are going to need but really isn't explicitly covered anywhere else, or least not in one place.  I think it would save a lot of frustration.  Maybe I'll write something up like that...

[Seems I've been beaten to the punch...](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

---

### Post by Big_Kahunaca on 2008-10-09
> **Therion said:**
> I've often thought what we need around here is a **Ten Things to do Immediately After Installing Ubuntu** that would be required reading for new install-ees.

I second this.  Perhaps we should compile one in this thread and submit it to the Powers That Be to turn it into a sticky.

Suggestions for "The List"?

---

### Post by SunnyRabbiera on 2008-10-09
> **Therion said:**
> I've often thought what we need around here is a **Ten Things to do Immediately After Installing Ubuntu** that would be required reading for new install-ees.  The article would cover just such things as this: Things that 99% of your typical computer users are going to need but really isn't explicitly covered anywhere else, or least not in one place.  I think it would save a lot of frustration.  Maybe I'll write something up like that...

Well we do have guides, but most of them are all over the place as you said.
We really need a help central providing graphical guides for newcomers.

---

### Post by mick222 on 2008-10-09
The sticky in multimedia covers just about every plugin you would ever need.
 Bye the way when you were in synaptic you could have just clicked on the ubuntu restricted extras and installed from there

---

### Post by Therion on 2008-10-09
> **mick222 said:**
> The sticky in multimedia covers just about every plugin you would ever need.
I'm somewhat experienced with Ubuntu and getting it up and running and some of those tut's scared ME (once I found a link to a link to a link that eventually drilled down to what I wanted, or would have had I been in need of it; if you get my point).

I was thinking more along the lines of something [like this](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html).  Short, sweet and not quite so overwhelmingly comprehensive.  Not too mention it should pinned to the "ABT" forum in particular.

> **mick222 said:**
>  Bye the way when you were in synaptic you could have just clicked on the ubuntu restricted extras and installed from there
We covered installing **ubuntu-restricted-extras** early on in this thread but that package is in the one of the repos the OP had yet to enable.  Hence the whole enabling the repo's approach.

If someone is interested in collaborating on such a project, PM me.

---

