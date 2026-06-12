---
title: "Why is it a good idea to advise people to use sudo?"
date: 2011-05-10
forum: Recurring Discussions
---

### Post by triceratops on 2011-05-10
Hi,

Okay I've been fumbling around the forums and giving some help (for better or worse).

Lots of people here advise other users to use sudo for access to superuser commands and file permissions rather than entering su directly.   Personally, I hate sudo and try to avoid it as much as possible.  If I have to, I use su-to-root in the DE or use a batch command to send me back to user as soon as I'm done with a set of commands.  

Is there an unofficial rule here at Ubuntu Forums that all answers must be given in terms of sudo?

EDIT: Oops, I don't think this topic should go here.  For future reference, which forum should I post a thread like this to?

---

### Post by steveneddy on 2011-05-10
Recurring discussions?

The long and winding argument......

[http://ubuntuforums.org/showthread.php?t=676176](http://ubuntuforums.org/showthread.php?t=676176)

---

### Post by 3Miro on 2011-05-10
Officially Ubuntu uses "sudo" and not "su". Also, "gksudo" for graphical apps.

---

### Post by triceratops on 2011-05-10
> **steveneddy said:**
> Recurring discussions?

The long and winding argument......

[http://ubuntuforums.org/showthread.php?t=676176](http://ubuntuforums.org/showthread.php?t=676176)

Okay.  Shouldn't've brought it up.  Mods: sorry to go there.  Guess I'm a "su" according to that categorization. 
  
> **3Miro said:**
> Officially Ubuntu uses "sudo" and not "su". Also, "gksudo" for graphical apps.

I will keep this in mind in the future.

I'm going to poke around and see why Canonical is so-so about *su*.  Doesn't make sense to me.  It's all good, since I have the option to administrate in other ways anyway.

---

### Post by jerenept on 2011-05-10
> **triceratops said:**
> Okay.  Shouldn't've brought it up.  Mods: sorry to go there.  Guess I'm a "su" according to that categorization. 
  


I will keep this in mind in the future.

I'm going to poke around and see why Canonical is so-so about *su*.  Doesn't make sense to me.  It's all good, since I have the option to administrate in other ways anyway.

sudo su

or 

sudo -i

---

### Post by earthpigg on 2011-05-10
for better or worse, sudo is the method encouraged by the distribution.

so, since it isn't an end-of-the-world difference, we generally go with the flow on things like that - things that are ultimately value judgements on "i like this better" or "i like that better".

similarly: i personally use synaptic and apt-get for most package management, but i still advise folks in absolute beginner talk to use the ubuntu software center.

pretty soon, i'll start answering questions with the assumption that the user is using Unity unless they mention otherwise - It will not matter in the least that I myself may be on openbox or gnome classic at the time. If the user doesn't specify otherwise, we ought to give standard advice that assumes a standard setup and that adheres to the decisions made by the folks that put Ubuntu together - again, unless the user *specifically* says they want or are doing something nonstandard.

In the context of this forum, we are volunteers and not policy makers. If we want to *become* policy makers, then we should do just that.

---

### Post by wojox on 2011-05-10
> **steveneddy said:**
> Recurring discussions?

:P


It's quicker to run 

```
sudo somecommand
```


Than to go through all that nonsense. You can also tweak visudo to speed it up more.

---

### Post by ErikNJ on 2011-05-10
It could be viewed as safer than running a root terminal.  Each time you enter a command that may cause havac, you must think to add "sudo."  If you were just logged in as root (su -), you may inadvertently do something you'd prefer you didn't.

For what it's worth, I run Fedora sometimes too and its default installation does not setup sudo for the user.  However, I usually add myself to the sudoer's file because I think it's a better method.  Do note that Fedora 15 (beta) allows you to add yourself as an "admin" and automatically add you to the sudoer's file.

---

### Post by triceratops on 2011-05-10
> **earthpigg said:**
> 
pretty soon, i'll start answering questions with the assumption that the user is using Unity unless they mention otherwise - It will not matter in the least that I myself may be on openbox or gnome classic at the time. If the user doesn't specify otherwise, we ought to give standard advice that assumes a standard setup and that adheres to the decisions made by the folks that put Ubuntu together - again, unless the user *specifically* says they want or are doing something nonstandard.

Okay, good point.  I do not use Unity and have no plans to migrate to it even after 11.10.  I guess, then, that if a question is posed and the user does not want a command syntax answer, I shouldn't answer it.  The user might be requesting help with Unity.

> **ErikNJ said:**
> 
For what it's worth, I run Fedora sometimes too and its default installation does not setup sudo for the user.  However, I usually add myself to the sudoer's file because I think it's a better method.  Do note that Fedora 15 (beta) allows you to add yourself as an "admin" and automatically add you to the sudoer's file.

I'm thinking of going Fedora for one of my machines as a test run.  I plan on jumping the Ubuntu ship when Wayland comes out (though I might stay with Debian for some of my machines, not sure yet.) I like the Fedora emphasis on user permission customization.

---

### Post by earthpigg on 2011-05-10
> Okay, good point.  I do not use Unity and have no plans to migrate to it even after 11.10.  I guess, then, that if a question is posed and the user does not want a command syntax answer, I shouldn't answer it.  The user might be requesting help with Unity.

Nah, I think answers with terminal copypasta are fine and consistent so long as they don't deviate from the standard methods and tools espoused by ubuntu. 

apt-get and not aptitude, for example, regardless of our personal opinions on the matter - based on the *de facto* status of apt-get as the 'official' package manager of the terminal. I cannot point you to any document that says that exactly, but I can point to many official documents that use apt-get and not aptitude.

That is just my opinion, though.

---

### Post by ErikNJ on 2011-05-10
> **triceratops said:**
> Okay, good point.  I do not use Unity and have no plans to 
I'm thinking of going Fedora for one of my machines as a test run.  I plan on jumping the Ubuntu ship when Wayland comes out (though I might stay with Debian for some of my machines, not sure yet.) I like the Fedora emphasis on user permission customization.

I think Fedora is planning on using Wayland as well (it was originally started by a Red Hat developer).

Should you decide to go without sudo, you can accomplish a similar action with "su -c"  The "-c" parameter means "command" and the root is only used for the command following "su -c."

---

### Post by el_koraco on 2011-05-11
> **earthpigg said:**
> 
apt-get and not aptitude, for example, regardless of our personal opinions on the matter - based on the *de facto* status of apt-get as the 'official' package manager of the terminal. I cannot point you to any document that says that exactly, but I can point to many official documents that use apt-get and not aptitude.


And because aptitude sucks.

---

### Post by earthpigg on 2011-05-11
> **el_koraco said:**
> And because aptitude sucks.

That is subjective. The whole point of my posts in this thread is to point out that, if we are merely acting as volunteers, our personal subjective opinions shouldn't be espoused in the support area at the expense of the established/official "Ubuntu way" of doing something. It would only serve to confuse and alienate new users at the best, and to break things for them at the worst.

Even if I loved aptitude, I wouldn't be giving directions in ABT using it.

---

### Post by iponeverything on 2011-05-11
old habits die hard.

I open an root window and keep it open when I working. But then again my business is systems/network administration. I don't advise it for my dad - it is like giving real hammer to a 4 year old boy -- and I get tried of fixing his system every other month..

---

### Post by el_koraco on 2011-05-11
> **earthpigg said:**
> That is subjective. The whole point of my posts in this thread is to point out that, if we are merely acting as volunteers, our personal subjective opinions shouldn't be espoused in the support area at the expense of the established/official "Ubuntu way" of doing something. It would only serve to confuse and alienate new users at the best, and to break things for them at the worst.



It was more like why apt-get is the "official" method. The only reason one could have to use aptitude is the "safe-upgrade" function, and due to the fact that until a few years ago apt-get wasn't good at removing things. Apt-get is the preferred method with running Sid, even aptosid, as well as Ubuntu development releases, cuz aptitude tries to hard to resolve dependencies and might mess up everything. Also, using the CLI is confusing to the newcomers one way or another, but answering questions like "x and y to be upgraded, z to be held back, j and k to be installed, y|n|maybe?" is downright annoying.

---

### Post by 3rdalbum on 2011-05-11
Ubuntu is developed and released with the assumption that you'll use *sudo* only when you really need to, and that you'll never 'su' to root.

I'd rather be safe and stick to *sudo*, than go it alone using 'su' in a distro that's not necessarily been tested and designed to stay together when you use 'su' :-)

---

### Post by triceratops on 2011-05-11
> **ErikNJ said:**
> I think Fedora is planning on using Wayland as well (it was originally started by a Red Hat developer).

Can't run, can't hide.  Will I be the last person using Xwindows?  Yes, it's a patched-up ancient system that's barely hanging on, but it's done me well all these years.  

Maybe it's just because I'm always cautious and a bit traditional.  I've continued to use MS-DOS well past the sell-by date.  I still find it useful for a very limited number of applications such as amateur radio software. 

> **3rdalbum said:**
> Ubuntu is developed and released with the assumption that you'll use *sudo* only when you really need to, and that you'll never 'su' to root.

I'd rather be safe and stick to *sudo*, than go it alone using 'su' in a distro that's not necessarily been tested and designed to stay together when you use 'su' :-)

