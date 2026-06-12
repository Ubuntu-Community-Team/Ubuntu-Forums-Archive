---
title: "Vim and Dvorak"
date: 2008-06-29
forum: Programming Talk
---

### Post by DeathOnJuice on 2008-06-29
Do any programmers here use Vim and the Dvorak keyboard layout? If so, do you use a workaround to have QWERTY navigation keys, or just use Dvorak and not have h, j, k, and l in a row? If you do have a workaround, what is it?

Thanks.

---

### Post by dwhitney67 on 2008-06-29
I use vim w/ a qwerty keyboard.  I'm old-school, and because of such I continue to use the h, j, k, and l keys to move the cursor around.  Occasionally I remember that the arrow keys on my keyboard can be used too!  To scroll up/down, I use the scroll-area of my laptop's touch-pad or the spin-wheel of my wireless mouse.

---

### Post by DeathOnJuice on 2008-06-30
Wait, you weren't really clear. Do you use the Dvorak layout for typing? I'm not sure if you understood my question... Sorry.

---

### Post by dwhitney67 on 2008-06-30
No I do not use the Dvorak-style keyboard.  The wiki page states that its popularity has increased in recent years especially among computer programmers and others whose jobs require them to do extensive amounts of typing.

Yeah there is probably about 5 or 6 people in the entire world that use it.  (This is my opinion, which may not necessarily be true... but it is still funny!)

As for me, I have been using qwerty keyboards (both on typewriters and computer keyboards) for over 25 years.  I have been a software engineer for over 18 years of that time, and being that I'm an old-dog with thoughts of more important things on my mind than a "new" keyboard, I have no plans nor the desire to try a Dvorak keyboard.  Heck, I don't even like M$ ergo keyboard.

Btw, code monkeys may think they type a lot, but on average, only 6 lines of code are developed on a daily basis on a typical project.  Before you say "that's bull", think about it... most of the time for a typical project is spent gathering requirements, performing design work, writing test plans, QA work... and of course, fixing bugs.  The key word above is "average"... YMMV.

---

### Post by DeathOnJuice on 2008-06-30
OK, but as it is, I DO use Dvorak and this problem is still unresolved :-/ .

No one has a fix to use Dvorak in insert mode, QWERTY in the other modes?

---

### Post by dwhitney67 on 2008-06-30
I re-read your OP again (and again)... what problem are you having?  The 'h', 'j', 'k', and 'l' keys are NOT used during insert mode, unless of course you are typing a word containing these characters.

After you have Esc(aped) out of insert mode, then these keys can be used to position the cursor.  On a Dvorak keyboard, these keys are sprinkled about the keyboard, thus perhaps not making them as convenient as in a qwerty keyboard.

However, as I mentioned in on of my earlier posts, one does not necessarily have to use these keys to move the cursor around.  The arrow keys can be used in their place.  Your keyboard has arrow keys, right??

---

### Post by days_of_ruin on 2008-06-30
Just use the arrow keys.

---

### Post by DeathOnJuice on 2008-06-30
> **dwhitney67 said:**
> I re-read your OP again (and again)... what problem are you having?  The 'h', 'j', 'k', and 'l' keys are NOT used during insert mode, unless of course you are typing a word containing these characters.

After you have Esc(aped) out of insert mode, then these keys can be used to position the cursor.  On a Dvorak keyboard, these keys are sprinkled about the keyboard, thus perhaps not making them as convenient as in a qwerty keyboard.

However, as I mentioned in on of my earlier posts, one does not necessarily have to use these keys to move the cursor around.  The arrow keys can be used in their place.  Your keyboard has arrow keys, right??

Yes, that's the problem. I suppose, if there is no fix to have h, j, k, and l be in their QWERTY positions while not in insert mode, I'll just use arrow keys. A bit less efficient, but oh well.

Thanks!

---

### Post by davis152 on 2008-06-30
You can remap keys in vim if you'd like. There are some examples in these vim tips (from Google:vim dvorak):

[http://www.vim.org/tips/tip.php?tip_id=1390](http://www.vim.org/tips/tip.php?tip_id=1390)
[http://www.vim.org/tips/tip.php?tip_id=1437](http://www.vim.org/tips/tip.php?tip_id=1437)

---

### Post by kiwiburger on 2010-03-16
> **DeathOnJuice said:**
> Do any programmers here use Vim and the Dvorak keyboard layout? If so, do you use a workaround to have QWERTY navigation keys, or just use Dvorak and not have h, j, k, and l in a row? If you do have a workaround, what is it?

Thanks.

Hi 

I use the dvorak keyboard with vim....it is just a case of learning the new positions of the keys....takes a bit of time, but not too hard to do.....I started to use the new keyboard about a month ago, and I am using it exclusively now....for me the hardest part is to get used to the 'L' position. But all in all...I recommend changing.

If you still want to use the same home keys then see this link.
[http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/dvorak/node11.html](http://www.sccs.swarthmore.edu/users/03/nori/maenad/geek/dvorak/node11.html)

Have fun.

---

### Post by LKjell on 2010-03-17
You should do as Kiwiburger since a lot of programs do use the hjkl shortcuts. Not all of them you can change so it is best to learn new way to do it.

---

### Post by blur xc on 2010-03-17
It's funny this thread pop up just as I started wondering if VIM users just ignore dvorak keyboards.  Remapping keys sounds like the hot ticket.

IMO, using the arrow keys in vim is cheating.  I'm still a beginner vim user and as I understand it, the whole point is to keep your fingers on the home row as much as possible.  

BM

---

### Post by Doctor Colossus on 2011-11-18
I'm aware this is an old thread, but for any future knowledge-seekers, I want to share [the Reddit thread]("http://www.reddit.com/r/vim/comments/faowz") I found on this subject, which contains a wealth of helpful advice.

Another nice tip, [courtesy of Xah Lee]("http://xahlee.org/kbd/vi_emacs_keybinding_design.html"), keyboard ninja:
> it should be noted, that vi's [FONT=Courier New]h j k l[/FONT] is not optimal. Better is
    [FONT=Courier New]i
jkl[/FONT]  Or, in Dvorak:

   [FONT=Courier New]c
htn[/FONT]

---

### Post by Rubi1200 on 2011-11-19
Thanks for sharing this information with the forums Doctor Colossus.

Thread closed.

Reason: necromancy.

---

