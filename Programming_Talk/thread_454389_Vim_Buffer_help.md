---
title: "Vim Buffer help"
date: 2007-05-25
forum: Programming Talk
---

### Post by DanielBaniel on 2007-05-25
'Hi

How do I un-hide a buffer?

I have been using 'set bufhidden=hidden' to hide the current buffer
('set hidden' sets all buffers to hidden). 
I don't know how to set it back to normal.

I have checked the help, google and tip #135 (very handy) but have not
found the answer.

Thanks
Daniel'

I sent that to the [email]vim@vim.org[/email] mailing list but got no replies. I'd love to know how to do that^.

To add one more question. How would I save the current edit session so I could reload it with all the same buffers (and also tabs and splits if possible) at a later stage?

Again, Thanks
Daniel

---

### Post by Billy the Kid on 2007-05-26
In answer to your first question, you simply use the ":unhide" or ":sunhide" commands.
To save a Vim session, use the ":mksession <path>" command.  For further instruction, I would 
refer to the documentation. 
Hope that helps.

---

### Post by DanielBaniel on 2007-05-26
Thank you.

mks is exactly what I was looking for.

My problem with hidden was caused by my own stupidity. Solved it now :)

-Daniel

---

