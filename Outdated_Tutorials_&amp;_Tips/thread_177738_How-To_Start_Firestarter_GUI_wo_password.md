---
title: "How-To Start Firestarter GUI w/o password"
date: 2006-05-16
forum: Outdated Tutorials &amp; Tips
---

### Post by SqRt7744 on 2006-05-16
I have been plagued for months by the firestarter gui constantly requiring a password when I log in to my Gnome session.  I finally found the solution in the french ubuntu forums!  It is simple enough:

First, system->preferences->sessions, click on the startup programs tab and add:
```

sudo firestarter --start-hidden

```

(I had gksudo firestarter previously so that it would start at all).

Now edit /etc/sudoers (after backing it up as /etc/sudoers.bak).  The file claims that it should only be edited with "visudo".  I'm skeptical, but whoever wrote that in the file presumably had a good reason to do so.  To be safe I will follow advice and use visudo here:

```

sudo cp /etc/sudoers /etc/sudoers.bak
export VISUAL="vim"
sudo visudo

```

the /etc/sudoers file will be opened by vi.  Press the 'i' key to change to insert mode, navigate to the 'defaults' line, and change it so it looks like this:

```

Defaults        !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"

```

Finally, at the bottom of the file, add a line which reads:
```

your_user_name ALL= NOPASSWD: /usr/sbin/firestarter

```

where you replace "your_user_name" with, well, your user name.
Save and exit by pressing the escape key followed by ZZ  (that is the shift key+2 presses of the z key)
  Your woes should now be a thing of the past!

I have heard that xlibs will be included with the final release of Dapper.  If you do not have it yet, I beleive it must be installed for this how-to to work, as some people seem to have been having issues relating to xlibs.  If that is the case for you please install it manually like this:
```

wget http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb
sudo dpkg -i xlibs_6.8.2-77_all.deb

```

**If you encounter problems** (eg. typo in the sudoers file), you must become root either by rebooting into recovery mode or by typing su (if you have set a password for root) and type
```

cp /etc/sudoers.bak /etc/sudoers

```
This will restore the sudoers file back to its original state.

---

### Post by chadk on 2006-05-16
I get a "you are changing a read only file" when I try to edit etc/sudoers -- so I used :w! to force it to save (I think)?

Didn't work for me though.  So I tried to remove firestarter:
chad@figment:~$ sudo apt-get remove firestarter
Reading package lists... Done
Building dependency tree... Done
Package firestarter is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Well I installed it again and it let me remove it.

---

### Post by xXx 0wn3d xXx on 2006-05-16
Thanks for this tutorial. Firestarter will finally start automatically :) 
Edit: I get an Xlib display error when launching synptic/update manager. I had to reboot into recovery mode and edit my sudoers file to fix it. Is this a problem with my install or does adding to the defaults of the sudoers file cause this ?

---

### Post by SqRt7744 on 2006-05-16
[QUOTE=chadk]I get a "you are changing a read only file" when I try to edit etc/sudoers -- so I used :w! to force it to save (I think)?

Didn't work for me though.  So I tried to remove firestarter:
chad@figment:~$ sudo apt-get remove firestarter
Reading package lists... Done
Building dependency tree... Done
Package firestarter is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Well I installed it again and it let me remove it.[/QUOTE]

Ack!  You may have forgotten to type "sudo visudo".  I.e., the file isn't read only for root!  After editing, press 'esc' then ':wq'.  ...that should take you back to command mode, write, then quit.  If it still gives you the read only warning, then something is wrong with the permissions, try
```

sudo chmod 600 /etc/sudoers

```

Also, you didn't have firestarter installed to begin with, no wonder it didn't work!  You have to install it!

```

sudo apt-get install firestarter

```

You may have to enable the universe repository in synaptic first though... not sure.

---

### Post by SqRt7744 on 2006-05-16
[QUOTE=MasterChief1234]Thanks for this tutorial. Firestarter will finally start automatically :) 
Edit: I get an Xlib display error when launching synptic/update manager. I had to reboot into recovery mode and edit my sudoers file to fix it. Is this a problem with my install or does adding to the defaults of the sudoers file cause this ?[/QUOTE]

Now that's the strangest thing.  Works fine for me...  Here's my sudoers file for comparison:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn,env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION"
# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
sqrt7744 ALL= NOPASSWD: /usr/sbin/firestarter


```

You may also want to try installing xlibs:
```

wget http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb

```
followed by
```

sudo dpkg -i xlibs_6.8.2-77_all.deb