I respect this philosophy.  Maybe I should work *sudo* into scripts rather than just leave a root window open most of the day.  Sometimes I forget to leave root.  Big security issue there.

---

### Post by Thewhistlingwind on 2011-05-11
Because historically the root user has been known to cause more verbal abuse towards the computer then any other feature of UNIX?

---

### Post by anaconda on 2011-05-11
I think sudo is too dangerous for some jobs... more dangerous than a root terminal.

For example, if you are a sysadmin, and people often come to ask your help.. how is it safer to enter your password many times every day in front of other poeple.

I think it is safer to  not let other peole see you type your password too many times.

---

### Post by snowpine on 2011-05-11
> **anaconda said:**
> I think sudo is too dangerous for some jobs... more dangerous than a root terminal.

For example, if you are a sysadmin, and people often come to ask your help.. how is it safer to enter your password many times every day in front of other poeple.

I think it is safer to  not let other peole see you type your password too many times.

sudo -i

---

### Post by Dry Lips on 2011-05-11
> **jerenept said:**
> sudo su

or 

sudo -i

What's the difference between sudo -i and sudo su?
On my 8.04 server I had root enabled, but I've disabled it now.
When I do "sudo su" I get this response 
> 
Your account has expired; please contact your system administrator su: User account has expired (Ignored) user@computer:/#Does sudo su use root if available, before doing something similar
to sudo -i if you haven't root enabled?

