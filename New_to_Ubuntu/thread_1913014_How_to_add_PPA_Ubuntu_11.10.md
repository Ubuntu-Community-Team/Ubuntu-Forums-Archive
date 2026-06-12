---
title: "How to add PPA Ubuntu 11.10?"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by coldjeanz on 2012-01-21
I want to use this to switch my navigation arrows to the left side:

[http://ubuntuforums.org/showpost.php?p=11514552&postcount=9](http://ubuntuforums.org/showpost.php?p=11514552&postcount=9)

But it just says command not found when I do. What's wrong?

---

### Post by Double.J on 2012-01-21
Hi there, which of the commands returns the error?

Many thanks
:)

---

### Post by coldjeanz on 2012-01-21
Well I entered this in first

```
$ sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav

```

and it says command not found. can't even get to the other commands.

---

### Post by matt_symes on 2012-01-21
Hi

Open a terminal and copy and paste or type

```
dpkg -l python-software-properties
```

That is a small L after dpkg. Post the results back here.

Kind regards

---

### Post by Krytarik on 2012-01-21
> **coldjeanz said:**
> Well I entered this in first

```
$ sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav

```and it says command not found.
Although *matt_symes'* thinking makes sense too, it's much more likely that you just copy & paste the leading "$" and space with the actual command, right!? :D

Regards.

---

### Post by Double.J on 2012-01-21
> **Krytarik said:**
> Although *matt_symes* thinking makes sense too, it's much more likely that you just copy & paste the trailing "$" and space with the actual command, right!? :D

Regards.

Good catch Krytarik!

Coldjeanz - the command should start at "sudo" the "$" is to show that you're at a prompt :)

---

### Post by matt_symes on 2012-01-21
Hi

You may well be right there Krytarik. :)

@OP. Do you know the $ is a placeholder for the command prompt ?

So you would type in
[FONT=monospace]
[/FONT]```
sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav
```

without the leading $. The same for the other commands.

Kind regards

---

### Post by coldjeanz on 2012-01-21
You guys are right the $ thing was messing me up.

So I entered this in

```
sudo add-apt-repository ppa:iammuneeb/nautilus-leftnav
```

And it asked if I wanted to continue so I said yes. Then I put this in next

```
sudo apt-get update
```

Then it updated a bunch of stuff then I tried to put this:

```
sudo apt-get install nautilus
```

And it said nautilus already installed so nothing happened.

Anyway I logged out and logged back in and the navigation arrows are still on the right side. Did I do something wrong with the steps?

---

### Post by Krytarik on 2012-01-21
> **coldjeanz said:**
> Then it updated a bunch of stuff then I tried to put this:

```
sudo apt-get install nautilus
```And it said nautilus already installed so nothing happened.
That's right; you, and anyone else who has Nautilus already installed, need to "upgrade" it:
```
sudo apt-get upgrade
```

---

### Post by coldjeanz on 2012-01-21
Tried that and it says something about "0 to upgrade" "0 to remove" or something similar. 

Edit: It says nautilus already at newest version

---

### Post by Krytarik on 2012-01-21
> **coldjeanz said:**
> Tried that and it says something about "0 to upgrade" "0 to remove" or something similar. 

Edit: It says nautilus already at newest version
Hehe, that's because the version of Nautilus in the official repos has since outpaced those in that PPA :P :

[https://launchpad.net/~iammuneeb/+archive/nautilus-leftnav]("https://launchpad.net/%7Eiammuneeb/+archive/nautilus-leftnav")

Also considering its now older code base, I'd rather try following the instructions in this thread, there you can even add additional buttons, in a variety of setups :D :

[http://ubuntuforums.org/showthread.php?t=1904510](http://ubuntuforums.org/showthread.php?t=1904510)

---

### Post by anewguy on 2012-01-21
Also keep in mind that if you are using Unity, the default desktop in 11.04 and 11.10, the close, minimize and maximize buttons are hard coded to be on the left.  Unless something has drastically changed since the many, many threads on this since 11.04 and beta, etc., for 11.10, you will not be able to move them.

Dave ;)

---

### Post by Krytarik on 2012-01-21
> **anewguy said:**
> Also keep in mind that if you are using Unity, the default desktop in 11.04 and 11.10, the close, minimize and maximize buttons are hard coded to be on the left.
It's not about moving the window control buttons, but about moving the toolbar buttons of Nautilus. ;-)

---