```

---

### Post by testube_babies on 2006-05-16
I have a question that may or may not be appropriate to ask here.  Why do you use **sudo** firestarter instead of **gksudo** firestarter?

---

### Post by vaskark on 2006-05-17
Ouch. I effed up somehow, and my /etc/sudoers file cannot be accessed now. This is what I get at the CLI:
```
[vaskark@dapper ~]# sudo visudo
sudo: unknown defaults entry `fqdni' referenced near line 16
sudo: parse error in /etc/sudoers near line 15
Broken pipe
``` Does anyone know how I can fix this? Until I do I guess I won't be running anything with root priviledges. Thanks.

](*,)

---

### Post by Burgundavia on 2006-05-17
Just as a note, you do NOT need Firestarter to be running for your firewall to be running. Firestarter is only a monitoring app.

Corey

---

### Post by SqRt7744 on 2006-05-17
[QUOTE=vaskark]Ouch. I effed up somehow, and my /etc/sudoers file cannot be accessed now. This is what I get at the CLI:
```
[vaskark@dapper ~]# sudo visudo
sudo: unknown defaults entry `fqdni' referenced near line 16
sudo: parse error in /etc/sudoers near line 15
Broken pipe
``` Does anyone know how I can fix this? Until I do I guess I won't be running anything with root priviledges. Thanks.

](*,)[/QUOTE]

Yes, you did indeed.  A typo!  "fqdni" should read "fqdn".  In any case, you have to fix it first, but apparently you can't use sudo to do it, so copy down the correct line onto paper, reboot, go into recovery mode.  this will take you to a root terminal.  type

EITHER:
vim /etc/sudoers
press i to enter insert mode, fix your typo, press 'esc', ZZ.  Done!  Reboot and sudo should work again for you.
OR:
pico /etc/sudoers 
this might be more natural to you.  I like vim, but many do not. pico is more intuitive.

---

### Post by SqRt7744 on 2006-05-17
[QUOTE=testube_babies]I have a question that may or may not be appropriate to ask here.  Why do you use **sudo** firestarter instead of **gksudo** firestarter?[/QUOTE]

gksudo brings up a box into which you type your sudo password, you encounter it for example when you load synaptic.  Since we have killed the necessity to enter a password to load the firestarter GUI, we no longer need gksudo.  sudo gives firestarter root priveleges without the necessity of a password being entered at all.

---

### Post by frying_fish on 2006-05-17
vaskark : You don't need to type sudo visudo if you are already root.  as you seem to have been in what you have copied into your post.

If you are root, just type visudo.  Or if you want to try another editor there is nano (if its installed) or gedit.  So you could do gedit /etc/sudoers  and edit it then.

---

### Post by cutOff on 2006-05-17
[QUOTE=Burgundavia]Just as a note, you do NOT need Firestarter to be running for your firewall to be running. Firestarter is only a monitoring app.

Corey[/QUOTE]
Rather than a monitoring app, it's a simple GUI to set up firewall policies.

And yes, it's not needed to run it everytime.

---

### Post by vaskark on 2006-05-17
[quote=SqRt7744]Yes, you did indeed.  A typo!  "fqdni" should read "fqdn".  In any case, you have to fix it first, but apparently you can't use sudo to do it, so copy down the correct line onto paper, reboot, go into recovery mode.  this will take you to a root terminal.  type

EITHER:
vim /etc/sudoers
press i to enter insert mode, fix your typo, press 'esc', ZZ.  Done!  Reboot and sudo should work again for you.
OR:
pico /etc/sudoers 
this might be more natural to you.  I like vim, but many do not. pico is more intuitive.[/quote] 
Fixed! Many thanks.
:D

---

### Post by missmoondog on 2006-05-17
when i do this part "Save and exit by pressing the escape key followed by ZZ (that is the shift key+2 presses of the z key)" it just types 1 of the Z' in there and does nothing after that. when i colse and reopen the file, it is not saved correctly. i see that after pressing z the first time, a line pops up saying suspend disabled right above the list of keystroke options.

---

### Post by SqRt7744 on 2006-05-17
[QUOTE=missmoondog]when i do this part "Save and exit by pressing the escape key followed by ZZ (that is the shift key+2 presses of the z key)" it just types 1 of the Z' in there and does nothing after that. when i colse and reopen the file, it is not saved correctly. i see that after pressing z the first time, a line pops up saying suspend disabled right above the list of keystroke options.[/QUOTE]

Did you remember to press escape first?  In the bottom left hand corner it says "-- INSERT --" if it is in insert mode (i.e. you pressed 'i' previously).  When you press escape, it takes you into command mode, and the INSERT message disappears.  You can then either type two capital ZZ's to save and exit, or do it more explicity by typing ":wq" without the quotes.

Though it could also be that your default editor is not vim but something else, like PICO.  If so, use the commands specific to your editor to save and quit.  My instructions pertain only to vim.

---

### Post by chadk on 2006-05-17
I did this same thing, had to reboot and go into recover mode then vi /etc/sudoers to fix it back to fqdn (my mistake was removing the "n" making it fqd)

Anyway, I DO have firestarter installed:
```
chad@figment:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
firestarter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

