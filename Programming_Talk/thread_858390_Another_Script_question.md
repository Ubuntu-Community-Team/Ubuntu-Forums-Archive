---
title: "Another Script question"
date: 2008-07-13
forum: Programming Talk
---

### Post by blooddrunk on 2008-07-13
In my C program I need to add the 'useradd' function. But ,as you all know, adding a user in Linux requires root privileges. Is there a way through a script or system()function to make that command run on every computer without prompting for root's password. 10x in advance

---

### Post by unutbu on 2008-07-13
Run your program as root.

---

### Post by imdano on 2008-07-13
Yeah, it'd sort of defeat the purpose of making adding a user require root privileges if you could get around it with a script or function call.

---

### Post by LaRoza on 2008-07-13
> **blooddrunk said:**
> Is there a way through a script or system()function to make that command run on every computer without prompting for root's password.

What? Did I read that correctly?

---

### Post by pmasiar on 2008-07-13
> **blooddrunk said:**
> Is there a way through a script or system()function to make that command run on every computer without prompting for root's password. 

No, and if you think for about 5 secs, you will realize why :-)

---

### Post by LaRoza on 2008-07-13
> **pmasiar said:**
> No, and if you think for about 5 secs, you will realize why :-)

Technically, before they fixed that sudo bug (which could be used to bypass the prompt on a local machine) you could, but that was a bad bug and not a feature. It doesn't exist anymore.

---

### Post by blooddrunk on 2008-07-14
> **LaRoza said:**
> Technically, before they fixed that sudo bug (which could be used to bypass the prompt on a local machine) you could, but that was a bad bug and not a feature. It doesn't exist anymore.

I thought so. Thanks to all of you, anyway

---

### Post by rnodal on 2008-07-15
Or you can exploit some system function that would allow you to execute your own code but you don't want to do that because it is not nice. :)

---

