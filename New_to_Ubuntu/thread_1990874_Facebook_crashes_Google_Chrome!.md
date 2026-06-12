---
title: "Facebook crashes Google Chrome!"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by Shadius on 2012-05-30
Hey everybody :)

Everytime I try to go to Facebook.com, Google Chrome will crash. What I mean by crash is that Google Chrome will just close. I try opening Google Chrome again and going back to Facebook.com and it'll kill Google Chrome again! Why is this happening? Is this a bug? By the way, Facebook.com works fine on Firefox!

---

### Post by Senior_Buckethead on 2012-06-05
I think you have a bouncing baby bug. It works for me. What version of chrome annd what version of Ubuntu you running?

---

### Post by Shadius on 2012-06-05
> **Senior_Buckethead said:**
> I think you have a bouncing baby bug. It works for me. What version of chrome annd what version of Ubuntu you running?

Bouncing baby bug? I have Chrome Version 19.0.1084.52 and I'm running Ubuntu 12.04. I've noticed it's not only Facebook.com, but other sites too. It crashed on me like 10 times in a row yesterday! I was so frustrated!

---

### Post by Senior_Buckethead on 2012-06-05
> **Shadius said:**
> Bouncing baby bug? I have Chrome Version 19.0.1084.52 and I'm running Ubuntu 12.04. I've noticed it's not only Facebook.com, but other sites too. It crashed on me like 10 times in a row yesterday! I was so frustrated!

Well isnt that just plain odd, ive got 18.0.1025.168 (Developer Build 134367 Linux) Ubuntu 12.04, and works just fine. Have you both submitted bug reports at launchpad?

---

### Post by Shadius on 2012-06-05
> **Senior_Buckethead said:**
> Well isnt that just plain odd, ive got 18.0.1025.168 (Developer Build 134367 Linux) Ubuntu 12.04, and works just fine. Have you both submitted bug reports at launchpad?

I haven't done a bug report at Launchpad as I don't know how. Please advise.

---

### Post by vasa1 on 2012-06-05
I think you could hold off a bit on reporting a bug. I suggest that you wait for a little more feedback.

I'm not seeing any problem at least as far as the log-in page goes. I won't go further because I don't have an account.

My Chrome is 19.0.1084.52 (Official Build 138391).

There are a few things you could try first. You also said it's not just Facebook. If you mention a few others, someone may see a pattern.

Another thing you could try is to go to your extensions page and temporarily disable all extensions and then try the troublesome sites.

There are more things that can be done as well.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> I think you could hold off a bit on reporting a bug. I suggest that you wait for a little more feedback.

I'm not seeing any problem at least as far as the log-in page goes. I won't go further because I don't have an account.

My Chrome is 19.0.1084.52 (Official Build 138391).

There are a few things you could try first. You also said it's not just Facebook. If you mention a few others, someone may see a pattern.

Another thing you could try is to go to your extensions page and temporarily disable all extensions and then try the troublesome sites.

There are more things that can be done as well.

I tried disabling all my extensions and it still happens. It just crashed twice on me just now. I was trying to go to YouTube.

---

### Post by vasa1 on 2012-06-05
Okay. Have you cleared your cache? Press ctrl + shift + delete to bring up a screen that will give you choices of what you may like to delete.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> Okay. Have you cleared your cache? Press ctrl + shift + delete to bring up a screen that will give you choices of what you may like to delete.

Done. Cleared everything since the beginning of time.

---

### Post by vasa1 on 2012-06-05
> **Shadius said:**
> Done. Cleared everything since the beginning of time.
Assuming that didn't help, here's my last suggestion.

Look for this folder:
/home/your_name/.config/google-chrome/Default

Without any instance of Chrome running, rename that folder to Default.bak. In other words, you should be starting with a clean Chrome, no extensions, no cookies, no history, no nothing.

*Then* start Chrome. It will create a new folder called Default with none of the old baggage. You may have to re-enter usernames and passwords for sites that need logging in.

If you still have problems, I'm out of solutions!

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> Assuming that didn't help, here's my last suggestion.

Look for this folder:
/home/your_name/.config/google-chrome/Default

Without any instance of Chrome running, rename that folder to Default.bak. In other words, you should be starting with a clean Chrome, no extensions, no cookies, no history, no nothing.

*Then* start Chrome. It will create a new folder called Default with none of the old baggage. You may have to re-enter usernames and passwords for sites that need logging in.

If you still have problems, I'm out of solutions!

It hasn't crashed since I cleared the cache, but if it does again, I will try your suggestion! Thanks for the help!

---

### Post by vasa1 on 2012-06-05
> **Shadius said:**
> It hasn't crashed since I cleared the cache, but if it does again, I will try your suggestion! Thanks for the help!

No problem. Depending on your needs, you may find you don't need a lot of stuff that's in the Default folder and things can get pretty bloated in there.

I used to know quite a bit about that folder at one time. I'll see if I can find some links on the subject.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> No problem. Depending on your needs, you may find you don't need a lot of stuff that's in the Default folder and things can get pretty bloated in there.

I used to know quite a bit about that folder at one time. I'll see if I can find some links on the subject.

Thanks a lot! That would definitely help. The only reason I switched to Google Chrome was because Flash doesn't work on Firefox. :( Flash just needs to disappear already!

---

### Post by vasa1 on 2012-06-05
Here's one useful link:
[http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> Here's one useful link:
[http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059](http://support.google.com/chrome/bin/answer.py?hl=en&answer=142059)

Very useful. Thanks.

---

### Post by vasa1 on 2012-06-05
This is a bit old but much of it is still relevant:
[http://superuser.com/questions/13929/backing-up-google-chrome](http://superuser.com/questions/13929/backing-up-google-chrome)

The one caution, IMO, is not to go overboard installing extensions, even if they are from the official webstore.

I try to limit my use to very well known extensions that have been around for a while.

---

### Post by Shadius on 2012-06-05
> **vasa1 said:**
> This is a bit old but much of it is still relevant:
[http://superuser.com/questions/13929/backing-up-google-chrome](http://superuser.com/questions/13929/backing-up-google-chrome)

The one caution, IMO, is not to go overboard installing extensions, even if they are from the official webstore.

I try to limit my use to very well known extensions that have been around for a while.

Yeah, I definitely don't have a lot of extensions, only 4. I don't like to install a bunch of useless things.

---

### Post by stmiller on 2012-06-06
Don't just disable, but fully remove all extensions. One extension (even if disabled) is probably the culprit.

---

### Post by Shadius on 2012-06-06
> **stmiller said:**
> Don't just disable, but fully remove all extensions. One extension (even if disabled) is probably the culprit.

Hmm...good idea. I'll try that.

---

### Post by vasa1 on 2012-06-07
> **stmiller said:**
> Don't just disable, but fully remove all extensions. One extension (even if disabled) is probably the culprit.
I don't get the logic of that but anyway ...

---

