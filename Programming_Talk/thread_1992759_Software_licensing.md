---
title: "Software licensing?"
date: 2012-05-31
forum: Programming Talk
---

### Post by bcooperizcool on 2012-05-31
I am wondering, if it is even possible, to make software licensing tool out of shell.

I know it would need to be simple, but it would hopefully work.

I would need to check online once (that's the easy part) on my server, to see if some number or code or user is there. (I haven't done that part yet... making the server...).

How do other programs save the state of if a license is there?  So people who haven't bought the licence can't just change a file or state in something.

I have seen some programs (apps) check online for a license and then never ask again.  How do they do it?  How could I do in in shell?  Can I export and then protect a variable?  To check every time?   Could I make a variable so that only I know it? Or how? encrypt a file?  It would be part of a complete script, so user input is limited.  (text prompts can't accept input I don't think... idk).

Sorry if this doesn't make sense.  I know this is probably not the best language to do it in, but I want to see if it can be done.  And I know shell is open, but I can compile it. So that's not an issue with someone just changing the code ;)

Thanks!

---

### Post by Bachstelze on 2012-05-31
You do know that any scheme you could come up with can be easily worked around, right?

---

### Post by bcooperizcool on 2012-05-31
Yes, but hopefully a little deterred by compiled shell.

I'm just wanting an idea, not if its uncrackable ;)

---

### Post by r+9 on 2012-05-31
Is anyone else amused by this question on a forum for FOSS operating system?

I've never heard of compiled shell, I'll need to google that, generally shells are executing OS level commands, so they are easy to read and have limited io (limited to the OS).

Normally you hide the stuff you don't want users to mess with within binaries, so the compiled product (C or Python) which can usually make system calls like a shell.

---

### Post by melrokz on 2012-06-01
I agree. You can't implement software licensing in a shell script. And FYI shell scripts are interpreted, not compiled. :lolflag:

---

### Post by bcooperizcool on 2012-06-01
I didn't know about system call like that, well, kind of.

And its kind of compiling I think?  It hides the source at any rate
[http://www.datsi.fi.upm.es/~frosal/sources/shc.html](http://www.datsi.fi.upm.es/~frosal/sources/shc.html)

Anyway, could I maybe make an encryption of a file or script that sends something to the main script?  Idk.  Hmmmm....

---

### Post by 11jmb on 2012-06-01
With RE and profiling tools, it can be pretty easy to figure out which part of the software can be edited to circumvent a DRM.

Compiling your source is known as "security through obscurity" and is considered more of an inconvenience to attackers than a real security feature.

---

### Post by PaulM1985 on 2012-06-01
What exactly is your plan here?  Have you got some software you have written and you are trying to licence it yourself, or are you trying to write a licencing component for people to use to licence their software?

If you have written something and are trying to license it yourself I would say, don't bother with the licensing and focus on your product.  If you write something good, people would be happy to give you a bit of money for it.  You only need to worry if your program becomes hugely popular and you have millions of users.  Since this is not that likely, at least for now anyway :-), why not focus all your efforts into making something worthy of licensing, rather than focus on something which isn't the main product.

Paul

---

### Post by bcooperizcool on 2012-06-01
> **PaulM1985 said:**
> What exactly is your plan here?  Have you got some software you have written and you are trying to licence it yourself, or are you trying to write a licencing component for people to use to licence their software?

If you have written something and are trying to license it yourself I would say, don't bother with the licensing and focus on your product.  If you write something good, people would be happy to give you a bit of money for it.  You only need to worry if your program becomes hugely popular and you have millions of users.  Since this is not that likely, at least for now anyway :-), why not focus all your efforts into making something worthy of licensing, rather than focus on something which isn't the main product.

Paul

I do have software :)  I make apps for iOS. I am trying to write some sort of simple software licencing, even if it's nothing major, to stop people from simply just downloading something without paying for it ;)  or distributing it easily, without any knowledge at all, just by handing or emailing the file right away.

Or maybe even detecting if it is not a legitimate copy and doing something funny for all I care ;)  

The licensing thing is just really the last step before I start publishing stuff :)  

Really, thank you for this reply though, as this is the friendliest one I have received thus far and the most encouraging :)

---

### Post by PaulM1985 on 2012-06-01
I think you're best bet at the moment is pricing it appropriately.  You can work on licensing but as people have said, people can get round it.

Alot of people won't try to rip you off and if you can make it cheap and people really like it, they are more likely to tell their friends to get it for $1, $2, $5, rather than bothering sending files across by email.

Also, think about what it does mean if people are sharing your stuff for free, it means people are actually looking at your product.  Alot of bands put their stuff on youtube for free so that people watch them and get to know them in the hope that they will actually spend their money on them.  People used to download pirate music to check it out and then go out and buy the album if they like it.  If you are starting out, publicity is more the key rather than preventing your first 100 users from giving your work away.

Paul

---

### Post by inashdeen on 2012-06-01
One clear reminder is that, a license check with shell, or bash is definitely hazard since there is always a "simple" work around. you need to of course make it tougher if you really need to license it.

I had made a licensing software though, well not for paying stuff , but rather a notification that the program i build is an open source software and you must abide by it.
once, the person agree to the license, i just send command 
rm -rf to delete the licensing part.

well of course, this is a simple licensing scheme, and many people can get over it

---

### Post by 11jmb on 2012-06-01
> **PaulM1985 said:**
> I think you're best bet at the moment is pricing it appropriately.  You can work on licensing but as people have said, people can get round it.

Alot of people won't try to rip you off and if you can make it cheap and people really like it, they are more likely to tell their friends to get it for $1, $2, $5, rather than bothering sending files across by email.

Also, think about what it does mean if people are sharing your stuff for free, it means people are actually looking at your product.  Alot of bands put their stuff on youtube for free so that people watch them and get to know them in the hope that they will actually spend their money on them.  People used to download pirate music to check it out and then go out and buy the album if they like it.  If you are starting out, publicity is more the key rather than preventing your first 100 users from giving your work away.

Paul

I agree entirely. I think that restrictive licensing is more likely to turn users away and encourage piracy. You will always have the people who will try to rip you off (and usually succeed, despite your best efforts), but a good goal is to create a positive experience for your paying users. 

For example, I know some people who pirate games that they would otherwise be willing to buy in order to play the game without the horribly restrictive DRM's. Licensing software does very little to prevent piracy, and in very extreme cases (such as modern video games), can actually encourage piracy.

---

### Post by bcooperizcool on 2012-06-01
> **PaulM1985 said:**
> I think you're best bet at the moment is pricing it appropriately.  You can work on licensing but as people have said, people can get round it.

Alot of people won't try to rip you off and if you can make it cheap and people really like it, they are more likely to tell their friends to get it for $1, $2, $5, rather than bothering sending files across by email.

Also, think about what it does mean if people are sharing your stuff for free, it means people are actually looking at your product.  Alot of bands put their stuff on youtube for free so that people watch them and get to know them in the hope that they will actually spend their money on them.  People used to download pirate music to check it out and then go out and buy the album if they like it.  If you are starting out, publicity is more the key rather than preventing your first 100 users from giving your work away.

Paul

Thank you :)  You have talked some sense into me ;)

---

