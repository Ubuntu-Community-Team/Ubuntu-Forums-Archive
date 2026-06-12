---
title: "[SOLVED] You didn’t run visudo as root."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Andrew U.K. on 2008-08-26
Hi,

I'm new to linux and have got into it through Mythbuntu. I'm trying to get the p.c. to power up with the APCI. I need to give mythbuntu the permissions to do this which I am doing through editing the sudoers file with a script that I am copy and pasting in as the instructions show (All of my experience with linux so far is copy and paste).
So in the Terminal I paste **sudo visudo** I am asked for my password which I give and then the sudoers file appears in the window. I paste the script in at the bottom. 
At the very bottom of the window is **You didn’t run visudo as root**. I understand that there should be an option to save or quit. 
I take it I'm not running visudo as root how on earth do I?

Thanks in advance
Andrew

---

### Post by jerome1232 on 2008-08-26
if you ran sudo visudo then you ran it as root, actually in vi there's no option to save/quit, what you want to do is press esc to get out of insert mode, then hit :wq  or alternativly hit esc and type ZZ, those both save and quit

---

### Post by Andrew U.K. on 2008-08-26
Thanks for the reply,
How do I move down to create a new line. The last line is **%admin ALL=(ALL) ALL**I need to add another line beginning with **%myth ALL =** etc. But the cursor won't move down when I get to the end or when I press enter.

Cheers 
Andrew

---

### Post by Andrew U.K. on 2008-08-26
.

---

### Post by jerome1232 on 2008-08-26
a few commands in vi,

'i'   insert mode
'o'   create new line, puts you in insert mode
'a'   pretty much the same as i but you the cursor moves one character forward
'dd'(when in command mode) deletes the entire line
'/'(when in command mode)  searches the document for the text you enter after '/'
there's alot more if you google vi you should get a good howto for using vi

---

### Post by Andrew U.K. on 2008-08-26
thanks again,
I'll check it out.

---

### Post by jerome1232 on 2008-08-26
an important one I forgot to mention, :q! quits without saving (if you made a mistake and don't know what the heck happened)

---

### Post by Pa100ka on 2008-08-26
Just to state the bleeding obvious:

OP: To add a line at the end, go to the last character of the last line using the arrow keys, then press a (append mode).

Then press Enter and you should have a new line to type into.

When done, press escape (to exit append mode), colon. wq (write quit) as others have explained (or q! if it is messed up).

Pa100ka

---

### Post by Andrew U.K. on 2008-08-26
All sorted, file edited.

I have zero computing experience apart from moving files around on a windows machine, just the usual stuff. I'm going through periods of frustration so when I manage to complete a task such as editing sudoers file (it's taken me about 3 hours) i'm overjoyed. Thanks Again. 

Andrew

---

### Post by Too Late on 2008-08-26
You can edit the /etc/sudoers file with nano, too. Just open it with sudo:
```
sudo nano /etc/sudoers
```
Nano is much easier to use. However, it's not recommended to use that when editing the sudoers file. I don't know why.

And yes I did notice that you already managed to edit that.

---

### Post by jerome1232 on 2008-08-26
Actually you can't use that to edit the sudoers file (at least I tried once and it said 'no', and visudo does syntax checking after your done to make sure you didn't f*** up your sudoers file and have no way to change after your done.

---

### Post by Pa100ka on 2008-08-26
Nor me. But the sudoers file says it MUST be edited with visudo. So I just follow the instructions.

Doesn't hurt to become sufficiently proficient with vi, though, IMHO. If one visits a client *nix site it is the one editor which is always available.

Pa100ka

---

### Post by Too Late on 2008-08-26
> **jerome1232 said:**
> Actually you can't use that to edit the sudoers file (at least I tried once and it said 'no', and visudo does syntax checking after your done to make sure you didn't f*** up your sudoers file and have no way to change after your done.
I've successfully edited my sudoers file with nano and it's working fine. But when I try to open that with gedit, it stays as read-only.

And of course, learning to use vi(m) *would* be very nice, but I've used linux only about 3 years now, so it's not yet my time to do that. :)

---

