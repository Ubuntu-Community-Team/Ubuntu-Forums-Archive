---
title: "Adobe Flash 11 video performance in Google Chrome."
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by PhantmKllr on 2011-10-10
New installation of Ubuntu on my main desktop (specs in the signature), and Flash video performance still sucks, running in Google Chrome (beta) that is.

If I run video in Firefox, or in full-screen within Chrome, I get GPU acceleration. Anyone know the fix for this, if any?

Another thing is that right-clicking on a flash video (video only) doesn't get me a context menu.

Anybody having similar issues?

---

### Post by Jeinhor on 2011-10-10
I have issues with flash being slow in fullscreen, but I do think I have GPU acceleration.

Try the following:

```
echo "OverrideGPUValidation=true" > ~/mss.cfg
sudo mkdir /etc/adobe
sudo mv ~/mss.cfg /etc/adobe
```

That helped in Ubuntu 11.04 for me, but it doesn't in 11.10. Worth a try at least :) (remember to restart the browser)

---

### Post by Harry33 on 2011-10-10
> **PhantmKllr said:**
> 
...
Another thing is that right-clicking on a flash video (video only) doesn't get me a context menu.

Anybody having similar issues?

This is also the case when using Chromium (from Oneiric repos).
Firefox shows it OK.

---

### Post by PhantmKllr on 2011-10-10
> **Jeinhor said:**
> I have issues with flash being slow in fullscreen, but I do think I have GPU acceleration.

Try the following:

```
echo "OverrideGPUValidation=true" > ~/mss.cfg
sudo mkdir /etc/adobe
sudo mv ~/mss.cfg /etc/adobe
```

That helped in Ubuntu 11.04 for me, but it doesn't in 11.10. Worth a try at least :) (remember to restart the browser)

I've seen this fix before around the internet, but I'm reluctant to use it. You see, Flash Player works fine with my graphics card. I only experience poor performance when watching video, and only in Google Chrome.

---

### Post by PhantmKllr on 2011-10-10
New developments:

Apparently, I get good performance when watching higher resolution video. Odd...

---

