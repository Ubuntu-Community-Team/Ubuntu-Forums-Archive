---
title: "No cursor in Terminal Ubuntu 12:04"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by Decani on 2012-06-09
Hi,

I would appreciate some help please. I am using Ubuntu 12:04, but I am having a problem with the Terminal. I can open it up ok, but there's no cursor (terminal prompt). As you can guess, this is a real nuisance because it makes it impossible for me to type entries. 

Any help for a newbie would be greatly appreciated.

Many thanks.

Decani.:(

---

### Post by vasa1 on 2012-06-10
> **Decani said:**
> Hi,

I would appreciate some help please. I am using Ubuntu 12:04, but I am having a problem with the Terminal. I can open it up ok, but there's no cursor (terminal prompt). As you can guess, this is a real nuisance because it makes it impossible for me to type entries. 

Any help for a newbie would be greatly appreciated.

Many thanks.

Decani.:(

It's hard to say but it certainly is because of some "tweak" you have applied. If you let people know what mods you have made, someone may be able to help. Don't omit mods because you may think they aren't related to your problem.

---

### Post by tjacks on 2012-12-22
I have had the same problem and i had made no "tweaks" before it stopped working.

---

### Post by tjacks on 2012-12-24
Bump, this really becoming a problem. I use terminal alot.

---

### Post by ibjsb4 on 2012-12-24
What has happen to me in the past was a blank terminal screen.  For some reason black on black was default and just needed to be changed.

You could also create a new profile ( under edit>profiles) and see if that gets you anywhere.

---

### Post by Dennis N on 2012-12-24
> **tjacks said:**
> Bump, this really becoming a problem. I use terminal alot.

There is a command to turn the cursor on or off, but it only works during the current session (until you quit the terminal). Still, you can try it to see if the cursor can be turned on:

Start the terminal and enter the command

```
setterm -cursor on
```

If by some chance this should work, the command could be placed in ~/.bashrc or ~/.bash_aliases to automatcally insure it comes on.

---

### Post by vasa1 on 2012-12-24
> **Dennis N said:**
> ...
If by some chance this should work, the command could be placed in ~/.bashrc or ~/.bash_aliases to automatcally insure it comes on.
How would putting the command in ~/.bash_aliases help?

---

### Post by Dennis N on 2012-12-24
> **vasa1 said:**
> How would putting the command in ~/.bash_aliases help?

The terminal reads this file every time it starts up. It is intended for your alias definitions, but other commands can be placed there, such as altering $PATH


Edit: It may need to be created by the user. Look at .bashrc and you see the reference to it. It is read only if present.

---

### Post by vasa1 on 2012-12-24
> **Dennis N said:**
> The terminal reads this file every time it starts up. It is intended for your alias definitions, but other commands can be placed there, such as altering $PATH
Okay, thanks! Just tried it and it works perfectly. Learned something new :)

---

### Post by Dennis N on 2012-12-24
If the suggestion in post #6 does not work, I would suggest you try purging and reinstalling the terminal (probably gnome-terminal). 

Should that fail to correct the problem, another idea is to install a different terminal along with or in place of your existing one:

try **lxterminal** or **xfce4-terminal**

One of those might work for you.

---

### Post by Mukumbu on 2012-12-30
> **ibjsb4 said:**
> What has happen to me in the past was a blank terminal screen.  For some reason black on black was default and just needed to be changed.

You could also create a new profile ( under edit>profiles) and see if that gets you anywhere.
this worked for me.  After opening terminal, I went into the settings and un checked "use default theme" on the colors tab in Profile Settings on the Edit menu.

Thank you.

---