but even after I do this:
```
chad@figment:~$ sudo apt-get remove firestarter
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firestarter
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1950kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 67891 files and directories currently installed.)
Removing firestarter ...

```
I still get that PASSWORD prompt when I log in (for firestarter) -- even though I remove it from my session EVERY time I log in.  I can't seem to get rid of this thing. lol

---

### Post by SqRt7744 on 2006-05-17
> 
I still get that PASSWORD prompt when I log in (for firestarter) -- even though I remove it from my session EVERY time I log in.  I can't seem to get rid of this thing. lol

Interesting.  Actually, I'm amazed that this hasn't worked for you at all.  Maybe it's because you're using Breezy...  Anyway, open system->preferences->session, and delete firestarter from the the "current session" and "Startup programs" tabs.  The reason why it is coming up with a box asking you for a password must be because you are loading it with "gksudo firestarter" rather than "sudo firestarter".  If you follow the instructions carefully again from the beginning, after reinstalling firestarter, I would be very surprised if you had any further issues.

In the *worst case*, rename ~/.gnome2/sessions to ~/.gnome2/old.sessions or something like that and log out and back in.

btw, i like your "linux hates me" tag :)

---

### Post by woedend on 2006-05-17
[QUOTE=missmoondog]when i do this part "Save and exit by pressing the escape key followed by ZZ (that is the shift key+2 presses of the z key)" it just types 1 of the Z' in there and does nothing after that. when i colse and reopen the file, it is not saved correctly. i see that after pressing z the first time, a line pops up saying suspend disabled right above the list of keystroke options.[/QUOTE]


For some reason visudo uses nano for me, although a cpl weeks ago it was fine(i dont like nano and never use it)...and ZZ didn't do anything for me either.  If that's the case for you, I had to push ctrl + o, it asks you where to save the file, you want it to be /etc/sudoers.

---

### Post by SqRt7744 on 2006-05-17
[QUOTE=woedend]For some reason visudo uses nano for me, although a cpl weeks ago it was fine(i dont like nano and never use it)...and ZZ didn't do anything for me either.  If that's the case for you, I had to push ctrl + o, it asks you where to save the file, you want it to be /etc/sudoers.[/QUOTE]

Yeah, I just noticed that myself.  Normally vi or vim is the default editor, however, if you once load nano, it makes itself the default and when you then type "sudo visudo", the default editor nano is used instead of vi.  Annoying.  Easy to fix though, you just have to set the default editor environment variable back to vim or whatever.  I can't remember the syntax atm, but it's something like
export EDITOR="vim"
you'll have to try and see, i have to head out!  good luck.  I'll add that to the how-to later on to ensure people are using vim and don't run into that problem.

EDIT: updated how-to to ensure vim is used!

---

