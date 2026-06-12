---
title: "Need to read info from file (bash-noob)"
date: 2006-02-20
forum: Programming Talk
---

### Post by helgman on 2006-02-20
Hi!

I've been bangning my head trying to figure this out but now I'm about to give up. I need to get information from a file and then use it to make new users on my system. The file with the users looks something like this:

Username FirstName LastName Group Password

My question is, how do I extract the information from the file and then use it to add the users? My plan is to add the user with **useradd [Userrname] -c [FirstName],[LastName ] -g [Group]** (does this have to be GID?), then do a **passwd [Username]**. (Guess my first question should be if this way is even possible.)

I don't really need a complete script, just a kick in the right direction (I need to learn this).

---

### Post by helgman on 2006-02-20
I might have figured it out ... **cut** seems to be what I am looking for. *fingers crossed*

---

### Post by nagilum on 2006-02-20
Yes, ***cut -f <column>*** is the easiest way to do this. Although it by default only splits at TAB characters, if you want spaces the additional paramter ***-d " "*** is needed. If you want to mix spaces and TABs 'awk' might be the better choice. It can split a line like yours with ***awk '{ print $<column> }'***.

---

