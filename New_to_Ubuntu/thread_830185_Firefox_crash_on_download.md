---
title: "Firefox crash on download"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by mistersam on 2008-06-15
After the recent update to Firefox 3 from the repositories (Hardy). Everytime I download a file (be it a jpeg, zip, etc...) Firefox crashes. The files is downloaded, but the broser closes itself.

This happens everytime, no exceptions.

---

### Post by MasterSander on 2008-06-15
Try reinstalling

---

### Post by Acglaphotis on 2008-06-15
Don't be so drastic. Try downgrading.

---

### Post by kansasnoob on 2008-06-15
Something that comes to mind, and may or may not apply, is the difference between versions of Firefox 3.

I got FF3 RC1 the same day as some got FF3 RC2 just because some people choose to install updates that are "Hardy Proposed" instead of waiting for the "Recommended Updates".

Those who choose to "tick" pre-released and unsupported updates do tend to encounter more problems than those who wait until the true Linux gurus have all the problems worked out.

Just look at Software Sources and see what you have selected. Sadly the Firefox "Help" button won't tell you whether you have RC1 or RC2.

IMO RC2 is simply not ready for prime time, nor is Kernel blah, blah.19, etc.

---

### Post by kansasnoob on 2008-06-15
"Try downgrading."

How do you do that?

I followed a thread dealing with audio that had to do with a Kernel update (.19) and it required going back to Kernel xxxxx.18. Same update rules apply! If you're playing it safe and only receiving approved updates you'll have kernel xxxxxxxxxxxxx.18!

But how would someone go from FF3 RC2 back to FF3 RC1?

How much would someone have to back out of? Dependencies are a real beeotch.

I'm thinking that "ticking" pre-leased and unsupported should require a "Q&A" to stop folks from going into territory that may surpass their capabilities.

---

### Post by mistersam on 2008-06-15
I found the problem. I had Prism installed on FX 3 beta 5. It worked with no problem. Now that I've upgraded to FX 3, whenever I save anything it crashes. If I disable the Prism add on, everything works again.

---

### Post by st33med on 2008-06-15
> **mistersam said:**
> I found the problem. I had Prism installed on FX 3 beta 5. It worked with no problem. Now that I've upgraded to FX 3, whenever I save anything it crashes. If I disable the Prism add on, everything works again.

Most likely because it has not been updated properly for FF3rc1.

---

### Post by dslehman on 2008-06-16
First try to reinstall firefox 3 on hardy:

```

sudo aptitude reinstall firefox-3.0

```

If that doesn't cut it, try to purge and reinstall firefox 3:
```

sudo aptitude purge firefox-3.0
sudo aptitude install firefox-3.0

```

Instructions on going back to firefox 2 are here:
[http://ubuntuforums.org/showthread.php?p=5195190#post5195190](http://ubuntuforums.org/showthread.php?p=5195190#post5195190)

---

### Post by jaygo on 2008-06-29
Thanks, sam, that fixed it. I had started working backwards through all of my extensions but you saved me some time. Serves me right for playing with beta extensions ...

---

