---
title: "How to scroll one page with the mouse-wheel?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Markstar on 2008-10-20
Hi,

I'm new to Ubuntu and I was wondering where the option is to enable the option to scroll one page at a time is??? 

Scrolling a few lines at a time is really annoying...

Thanks in advance!

Kind regards
  Markstar

---

### Post by arikshtiv on 2008-10-20
in what program?

---

### Post by stinger30au on 2008-10-20
if u are talking firefox it will do it if u turn the scroll wheel on you mouse fast enough. my pc does it all the time and its really annoying

---

### Post by a0u on 2008-10-20
It's important to note that there really isn't (yet) any entirely clean way to globally set the mouse scroll speed.  X treats a scrolling action as a button press event; it's up to the application itself to choose how to respond to that.  Thus, you may have to change the settings for each application individually, so you have to let us know which program you need adjusted.

---

### Post by Markstar on 2008-10-20
> **arikshtiv said:**
> in what program?In all programs! :)

@stinger: That does not sound like a very elegant solution. All I want is to scroll one page with every step of the mouse-wheel. :(

**Edit:**@a0u: That sound messy! :( 

So there is no easy way to do this? That would be very unfortunate! :cry:

---

### Post by a0u on 2008-10-20
> **Markstar said:**
> In all programs! :)

@stinger: That does not sound like a very elegant solution. All I want is to scroll one page with every step of the mouse-wheel. :(

**Edit:**@a0u: That sound messy! :( 

So there is no easy way to do this? That would be very unfortunate! :cry:

Apparently there are [a few options]("http://ubuntuforums.org/showpost.php?p=5632975&postcount=8") you can include in xorg.conf.  Looking through archived threads, it seems that it works for some users but not all.  It's still worth a try, though.

However...if you are looking to scroll up/down one page (as in a page length), couldn't you simply use the Page Up / Page Down keys?

---

### Post by kaibob on 2008-10-20
I don't know of a way to do what you want with all applications. You can do this with Firefox by changing the mousewheel.withnokey.action option:

[http://kb.mozillazine.org/About:config_entries](http://kb.mozillazine.org/About:config_entries)

EDIT: Well, for some reason, the link won't work. Do a google search on...

firefox about:config

...and the first result is the correct page.

---

### Post by Markstar on 2008-10-21
@aOu: Sadly this didn't work (even after restarting). :(

@kaibob: Thanks, but I was really hoping I could get this to work in all applications. Furthermore, scrolling by a certain amount of lines is pretty imprecise, isn't it?

---

### Post by philinux on 2008-10-21
I just use page down/up. At least this works in all programs. LOL

---

### Post by wizard10000 on 2008-10-21
> **a0u said:**
> ...couldn't you simply use the Page Up / Page Down keys?

Or assign PgUp/PgDn to the mousewheel with xbindkeys :)

---

### Post by Markstar on 2008-10-21
Since I have my right hand on the mouse most of the time, pressing PgUp/PgDn all the time is rather inconvenient. ;)

 > **wizard10000 said:**
> Or assign PgUp/PgDn to the mousewheel with xbindkeys :)Hmm, good idea. I think I will do that (as soon as I figure out how to do that), even if it is not an optimal solution.

---

### Post by kaibob on 2008-10-21
> **Markstar said:**
> @kaibob: Thanks, but I was really hoping I could get this to work in all applications. Furthermore, scrolling by a certain amount of lines is pretty imprecise, isn't it?

The Firefox about:config option I mentioned is labeled "scroll document by one page." A more precise description would probably be scroll document by one screen. There is a different option labeled "scroll document by a number of lines", and that is not what you're looking for. 

The issue you raise (scrolling a page at a time in all applications) has been discussed in this forum a number of times over the past few years, and I don't recall anyone having a solution. Perhaps someone will see this post and have a suggestion. Perhaps xbindkeys is the answer. 

Sorry I couldn't help.

---

### Post by Markstar on 2008-10-21
> **kaibob said:**
> The Firefox about:config option I mentioned is labeled "scroll document by one page." A more precise description would probably be scroll document by one screen. There is a different option labeled "scroll document by a number of lines", and that is not what you're looking for. 

The issue you raise (scrolling a page at a time in all applications) has been discussed in this forum a number of times over the past few years, and I don't recall anyone having a solution.Maybe because all Linux gurus only use the keyboard. :p

> Perhaps someone will see this post and have a suggestion. Perhaps xbindkeys is the answer. 

Sorry I couldn't help.No problem, I still appreciate the effort to come to a forum and help out ignorant people like me! 

Anyways, now it would be nice if I could figure out how to get xbindkeys to work. I installed the packages (including the config), but 
a) I don't know what to do
b) when I "New" at the bottom and then go to "Get Key", the application crashes:
```
markstar@HA06:~$ sudo xbindkeys-config 
open file: No such file or directory
xbindkeys: no process killed
Error : /home/markstar/.xbindkeysrc not found or reading not allowed.
please, create one with 'xbindkeys --defaults > /home/markstar/.xbindkeysrc'.
or, if you want scheme configuration style,
with 'xbindkeys --defaults-guile > /home/markstar/.xbindkeysrc.scm'.
Segmentation fault
``` :(

---

### Post by wizard10000 on 2008-10-21
> **Markstar said:**
> ...b) when I "New" at the bottom and then go to "Get Key", the application crashes

