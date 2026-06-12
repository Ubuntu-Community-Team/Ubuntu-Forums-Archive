---
title: "[SOLVED] The ISD - Server could not be started because port 5800 in use"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Jimtuv on 2008-05-08
I get this error when logging in:

The ISD - Server could not be started because port 5800 in use 

in 3 separate text boxes

This showed up after I hit the Remember currently running applications under the Session Options tab.

One thing I noticed it that in the current session a program call ica is doubled up. sometimes tripled or even quadrupled.

ica -session 117f00010100012102 etc....
ica -session 117f00010100012102 .......

My question is how to edit out the extra occurrence of this program. Is there a script that can be edited? If so where is it?:confused:

---

### Post by Jimtuv on 2008-05-08
I solved this myself. What I did is to go:

System > Preferences > Sessions

and then in the Currant Sessions tab I removed all occurrences of

ica -session  117f000101001210253 etc.....

hit apply. made sure nothing else was doubled and then I went to the Sessions Options tab and hit Remember Currently Running Applications.

I hope this will help some one.

---

### Post by DyBurke on 2008-06-23
That's somewhat useful as it gets the error out of my face, however I'd like to know what that is and how to change the port.

---

### Post by Jimtuv on 2008-06-24
I ended up deleting the account and making a new one. Still have no clue why it happened though. I have not had a problem with this since deleting the user account. Make sure though if it is an administrator that you set up the new user first!

---

