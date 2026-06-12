---
title: "Password Protect CUPS?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by twirp on 2008-11-03
Is there a way to make it so a user has to login whenever they go to localhost:631 ?
Because I went to another computer and typed in myip:631, then went to printers and clicked print test page, and it printed one without trying to authenticate me or anything.

So I was wondering if there was a way to force authentication?  I want to share it with my other PC, but I'd like to be able to have it so only people who have a username and password can go in and do stuff.

Thanks for any help :)

---

### Post by cmnorton on 2008-11-05
This is an interesting post. I can use locahost:631, but have to have my user be in the lpadmin group, if I want to make any admin changes to any printer, like modify, delete, or create. 

I'd look in /etc/groups to see if your user is already there. I had to add myself to the lpadmin group, unless this represents a change in 8.10.

---