Open a terminal window and type this - 

xbindkeys --defaults > /home/markstar/.xbindkeysrc

then smack the enter key.  That'll create the default configuration file xbindkeys is looking for.

---

### Post by Markstar on 2008-10-21
Alright, I did that and it seems I can do stuff now...though I'm still not sure how.

I tried:
1. "New" at the bottom 
2. Enter name for the new command ("PageUp")
3. Press "Get Key" -> a new window opens asking me to hit a key
3.1 What do I do now??? When I scroll the mouse-wheel up nothing happens. :(

Keys seem to work (the text field "Key" gets modified), but I'm not even sure what I'm supposed to do next...how do I tell it to go one page up/down in all applications?

Sorry, I'm pretty lost right now.

---

### Post by wizard10000 on 2008-10-21
> **Markstar said:**
> Alright, I did that and it seems I can do stuff now...though I'm still not sure how.

I tried:
1. "New" at the bottom 
2. Enter name for the new command ("PageUp")
3. Press "Get Key" -> a new window opens asking me to hit a key
3.1 What do I do now??? When I scroll the mouse-wheel up nothing happens. :(

Keys seem to work (the text field "Key" gets modified), but I'm not even sure what I'm supposed to do next...how do I tell it to go one page up/down in all applications?

Sorry, I'm pretty lost right now.

My bad - you'll also need xvkbd.  Look here - 

[http://www.linuxquestions.org/questions/slackware-14/how-to-swap-mouse-buttons-in-xbindkeys-since-slackwares-xmodmap-aint-working-4-me-489285/](http://www.linuxquestions.org/questions/slackware-14/how-to-swap-mouse-buttons-in-xbindkeys-since-slackwares-xmodmap-aint-working-4-me-489285/)

Here's where to start -

> #the following line make button 8 of my mouse issue the Alt Key & Left Arrow key
"/usr/bin/X11/xvkbd -xsendevent -text "\[Alt]\[left]""
m:0x0 + b:8
#the following line make button 8 of my mouse issue the Alt Key & Right Arrow key
"/usr/bin/X11/xvkbd -xsendevent -text "\[Alt]\[right]""
m:0x0 + b:9

Your scrollwheel would be b:4 and b:5 - then all you'd need is the keyboard commands for PgUp and PgDn  :)

---

### Post by wizard10000 on 2008-10-22
Okay, I got it working.  Here's a quick and dirty readme -

1.  Install xbindkeys, xbindkeys-config and xvkbd,

2.  Create xbindkeys config file by running

xbindkeys --defaults > ~/.xbindkeysrc

3.  Add the following to ~/.xbindkeysrc -

```
#mousewheel page up
"xvkbd -text "\[Prior]""
  b:4

#mousewheel page down
"xvkbd -text "\[Next]""
  b:5
```

4.  Test by running xbindkeys - if you're happy with the way things work add xbindkeys to your session under System --> Preferences --> Sessions --> Startup Programs.  Click the "Add" button and fill in the information there.

I did find that on startup xbindkeys is a little quirky - the first time I tried to scroll down after starting it it went all the way to the bottom of the page but after that it worked fine.

Have fun -

---

### Post by wizard10000 on 2008-10-22
Meh.  I had it working and now it doesn't.

Back to the drawing board  :)

---

### Post by Markstar on 2008-10-22
Oh, too bad. I was just about to try it out (I installed xbindkeys and xbindkeys-config yesterday, but couldn't get it to work. :(

---

### Post by steveneddy on 2008-10-31
> **Markstar said:**
> Oh, too bad. I was just about to try it out (I installed xbindkeys and xbindkeys-config yesterday, but couldn't get it to work. :(

You might try BTNX.

It is a mouse button config tool that you could assign keyboard buttons to on the mouse, including the mouse wheel.

---

