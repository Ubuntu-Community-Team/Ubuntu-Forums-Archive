---
title: "Digg api python"
date: 2011-07-14
forum: Programming Talk
---

### Post by mikedemon on 2011-07-14
Hi

I want to count the total number of friends and fans of certain users from Digg using phyton . Can you please recommend a Toolkit? I never used Diggs APIs before, can you please provide a simple code or tutorial site that I can learn from.

I was looking , [http://services.digg.com/2.0/digg.hasDugg](http://services.digg.com/2.0/digg.hasDugg) APIs , is this right one to use?

Thank you in advance

---

### Post by cgroza on 2011-07-14
I suggest urllib to interface with their online API. It is in the standard python distribution.

---

### Post by TwoEars on 2011-07-14
> **mikedemon said:**
> Hi

I want to count the total number of friends and fans of certain users from Digg using phyton . Can you please recommend a Toolkit? I never used Diggs APIs before, can you please provide a simple code or tutorial site that I can learn from.

I was looking , [http://services.digg.com/2.0/digg.hasDugg](http://services.digg.com/2.0/digg.hasDugg) APIs , is this right one to use?

Thank you in advance

Download the toolkit as instructed here - [http://developers.digg.com/toolkits](http://developers.digg.com/toolkits)

And read the documentation located here - [http://developers.digg.com/documentation](http://developers.digg.com/documentation)

---

### Post by mikedemon on 2011-07-14
> **TwoEars said:**
> Download the toolkit as instructed here - [http://developers.digg.com/toolkits](http://developers.digg.com/toolkits)
 
And read the documentation located here - [http://developers.digg.com/documentation](http://developers.digg.com/documentation)
 
 
Hi , installed the toolkit and been reading the document. I managed to authenticate my app via oauth , Dont know what to do next. i got the keys now what do i do with them?, Can you please provide a sample python code.
 
thank you

---

### Post by TwoEars on 2011-07-15
> **mikedemon said:**
> Hi , installed the toolkit and been reading the document. I managed to authenticate my app via oauth , Dont know what to do next. i got the keys now what do i do with them?, Can you please provide a sample python code.
 
thank you


I haven't used the toolkit before, but it's for the digg api 1, not digg api 2. If you want 2, you'll have to implement your own toolkit (easy enough to do, but you'll need the required knowledge). Anyway, now that I've seen it's for api 1, you might as well go for PyDigg - [http://code.google.com/p/pydigg/](http://code.google.com/p/pydigg/) which is more feature complete and easier to read for you.

Sample code here - [http://neothoughts.com/pydigg/](http://neothoughts.com/pydigg/)

---

