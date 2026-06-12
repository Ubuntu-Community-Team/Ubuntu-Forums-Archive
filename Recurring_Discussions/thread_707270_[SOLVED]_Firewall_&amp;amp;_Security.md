---
title: "[SOLVED] Firewall &amp;amp; Security"
date: 2008-02-25
forum: Recurring Discussions
---

### Post by candive on 2008-02-25
Hi all,

I am trying to load a firewall "Firestarter" & antivirus if needed.
I have been going around in circles which I really do not enjoy.
I have tried to follow the help instructions but get nowhere. :confused:

Please help.
I would like to make Linux permanent!

Thank you.

---

### Post by sayakb on 2008-02-25
To install firestarter, just open a terminal, and type:

```
sudo apt-get install firestarter
```

Configuration for firestarter is very easy indeed. Also, Linux doesn't need an antivirus. If you want it anyhow, just visit [www.avast.com](www.avast.com) and download the deb package for avast antivirus. ClamAV is equally good.

PS: After you have installed avast, to run it, just type in avastgui at a terminal..

---

### Post by neurostu on 2008-02-25
for firestarter have you tried:
```
 sudo apt-get install firestarter 
```

As far as anti-virus what software are you trying to use?

---

### Post by seventhc on 2008-02-25
Ubuntu also already has a built in firewall, it's called iptables and unless you need to make any specific changes, you can just leave it as is. Firestarter just gives you a gui to work with, but by default iptables blocks all incoming traffic but allows your programs that need to connect to do so.

---

### Post by sayakb on 2008-02-25
> **seventhc said:**
> Ubuntu also already has a built in firewall, it's called iptables and unless you need to make any specific changes, you can just leave it as is. Firestarted just gives you a gui to work with, but by default iptables blocks all incoming traffic but allows your programs that need to connect to do so.

+1
With Linux, you need not worry about any firewall or antivirus. Remember, this is not Windows ;)

---

### Post by candive on 2008-02-25
Cool!

So if I have this right firestarter is a Grapic UI that manages the firewall that is already part of Gutsy.

Thank you, all.

Learning curve!!  :guitar:

---

### Post by seventhc on 2008-02-25
> **candive said:**
> Cool!

So if I have this right firestarter is a Grapic UI that manages the firewall that is already part of Gutsy.
Exactly. :)
Iptables would be configured using the terminal, firestarter lets you use a gui to do it.

---

### Post by neurostu on 2008-02-25
> With Linux, you need not worry about any firewall or antivirus. Remember, this is not Windows

Ok first of all, just b/c you are running linux doesn't mean your box is 100% secure. Security is something everybody should think about and implement.

Sure windows boxes are the major targets or attacks and linux boxes are for the most part ignored but I know **plenty** of people who have had their linux machines compromised.

If someone wants to setup a firewall GREAT for them. If someone wants to install anti-virus software even better, but it is unwise to say "Hey this is linux you don't need anti-virus or a firewall"  

Apple is currently having this problem as their user base is growing. For years they have sold themselves as the "more secure" option to windows.  Now the data is starting to show they Mac OS X has vulnerabilities and lots of them. Viruses are starting to show up written specifically for Mac.

If your running linux then the chances of having your machine attacked are much lower and the chances of those attacks actually succeeding are lower still but they still happen.

The reason why windows has been such a successful target is because its user base was security illiterate. All you had to do was compromise the windows code and you could get on 99% of the machine on the net. Its kind of funny but a few little security tweaks can prevent the majority of the windows attacks, as your machine no longer would fit the "cookie cutter" mold.

The linux community is growing very fast and if as a community we don't strive to maintain standards of security and move beyond the packaged security features then eventually we will be targeted by mainstream hackers.

Yes I agree that linux is more secure then windows but **everyone** should be concerned about the security of their machine.

---

### Post by sayakb on 2008-02-25
> **neurostu said:**
> Ok first of all, just b/c you are running linux doesn't mean your box is 100% secure. Security is something everybody should think about and implement.

Sure windows boxes are the major targets or attacks and linux boxes are for the most part ignored but I know **plenty** of people who have had their linux machines compromised.

If someone wants to setup a firewall GREAT for them. If someone wants to install anti-virus software even better, but it is unwise to say "Hey this is linux you don't need anti-virus or a firewall"  

Apple is currently having this problem as their user base is growing. For years they have sold themselves as the "more secure" option to windows.  Now the data is starting to show they Mac OS X has vulnerabilities and lots of them. Viruses are starting to show up written specifically for Mac.

If your running linux then the chances of having your machine attacked are much lower and the chances of those attacks actually succeeding are lower still but they still happen.

The reason why windows has been such a successful target is because its user base was security illiterate. All you had to do was compromise the windows code and you could get on 99% of the machine on the net. Its kind of funny but a few little security tweaks can prevent the majority of the windows attacks, as your machine no longer would fit the "cookie cutter" mold.