### Post by saphil on 2006-05-17
You can also just 
sudo vi sudoers 
and fix it there.  (though there is a persistent notion floating about that you can't) In xNIX, everything is just a file.
my favoured one is 
sudo pico filename.  It is a bit friendlier, though not as powerful as vi

---

### Post by missmoondog on 2006-05-18
just installed dapper on another machine. on this machine everything was going good until the very end. i get this on here

Warning: undeclared Cmnd_Alias `NOPASSWD' referenced near line 19
>>> sudoers file: syntax error, line 18 <<<
What now?

edit:
oops! dang it, forgot the :

edit 2:
firestarter still doesn't start after a fresh start or rebooting but will start without any prompts after i logout and log back in.

---

### Post by SqRt7744 on 2006-05-18
[QUOTE=missmoondog]
firestarter still doesn't start after a fresh start or rebooting but will start without any prompts after i logout and log back in.[/QUOTE]

Honestly I don't know what the problem is...  does it not start at all after a reboot?  You can check with
```
sudo /etc/init.d/firestarter status
```
In any case if you're having this much trouble getting firestarter working I wouldn't bother.  As has already been pointed out, this is really only for a graphical interface, not really of critical importance.  Cut your losses and move on!  :)

---

### Post by woedend on 2006-05-18
wait wait...don't confuse firestarter with the firestarter gui.
I just want to make sure we're on the same lines.  Normally, firestarter is loaded automatically on boot.  And the only way to make sure of that is to do what sqrt has suggested.  The gui is not loaded.   If the gui is what you are having trouble with... is gksudo firestarter on your gnome session list for startup?

---

### Post by missmoondog on 2006-05-19
yes, i am aware of the fact firestarter (the firewall) starts at bootup. i just like the icon in the tray.

no, it (the gui) does not start after reboot. only after logging in, back out and then back in.

---

### Post by SqRt7744 on 2006-05-19
[QUOTE=missmoondog]
no, it (the gui) does not start after reboot. only after logging in, back out and then back in.[/QUOTE]

It's probably micro$oft throwing monkey wrenches at your computer.  No, seriously, I have no explanations.  It works fine on both my computers...  Sorry about that!

---

### Post by helpme on 2006-05-19
Isn't running an application by default as root without a password a rather not so brilliant idea?
Especially if this application is a security sensitive application and it's not even needed to run in order to have what the application provides?

I mean, this is a security tool, why go to this length to make it as insecure as possible?

---

### Post by SqRt7744 on 2006-05-19
[QUOTE=helpme]Isn't running an application by default as root without a password a rather not so brilliant idea?
Especially if this application is a security sensitive application and it's not even needed to run in order to have what the application provides?

I mean, this is a security tool, why go to this length to make it as insecure as possible?[/QUOTE]

Well, we are only giving this one application root priviledges, and since it won't run without them, we have no choice.  As for the no-password requirement, we know what we are starting, so why should we need to enter a password each time?  It is redundant to ask the user the same question for the same app each time the user logs in.  This is the reason why the sudoers file exists, to eliminate such redundancies and allow users to perform certain root tasks.  The changes to the sudoers file are also necessary to allow a sudo'd program to connect to the X server, also a necessary requirement to run the firestarter GUI.  If you think this is insecure, take it up with the firestarter/sudo people, for there is no other way to run their app.  
Actually this is all pretty basic stuff, I don't think we are going to any great length as your post seems to imply.

---

### Post by missmoondog on 2006-05-21
don't know why i tried this on another machine as i believe this is what causing all my problems of nothing starting under sytem/administration unless i go through terminal now. i have another thread going on that issue already.

how do i go back to editing the sudoers list? when i type in the 
export VISUAL="vim"
sudo visudo
commands and type "i" it either just enters an "i" or pops up "automatically indent" at the bottom.

---

### Post by missmoondog on 2006-05-21
[QUOTE=MasterChief1234]Thanks for this tutorial. Firestarter will finally start automatically :) 
Edit: I get an Xlib display error when launching synptic/update manager. I had to reboot into recovery mode and edit my sudoers file to fix it. Is this a problem with my install or does adding to the defaults of the sudoers file cause this ?[/QUOTE]

yes, i can confirm this is an issue. i just tried this on my second computer and after foobarring my programs in the system/administration, i restarted in recovery mode and edited the sudoers list. now, at least synaptic and everything else in the section of progrmas starts the gui when clicked.

---

### Post by SqRt7744 on 2006-05-22
[QUOTE=missmoondog]
how do i go back to editing the sudoers list? when i type in the 
export VISUAL="vim"
sudo visudo
commands and type "i" it either just enters an "i" or pops up "automatically indent" at the bottom.[/QUOTE]

It sounds like visudo isn't using vim even though you are specifically telling it to with the export VISUAL="vim" command.  From your description it's probably nano or pico.  That's odd, but no big deal.  Just edit the file with that editor and save it (ctrl-X) i believe.  No need to press 'i' and 'esc' to switch between command and insert mode, this only works with vim or vi.

Also, one of my first posts in this thread explains how to install xlibs with wget.  If you're getting that xlib error message, you may want to try that.

---

### Post by missmoondog on 2006-05-22
[QUOTE=SqRt7744]It sounds like visudo isn't using vim even though you are specifically telling it to with the export VISUAL="vim" command.  From your description it's probably nano or pico.  That's odd, but no big deal.  Just edit the file with that editor and save it (ctrl-X) i believe.  No need to press 'i' and 'esc' to switch between command and insert mode, this only works with vim or vi.

Also, one of my first posts in this thread explains how to install xlibs with wget.  If you're getting that xlib error message, you may want to try that.[/QUOTE]

what's really odd is that when i originally edit the file, it works using the commands you say to use. once it's edited and saved, i can't and couldn't do anything with it using that code again.

not going though all the changes to change editors or even trying this trick again, but i really do appreciate the help.

thank you

---

### Post by helpme on 2006-05-23
[QUOTE=SqRt7744]Well, we are only giving this one application root priviledges, and since it won't run without them, we have no choice.  
[/QUOTE]
But that's the problem. The firewall runs just fine in the background. 

Firestarter is simply a gui to configure it and to get some information and as such its only reasonable that only root can run it.
The solution is obvious, just run it manually when you need it, everything else is a bad idea securitywise and after all, running a firewall in the first place is about security, isn't it?

---

### Post by SqRt7744 on 2006-05-23
[QUOTE=helpme]
The solution is obvious, just run it manually when you need it, everything else is a bad idea securitywise and after all, running a firewall in the first place is about security, isn't it?[/QUOTE]

It seems you take issue with firestarter itself? I haven't heard about any actual security problems.  In any case I like to have it running all the time, as it is a handy network monitor and provides me with an easy interface for quickly opening/closing ports, which I do quite frequently.  I also like being able to monitor all current open connections, look up hostnames, and block certain IP's/ranges.  I am aware that this can all be accomplished from the command line however many people prefer the interface provided by firestarter.

---

### Post by helpme on 2006-05-24
[QUOTE=SqRt7744]It seems you take issue with firestarter itself? [/QUOTE]
No, not at all.
In fact, I really like firestarter.

But firestarter is a security tool that should be used accordingly. It has the potential to seriously compromise your security, after all, it's a tool to configure your firewall, so making it run automatically, as root, without a password simply is a bad idea securitywise.

---

### Post by missmoondog on 2006-05-24
it's only bad security wise IF you have some lame and feeble password. otherwise, that issue is not even close to important for me. as was stated by sqrt7744, i like to have the gui in the tray for monitoring things with just the one click instead of that jumping through hoops with terminal just to look at that.

now, after all has been said and done, i will just leave it as is, default install, and load it manually everytime. at least until after dapper final is out and this issue has been fixed.

thanks for all the help folks.

---

### Post by panurge77 on 2006-05-24
Two things: 
1- firestarter only appears at panel after a first event is logged (that does not make a problem)
2- gksudo got broken (synaptic, updates etc wont start now)

:-?

---

### Post by SqRt7744 on 2006-05-24
[QUOTE=panurge77]Two things: 
1- firestarter only appears at panel after a first event is logged (that does not make a problem)
2- gksudo got broken (synaptic, updates etc wont start now)

:-?[/QUOTE]

it sounds to me like there is a typo in your sudoers file.  Look back to the first page, I posted a copy of my file.  make sure yours is identical.  If you are having trouble with the vim editor it should be okay to edit /etc/sudoers with gedit even though it claims you shouldn't.  Any sudo/gksudo usage will terminate with an error if there is a typo in your sudoers file.  Be sure you are autostarting firestarter with sudo and not gksudo.

---

### Post by panurge77 on 2006-05-25
I copied everything to avoid typos. I tried both sudo and gksudo.

---

### Post by SqRt7744 on 2006-05-25
[QUOTE=panurge77]I copied everything to avoid typos. I tried both sudo and gksudo.[/QUOTE]

Did you install xlibs (see post on first page)? Also, you say you copied everything, but did you remember to change "sqrt7744" to you own username?

If you can't get it to work, boot into recovery mode and edit /etc/sudoers back to its original state, i.e. remove the extra stuff on the defaults line (env_reset,env_keep+="DISPLAY HOME XAUTHORIZATION") and comment out the firestarter line at the bottom (by putting # in front of it).

---

### Post by panurge77 on 2006-05-25
Yes, I've changed the username and I've also restored the file to the original. So things are back to normality. It was probably the xlibs that was missing.

floyd@tchs:~$ sudo apt-get install xlibs
Reading package lists... Done
Building dependency tree... Done
Package xlibs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxft1 xkeyboard-config
E: Package xlibs has no installation candidate

---

### Post by SqRt7744 on 2006-05-25
[QUOTE=panurge77]Yes, I've changed the username and I've also restored the file to the original. So things are back to normality. It was probably the xlibs that was missing.
[/QUOTE]

see this post to install xlibs: [http://www.ubuntuforums.org/showpost.php?p=1024529&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1024529&postcount=5)

---

