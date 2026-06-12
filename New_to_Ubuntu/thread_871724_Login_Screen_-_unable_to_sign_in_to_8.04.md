---
title: "Login Screen - unable to sign in to 8.04"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by RunCorp on 2008-07-27
I've searched for this problem on the forum.  But did not see it resolved for other people either.  I'll give it a try anyway.  

I am absolutely new to Ubuntu and installed 8.04 on an older machine to test.  I paid close attention to the 7 easy questions and recorded my password.  I am very sure of this.  However, I did not see anywhere indicating my user ID.  I rebooted and reformatted - re-installed and once again ... carefully looked at the screen for a USERNAME.  I do not have this information and am unable to sign on to Ubuntu for the first time.  

I do know the name of the machine, apparently that is not the USERNAME either.  Is there a way to figure out what Ubuntu has assigned as a user ID?  The installation process never asked me.  I only typed a password.  (BTW, I tried blanks, and same user id as PSW to no avail.)   Any help is appreciated, thanks.

---

### Post by coffeecat on 2008-07-27
You would have assigned your username on the page you assigned your password. However, you may have not noticed something. The first field is 'name' (or something similar). If you put in a name with a space, it will automatically fill the next field (username) with the first word only.

For example, if you put 'John Smith' in the first field, 'john' (all lowercase) will appear in the next, and you can change this if you want. If you didn't notice this, that may be why you thought you didn't have a chance to assign your username.

And the same page assigns the computer hostname, which is not your username.

---

### Post by RunCorp on 2008-07-27
Thanks, your comment about changing the case in the name appeared to have worked.

---

### Post by billgoldberg on 2008-07-27
When you start you're computer, you see something called grub.

Press "esc" to access it.

Boot into recovery mode

give in this command

ls -la /home

It should list your username

(the bottom right word)

---

### Post by billgoldberg on 2008-07-27
Mark your thread as solved please.

---

### Post by candtalan on 2008-07-27
At the stage of entering your password (two times) you are using the same display screen as your user name and also your ID, these will be at the upper part of the screen.

My user name happens to be candt and -immediately- the login ID is *also* inserted automagically also as candt!  I am not asked to enter it, it is offered as a likely default. It can be changed, just by typing in something else if you wish.

So it is very likely that your login id will be the same as your name that you entered.

There are other ways of finding it out also, butu you may need some further details for that.
hth

---