The linux community is growing very fast and if as a community we don't strive to maintain standards of security and move beyond the packaged security features then eventually we will be targeted by mainstream hackers.

Yes I agree that linux is more secure then windows but **everyone** should be concerned about the security of their machine.

But is there any antivirus that provides active protection yet? I am using avast, but it doesnt have any autoprotect options (like it has under Windows)

---

### Post by neurostu on 2008-02-25
I'm not aware of any. Aside from what I said above I personally think that autopretect is a little overkill (it takes a TON of resources). 

Again just tweaking your machine from the norm will block 99% of the attacks. Things like:
 - closing up unused ports
 - Watching what programs you install
 - Only installing from trusted sites
 - Blocking scripts in your web browser
 - keeping your browser up to date .

  Should really be enough to block most attacks, Then run anti-virus scans every night when you go to bed. you can even set up CRON jobs to run the scans for you everynight.  

You don't have to be a security nazi, just do your best to educate yourself and take active steps to ensure your machine is protected.

---

### Post by candive on 2008-02-25
Correct me if I'm wrong.

Cracker = Bad, Black Hat.
Hacker = Good, White Hat.

With the knowledge required for Linux, I figure there are lots of Hackers here.
And yes the other.

Fire starter done.

Thank you very much!! :)

.

---

### Post by seventhc on 2008-02-25
I don't think anyone here was saying not to care about security, but there is a built in firewall with a good configuration out of the box.
As for AV I think there are no known viruses in the wild at this time, even if a virus did infect your machine it wouldn't be able to get root permissions to do any real damage. Of course it could wreak havoc in your home directory( I have mine backed up).
I used to use clam av and scanned my machine it always showed 0 found, so I did stop using it.
As far as any av's that uses autoprotect, I am not sure. My guess is, if a virus was released that effected ubuntu it would be so new that even autoprotect might not protect agains it until the next update.
I encourage people to keep security in mind, but as for av goes, there just aren't enough known issues out there yet.
I do however think that if you trade files back and forth between other windows users it would be good to use so you don't unknowingly send them something that may be infected.
It all comes down to opinion in this area, some people use it and some don't.
As I stated earlier I did use it, but never found anything, so at that point I decided not to use to just to save resources.
Most virus writers will write them for windows since it has such a large user base, and it won't need root permissions.
As an example if you open notepad...you can write about 3 or 4 lines of code...save it as a batch file. If you double click on it, next time you reboot, xp will be gone. I have done this on my own machine.
So it doesn't take much to hurt windows.

---

### Post by seventhc on 2008-02-25
No box is 100%, secure if it's on the net, it's at risk. The only secure machine is one that is not connected and preferably turned off, 1000 miles from the nearest civilization. But that doesn't make for a very fun computing experience now, does it. lol

---

### Post by neurostu on 2008-02-25
> 1000 miles from the nearest civilization

Oh man... I can't even begin to image what kind of bugs you'd face in those circumstances. You're box would probably be swarming bugs: ants, beatles, moths,  maybe even a scorpion or two...

---

### Post by saxuntu on 2008-02-25
I read an article recently that said linux machines are being compromised by rootkits and botnets at an alarming rate. I know rkhunter and chkrootkit take care of rootkits, but what about botnets? Any type of scanner or extra precaution to take with them?

---

### Post by seventhc on 2008-02-25
> **neurostu said:**
> Oh man... I can't even begin to image what kind of bugs you'd face in those circumstances. You're box would probably be swarming bugs: ants, beatles, moths,  maybe even a scorpion or two...
Thats why I had leave it there :(

---

### Post by -Phoenix- on 2008-02-25
> Cracker = Bad, Black Hat.
Hacker = Good, White Hat.

Not exactly.  Hackers are typically taking over computers (through known vulnerabilities), crackers are trying to figure out passwords.

White hat/Black hat is a philosophy.  Kind of like Light side/Dark side, though they can both wield the force.   :twisted:

---

### Post by candive on 2008-02-25
Only I could crash a firewall as soon as I open it.
I kept hitting next.
Firewall status Disabled.
It says to check my connection, so how is it I am posting?

---

### Post by candive on 2008-02-25
GOT IT !!:guitar:

---

### Post by seventhc on 2008-02-25
The true meaning of the word hacker doesn't have any bad conotations to it, it's news and media that gave it a bad name.
[http://en.wikipedia.org/wiki/Hacker_definition_controversy](http://en.wikipedia.org/wiki/Hacker_definition_controversy)

---

### Post by jbalazs on 2008-02-25
Test your firewall here it's works great 

[http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/)

---

### Post by candive on 2008-02-25
How did I get here? again!
I crashed windows by running an optimize HDD.  :lolflag:

Windows & Optimize obviously a conflict in terms!

---

### Post by aev on 2008-02-25
> **LinuxIsInnovation said:**
> +1
With Linux, you need not worry about any firewall or antivirus. Remember, this is not Windows ;)

our server just got hacked plus several linux boxes different flavours. Always good to have more defenses.

---

