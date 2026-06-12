---
title: "[SOLVED] Multiple select with ctrl-click not working ?!"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Roelski on 2008-10-15
Hi all,

I'm encountering the following strange problem using Ubuntu 8.04.

Logged in properly under my own account, I can't select multiple non-adjacent items on the desktop, in nautilus or excel (oops... OoSpreadsheet, that is).  This would typically be done by holding down the ctrl (control) key, while clicking different items.

E.g.: files A, B, C, D in a row - to select A & C: click A, hold ctrl down and click C.  B is not selected.

What did I check:
- the key is working properly, as it works to set text to bold in OoWriter (you know... Word), ctrl-alt-del (to log out), etc.  Seems not to be a harware failure.
- moreover: when logging in under my wife's profile, ctrl-click works just as expected...
- I'm running 8.04 with all the latest updates, although I don't recall having the problem under 7.10.
- I haven't changed any of the Gnome-settings (such as themes, pointers, behaviour,...) for as far as I know.  I use ubuntu "as is".

Conclusion: not withstanding the last bullet above, I guess this is related to my Gnome / Nautilus settings, which I may have changed unintentionally... but i dunno how I did it, nor how to reverse it.

Question:
- any comments? 
- any suggested checks to run?
- any solutions? (you never know?)
- does this sound familiar to anyone?

Thanks for any help.

Best regs,


Roelski

---

### Post by jamesrl on 2008-10-15
Ignore this; I didn't read carefully enough.  Jerome1232 is right, that is the normal ctrl behavior.
[I]Seems like you should be able to nail this down, as your wife's account works.  
First guess would be to check that the System->Preferences->keyboard layout is the same between your wife's account and you.

Next idea is to see how different gconf settings are between you.  
In both accounts, run

```

gconftool-2 --dump / > my_gconf_settings

```
(gconftool-2 --dump lists all the settings in the gnome conf editor, you can see them in a GUI format with gconf-editor)
and then compare the two files
```

diff ~/my_gconf_settings ~wife/my_gconf_settings

```
and see if there's anything in there that seems like a clue.[/I]

---

### Post by jerome1232 on 2008-10-15
Wait reading your post it sounds like normal behavior.

A B C

If you click A, then hold ctrl and click C then only A and C should be selected

If you click A, then hold shift and click C then A B and C should be selected.

This is the way it has always been.

---

### Post by Roelski on 2008-10-16
Hmm, didn't make myself clear enoug to you - my mistake and i apologize.

> **Roelski said:**
> 
E.g.: files A, B, C, D in a row - to select A & C: click A, hold ctrl down and click C.  B is not selected.


This is indeed the expected behaviour, but what happens is:

> click A, hold ctrl, click C = only A stays selected and nothing happens with C.


On the other: shift-clicking for adjacent files works fine.

I'll try JamesRL's suggestion later tonight and add to this post.

Thx for your answers,


Roelski

---

### Post by Roelski on 2008-10-16
Okay, here's the short of the story...

I tried JamesRL's suggestion and managed to export both my own and my wife's settings.  The diff-thing also worked fine.

Problem is that the diff-file is 1300 lines... and also mentions some really private data (like email adresses, SSIDs, etc).  I'm willing to share this with you on a private basis, but I'd rather not publish the files on the web. Pls send me a pm if you're still willing to help me and I will send over the files (assuming you are trustworthy...)

Btw, the keyboard layouts are the same in both accounts (Belgium, default).

I can think of another issue:  I've been "carrying along" my entire home-folder (including all hidden folders) since Dapper. It's on separate partition, which allows me to easily erase the OS partition for a clean install.  This comes out pretty handy since all my settings are kept from Dapper to Edgy, Feisty and now Hardy.

However, I've now started thinking that this method may have corrupted some of my settings...  

- Would such reasoning make sense?  
- And if: is there a work-around to do a specific "clean-up" of the settings?  (that is: i'm will to loose anything, except docs, mails, pw's, logins, etc, but don't bother about lay-outs of menu's, color schemes, etc.)

Looking forward to your comments,



Roelski

---

### Post by Roelski on 2008-10-16
Hi guys,

I solved the problem in a less fashionable way. 

I found out in several internet posts that Gnome can be reset by deleting or renaming the following hidden folders:

- .gconf*
- .gnome*
- .metacity

I added OLD- to all of them and fully rebooted my system.  Got back online quickly after it and only had to reset my mail account settings in Evolution, desktop picture, and a few limited other settings.

Rest seems to be working fine... and CTRL-key is behaving as expected.

Thanks for the support!
Have a great weekend (I took a day off !) :guitar:

---

### Post by Shadowking on 2009-07-05
> **Roelski said:**
> Hi all,

I'm encountering the following strange problem using Ubuntu 8.04.

Logged in properly under my own account, I can't select multiple non-adjacent items on the desktop, in nautilus or excel (oops... OoSpreadsheet, that is).  This would typically be done by holding down the ctrl (control) key, while clicking different items.

E.g.: files A, B, C, D in a row - to select A & C: click A, hold ctrl down and click C.  B is not selected.

What did I check:
- the key is working properly, as it works to set text to bold in OoWriter (you know... Word), ctrl-alt-del (to log out), etc.  Seems not to be a harware failure.
- moreover: when logging in under my wife's profile, ctrl-click works just as expected...
- I'm running 8.04 with all the latest updates, although I don't recall having the problem under 7.10.
- I haven't changed any of the Gnome-settings (such as themes, pointers, behaviour,...) for as far as I know.  I use ubuntu "as is".

Conclusion: not withstanding the last bullet above, I guess this is related to my Gnome / Nautilus settings, which I may have changed unintentionally... but i dunno how I did it, nor how to reverse it.

Question:
- any comments? 
- any suggested checks to run?
- any solutions? (you never know?)
- does this sound familiar to anyone?

Thanks for any help.

Best regs,


Roelski

I don't know how this was solved, but I solved it this way.

System -> Preferences -> Windows -> Movement Key -> CTRL was selected.
I changed it to the Windows key.

Done!

---

