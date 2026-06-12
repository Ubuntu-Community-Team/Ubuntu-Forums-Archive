---
title: "Amarok is not working. At all"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by mmejanvier on 2008-04-30
So let's just break it down:

I have a linux

I am an idiot

My amarok quit working

I can't use my ipod now

Life has no meaning

When I try to start amarok, this is says some gibberish about:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.

etc.

PFFfffffffffffffffffffft!!!!

---

### Post by Ek0nomik on 2008-04-30
This may help you:  [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/149936](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/149936)

I know it looks daunting, but just follow some of the steps people provide towards the end of the web page.  It looks as though most people got it working.

I would look at what tbrier wrote as well as the people talking about user groups.  It looks as though it's database related.

If this sounds a little too daunting, perhaps I would try completely removing Amarok, along with the database (sqlite), and reinstalling.

---

### Post by mmejanvier on 2008-04-30
I was hoping for something a little more step-by-step

Really don't know how to do any of those things. 

Um

But thanks for trying to help. I think it's time to just get a different computer.

All I want to do is use my stoopid ipod, and I can't do it.

---

### Post by hermes0710 on 2008-04-30
> **mmejanvier said:**
> I was hoping for something a little more step-by-step

Really don't know how to do any of those things. 

Um

But thanks for trying to help. I think it's time to just get a different computer.

All I want to do is use my stoopid ipod, and I can't do it.

You had it working but it suddenly stopped? You should try totally removing amarok and then reinstalling it.

```
sudo apt-get purge amarok
```
```
sudo apt-get install amarok
```

---

### Post by mmejanvier on 2008-04-30
I've uninstalled and reinstalled amarok a lot. I think. Just tried that code and it said: Invalid operation purge.

---

### Post by hermes0710 on 2008-04-30
Try ```
dpkg --purge amarok
``` instead of the first command I posted before.

---

### Post by mmejanvier on 2008-04-30
requested operation requires superuser privilege

Thanks for helping guys.

Suprisingly, this didn't work either:

dave@dave-laptop:~$ Dude make amarok not be broken
bash: dude, not a valid command

8-[8-[

---

### Post by hermes0710 on 2008-04-30
> **mmejanvier said:**
> requested operation requires superuser privilege

Thanks for helping guys.

Suprisingly, this didn't work either:

dave@dave-laptop:~$ Dude make amarok not be broken
bash: dude, not a valid command

8-[8-[

You must execute the command as root:

```
sudo dpkg --purge amarok
```

For installing:

```
sudo apt-get install amarok
```

---

### Post by Ek0nomik on 2008-04-30
> **mmejanvier said:**
> I was hoping for something a little more step-by-step

Really don't know how to do any of those things. 

Um

But thanks for trying to help. I think it's time to just get a different computer.

All I want to do is use my stoopid ipod, and I can't do it.

Well, you are free to do as you wish, but just because Amarok isn't working I wouldn't say it's time for a new computer.  Apparently something has gone wrong with Amarok.

Have you been running Amarok in the terminal at all?

Try opening Amarok from the terminal to see if you can get any more useful output:

```
amarok &
```

---

### Post by mmejanvier on 2008-04-30
It says that there are dependability issues. I've already uninstalled and reinstalled amarok.

My main reasons for wanting a new computer: I do not understand this system. I do not understand code. It makes everyday use of my computer really frustrating and confusing. The applications are unreliable and crash all of the time.

---

### Post by Ek0nomik on 2008-04-30
> **mmejanvier said:**
> It says that there are dependability issues. I've already uninstalled and reinstalled amarok.

My main reasons for wanting a new computer: I do not understand this system. I do not understand code. It makes everyday use of my computer really frustrating and confusing. The applications are unreliable and crash all of the time.

It helps if you actually post the 'issues' or errors you are getting.  None of us can see the error you get unless you tell us.

What system don't you understand?  Ubuntu?  If you don't want Ubuntu on it anymore you can install Windows on it.  I guess I have never had your issue of software crashing all the time.  Perhaps Ubuntu just wasn't a flavor of Linux for you?  There are plenty of other versions out there.

---

### Post by stchman on 2008-04-30
Try:

```
sudo apt-get autoremove amarok

```
Go to synaptic and remove the residual config then reinstall.
```

sudo apt-get install amarok

```

---

