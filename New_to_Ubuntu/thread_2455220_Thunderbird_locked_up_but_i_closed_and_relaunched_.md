---
title: "Thunderbird locked up but i closed and relaunched it"
date: 2020-12-15
forum: New to Ubuntu
---

### Post by Kusho on 2020-12-15
Thunderbird somehow had like 100 emails open all at once.  I didnt open them.  I tried closing them one at a time but it was impossible.  So I closed thunderbird.  The problem is when I relaunched it nothing changed.  They were all still open.  Now when I open thunderbird its blank.  Is there a way to reset it so when i restart thunderbird its a new secession with nothing open?

And please dumb down the fix.  Thanks.
Oh and I have the latest Ubuntu.   20.10 i believe.

---

### Post by howefield on 2020-12-15
You could rename ~/.thunderbird in your home folder, then Thunderbird will start completely afresh.

---

### Post by ActionParsnip on 2020-12-15
Does a magic reboot fix it ?

---

### Post by Kusho on 2020-12-15
tom@tom-Inspiron-5755:~$ rename ~/.thunderbird
Unknown regexp modifier "/t" at (user-supplied code), at end of line
syntax error at (user-supplied code), near "/."



Like i said dumb down the fix.  Reboot got Thunderbird to open but again there are an unlimited number of open emails and i cant close them.  I can see the window now but nothing works.

---

### Post by howefield on 2020-12-15
OK, open the file manager which should open in your /home folder, then press the Ctrl and H keys which will allow hidden files to be visible.

Then look for .thunderbird, right click on it and rename it to something else. That way you still have access to it but Thunderbird in the meantime will open afresh. This will mean setting up your Thunderbird account(s) again.

---

### Post by Kusho on 2020-12-15
that fixed it.  i can resetup my Thunderbird rather easily.  Thanks

---

