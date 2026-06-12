---
title: "Wireless issues + terminal features(vim etc)"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by nbcormier on 2012-03-18
I just dual booted Ubuntu 11.10 along-side of windows 7.  This is my first unix-like install ive done and other wireless posts really havent applied to my issue.  I'm using a Lenovo ThinkPad Edge E420.

While in Ubuntu, there are no wireless connections listed at all.  Do I need to go into the terminal for this?

Secondly, what usual unix features are not automatically set up in the terminal from install?  For instance, I know that text editors are not, I tried to open up a vim file and it didnt let me.  How can I get my terminal working like a fully functioning Unix terminal?

Thanks alot,
nbcormier

---

### Post by sandyd on 2012-03-18
> **nbcormier said:**
> I just dual booted Ubuntu 11.10 along-side of windows 7.  This is my first unix-like install ive done and other wireless posts really havent applied to my issue.  I'm using a Lenovo ThinkPad Edge E420.

While in Ubuntu, there are no wireless connections listed at all.  Do I need to go into the terminal for this?

Secondly, what usual unix features are not automatically set up in the terminal from install?  For instance, I know that text editors are not, I tried to open up a vim file and it didnt let me.  How can I get my terminal working like a fully functioning Unix terminal?

Thanks alot,
nbcormier
1.
Your wireless is a Centrino Wireless-N 1000. Should work out of the box if you have *linux-firmware* package installed. If you don't, download it from another computer, and install it.

Its the
```
[FONT=monospace]
[/FONT] /lib/firmware/iwlwifi-1000-3.ucode 
/lib/firmware/iwlwifi-1000-5.ucode

```
firmware blobs.

2.
You might want to use *nano* instead.

---

