---
title: "[SOLVED] LAMPP for Hardy??"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Joe Dinmore on 2008-07-08
I´ve installed Hardy; now I want a LAMPP. I dimly remember from Feisty that there was a magic incantation you could type into Synaptic Package Manager to accomplish an ¨all in one¨ download.
Can someone tell me what is is? I use it to develop web pages in PHP.

- And can anyone tell me why I have to type TWO ´ (apostrophe) to get one to work? Wasn a problem with Fiesty ...

---

### Post by ChameleonDave on 2008-07-08
> **Joe Dinmore said:**
> I´ve installed Hardy; now I want a LAMPP. I dimly remember from Feisty that there was a magic incantation you could type into Synaptic Package Manager to accomplish an ¨all in one¨ download.
Can someone tell me what is is? I use it to develop web pages in PHP.

- And can anyone tell me why I have to type TWO ´ (apostrophe) to get one to work? Wasn a problem with Fiesty ...

What exactly do you mean by "LAMPP"?

What you call an apostrophe (') is actually an acute accent (´).  Also, you are using umlauts (¨) instead of double quotation marks (").  That would indicate that your keyboard is not properly set up, or that you are using it wrongly.  That could affect any commands that you type in, because it is essential to get them exactly right.

Your other question is impossible to answer because it seems to refer to some guide that you are following, but we can't know what you are talking about unless you tell us.

---

### Post by Joe Dinmore on 2008-07-08
> **ChameleonDave said:**
> What exactly do you mean by "LAMPP"?



What you call an apostrophe (') is actually an acute accent (´).  Also, you are using umlauts (¨) instead of double quotation marks (").  That would indicate that your keyboard is not properly set up, or that you are using it wrongly.  That could affect any commands that you type in, because it is essential to get them exactly right.

Your other question is impossible to answer because it seems to refer to some guide that you are following, but we can't know what you are talking about unless you tell us.

LAMPP = Linux, Apache, MySQL, PHP, Perl.
Sorry, I thought that was a really common acronym.

Re keyboard problems. when I hit the key just to the right of the colon/semicolon key, nothing appears onscreen. I need to hit it twice to get anything to show up. You´re right - it IS a problem, one which I have never expereinced before. Do you have any suggestions for fixing it?
This is a new installation of Hardy.

---

### Post by alloftheabove on 2008-07-08
I have not a clue to solve your keyboard troubles, however lampp is more commonly known as xampp for linux.  If you really want lampp/xampp you may as well go to the installation page [http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html").  You won't need single or double quotes to get it extracted or to start it.

Actually, you could check your keyboard preferences.  System > preferences > keyboard.  A window with tabs will pop up, check the layout tab, it will list the layout(s?) you are currently using.  If you need to change the layout, click on add and select your layout from the dropdown.  You probably will need to click the bubble to tell ubuntu that you want to use that layout as the default.  The button is to the right of the layout list in the layout tab.  If I'm confusing you, don't be afraid to have me clarify.

---

### Post by dmizer on 2008-07-08
```
sudo aptitude install lamp-server
```

you'll have to install pearl separately.

---

### Post by ChameleonDave on 2008-07-08
> **Joe Dinmore said:**
> 
Re keyboard problems. when I hit the key just to the right of the colon/semicolon key, nothing appears onscreen. I need to hit it twice to get anything to show up. You´re right - it IS a problem, one which I have never expereinced before. Do you have any suggestions for fixing it?

You must have chosen "US-international" as your keyboard layout when you installed Hardy.  The correct way to use US-international is to press space after those keys, rather than pressing those keys twice.

It is quite a hassle.  It's only worth the effort if you habitually enter a large number of accents when you type, e.g. if you write French every day.

If you don't need special characters so frequently, then the "Alt-Gr" variant of US-international is preferable.  That what I use.  With that one, accents don't come up unless you use the Alt-Gr key.  In other word, if you never press the Alt-Gr key, that layout functions identically to the "United States" keyboard layout without any special characters.

See also:
[http://en.wikipedia.org/wiki/Keyboard_layout#US-International](http://en.wikipedia.org/wiki/Keyboard_layout#US-International)
[http://en.wikipedia.org/wiki/AltGr_key](http://en.wikipedia.org/wiki/AltGr_key)

Each desktop environment has a GUI for choosing keyboard layouts, usually under regional and language settings.

---

### Post by alloftheabove on 2008-07-08
How do you get those special letters and symbols using a standard us keyboard?

EDIT:  That question was for chameleonDave.

---

### Post by Joe Dinmore on 2008-07-08
> **dmizer said:**
> ```
sudo aptitude install lamp-server
```

you'll have to install pearl separately.

That's it! bewdy. Thank you for that.

---

### Post by Joe Dinmore on 2008-07-08
> **ChameleonDave said:**
> I must have chosen "US-international" as your keyboard layout when you installed Hardy.  The correct way to use US-international is to press space after those keys, rather than pressing those keys twice.

It is quite a hassle.  It's only worth the effort if you habitually enter a large number of accents when you type, e.g. if you write French every day.

If you don't need special characters so frequently, then the "Alt-Gr" variant of US-international is preferable.  That what I use.  With that one, accents don't come up unless you use the Alt-Gr key.  In other word, if you never press the Alt-Gr key, that layout functions identically to the "United States" keyboard layout without any special characters.

Each desktop environment has a GUI for choosing keyboard layouts.
I shall try that ... 
yep! that did it. Thanks for that.

---

### Post by ChameleonDave on 2008-07-08
> **alloftheabove said:**
> How do you get those special letters and symbols using a standard us keyboard?

EDIT:  That question was for chameleonDave.

If you mean how can you get them with the standard US keyboard layout enabled, the answer is that you can't.  You must enable a layout with accents, such as US-international.

Looking at System Settings for KDE 4, I can see that it very helpfully informs the GUI user what commands are being used behind the scenes.  (I believe that all GUIs should do that!  GUIs should inform people, not dumb them down!).

```

setxkbmap -model pc104 -layout us -variant            # *Standard US layout*
setxkbmap -model pc104 -layout us -variant intl       # *This is US-international*
setxkbmap -model pc104 -layout us -variant alt-intl   # *Older alternative version of the above*
setxkbmap -model pc104 -layout us -variant altgr-intl # *This variant uses the AltGr key*

```

If you mean to ask whether you can get accents with a physical keyboard which follows the standard US layout, then yes.  Absolutely any keyboard can do so.  It doesn't matter what letters are printed on the keys.  I used to use the Spanish layout on a UK keyboard.  I now use US-international with AltGr, on a US keyboard (all keyboards are US here in Australia).

---

