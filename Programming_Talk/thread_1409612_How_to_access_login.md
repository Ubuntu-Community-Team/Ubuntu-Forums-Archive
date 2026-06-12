---
title: "How to access login"
date: 2010-02-17
forum: Programming Talk
---

### Post by swappo1 on 2010-02-17
Hello,

I am writing a program in C/C++ that will open up the link to my email on the web weekly and enter my password.  Since this is my personal PC, I want to stay logged in permenantly rather than having to login every other week.  I am not sure how I would access the field to enter a string on the login form.  Can someone point me in the right direction?  Thanks.

---

### Post by TheOrangePeanut on 2010-02-17
Sorry, what is the purpose of your C++ program?  What do you mean by "open up the link to my email?"

If you want to 'log in' by sending information through a web form, you don't have to go through the form itself per se.  Suppose you have a login form with a username and password field, and it may POST to a script that processes the login (checking against a database, etc).  If that is the case, you can use cURL to do that automatically.  It allows you to POST to a script on the web without actually submitting a form.

There is a good chance I missed the point, but if you clarify I can probably help you more.

---

### Post by swappo1 on 2010-02-17
> If you want to 'log in' by sending information through a web form, you don't have to go through the form itself per se.
That's exactly what I want to do.  I'll look in to cURL.  Thanks.

---

