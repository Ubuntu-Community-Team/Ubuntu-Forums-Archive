---
title: "Need help moving cursor"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by dimension123 on 2012-07-10
I am in the terminal and I wanted to reconfigure some changing for security purposes. I am in the directory comman, "vim.tiny /etc/fstab". I want to reconfigure this but when I go all the way to the bottom right the cursor is not allowing me to move any further to the right which prevents me from typing in another command. How am I able to move the cursor to the right so that I can type in my command?? I know its a stupid question but i need help anyone pleaase??? thank you

---

### Post by ubudog on 2012-07-10
Type 'I' to edit.  Be sure you have permissions to edit the file too:
```
sudo vim /etc/fstab
```

When you're finished, press escape and type :wq to save and quit.

Hope that helps,
ubudog

---

### Post by CharlesA on 2012-07-10
Home and End should work in vim. nano or pico might be a better choice tho, vim.tiny is a stripped down version of vim.

i = insert
a = append

See here for more:
[http://bullium.com/support/vim.html](http://bullium.com/support/vim.html)

---

### Post by bogan on 2012-07-10
Hi!,** dimension12**3,

You Posted: > I am in the directory comman, "vim.tiny /etc/fstab". I want to reconfigure this[COLOR=Pink]Please explain what you meant by that.

Do yiu want to alter the Terminal prompt line? [/COLOR][COLOR=Pink]

Are you in a 'Full Screen' terminal window? [/COLOR][COLOR=Pink]

What sort of Terminal are you using: Gnome-terminal, Term from Dash, from 'Ctrl+Alt+t', XTerm or UXTerm or what? [/COLOR]

Have you tried pressing 'F11'?. or 'Alt+Right-Click' and selecting 'Resize'to make the terminal window smaller.

Can you Post a screenshot?

Edit: Before I read CharlesA's Post, I had not seen the significance of the "vim", so ignore the first part of my Post.

Chao!, **bogan.**

---

### Post by dimension123 on 2012-07-10
Hmm.. nothing suggested seemed to work : ( .. Its kind of hard to explain, let me give it another shot. I am in the directory of vim.tiny /etc/fstab and this directory gives me the file of that command , so I am trying to reconfigure this by adding a new command to it but when I go all the way at the bottom right of this comman the cursor stops at the 0 and flashes but it wont let me go any more further to the right so that I can type in a new command. is there a way a can move the cursor beyond that point so that i can add another command? If its still confusing to understand I will post a picture up if necessary .. thanks guys!

---

### Post by ubudog on 2012-07-10
> **dimension123 said:**
> Hmm.. nothing suggested seemed to work : ( .. Its kind of hard to explain, let me give it another shot. I am in the directory of vim.tiny /etc/fstab and this directory gives me the file of that command , so I am trying to reconfigure this by adding a new command to it but when I go all the way at the bottom right of this comman the cursor stops at the 0 and flashes but it wont let me go any more further to the right so that I can type in a new command. is there a way a can move the cursor beyond that point so that i can add another command? If its still confusing to understand I will post a picture up if necessary .. thanks guys!

Hmm... could you post a screenshot?

---

### Post by Cheesemill on 2012-07-10
If you are using the vi application (which is what I think you are trying to say) then you need to press **a** to put vi into append mode.

[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

---

### Post by dimension123 on 2012-07-10
actually "a" worked thank you so much !!

---

