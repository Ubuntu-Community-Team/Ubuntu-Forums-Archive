---
title: "dbus and a 'a{sv}' signature"
date: 2008-10-26
forum: Programming Talk
---

### Post by DLGandalf on 2008-10-26
how do I create the above signature?

I did something like:

dict:string:variant:"",""

but it tells me variant is not a valid type, this isn't weird as to variant is a container, and nested container are not allowed(variant is in a dict), but how on earth will I be able to make a signature like that?!

btw I want to send a notify to the desktop with notification-daemon through dbus-send in bash.

---

### Post by Guillaume86 on 2009-04-29
I've exactly the same problem, but the problem is that dbus-send do not support nested containers (look at the man page).
To send simple notifications you can use notify-send (in the notification-bin package i think) but to do advanced stuff like update a notification (what I wanted to do) you have to use C or pyhton...

---

