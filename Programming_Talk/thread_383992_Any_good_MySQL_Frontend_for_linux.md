---
title: "Any good MySQL Frontend for linux?"
date: 2007-03-13
forum: Programming Talk
---

### Post by HighD on 2007-03-13
Any good functional MySQL frontends for Linux(Ubuntu)???  What's your choice and why? I'm just starting to use MySQL and wanted to know if there were any? I just want to hear some opinions :mrgreen:

---

### Post by jonathan_c on 2007-03-13
I've found [SquirrelSQL]("http://www.squirrelsql.org/") to be quite handy. I use it at work regularly. It has the nice auto-completion that Query Analyzer has (by MS). It's a little work to set it up, but once you do, it's a good experience.

Another client I've used was Tora. This is a pretty good tool as well (though I still prefer SquirrelSQL). You can install it via:
```
apt-get install tora libqt3-mt-mysql 
```
Tora supports any DB that has a QT binding to it, so in this instance its MySQL.

Both of the clients support many other DBs besides MySQL.

---

### Post by derby007 on 2007-03-14
I use MySQLNavigator (/pub/ubuntu/archive/pool/universe/m/mysql-navigator) and it serves my (simple) purposes.

---

### Post by Mirrorball on 2007-03-14
Good old phpMyAdmin.

---

### Post by gh0st on 2007-03-14
MySQL administrator does the job for me, decent GUI, pretty powerful, no complaints at all. It's in the main repos I installed it from add/remove programs. You might wanna try it.

---

### Post by jammodotnet on 2007-03-18
> **gh0st said:**
> MySQL administrator does the job for me, decent GUI, pretty powerful, no complaints at all. It's in the main repos I installed it from add/remove programs. You might wanna try it.

I just installed it from Synaptic, but I do not know where to find the application?!

I suspected: >Applications >  Programming, but it's not there.

Can you help me locate it?
:(

---

### Post by gh0st on 2007-03-18
I installed it on a Fiesty testing server last time but I've wiped the system since then. I just tried installing it on another Fiesty testing server I have and here's what happened:

I installed the package "mysql-admin" from Synaptic and then when I looked under "Applications \ Programming" on the menu it was there.

What version of Ubuntu are you using? Maybe Edgy and Dapper do it differently. If it doesn't appear on your menu you could try seeing if it's listed in your menu editor but not displayed, that happens sometimes.

Have a look under "System \ Preferences \ Main Menu" and see if it's ticked in there. If it's not ticked then it won't appear on your menu. If it's not listed in there at all I don't know what to suggest.

I found I can get it to run by just typing "mysql-admin" in the terminal. You could make yourself a desktop shortcut or even a menu entry if that works.

Hope that helps a bit, good luck :)

---

### Post by [h2o] on 2007-03-18
> **jammodotnet said:**
> I just installed it from Synaptic, but I do not know where to find the application?!

I suspected: >Applications >  Programming, but it's not there.

Can you help me locate it?
:(

Mine is in "Applications -> System Tools" (or whatever it might be called in english).

---

### Post by jammodotnet on 2007-03-18
> **gh0st said:**
> I installed it on a Fiesty testing server last time but I've wiped the system since then. I just tried installing it on another Fiesty testing server I have and here's what happened:

I installed the package "mysql-admin" from Synaptic and then when I looked under "Applications \ Programming" on the menu it was there.

What version of Ubuntu are you using? Maybe Edgy and Dapper do it differently. If it doesn't appear on your menu you could try seeing if it's listed in your menu editor but not displayed, that happens sometimes.

Have a look under "System \ Preferences \ Main Menu" and see if it's ticked in there. If it's not ticked then it won't appear on your menu. If it's not listed in there at all I don't know what to suggest.

I found I can get it to run by just typing "mysql-admin" in the terminal. You could make yourself a desktop shortcut or even a menu entry if that works.

Hope that helps a bit, good luck :)

i've tried all you mentioned - still, none found.
i even went back into Synaptic and viewed All Installed. i can see all the applications i've installed, it even shows MySQL Navigator.

> **'[h2o] said:**
> Mine is in "Applications -> System Tools" (or whatever it might be called in english).

ive tried that too.
:(

i navigated to my root in my file browser, and did a search. nothing found.

i have Xampp installed and it use it daily. phpmyadmin works fine, but i was (as everyone else) looking for something different to use.

---

### Post by HighD on 2007-03-18
> **derby007 said:**
> I use MySQLNavigator (/pub/ubuntu/archive/pool/universe/m/mysql-navigator) and it serves my (simple) purposes.

Interesting!! I might try it soon. Never heard of it.

> **gh0st said:**
> MySQL administrator does the job for me, decent GUI, pretty powerful, no complaints at all. It's in the main repos I installed it from add/remove programs. You might wanna try it.

Hmm....gotta give it a try.

I want to know about a good frontend cause I'm currently a student and getting into MySQL. The thing is I'm developing in .NET so I  created a virtual machine to install Visual Studio and work with both MySQL in Ubuntu and Visual Studio. I was looking into some Windows MySQL frontend apps, so I can install in my virtual machine and connect to MySQL, but I really don't want to do this. I need one that runs on my Ubuntu box. :)

Thanks everybody for your anwers

---

### Post by HeavyEddie on 2007-03-18
It isn't free, but navicat is awesome!

---

### Post by gh0st on 2007-03-18
> **jammodotnet said:**
> i've tried all you mentioned - still, none found.
i even went back into Synaptic and viewed All Installed. i can see all the applications i've installed, it even shows MySQL Navigator.


That's weird it should work. One thing that bothers me though is you called it MySQL Navigator, thats a different package, I'm using MySQL Administrator.

Did you install "mysql-admin" or "mysql-navigator" in Synaptic? If you want to check you could just do the following:

```

sudo apt-get install mysql-admin

```

You might find you picked the wrong package. There are so many to choose from it's easily done. I wasn't sure which one I needed at first. 

If you definitely have "mysql-admin" package installed and even running from the terminal doesn't work then I don't know what to suggest. Sorry :( 

Hope that info helps in some way :)

---

### Post by rabideau on 2007-04-07
I am using fiesty and used synaptic... search navigator and bingo found mysqlnavigator.

---