---

### Post by demilord on 2011-05-11
su = sudo -i
commands..

The idea of sudo is to keep users as far as less in the root environment so it prevents problems whih only occurs as root :)

---

### Post by snowpine on 2011-05-11
> **Dry Lips said:**
> What's the difference between sudo -i and sudo su?
On my 8.04 server I had root enabled, but I've disabled it now.
When I do "sudo su" I get this response 
Does sudo su use root if available, before doing something similar
to sudo -i if you haven't root enabled?

[http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

---

### Post by handy on 2011-05-11
I've become quite happy to use sudo. I have a short list of aliases in my .bashrc that I use that are sudo based; I call the alias, get asked for my password & carry on. Suits me.

---

### Post by triceratops on 2011-05-11
> **handy said:**
> I've become quite happy to use sudo. I have a short list of aliases in my .bashrc that I use that are sudo based; I call the alias, get asked for my password & carry on. Suits me.

Great idea!  Thanks

---

### Post by marshmallow1304 on 2011-05-11
> **el_koraco said:**
> And because aptitude sucks.

Having more features, better dependency handling, automatic dependency cleaning, and a better search function == suck ?

---

### Post by handy on 2011-05-11
> **triceratops said:**
> Great idea!  Thanks

If you need any inspiration, I'm sure that there used to be quite a well frequented thread on people's .bashrc scripts here.

I never used it myself, but I'm sure that if I did look into it I'd find some great command lines aliased down to a (hopefully) memorable few letters. :)

