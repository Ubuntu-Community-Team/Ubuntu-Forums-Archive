---
title: "HOWTO Prevent a forkbomb attack"
date: 2007-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by puterboy on 2007-11-28
So there have been lots of warnings not to run a forkbomb code. 

[color=darkred]Edit: What is a for bomb you ask ?[/color] [http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

[color=darkred]Report fork bombs if you see them posted on the forums.

/Edit[/color]

**[size=2][color=red]EDIT: THIS SOLUTION DOES NOT WORK :( SEE :[/color]**[/size][http://ubuntuforums.org/showpost.php?p=3876330&postcount=32](http://ubuntuforums.org/showpost.php?p=3876330&postcount=32)

This did though : [http://ubuntuforums.org/showpost.php?p=3876483&postcount=33](http://ubuntuforums.org/showpost.php?p=3876483&postcount=33)

[COLOR=BLUE]just though you should know[/color] ~   [color=navy]bodhi.[/color][color=darkgray]zazen[/color]

The attack works by running a process that runs more copies of itself until your system crashes. Not a good thing. How can you protect yourseklf? Limit the number of processes you can run. So, run:

```
sudo nano /etc/security/limits.conf
```

Add this line:

```
*username* hard nproc 300
```

Save it, and you're protected!

---

### Post by XVII on 2007-11-28
Would that really protect you from a forkbomb attack or just limit the chances that you would get one?

---

### Post by diatribe on 2007-11-28
it limits the number of processes to 300, so therefore it will prevent a forkbomb from starting any processes past 300, getting one is up to you ;p

---

### Post by stealth17 on 2007-11-28
> **XVII said:**
> Would that really protect you from a forkbomb attack or just limit the chances that you would get one?

Looks to me like it would just keep it from completely crashing the system so you can at least have a chance to stop the attack

---

### Post by Dr Small on 2007-11-28
The fork bomb reminds me of Windows Key + E on Vista.. :D

---

### Post by XVII on 2007-11-28
> **Dr Small said:**
> The fork bomb reminds me of Windows Key + E on Vista.. :D

I did that to someone at school.  They got up to get something and they had 100+ windows when they came back.

Right click and close all FTW.

---

### Post by bodhi.zazen on 2007-11-28
LOL

Best way to prevent a fork bomb is **not to enter it in the terminal** :twisted:

@puterboy: I edited your post eliminating the code and replacing it with a link.

---

### Post by XVII on 2007-11-28
> **bodhi.zazen said:**
> LOL

Best way to prevent a fork bomb is **not to enter it in the terminal** :twisted:

I edited your post eliminating the code and replacing it with a link.

*How to Avoid a Fork Bomb for Dummies*.

---

### Post by FuturePilot on 2007-11-28
> **Dr Small said:**
> The fork bomb reminds me of Windows Key + E on Vista.. :D

Don't put any books on your keyboard :twisted: :lolflag:

Good How To though.

---

### Post by santiagoward2000 on 2007-11-28
> **Dr Small said:**
> The fork bomb reminds me of Windows Key + E on Vista.. :D

I don't have any Vista around to try it, and I couldn't find it on Google. What does it do?

---

### Post by puterboy on 2007-11-29
@bodhi.zazen - Thank you. Good idea. I was a little worried ppl might run it 

And yes, I agree the best thing is not to run it, but after being proven as a system crasher, i was more worried about viruses that run a forkbomb than people who run one in their terminal.

---

### Post by aaargh486 on 2007-11-29
> **santiagoward2000 said:**
> I don't have any Vista around to try it, and I couldn't find it on Google. What does it do?

It opens an instance of Windows Explorer. If you hold it for a couple of minutes, so many windows would have been spawned that it would completely lock up your PC.

---

### Post by bapoumba on 2007-11-29
[http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb](http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb)
[http://www.linuxquestions.org/questions/linux-security-4/how-can-i-prevent-forkbombs-338560/](http://www.linuxquestions.org/questions/linux-security-4/how-can-i-prevent-forkbombs-338560/)

---

### Post by santiagoward2000 on 2007-11-29
> **aaargh486 said:**
> It opens an instance of Windows Explorer. If you hold it for a couple of minutes, so many windows would have been spawned that it would completely lock up your PC.

HAHA! COOL! Too bad I don't have any pc with Vista at hand...

---

### Post by XVII on 2007-11-30
> **santiagoward2000 said:**
> HAHA! COOL! Too bad I don't have any pc with Vista at hand...

It works on all versions of Windows.

---

### Post by Vadi on 2007-11-30
I tried that on my friends vista. I held it down for ~10 seconds, the laptop was unresponsible for the next 2 mins, and then it simply shut down. Heh.

Anyway, hm, what are the chances of my legitimately running more than 300 processes?

---

### Post by jinx099 on 2007-11-30
So say you run this max processors command, and then you run a forkbomb.  What happens when the forkbomb reaches the max processes?  Does that prevent legitimate processes from running?  Seems like the forkbomb would turn into a DoS attack with that limitation.

---

### Post by raul_ on 2007-11-30
> **jinx099 said:**
> So say you run this max processors command, and then you run a forkbomb.  What happens when the forkbomb reaches the max processes?  Does that prevent legitimate processes from running?  Seems like the forkbomb would turn into a DoS attack with that limitation.

Yes, it prevents the user from launching more processes. But your computer won't be unusable.

---

### Post by XVII on 2007-11-30
> **raul_ said:**
> Yes, it prevents the user from launching more processes. But your computer won't be unusable.

It would be, partially.

---

### Post by raul_ on 2007-11-30
You could kill the processes by hand :) of course you would need another program to be launched, and you can't launch any more programs.:evil:

---

### Post by smartboyathome on 2007-12-01
you could switch to a virtual terminal though, right? And if so, what process(es) would you kill?

---

### Post by jinx099 on 2007-12-01
Isn't *kill* a process... a process that would not be able to run?!

---

### Post by raul_ on 2007-12-01
> **jinx099 said:**
> Isn't *kill* a process... a process that would not be able to run?!

my point exactly

---

### Post by XVII on 2007-12-01
> **jinx099 said:**
> Isn't *kill* a process... a process that would not be able to run?!

So this prevents the fork bomb and renders your computer useless?

---

### Post by raul_ on 2007-12-01
> **XVII said:**
> So this prevents the fork bomb and renders your computer useless?

Yes, that's why forkbombs are a pain in the ***. Still, you should be able to save your work before having to reboot

---

### Post by XVII on 2007-12-01
> **raul_ said:**
> Yes, that's why forkbombs are a pain in the ***. Still, you should be able to save your work before having to reboot

Yeah if the program to save it is already running, if not you're screwed.

---

### Post by raul_ on 2007-12-01
> **XVII said:**
> Yeah if the program to save it is already running, if not you're screwed.

:D nasty little trick isn't it?

---

### Post by XVII on 2007-12-01
> **raul_ said:**
> :D nasty little trick isn't it?

Yeah, looks like their really isn't an affective way to stop a forkbomb.

---

### Post by Vadi on 2007-12-01
Why can't we limit the number of copies of a process to x copies?

---

### Post by XVII on 2007-12-01
> **Vadi said:**
> Why can't we limit the number of copies of a process to x copies?

I think that's what this does.

---

### Post by raul_ on 2007-12-01
> **Vadi said:**
> Why can't we limit the number of copies of a process to x copies?

Because every process is a copy of another one. The way *nix systems create processes is by forks/execs:

a parent process forks itself, and is typically followed by exec(), that "tells" what code the child process should run. Of course this is all very vague.

The point is:

1- the fork bomb only creates copies of copies, so one process never has more than one copy.

2- if you do those kinds of limitations, you always prevent legitimate processes of being created

---

### Post by bodhi.zazen on 2007-12-02
[size=4][color=red]JUST A HEADS UP, THIS SOLUTION DOES NOT WORK[/COLOR][/SIZE]

He he he...

I was intrigued, so I decided to play with fork bombs .... (I used the first one posted here : [http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb) ; this is the same as originally posted here.)

I made the edit to /etc/security/limits.conf -> ran a fork bomb -> total system lockup

:lolflag:

=====================

OK, so second attempt, This time I brought in re-enforcements :twisted:

Made the edit to /etc/security/limits.conf , rebooted just to make sure the edit took 

1. ssh into box, sudo -i (to become root via ssh connection)

2. log into console 2 , sudo -i to become root on local console.

3. Start a root terminal in X

You would think that would be enough, 3 root access points

[size=2]FORK BOMB'S AWAY[/size]

Cool - An error message flashes by rapidly, too fast to catch.

The user who started to for bomb can not do anything.

The system is running  V E R Y ... S L O W

Root can do things ...

OK, lets try to stop this crazy process ...

[http://en.wikipedia.org/wiki/Fork_bomb#Difficulty_of_cure](http://en.wikipedia.org/wiki/Fork_bomb#Difficulty_of_cure)

OK, first of all the "problem" is the user who started the fork bomb has started hundreds(300 ?)  of processes, and they keep spawning ....

> :: fork failed: resource temporarily unavailablescrolls incessantly across the usres terminal .... :lolflag:

I tried several "do nothing" commands as root, no joy.

You can kill a process as root, still leaves 299 to go , and they re-spawn (that is the problem)

Eventually it locked .... When this happened, I could not change to the second console, the ssh session was terminated ....

====================

3rd try :

OK, this time I wondered if I could just telinit 1 (AKA single user mode ; AKA Recovery mode).

It took 15 seconds and the system eventually went to an init of 1 , and there it sat frozen ...

The ssh session remained open, but unresponsive.

The system sits at :

> Ubuntu login : _

One can not log in or enter commands

===================

Score :[color=red] Fork bomb: 3[/color] [color=blue]This "fix": 0[/color]

FYI: The fix to a fork bomb seems to be -> reboot

---

### Post by bodhi.zazen on 2007-12-02
> **bapoumba said:**
> [http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb](http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb)
[http://www.linuxquestions.org/questions/linux-security-4/how-can-i-prevent-forkbombs-338560/](http://www.linuxquestions.org/questions/linux-security-4/how-can-i-prevent-forkbombs-338560/)

Turns out this solution works, sort of ...

[http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb](http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb)

First, **don't run** ```
usermod -G untrusted [username]
```

If you do, your user will belong ONLY to untrusted.

Rather, edit /etc/group directly or run 

```
sudo adduser <username> untrusted
```

Second, a soft limit of 35 is too low, at that level a user can not log into gnome normally :

I set it to 50, but this was enough to allow the fork bomb to do it's thing :(

BUT, eventually it burns out (ie stops)
If you ssh in and, as the user who started the fork bomb, run 

```
kill -9 -1
```Which stops the fork bomb immediately, but logs you out (both of the gnome session and ssh).

**So, what worked** :

```
@untrusted      soft     nproc   50
```

I am sure there are other permutations, but I did not work through any more then the above. Also, the users may run into problems with limited resources, ie at 35 I could not log into gnome normally, so you may need to work through some if you want to further optimize this "fix"

/me" trusts" himself again.

HTH

---

### Post by nikoPSK on 2007-12-05
windows e opened windows explorer....:confused:

---

