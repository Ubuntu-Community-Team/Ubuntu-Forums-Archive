---
title: "Root"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by reyals140 on 2008-12-01
How do I login as, and stay loged in as, root?
I keep running into problem after problem that requires me to be root.
To answer most probably response based on all the answer I can find with search.
I don't care about security, being loged in as root has no effect on that.
And I don't want to have to learn all the terminal commands and sudo or su or whatever to do it manually.  I want simplicity.

---

### Post by ibizatunes on 2008-12-01
You shouldnt really run as root, but if you want too, enable the account in user manager in system > then in system go to login and enable administrator login,

Log off and log back in as root, with your password

What is asking you to be root to run??

Enabling root is a big security floor!!

---

### Post by bcd87 on 2008-12-01
[Clickety](http://www.google.nl/search?q=enable+root+user+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:nl:official&client=firefox-a)

You could've found it yourself probably. Google is your friend.
Not a smart thing to do, but you have your mind made up about it, it seems.

---

### Post by reyals140 on 2008-12-01
> **ibizatunes said:**
> You shouldnt really run as root, but if you want too, enable the account in user manager in system > then in system go to login and enable administrator login,

Log off and log back in as root, with your password

What is asking you to be root to run??

Enabling root is a big security floor!!

How?  If I downloaded a trojan thinking it's something else I'm going to give it all the permissions it needs to run anyway thinking it's safe so how is not being loged in as root going to protect me?

But I've had many issues that keep forcing me to google the proper sudo what ever command; I'd rather just use the GUI given to me with out being told 'I can't do that', 'I don't own that', or 'I need more permissions to do that'

But if you're wondering, this time my exact problem is I'm trying to share stuff on the network and I can't do that because I don't own it and get told to edit a file to allow non-owners to share... Well guess what... only root has write access to that file.  I've spent 45 mins trying to do what takes 1 on windows.


> **bcd87 said:**
> [Clickety](http://www.google.nl/search?q=enable+root+user+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:nl:official&client=firefox-a)

You could've found it yourself probably. Google is your friend.
Not a smart thing to do, but you have your mind made up about it, it seems.

I tried google, everything either said that
a)Disabled
b)To use
sudo passwd root
Which does nothing
c)Only told you how to do it in a terminal
d)Was too complex
ibizatunes' answer is just what I wanted.

---

### Post by Her Ghost on 2008-12-01
not that I suspect it will change your mind, but the protection it offers is that it will ask you to grant it permission to perform certain tasks.  now, I know that when performing a task yourself you are likely to just provide the password, but this forms a logical chain of:

*user action > root prompt > result*

the root prompt basically says, "were you expecting this?".  if you are permanently logged in a root then the benefit you get is:

*user action > result*

but, significantly, you also lose out on the:

*accidental action or malicious action > root prompt > result*

and just end up with no control over anything.

Like I said, not expecting to change your mind, but worth noting.

---

### Post by Hallvor on 2008-12-01
Perhaps you should try opening a terminal and type

```
gksu nautilus
```

This will open Nautilus in root mode. You should be able to change the permissions from Nautilus.

---

### Post by reyals140 on 2008-12-01
> **Her Ghost said:**
> not that I suspect it will change your mind, but the protection it offers is that it will ask you to grant it permission to perform certain tasks.  now, I know that when performing a task yourself you are likely to just provide the password, but this forms a logical chain of:

*user action > root prompt > result*

the root prompt basically says, "were you expecting this?".  if you are permanently logged in a root then the benefit you get is:

*user action > result*

but, significantly, you also lose out on the:

*accidental action or malicious action > root prompt > result*

and just end up with no control over anything.

Like I said, not expecting to change your mind, but worth noting.

Can you give me an example of a malicious action that I would myself not activate thinking it's innocent?

So why can't I click 'share' and get a root prompt and confirm that I yes... I do infact own my hard drive.  Why can't I edit a file, press save, and get a prompt to confirm that yes... I am in fact root and would like to edit my files?


P.S. to the original fix.  You still have to go System>Admin
istration>Login Window>Security>Allow Local system admin....

---

### Post by reyals140 on 2008-12-01
> **Hallvor said:**
> Perhaps you should try opening a terminal and type

```
gksu nautilus
```

This will open Nautilus in root mode. You should be able to change the permissions from Nautilus.

Because I'm getting sick and tired of googling for the proper linux command to do what I want it to do.
I googled for that command for a while and never found it.
It took me like 30 mins to find the proper crap to type into the console to get it to mount a usb drive that 'hadn't been properly closed'
Another 30 mins to find the stuff to type get it to install my video card drives.
Ect
I just want it to work when I click the button.  The button, not some cryptic command line command, things that have been dead a long long time.

---

### Post by Her Ghost on 2008-12-01
It depends entirely on how you use your machine and your attitude to security.