I think that there may have been such a thread started up recently, I suggest that if you do, do a search you look for the big one as there will obviously be so much more to chew on. [-o<

---

### Post by el_koraco on 2011-05-11
> **marshmallow1304 said:**
> Having more features, better dependency handling, automatic dependency cleaning, and a better search function == suck ?

it's highly personal :D
I vowed to never use it again after during one of its dependency handling escapades it removed a library that messed up my Docky. Took me three days to find out just what went wrong. Though, apt-get can have its moments...

---

### Post by forrestcupp on 2011-05-11
Sudo protects the ignorant from forgetting that they typed su. I don't think it much matters anymore since most people who are ignorant are going to either copy/paste commands or just only use the GUI.

> **marshmallow1304 said:**
> Having more features, better dependency handling, automatic dependency cleaning, and a better search function == suck ?
That may have been true 4 or 5 years ago until apt-get became better than aptitude.

---

### Post by Dry Lips on 2011-05-11
> **snowpine said:**
> [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4)

Excellent, thanks for this link!

---

### Post by lykwydchykyn on 2011-05-11
> **forrestcupp said:**
> That may have been true 4 or 5 years ago until apt-get became better than aptitude.

Suit yourself, but on a headless server I greatly appreciate aptitude's Ncurses interface.  Can't understand why the Ubuntu community standardized on apt-get, but oh well.

I try to remember to use apt-get in helping people just because mixing the two is bad for dependency handling.  But I have a whole lot of muscle memory tied up in aptitude.

As for sudo/su:  people often debate which is more secure, but it seems to me nothing is LESS secure than having both of them enabled.  And disabling sudo on Ubuntu is liable to break all kinds of things...

I've gotten to where I enable sudo and disable root on all my Debian servers now.

---

### Post by handy on 2011-05-11
> **forrestcupp said:**
> Sudo protects the ignorant from forgetting that they typed su. I don't think it much matters anymore since most people who are ignorant are going to either copy/paste commands or just only use the GUI. ...

So many of us only use su when we must. For me that could be less than once every 12 months. Admittedly I do have root to log in to if required on Arch, though that is a very rare occurrence also.

I like sudo, it is simple & effective. Admittedly it took me a few months to like it, but what is done is done...

---

### Post by Dry Lips on 2011-05-11
> **handy said:**
> So many of us only use su when we must. For me that could be less than once every 12 months. Admittedly I do have root to log in to if required on Arch, though that is a very rare occurrence also.

I like sudo, it is simple & effective. Admittedly it took me a few months to like it, but what is done is done...

Yo Handy!

Out of curiosity, in what instances do you need su?

---

### Post by sostentado on 2011-05-11
you use sudo when an application requires root permission, it it's not, then just run the command

---

### Post by aysiu on 2011-05-11
I'm not sure what there is to debate.

If you want to escalate privilege on one command use ```
sudo
``` If you want a persistent root prompt, use ```
sudo -i
```

---

### Post by handy on 2011-05-12
> **Dry Lips said:**
> Yo Handy!

Out of curiosity, in what instances do you need su?

I can't tell you m8, it really happens so incredibly rarely & it would seem that there is no consistency in the need.

It is so easy to just log in as root on Arch anyway. Which is again, is a relatively rare occurrence.

Sorry I couldn't give you reply that was a tad more useful. :)

---

### Post by Dearhell on 2011-05-12
So a program is installed the same way using "sudo apt-get install program" without beeing in the root account than using "apt-get install program" when you are already in the root account?

---

### Post by aysiu on 2011-05-12
> **Dearhell said:**
> So a program is installed the same way using "sudo apt-get install program" without beeing in the root account than using "apt-get install program" when you are already in the root account?
These two are the same: ```
sudo apt-get update
sudo apt-get install *programname*
``` ```
sudo -i
apt-get update
apt-get install *programname*
exit
```

---

