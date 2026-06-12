---
title: "why so easy to break?..."
date: 2011-10-04
forum: New to Ubuntu
---

### Post by kenhmusic on 2011-10-04
I've already completely broken my Linux once, and almost broken it twice simply trying to set up my mouse's extra buttons to work properly and installing graphics cards.

I did this following the advice of other Linux users each and every time.

Could some of the more knowledgeable Linux people be so kind as to set up authoritative tutorials to set up the basic things with Linux, such as extra mouse buttons, graphics card drivers, perhaps disabling one's mousepad when an external mouse is connected, and other rudimentary tasks of that nature?

It's one thing if I'm trying to push the cutting edge of what my system can do, but I don't think I should have to feel afraid of taking someone's advice on the forum because it may wind up being ever-so-slightly incorrect and thus breaking my system.

---

### Post by audiomick on 2011-10-04
By typing "mouse buttons" in the search window here

[https://help.ubuntu.com/](https://help.ubuntu.com/)

I immediately found this

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

For the graphics issue, I would suggest a similar search.

The info is generally there somewhere. You just have to go and look for it. Don't forget, by the way, that all help offered on the forum is voluntary. It is being offered because people want to help, not because they are obliged to.

---

### Post by grahammechanical on 2011-10-04
Some people like the idea that Linux is extremely user configurable and they do not like the fact that Ubuntu is moving towards being less user configurable.

The freedom to modify the OS brings with it the freedom to break it. I have noticed from posts on this forum that some absolute beginners break the system trying to do things that absolute beginners should not try to do. 

If you purchased a computer with an OS pre-installed you would expect all the hardware to work as it should. If you could buy a machine with Linux pre-installed then everything would work as it should. The supplier would have a legal responsibility to make sure the produce was fit for sale.

I installed Ubuntu myself. I do not expect everything to work. This is a small price to pay for a quality operating system and applications that I received without charge.

Regards.

---

### Post by anewguy on 2011-10-04
I notice that your bean count is 1.  This means that you didn't post anything other than this post.  This means you blindly followed threads on how to get things working without really knowing if they were for you or not.  This is called Absolute Beginner Talk for a reason - we expect the beginner, and the not so beginner as well (I still post lots of questions), to come here and open threads looking for help.  We can't help if we're not asked, and as with any OS you shouldn't blindly try things.

Can we "fix" everything?  Maybe not.  Can we "fix" most things?  Definitely.

So, rather than waiting until you've tried things that you apparently didn't know for sure what they might do, or even more importantly having an idea on how to at least get back to where you were, you should have posted here asking for help.

So, do you want to open a thread for each of your problems giving some specifics as to what the problem is and what you've tried, or do you just want to complain?


Dave ;)

---

### Post by bodhi.zazen on 2011-10-04
> **kenhmusic said:**
> I've already completely broken my Linux once, and almost broken it twice simply trying to set up my mouse's extra buttons to work properly and installing graphics cards.

I did this following the advice of other Linux users each and every time.

Could some of the more knowledgeable Linux people be so kind as to set up authoritative tutorials to set up the basic things with Linux, such as extra mouse buttons, graphics card drivers, perhaps disabling one's mousepad when an external mouse is connected, and other rudimentary tasks of that nature?

It's one thing if I'm trying to push the cutting edge of what my system can do, but I don't think I should have to feel afraid of taking someone's advice on the forum because it may wind up being ever-so-slightly incorrect and thus breaking my system.

As with any OS, when you start editing system files it is easy to break them.

You should always back system files up before you edit them, then if you have a problem, restore from backup.

You should also add comments to your edit and save a copy of your working configuration files.

If you run into a problem, ask for help.

---

### Post by Slim Odds on 2011-10-04
> **bodhi.zazen said:**
> As with any OS, when you start editing system files it is easy to break them.

You should always back system files up before you edit them, then if you have a problem, restore from backup.

You should also add comments to your edit and save a copy of your working configuration files.

If you run into a problem, ask for help.

I totally agree, with simple backups of configuration files you can restore almost any change with a Live CD or Live USB (thumb drive).

---

### Post by TLARbb on 2011-10-04
I don't  have many beans either and here comes a real absolute beginner question - How do you back up the configuration files?  I just read that here and that's the extent of my knowledge of the subject.  I.e., you can back up the configuration files.  I feel that slapped me in the face and I noticed it, so I'd like to know the procedure to do it.  
 
Ed

---

### Post by Dangertux on 2011-10-04
> **bodhi.zazen said:**
> As with any OS, when you start editing system files it is easy to break them.

You should always back system files up before you edit them, then if you have a problem, restore from backup.

You should also add comments to your edit and save a copy of your working configuration files.

If you run into a problem, ask for help.

+1 I don't think anyone emphasizes backing up configuration files before changing them. 

It really does help if you muck things up to have a known good configuration to revert to.

To answer the question above me I will use /etc/hosts as an example file. So we edit that but to back it up before we do we can simply 

```

cp /etc/hosts /etc/hosts.backup

```

If things go south just 

```

cp /etc/hosts.backup /etc/hosts

```

And you're back where you started. Depending on the file Prepend sudo as necessary.

---