If you were working on, say, a Spreadsheet, and you suddenly got an unrelated prompt for root password from another window, would you provide it without looking into what was going on first?  If you would, then yes, you might as well be logged in as root since you, the user, are not adding to the security of the system.  If however, you would take a look and try to figure out what was going on (and, moreover, you wouldn't be too pleased that things were randomly requesting root privileges) then the root prompt being there is a way of giving you "final say" over what goes on.

I appreciate that at times it can be annoying, but it isn't there to annoy you, it is there to ensure you have control over your system.

As for the editing of files, I can see that it can be annoying to be told at the end rather than prompted at the beginning, but that's just the way it works I guess.  You can get around it by planning ahead and editing protected files as root from the start, instead of just "ok-ing" it at the end.

---

### Post by reyals140 on 2008-12-01
> **Her Ghost said:**
> If you were working on, say, a Spreadsheet, and you suddenly got an unrelated prompt for root password from another window, would you provide it without looking into what was going on first?  If you would, then yes, you might as well be logged in as root since you, the user, are not adding to the security of the system.  If however, you would take a look and try to figure out what was going on (and, moreover, you wouldn't be too pleased that things were randomly requesting root privileges) then the root prompt being there is a way of giving you "final say" over what goes on.
But how would that happen?
If something is requesting a root password it already has to be on my computer, and the only way it's going to be on my computer is if I let it, and if I let it on my computer I gave it root to do whatever it wanted when it installed.....
So, how would that happen?

---

### Post by jimmy the saint on 2008-12-01
> **reyals140 said:**
> Because I'm getting sick and tired of googling for the proper linux command to do what I want it to do.
I googled for that command for a while and never found it.
It took me like 30 mins to find the proper crap to type into the console to get it to mount a usb drive that 'hadn't been properly closed'
Another 30 mins to find the stuff to type get it to install my video card drives.
Ect
I just want it to work when I click the button.  The button, not some cryptic command line command, things that have been dead a long long time.

I so rarely say this, but maybe you would be better off sticking with windows.  I mean, if you have no need for basic security and no desire to learn the OS, why are you using it?  If you indeed did the research, you would find that any gui app can be run with with root privileges via "gksu"

I have similar problems with the way other OSs work.  I hate having to search around for an appropriate program to complete a task, then figure out if it is free (beer), then download it, then install it.  That's why I use Ubuntu instead.  

For the record, this entire thread is dangerously close to violating the Forum code of conduct.  The codes clearly state that instructions on how to use the root account are not to be shared.  If a user is so inexperienced that they cannot figure it out or research it, they are not likely to be knowlegable enough to utilize that account safely.  Instead, the proper use of sudo should be explained.

---

### Post by 3rdalbum on 2008-12-01
BEFORE you go ahead and enable the root account, I have a solution for you that requires absolutely no terminal work at all.

Go into Synaptic Package Manager. Use the quick-search box at the top of the window to search for "nautilus-gksu". Install it. Also search for "nautilus-open-terminal" and install that, for goood measure (it comes in handy).

Log out. Log back in. Now, whenever you need to open a file browser window as root, or open a system file as root in order to make changes, simply right-click the file or enclosing folder and use the "Open as Administrator" menu item.

If you need to do some terminal commands as root, you can right-click a folder in your home directory, choose Open As Administrator, and then in the window that opens you can right-click and choose "Open in Terminal". Now you'll have a root terminal.

See? A lot of old hands at Linux think in terms of the terminal commands, but there's very often a GUI way available. Seriously, don't enable the root account. I don't have the time right now to tell you why not to run perminantly as root (if you really want to know, send me a PM and I'll explain everything at a later date). Just trust us on this one. Or if you don't trust everyone else here, at least trust ME as a budding security enthusiast.

---

### Post by reyals140 on 2008-12-01
> **jimmy the saint said:**
> I so rarely say this, but maybe you would be better off sticking with windows.  I mean, if you have no need for basic security and no desire to learn the OS, why are you using it?  If you indeed did the research, you would find that any gui app can be run with with root privileges via "gksu"

I have similar problems with the way other OSs work.  I hate having to search around for an appropriate program to complete a task, then figure out if it is free (beer), then download it, then install it.  That's why I use Ubuntu instead. 
So uh... you don't have to search for, download, or install programs on Ubuntu... wow, how do I enable such a powerful feature? :rolleyes:

And I'd know the name of the program I needed to gksu how?  Plus... don't you see how that's more work then a right click?


> **3rdalbum said:**
> BEFORE you go ahead and enable the root account, I have a solution for you that requires absolutely no terminal work at all.

Go into Synaptic Package Manager. Use the quick-search box at the top of the window to search for "nautilus-gksu". Install it. Also search for "nautilus-open-terminal" and install that, for goood measure (it comes in handy).

Log out. Log back in. Now, whenever you need to open a file browser window as root, or open a system file as root in order to make changes, simply right-click the file or enclosing folder and use the "Open as Administrator" menu item.

If you need to do some terminal commands as root, you can right-click a folder in your home directory, choose Open As Administrator, and then in the window that opens you can right-click and choose "Open in Terminal". Now you'll have a root terminal.

See? A lot of old hands at Linux think in terms of the terminal commands, but there's very often a GUI way available. Seriously, don't enable the root account. I don't have the time right now to tell you why not to run perminantly as root (if you really want to know, send me a PM and I'll explain everything at a later date). Just trust us on this one. Or if you don't trust everyone else here, at least trust ME as a budding security enthusiast.

