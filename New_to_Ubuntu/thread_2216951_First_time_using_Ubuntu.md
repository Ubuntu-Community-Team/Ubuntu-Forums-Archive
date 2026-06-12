---
title: "First time using Ubuntu"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by anumaz on 2014-04-14
Hey all,

After being disappointed with Windows for over 15 years, I made the switch to Ubuntu. But hey, that is nothing like Windows! Thus, I have a few questions. First thing I always did when I installed Windows on other computers was installing my drivers for my hardwares (sound card, video card, motherboard, etc.)

So...! How do I check if those are -already installed- (which I doubt as I didn't do that!), and how can I have a list of my hardwares so I know where to go to find them?

That's my first question. Others may follow.

Thank you,
Anthony Dupont

(It's a pleasure to join you guys! I've only heard good things about ubuntu and this forum.)

---

### Post by pfeiffep on 2014-04-14
> **anumaz said:**
> Hey all,

After being disappointed with Windows for over 15 years, I made the switch to Ubuntu. But hey, that is nothing like Windows! Thus, I have a few questions. First thing I always did when I installed Windows on other computers was installing my drivers for my hardwares (sound card, video card, motherboard, etc.)

So...! How do I check if those are -already installed- (which I doubt as I didn't do that!), and how can I have a list of my hardwares so I know where to go to find them?

That's my first question. Others may follow.

Thank you,
Anthony Dupont

(It's a pleasure to join you guys! I've only heard good things about ubuntu and this forum.)

Welcome to the forum!

There's a good possibility that your system functions just fine as MANY drivers are included. 
Are you using a live DVD / USB?
Does your system function as you expected?

---

### Post by anumaz on 2014-04-14
> **pfeiffep said:**
> Welcome to the forum!

There's a good possibility that your system functions just fine as MANY drivers are included. 
Are you using a live DVD / USB?
Does your system function as you expected?

Hi, and thanks!

It works fine, really. I have the sound working fine. I guess my motherboard works fine. I'm not too sure about the graphic card, though. I started a game and lagged a lot, just like a graphical bug.

No I do not have a live DVD / USB. I must find out (idk how) which one I have (I don't remember) and must install the drivers, I guess.

Anthony D.

---

### Post by anumaz on 2014-04-14
Just an addition to last post, I went into 'All Settings', then 'Details', then 'Graphics' and it says on the Driver line: "Unknown", and it says on the Experience line: "Standard"

---

### Post by 3rdalbum on 2014-04-14
A live DVD or a live USB is a DVD or USB that contains Ubuntu, that you can boot from. It's what you would have downloaded to try Ubuntu or to install Ubuntu.

If you want to play games you might need a better graphics driver. If you open up the Software Sources (Third Party Software And Updates) program you go to the last tab and Ubuntu will ask you to choose a graphics driver. Only if there is another one to choose, mind.

---

### Post by anumaz on 2014-04-14
> **3rdalbum said:**
> A live DVD or a live USB is a DVD or USB that contains Ubuntu, that you can boot from. It's what you would have downloaded to try Ubuntu or to install Ubuntu.

If you want to play games you might need a better graphics driver. If you open up the Software Sources (Third Party Software And Updates) program you go to the last tab and Ubuntu will ask you to choose a graphics driver. Only if there is another one to choose, mind.

Hi,

Sorry I did not understand. I installed Ubuntu completely, from a USB.

How do I open the 'Software Sources' ??

Anthony

---

### Post by pfeiffep on 2014-04-14
System Settings | Software and Updates

---

### Post by anumaz on 2014-04-14
> **pfeiffep said:**
> System Settings | Software and Updates

Hi,

I'm in 'System Settings' and I do not have that.

---

### Post by anumaz on 2014-04-14
Addition to last, I am in system settings and I have 'Addiitional Drivers'. Going to install what they say, heh.

---

### Post by Bashing-om on 2014-04-14
anumaz; Hi ! My Welcome also to the forum.

First, this ain't Windows - as you have said -.
Drivers:
When you installed the system the kernel checked out your hardware and installed all the drivers you need. There are cases where with graphics,  wifi, and printers drivers you "might" have to intervene.

To look at your hardware and related drivers (in linux, modules) there are GUI means but the Command Line Interface is universal:
From terminal:
# is a comment #
sudo = Super User DO to gain elevated privileges of administrative authority
```

sudo lshw #to see all your hardware
sudo lshw -C display # to see your graphics
sudo lshw -C Network # to see what you have 
lspci -vnn | grep -i VGA ##to see your graphics card
sudo dmidecode #too see all about your motherboard

```
and the list of commands extends to thousands, the trick here is not to know all these commands, but where to find the info when you need it. - As you use the system what you use will become readily available to mind. -

The manual to your rescue ! - it is on-board ! -
```

man man # for instruction and direction to use the linux manual
man -k <command> to search for suitable command application
man <command> for info on a command or an application
# for instance, gedit, the default text editor for ubuntu, do:
man gedit
# or a particular command and it's usage, do:
man ls

```
In your search - google is your friend .
See the links in my signature.

Welcome to our world, and yes there will be hundreds of questions, and a steep learning curve. All will attest well worth the effort.
Your questions are welcome, here the only dumb question is the one that is not asked.


Now that you have got your feet wet
[INDENT][INDENT][INDENT][INDENT]Jump in
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
> **Bashing-om said:**
> anumaz; Hi ! My Welcome also to the forum.

First, this ain't Windows - as you have said -.
Drivers:
When you installed the system the kernel checked out your hardware and installed all the drivers you need. There are cases where with graphics,  wifi, and printers drivers you "might" have to intervene.

To look at your hardware and related drivers (in linux, modules) there are GUI means but the Command Line Interface is universal:
From terminal:
# is a comment #
sudo = Super User DO to gain elevated privileges of administrative authority
```

sudo lshw #to see all your hardware
sudo lshw -C display # to see your graphics
sudo lshw -C Network # to see what you have 
lspci -vnn | grep -i VGA ##to see your graphics card
sudo dmidecode #too see all about your motherboard

```
and the list of commands extends to thousands, the trick here is not to know all these commands, but where to find the info when you need it. - As you use the system what you use will become readily available to mind. -

The manual to your rescue ! - it is on-board ! -
```

man man # for instruction and direction to use the linux manual
man -k <command> to search for suitable command application
man <command> for info on a command or an application
# for instance, gedit, the default text editor for ubuntu, do:
man gedit
# or a particular command and it's usage, do:
man ls

```
In your search - google is your friend .
See the links in my signature.

Welcome to our world, and yes there will be hundreds of questions, and a steep learning curve. All will attest well worth the effort.
Your questions are welcome, here the only dumb question is the one that is not asked.


Now that you have got your feet wet
[INDENT][INDENT][INDENT][INDENT]Jump in
[/INDENT][/INDENT][/INDENT][/INDENT]

What a warm welcome!

I appreciate this community is mature and ready to help newbies like me. I am now restarting my system to check if it installed drivers properly. Be right back!

Anthony D.

---

### Post by Bashing-om on 2014-04-14
anumaz;

Haw !

[INDENT][INDENT]we'll be here
[/INDENT][/INDENT]

---

### Post by anumaz on 2014-04-14
> **Bashing-om said:**
> anumaz; Hi ! My Welcome also to the forum.

First, this ain't Windows - as you have said -.
Drivers:
When you installed the system the kernel checked out your hardware and installed all the drivers you need. There are cases where with graphics,  wifi, and printers drivers you "might" have to intervene.

To look at your hardware and related drivers (in linux, modules) there are GUI means but the Command Line Interface is universal:
From terminal:
# is a comment #
sudo = Super User DO to gain elevated privileges of administrative authority
```

sudo lshw #to see all your hardware
sudo lshw -C display # to see your graphics
sudo lshw -C Network # to see what you have 
lspci -vnn | grep -i VGA ##to see your graphics card
sudo dmidecode #too see all about your motherboard

```
and the list of commands extends to thousands, the trick here is not to know all these commands, but where to find the info when you need it. - As you use the system what you use will become readily available to mind. -

The manual to your rescue ! - it is on-board ! -
```

man man # for instruction and direction to use the linux manual
man -k <command> to search for suitable command application
man <command> for info on a command or an application
# for instance, gedit, the default text editor for ubuntu, do:
man gedit
# or a particular command and it's usage, do:
man ls

```
In your search - google is your friend .
See the links in my signature.

Welcome to our world, and yes there will be hundreds of questions, and a steep learning curve. All will attest well worth the effort.
Your questions are welcome, here the only dumb question is the one that is not asked.


Now that you have got your feet wet
[INDENT][INDENT][INDENT][INDENT]Jump in
[/INDENT][/INDENT][/INDENT][/INDENT]

What a warm welcome! It worked!

Everything is fine now.

Thanks a ton!

---

