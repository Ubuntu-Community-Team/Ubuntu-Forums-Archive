---
title: "Tilda in Startup Programs"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by apcfreak on 2008-06-03
Hello,
Yesterday I installed Tilda and got it working the way I wanted. I put an item in the Startup Programs dialog for it, but there is not sign of it after startup. I have tried putting a script in the startup list, basically just waiting 20 seconds before it starts Tilda, but I think it hangs. :confused:

---

### Post by gamx on 2008-06-04
I guess you mean Startup Programs under Sessions, right? I have done that and in my case it works properly... but only the first time. Then (and particularly if I have other windows maximized) it does not show up. I wonder if that is your problem too...

---

### Post by ZabiGG on 2008-06-04
I'm no expert with Tilda, but I found this bug report

[https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/93914](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/93914)

The last post might prove helpful to solve your problem, but since you provide no error output, I'm not even sure it applies.

Z.

---

### Post by apcfreak on 2008-06-04
Yes, I mean the Startup Programs under Sessions. 
Hmm, I'm not having any errors, and I don't have any other windows active. It works fine by just typing 'tilda' into the terminal, just not at startup.

---

### Post by ZabiGG on 2008-06-04
OK, so since it doesn't appear to work from the GUI, you may want to try to add it to your profile using the terminal. 

[http://ubuntuforums.org/showpost.php?p=5094691&postcount=11](http://ubuntuforums.org/showpost.php?p=5094691&postcount=11)

---

### Post by apcfreak on 2008-06-05
> **ZabiGG said:**
> OK, so since it doesn't appear to work from the GUI, you may want to try to add it to your profile using the terminal. 

[http://ubuntuforums.org/showpost.php?p=5094691&postcount=11](http://ubuntuforums.org/showpost.php?p=5094691&postcount=11)

I did it like that, and it made start up hang at the black screen, so I had to log in via gnome failsafe and revert it.

---

### Post by ZabiGG on 2008-06-05
Wow. Sorry then I'm stumped :(

Did you investigate on the developer's site? Maybe it's a bug...

---

### Post by love2learn on 2009-10-09
I know this is a relatively old post to be answering to but, it is one of the top google hits for tilda + ubuntu + startup so I think it would be nice to solve it.  I know there are several bugs involving tilda and starting up but I think i have a very temperary work around until things get solved.

What worked for me in jaunty is putting the "tilda" command in the "startup applications preferences AND going into system>preferences>assistive technologies at this screen you want to make sure you check "enable assistive technologies"  then click preferred applications>accessability and change the visual area to custom, then i checked the box that says "run at startup" and typed "tilda" in the box.

I did both of these procedures and now i have no problems with tilda.

*some disclaimers*
I do not claim this is the right or responsible way of doing things nor do I claim it will work for you. I am just saying it worked for me.

---

### Post by jflat06 on 2010-07-29
This is apparently still a bug. 

A workaround that I'm using is to do the following:

In the command field of your entry for tilda in the startup applications, instead of putting "tilda", put

bash -c "sleep 1s; tilda"

As another user pointed out, the bug probably has something to do with tilda being started before something else is initialized.

This just makes it start 1 second later, which is enough (at least on my computer) to avoid this problem.

---

### Post by p.s. on 2010-07-29
> **jflat06 said:**
> This is apparently still a bug. 

A workaround that I'm using is to do the following:

In the command field of your entry for tilda in the startup applications, instead of putting "tilda", put

bash -c "sleep 1s; tilda"

As another user pointed out, the bug probably has something to do with tilda being started before something else is initialized.

This just makes it start 1 second later, which is enough (at least on my computer) to avoid this problem.
I was able to add tilda at startup using the same method.

---