That works too... but it's still more work then just -being- root, especially since no one has given me a real security reason why it's bad to be root....

---

### Post by lakersforce on 2008-12-01
> **reyals140 said:**
> How do I login as, and stay loged in as, root?

You should not do that. [There are other ways!]("http://ubuntuforums.org/showthread.php?t=765414")

> **reyals140 said:**
> I'm getting sick and tired of googling for the proper linux command to do what I want it to do.


check out:
```
man intro
```


Also try this out (it solves the problems you describe and does it the way you want):

press alt+F2 and type
```
gksudo nautilus
```

---

### Post by reyals140 on 2008-12-01
> **lakersforce said:**
> You should not do that. [There are other ways!]("http://ubuntuforums.org/showthread.php?t=765414")
Like I said before I don't want to have to keep looking up a bunch of cryptic sudo terminal commands, I want it to work when I click the button.
3rdalbum option is the best, but still requires you to back track if you run into something you need to be root rather then knowing ahead of time that you need to be root.

---

### Post by 3rdalbum on 2008-12-01
> **reyals140 said:**
> Like I said before I don't want to have to keep looking up a bunch of cryptic sudo terminal commands, I want it to work when I click the button.
3rdalbum option is the best, but still requires you to back track if you run into something you need to be root rather then knowing ahead of time that you need to be root.

It becomes second-nature very quickly, and once your system is all set up you won't need root very often at all. I only tend to use root now when I'm installing programs or checking for updates, and Synaptic and Update Manager automatically ask anyway.

There are no "sudo" commands to learn; just put "sudo" in front of any command you want to run as root, and that's it.

If you really have your heart set on enabling a root account, even after the long PM I sent you (10 minutes of battery life left!), then go ahead and do it. Google will tell you how to do it, because we're not supposed to here on Ubuntu Forums (for liability reasons, I believe). Just don't be surprised if things go wrong for you, or if you decide to reinstall Ubuntu later down the track in order to get back to a rootless system.

---

### Post by hyper_ch on 2008-12-01
i have to agree with Jimmy the saint: I don't think linux suits you well... with the mindset you portray here linux won't make you happy.

---

### Post by mick222 on 2008-12-01
stay with it dont log in as root though if you want to pen a file as root either press f2 and gksu nautilus or right click and open as administrator .
 On the downloading programs almost everything is available through add remove or synaptic package manager.

---

### Post by reyals140 on 2008-12-01
> **hyper_ch said:**
> i have to agree with Jimmy the saint: I don't think linux suits you well... with the mindset you portray here linux won't make you happy.

LOL wanting thing to be simple and 'just work' isn't a linux mind set?  No wonder linux will never take off.....


Anyway since the only security hole that anyone has presented is that someone could force an already installed 'good' program to download and run a 'bad' program which would have access to everything I'd care about at just user level... the horror...... Yah sorry if I don't lose sleep over that risk to my firewalled computer.

Thanks to those that answered my questions.  Feel free to put this thread in jail or whatever.

---

### Post by Dj Melik on 2008-12-01
> **reyals140 said:**
> LOL wanting thing to be simple and 'just work' isn't a linux mind set?  No wonder linux will never take off.....


Anyway since the only security hole that anyone has presented is that someone could force an already installed 'good' program to download and run a 'bad' program which would have access to everything I'd care about at just user level... the horror...... Yah sorry if I don't lose sleep over that risk to my firewalled computer.

Thanks to those that answered my questions.  Feel free to put this thread in jail or whatever.
Yeah but at user level they won't be able to download the bad program and install it because it would need ROOT access. How is typing "sudo" so complex?

---

### Post by Her Ghost on 2008-12-01
> **reyals140 said:**
> LOL wanting thing to be simple and 'just work' isn't a linux mind set?  No wonder linux will never take off.....


Anyway since the only security hole that anyone has presented is that someone could force an already installed 'good' program to download and run a 'bad' program which would have access to everything I'd care about at just user level... the horror...... Yah sorry if I don't lose sleep over that risk to my firewalled computer.

Thanks to those that answered my questions.  Feel free to put this thread in jail or whatever.

People are only trying to help here, but it seems that you have already decided on your way forward irrespective of what these people are saying.

I am sure that if you want to you can live as root, but you (probably) won't find people who will tell you how to do that here.  This is not because they're being difficult or unhelpful, it is simply because it is not a good idea and will ultimately cause you a world of pain (whether you can see it now or not).

---

### Post by overdrank on 2008-12-01
> **reyals140 said:**
> 

Thanks to those that answered my questions.  Feel free to put this thread in jail or whatever.

Hi and you may look at the forums policy
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
Thread closed.

---

