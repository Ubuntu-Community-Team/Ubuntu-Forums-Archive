---
title: "can an /etc/init.d script launch a terminal?"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by rclocher3 on 2013-11-28
Hi all,

I wanted to have a script launch a terminal, with another script running inside the terminal of course, as soon as I log into Ubuntu.  So I created a script called /etc/init.d/robs-init-script, which was created by root and had "chmod +x" done by root.  Here's the script:

[INDENT]#!/bin/bash
/usr/bin/gnome-terminal --command="/home/rob/robs-update-checker" &>> /home/rob/initlog.txt
[/INDENT]

I ran "sudo update-rc.d robs-init-script defaults 98 02", following the instructions on this page: [http://help.ubuntu.com/community/UbuntuBootupHowto](http://help.ubuntu.com/community/UbuntuBootupHowto)

So as you can see, /etc/init.d/robs-init-script is meant to launch ~/robs-update-checker, and if there is a problem it's supposed to put the error message in ~/initlog.txt.  If I run /etc/init.d/robs-init-script from the command line myself, everything works perfectly.  Here are the contents of ~/initlog.txt after booting up once:

[INDENT]Failed to parse arguments: Cannot open display:
Failed to parse arguments: Cannot open display:
[/INDENT]

So for some reason my script in /etc/init.d can't launch a terminal.  I suspect it has something to do with the runlevel (whatever that is).  Would someone tell me what I'm doing wrong, and what I can do to launch a terminal after I log in?

- Rob

---

### Post by DuckHook on 2013-11-28
Don't DO things like this. /etc/init.d/ is meant to start critical system services. There's a reason that you can't change system settings without *sudo*. It's meant to make you pause and think: "Do I *really* want to do this?" init.d has finished its business long before X is even loaded. gnome-terminal depends not only on X but about a hundred other processes to start before it can even begin to load. You have been playing with live hand grenades as far as system stability goes.

The proper place for any user-defined action at login is "Startup Applications" available right from the power menu tool in the system tray. You can also launch scripts by placing them (or their symlinks) in ~/.config/autostart/

If you simply must run scripts with root privileges at start, then you call them from /etc/rc.local
No root privilege script should be run lightly at startup and, though it is just my opinion, running an automatic system update at login is not sufficient rationale for monkeying with rc.local especially since this can be set through the update manager to run regularly anyways.

EDIT:

There's a long tradition in Linux of hacking. I sometimes forget this trying to help beginners who are naturally curious. However, hackers know their system and the breakages come as a result of trying to push the envelope. When beginners do this, more often than not it comes from lack of knowledge and leads to frustration and the conclusion that Linux sucks. Here's what I would recommend to you as an obviously budding hacker. Once you are comfortable enough with the base system, install VirtualBox and then a separate instance of Ubuntu running inside VBox as a virtual machine. Hack that to your heart's content. Break it a million different ways. Delete all of init.d just to see what happens. Because by restoring a good snapshot, you get back to being as good as new.

---

### Post by rclocher3 on 2013-11-28
Hi Duckhook,

For your information, this "budding hacker" is 46 years old, and my first Usenet post was in 1991.  I've been a lot of places in my life and done a lot of things.  I was a software engineer for four years, working on mostly Microsoft platforms: C, C++, Pascal, Delphi, C#, VB.net, ASP.net, SQL, Javascript, etc.  In my university days I spent 18 months working on scientific simulations on DEC workstations running Ultrix, and back in high school I played with an S/370 mainframe.  I was a pretty good software engineer; the reason I stopped is because I got an offer I couldn't refuse, and now I'm running a small business in a different area of technology.  And for your information, I **am** experimenting on a virtual machine.

Thank you for your expert advice that you've donated for free to me, and surely to many other netizens.  Without people like you, Linux would have never gone anywhere.  I'm sure it's late and you're tired, and you've dealt with hordes of newbies doing foolish things to their systems, but you really should rein in the condescending attitude.  My mistake was trusting the badly-written documentation I linked to in my last post, part of the official Ubuntu wiki.  Yes, I should have dug a little deeper, and if I had I would have learned that /etc/init.d is for low-level processes and "Startup Applications" is for user-level processes.  But does that mistake truly merit your lecture, made to make me feel small?  You don't know me sir.

- Rob

- Rob

---

### Post by DuckHook on 2013-11-28
My deepest apologies. I feel awful. Making you feel small was the furthest thing from my mind, and, now that I re-read my reply in the clear light of morning, of course it would appear condescending to a seasoned user.

Not as an excuse but rather as explanation: it is natural to suppose that someone posting on an "Absolute Beginners" forum is... well... an absolute beginner. People with your IT background post in "General Help" or even more specialist subforums. When combined with the nature of the question--running an X program before X has loaded--I jumped to the conclusion that I was dealing with someone new to computing. And as regards "budding hacker", perhaps you will better understand my intent if I tell you that I consider this phrase nothing but the highest compliment. I am nothing more than a "budding hacker" myself, maybe not even that, having learned only the rudiments of programming decades ago and having nothing but the highest regard for the hacker community. Purely as a request, the next time you post, perhaps you might consider providing a tiny bit of your background. Context is so important and yet so hard to come by in the impersonal medium of the Internet.

You've taught me something very important today: how I mustn't take anything for granted even on a Absolute Beginners forum, and how the limitations of the medium can twist the best of intentions into the opposite: unintended but still real jabs to the poor recipient.

If it's of any comfort, I'm really smarting right now after reading your reply. For someone who likes to help, nothing hurts more than finding out that his intended help actually hurt the recipient, if that convoluted thought even makes any sense. Again, a thousand apologies.

And in nothing but the most generous spirit--go nuts breaking that VM!

---

### Post by rclocher3 on 2013-11-28
Haha, very well said sir!  (Or madam -- you're right, there is very little context available in an web forum.)  No worries, your apology is gratefully accepted.  I've learned something from you also, about how to be gracious when confronted with one's own error.  You're okay in my book.  Happy Thanksgiving to you if you're in the US, and if you're ever in southwestern Oregon and you wouldn't mind golfing with a double-bogey duffer then I'd be delighted to play a round with you, and buy you a beverage at the 19th hole ;)

- Rob

---

### Post by DuckHook on 2013-11-28
...sir on this end. Madam is the other half: she-who-must-be-obeyed.

I inhabit the great snowy expanse way to the north of you. The source of those Arctic fronts that you are occasionally blessed with. Our Thanksgiving has come and gone, but thank you for the good wishes.

Oregon eh? <sigh> Have always wanted to try Bandon. It's supposed to be heavenly--in a beat-you-bloody body-slam sort of way. We duffers are a masochistic lot, aren't we? I will permanently park this thread and just may look you up if I'm ever down Oregon-ways. ):P

The wonder of it all is that I may have ended up with a new golfing buddy mainly by having insulted him on a public forum! :roll:

Now, before the mods kick us off for being totally and outrageously off topic (not to mention maudlin), have a Happy Thanksgiving and may the Linux gods ever smile upon you.

---

### Post by ian-weisser on 2013-11-28
> **rclocher3 said:**
> [INDENT]#!/bin/bash
/usr/bin/gnome-terminal --command="/home/rob/robs-update-checker" &>> /home/rob/initlog.txt
[/INDENT]
[...][INDENT]Failed to parse arguments: Cannot open display:
Failed to parse arguments: Cannot open display:
[/INDENT]
[...]


It's not the runlevel.
It's the difference between boot and login.

Root, when it runs init at boot, has no display or console assigned. Doesn't even know what a display is. All those init jobs run even if nobody ever logs in.

When you login at a console or graphical prompt, *then *the system associates your input with a user and a display.
Try **printenv DISPLAY **to see the display environment variable. Every terminal and console will have a different display assigned (even two terminals on the same screen...plus the screen itself)

So you can see why an init job to open a terminal window before user login would fail ("I don't understand terminal or window, nor who would own it").
And you can see why a Startup Applications job to open a terminal window, with an associated user and display, would succeed.

---

### Post by rclocher3 on 2013-11-29
Hi Ian, my mistake was to write a script too late at night, when my  critical thinking abilities were diminished.  As my new buddy DuckHook  pointed out, I'm better off using "Startup Applications" to launch my  script.  I did that, but then I ran into a new problem: the script was  being launched by my user ID, and I needed it to do a task that requires  root privileges.  I figured out how to edit /etc/sudoers using "sudo  visudo" to give my user ID the privileges to run just that script with  sudo without requiring a password.  Now everything works hunky-dory.   Thanks for your input!

- Rob

---

### Post by DuckHook on 2013-11-29
Hi Rob,

Ian is one of those guru types who can write a script that will do anything from walking his dog to rocking him to sleep at night. Like all gurus, it is understandably difficult for him to bring his thoughts down to the level of us commoners. We do owe him an immense debt of gratitude for tenaciously pulling this thread back on topic though.

To put even more of my ignorance on public display, I've got a few observations about your original script. This takes us *waaay* past the parameters of an Absolute Beginners forum, but we passed that point at the outset and, who knows? ...some absolute beginners may find this actually useful.

The following simply expands on what Ian is saying:

First and foremost, you don't have to invoke gnome-terminal to run a script. By avoiding it, you also avoid having to wait for all of the processes that gnome-terminal depends upon. You can run scripts dealing with basic system stuff by using```
#!/bin/bash
```alone. We don't know the contents of /home/rob/robs-update-checker, but if it doesn't require X functions or Gnome functions, you can simply invoke it from /etc/rc.local, especially since you actually want to run yours at *system* startup rather than at login anyway. rc.local is itself a script and is always run after the system has loaded its low-level resources. At that point, the system can run shells (which is what *sh* or *bash* is) and any script you want *provided it doesn't involve X*. rc.local starts out empty, but is commonly used for things like adding (or subtracting) driver support, etc.

Example: I run both KVM and VirtualBox VMs. However, since these apps map to the same resources, their drivers will conflict. I want VirtualBox as my default VM, but I want to be able to switch to KVM whenever the fancy takes me. How do I deal with the fact that they both load incompatible drivers at boot without uninstalling either KVM or VirtualBox? Well, I just add the following lines to rc.local:```
rmmod kvm-intel
rmmod kvm
```which unloads these modules soon after they are loaded. This leaves only the VBox modules loaded. If I later decide to monkey around with KVM instead, I manually invoke another script I've written that unloads the VBox modules and loads the KVM modules back in.

Finally, in your case, you could simply paste the actual contents of /home/rob/robs-update-checker into rc.local itself. However, this is not considered good practice because it fills up rc.local with cruft. Moreover, in the event of a system re-install, rc.local is overwritten and you lose all of your script code. Good practice calls for building the script independently and just using rc.local to chainload it.

Doubtless, you got this stuff after the first two sentences. I am writing it mainly for the benefit of new users who may happen across this thread.

***Caveats***

rc.local is executed before any graphical environment is started up. X, Unity, etc. all start up at login, not at boot. So if you want, say, Synaptic to be up and running at login, rc.local is the wrong place to put it. But a script that calls APT to automatically update would work.

The use of the "gnome-terminal --command=" construct and placing it in "Startup Applications", is for apps like *Firefox* that depend not only on X, but the whole desktop environment. For most general users, the apps that they want to autostart happen to be graphical. Therefore, the use of "Startup Applications".

***Warning***

Unless you really know what you are doing, monkeying with rc.local will often lead to a broken system. This is not recommended for new users on their production machine.

***DOUBLE Warning***

Anything run in rc.local executes with root privileges. Indiscriminate use will compromise your system security and is an open invitation to getting owned. Under NO circumstances should you run scripts that you've downloaded from the Internet using rc.local or any of the other methods that run scripts at boot; not unless you've learned to read the contents of those scripts and understand *exactly* what it's doing.

---

### Post by rclocher3 on 2013-12-02
Well hey Duck,

This thread has all sorts of useful information now.  The script ~/robs-update-checker needs to run in a terminal because it needs user input, and of course it must run after login.  I did run into one minor problem that I'll mention in case anyone interested has actually made it this far in this long thread.  My script needed root privileges, but "Startup Applications" does its thing on behalf of the logged-in user, rather than as root.

People, the sudo command is very clever, because it can be configured very flexibly to allow a user (or a member of a group, etc) to run a command using sudo *without requiring a password*.  sudo's configuration is kept in /etc/sudoers, but one doesn't edit that file directly; instead one runs "sudo visudo", which edits a copy of the file, and then after the editor is closed, checks are made to see if the user made any critical mistakes.  Google "sudoers" for more information.  So I gave my username permission to run one particular command using sudo without requiring my password.  So now my script running with me logged in can run "sudo some_command_that_requires_root_privileges", and the script just runs without stopping to demand the password, hooray!  Of course I'll mention a caveat: giving a user permission to run a command or commands without typing the password weakens security, so consider whether doing so is really worthwhile, and be careful.

- Rob

---

