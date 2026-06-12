---
title: "Automated Package Installation Problem"
date: 2010-02-15
forum: Packaging and Compiling Programs
---

### Post by ShadyB_UK on 2010-02-15
Hey all.

Recently, I've been developing a hosting system with Ubuntu as a base, and is installed through one simple installer.

It asks you a couple of questions at the start, then configures the server, installs all the relevant software, and then installs a copy of my custom made control panel.

The purpose of this is automation - This is being deployed on many servers.
Everything is great, until it comes to MySQL.

Basically, when the script apt-get's MySQL, it comes up with a prompt asking you to enter a root password for MySQL. (blue background, dialog box).

I was wondering if there's any way to suppress this, and instead have the password set automatically using the mysqladmin command and the password I've put in at the start of the script.

It's the only thing that's been really bugging me, as apart from that, it requires no intervention at all.

Even if I can get it to enter a keystroke (enter) at the prompt, it would be good enough, but if there's a way to pass the password to the actual mysql installer, that would be brilliant.

Any suggestions?

Also, you may notice I'm new to the forums, but I've been a hardcore user of Ubuntu for many years :)

Thanks in advance,
Lee.

---

### Post by SevenMachines on 2010-02-16
hi,
$export DEBIAN_FRONTEND=noninteractive

would certainly work, the mysql-server will install without asking anything, does mean it has no root password though which you'd want to change afterwards. 
not entirely sure the best way to go about actually setting the password automatically too

---

### Post by ShadyB_UK on 2010-02-16
Thanks.

Do I just put that before the apt-get command for MySQL?

I can just use mysqladmin to set the password.

Will try this in a bit (away from the desk atm).

Thanks,
Lee.

---

### Post by SevenMachines on 2010-02-16
this would work
$sudo DEBIAN_FRONTEND=noninteractive  apt-get install mysql-server-5.1

if you dont want any interactivity with the rest of the packages installing i'm guessing exporting the variable before installing would probably work too

---

### Post by ShadyB_UK on 2010-02-19
Thankyou so much SevenMachines.

Everything worked as planned, so I can't thank you enough :)

---

