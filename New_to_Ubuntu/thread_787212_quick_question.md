---
title: "quick question"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Vrekk on 2008-05-08
Hey i am not new to Ubuntu, but i though this would be a good place to put it any .  In the termail, what is the thing you put in first that runs it as a admin, you know like the "xxx comand" type thing

---

### Post by Cypher on 2008-05-08
sudo

---

### Post by Lisa Y on 2008-05-08
Terminal*

You would type

```
 sudo su

```

---

### Post by Vrekk on 2008-05-08
thanks :)

---

### Post by Lisa Y on 2008-05-08
your welcome

---

### Post by Cypher on 2008-05-08
> **Lisa Y said:**
> Terminal*

You would type

```
 sudo su

```
..which essentially circumvents the whole security concept of using sudo for Admin commands. With the above command, your user account will become root and unless the user is paying attention, they could easily do things they did not intend to do.

It is always safe to prefix any Admin command with sudo just so you KNOW you're using an Admin command..

---

### Post by mankygitt on 2008-05-08
prefix your command with sudo

alternatively, switch to the super user > sudo su << Update - there are better methods..
however exercise caution if you're new to this, because you may find it easy to forget you've granted yourself "GOD" access and do something foolish.

Enjoy

Since posting the above, I have found this nice post which gives a nice overview on the right way to use sudo or the root account
[http://ubuntu-tutorials.com/2008/05/09/a-root-shell-on-ubuntu-the-right-way/](http://ubuntu-tutorials.com/2008/05/09/a-root-shell-on-ubuntu-the-right-way/)

---

### Post by hellmet on 2008-05-08
@OP. Just a suggestion - If you're new to Ubuntu, you're bound to have doubts like these. Why don't you check out the #ubuntu IRC channel? You'd get faster responses there too!!
No offense!

---

### Post by Whiffle on 2008-05-08
> **Cypher said:**
> ..which essentially circumvents the whole security concept of using sudo for Admin commands. With the above command, your user account will become root and unless the user is paying attention, they could easily do things they did not intend to do.

It is always safe to prefix any Admin command with sudo just so you KNOW you're using an Admin command..

Speaking of which, this is what happens when I use sudo on arch:

 ```

[andy@blacktop ~]$ sudo ls

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.


```

It wouldn't hurt if ubuntu had a similar warning.

---

