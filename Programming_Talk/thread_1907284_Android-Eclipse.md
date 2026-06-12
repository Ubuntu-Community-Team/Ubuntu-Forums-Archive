---
title: "Android-Eclipse"
date: 2012-01-11
forum: Programming Talk
---

### Post by shashanksingh on 2012-01-11
I downloaded the android-sdk at /opt/android-sdk-linux and referenced it to eclipse.

Eclipse it seems cannot execute files from the sdk location.
I thought it may be a permissions issue, so I did a chmod 777 on the sdk folder.
But the problem persists and I have no clue why...

I have attatched three screenshots.

Kindly suggest.

---

### Post by fct on 2012-01-12
Check that your eclipse version is actually compatible with the android SDK. Also check the JDK version, it should be 1.6 or later.

If you're using the SDK in a 64 bit machine, install ia32-libs.

Not sure what else could be the problem.

---

### Post by shashanksingh on 2012-01-12
> **fct said:**
> Check that your eclipse version is actually compatible with the android SDK. Also check the JDK version, it should be 1.6 or later.

If you're using the SDK in a 64 bit machine, install ia32-libs.

Not sure what else could be the problem.

I was the ia32-libs problem. Thank you :)
It was quite a pain though to understand what the problem could be. Somewhere in the installation they should just mention it, just like how Picassa does.

---

### Post by fct on 2012-01-12
Actually, it's been documented for a while. Check the Ubuntu troubleshooting section here:

[http://developer.android.com/sdk/installing.html](http://developer.android.com/sdk/installing.html)

Glad you solved your problem.

---

### Post by shashanksingh on 2012-01-12
Thanks again.

What I meant was that like picasa, during installatoin itself, makes sure the required libraries are present. It would be nice if the android-sdk installer could do the same. For the novice users.

And thank goodness there are android-people here in the forums as well, I might need a lot of help ahead :D

---

### Post by KdotJ on 2012-01-12
Good to see more Android folks :) 
I find the Android dev tools pretty annoying lol, its good that its standalone but as you say it would be nice if it sorted out dependency issues for you.

---

