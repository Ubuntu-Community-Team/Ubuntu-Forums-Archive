---
title: "Easy GTK question here"
date: 2007-12-08
forum: Programming Talk
---

### Post by jimmy the saint on 2007-12-08
I am rewriting this for brevity.
I need to know how difficult it would be for someone with limited knowledge of programing to create a front end for a simple command line program.

I have put together a few we pages, so I am somewhat familiar with html, but that's about it.

The program I have in mind is atitvout; a simple program that only has a few commands.  Essentially, I would be creating a gui that needs to issue a single command with a variety of options.  I figure a button with some check boxes underneath should do the trick.  Or maybe even a few buttons to it since there are only a few combinations i need.

Could someone with my low level of experience do this?  what would be the best approach?  what do I need?


Thank you.

---

### Post by LaRoza on 2007-12-09
Python + EasyGUI

See my wiki.

---

### Post by jimmy the saint on 2007-12-09
So I would definitely need to learn a language.  I was kind of hoping there would be a way to just fill in a textbox with the command to send to the terminal!!  Things are rarely that easy I am learning.  Oh well.  Thanks for the suggestion.  I guess Im going to learn something new!

---

### Post by Murk on 2007-12-09
I think what you only need is zenity, it is used to display gtk+ dialogs.

try zenity --entry --title="demo" --text="input something here:"

---

