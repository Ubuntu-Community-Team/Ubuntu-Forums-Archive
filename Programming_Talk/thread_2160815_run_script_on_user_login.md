---
title: "run script on user login?"
date: 2013-07-08
forum: Programming Talk
---

### Post by conradin on 2013-07-08
What i would like to do, is have some script that activates when a user logs in, and prevents this user from doing anything else, untill they can perform some task like confirm their existance, or in this case, provide a digital signature.
how can I set up a script to run on a specific user account (preventing other actions)/ how can i make this run when a user logs in?


I have an ssh server, and have recently been recruited to a research group.
on my ssh server, a user logs in, to gain access to various services, software, etc.
Unfortunately this user is also pending aproval for some papers (research articles). All contributing must waive or confirm thier contributions to the paper before it can be peer reviewed. Publishing research is how this group gets funding and recognition.
This researcher has recently changed all his contact informations however.

I am not looking to ban this user, just to convey a message, and get a certified response back.
Alternatively the user could opt to leave my server untill he wants to respond.
I will likely write in bash or Expect.

---

### Post by Vitsliputsli on 2013-07-08
You may use file .bash_login for it. If I understand you correct.

---

