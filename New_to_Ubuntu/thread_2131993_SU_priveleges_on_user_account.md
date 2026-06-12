---
title: "SU priveleges on user account"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by lile001 on 2013-04-03
I am adding a user to my very modest Ubuntu 12.04 system.  Currently, there is myself, with administrator priveleges, and one other user.  

I am not really very experienced with this sort of thing, but was easily able to set up the new user (call him "James") and get a basic amount of functionality going. I told james what his password would be. 

I began to customize this user's account somewhat, and immediately ran into trouble.  For example, I tried to install a CHrome extension under the user's account, but it failed, and I would guess that would be because James has no administrator priveleges.   

I went to a terminal on his account, logged in as myself (administrator larry) by using su larry, but larry doesn't have any rights writing files in his account either so that didn't work.   

What is the most straightforward way for an administrator to install programs in a non-administrator's account given that he knows the users password?

---

### Post by Cheesemill on 2013-04-03
You shouldn't need any special privileges for a user to install a Chrome extension.

Chrome extensions live in a users home folder so they already have write access. I've just tested this with unprivileged users on my machine and I can install extensions OK.

Is there a specific extension you are having problems with?
What error messages are you getting?

Edit - Just read your OP again, the easiest way for you to set up things on another users account is just to log in as that user.

---

### Post by lile001 on 2013-04-03
Ah, so my initial guess at the cause of the problem is wrong, and it is likely a specific problem with something, rather than a general problem of priveleges.  

For no reason I can explain, this all seems to be working properly today and the chrome extension is installing properly. Coulcn't get anything to work yesterday.   Thank you for your help, at least I learned a little bit about the subject of logins and administrator priveleges.

---

### Post by mamamia88 on 2013-04-03
Well you could add your user to the sudoers group and allow all members of the group sudo access if you need something like that in the future.

---

