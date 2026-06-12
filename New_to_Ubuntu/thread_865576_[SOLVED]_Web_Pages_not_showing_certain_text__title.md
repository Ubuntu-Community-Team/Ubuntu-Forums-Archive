---
title: "[SOLVED] Web Pages not showing certain text / titles / links"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by crjackson on 2008-07-20
Okay, so I've been building a system for my boss (not hardware, just building an Ubuntu 8.04 install).

Everything was fine and I was just about to pack it up for returning to him and now all of a sudden the web pages won't display correctly.

I even tried the epiphany browser with same results.  Please have a look and tell me how to fix this thing.  I've just spent the past 3 days setting it up and I don't want to start from scratch again if I don't have to.

As you can see, I'm getting horizontal lines where menu text should be.

Thanks

---

### Post by crjackson on 2008-07-20
So here is more info. If I start firefox by using the terminal "sudo firefox"  then all is well..  What's up with that?

Also I tried renaming the mozilla directory (to eleminate themes / extensions) and it had no effect.

---

### Post by crjackson on 2008-07-20
Okay, so it looks like I'm going to do a full install again and spending the next 2 day putting everything back...

---

### Post by crjackson on 2008-07-20
I removed and purged all firefox files and then reinstalled again.  It still does the same thing.  I HATE REINSTALLING.  DAMN IT!

---

### Post by dominiquec on 2008-07-20
I sympathize with you, friend.  This looks like a very peculiar case indeed.

The only thing I can think of is that the CSS on those pages must be messed up.  Does this happen with all web pages?  Or only with very specific ones?

---

### Post by Tigin on 2008-07-20
try apton cd to reinstall all your updates and packages , you can get it via applications>add-remove

---

### Post by crjackson on 2008-07-20
Thanks - I don't know what went wrong.  I'm elbow deep into a new install at this time.  It's going to be a VERY LONG NIGHT.

---

### Post by crjackson on 2008-07-20
> **dominiquec said:**
> I sympathize with you, friend.  This looks like a very peculiar case indeed.

The only thing I can think of is that the CSS on those pages must be messed up.  Does this happen with all web pages?  Or only with very specific ones?

It was on most pages.  Only a few pages didn't have this problem.

---

### Post by crjackson on 2008-07-20
> **Tigin said:**
> try apton cd to reinstall all your updates and packages , you can get it via applications>add-remove

I tried the option to remove all packages related to firefox.  Then I physically deleted all folders related to firefox.  Then I reinstalled from synaptic and got the very same problem.

I can't understand why it worked fine when launched as root but not as user.

---

### Post by crjackson on 2008-07-21
Problem solved with a second install session.  Now for all the tweaking and adding software.

I wish I knew what caused this, and how to fix it without doing a full install.

---

