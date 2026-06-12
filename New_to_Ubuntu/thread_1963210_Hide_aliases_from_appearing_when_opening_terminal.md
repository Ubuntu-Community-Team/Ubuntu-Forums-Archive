---
title: "Hide aliases from appearing when opening terminal"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by upsfeup on 2012-04-22
Hello,

I edited some lines (altered  HISTZISE and added an aliases) in .bashrc and now, every time I start the terminal the aliases declared in .bashrc appear on the top of the terminal window.

No idea why this happens. How I can revert that behavior?

I guess I could add an 'clear' to the end of the file, but is not the most elegant solution (as I still can see the lines being printed and this didn't happen before).

Any idea where I should look?

---

### Post by r-senior on 2012-04-22
That doesn't normally happen -- not for me anyway.

Check your alias definitions to make sure everything is in order. Perhaps you have an alias command on its own line that is showing the list of aliases rather than defining a new one?

---

### Post by upsfeup on 2012-04-22
> **r-senior said:**
> That doesn't normally happen -- not for me anyway.

Check your alias definitions to make sure everything is in order. Perhaps you have an alias command on its own line that is showing the list of aliases rather than defining a new one?

You were right! But the problem was on .bash_aliases file (that's why I missed it). One of the alias definitions was defined using -p . 

Fixed now. Thank you.

---

### Post by r-senior on 2012-04-22
Good. :)

If you go to the Thread Tools link just above your original post, you can mark it solved.

---

