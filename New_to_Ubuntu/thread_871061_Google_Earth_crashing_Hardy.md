---
title: "Google Earth crashing Hardy"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by seattle vic on 2008-07-26
I downloaded Earth from the Google site and loaded it; When I ran it, it reset X, same effect as when I do a ctrl-alt-backspace.  Then I uninstalled it and did it without sudo.  No change.  Then I realized that it was available from Synaptic, so I loaded that.  Same problem.  I guess it didn't crash the Kernel, but this is the first time any application has done this.

Any help?

Thanks in advance,

Vic

---

### Post by Pro-reason on 2008-07-26
Is your graphics card properly set up?  Are you able to use other high-graphics programs such as Compiz or 3D games?

---

### Post by stmcc on 2008-07-27
I am haveing the same problem. I am dual booted with XP and google earth works fine there. I have installed it Bin/ pkg/ and from GE. no help
[email]stmcc1@gmail.com[/email]

---

### Post by seattle vic on 2008-07-29
> **Pro-reason said:**
> Is your graphics card properly set up?  Are you able to use other high-graphics programs such as Compiz or 3D games?

Yes, I can run 3D graphics.  Is this just an issue with Hardy perhaps?

---

### Post by Pro-reason on 2008-07-29
> **seattle vic said:**
> Yes, I can run 3D graphics.  Is this just an issue with Hardy perhaps?

I'm using Google Earth on Hardy, without problems.

I notice that there are several versions of it available in the repositories (I have all Ubuntu repos enabled, plus Medibuntu and Linux Mint).  Perhaps some will work for you and some won't.

Did you install Hardy fresh, or did you upgrade from within Gutsy?  I had problems with various things before I did a fresh installation.

What kernel are you running (do *uname -a* in the terminal)?

---

### Post by steveneddy on 2008-07-29
Methinks a kernel issue.

I'll bet the -20 proposed kernel.

Need to use the -19 kernel.

---

### Post by Pro-reason on 2008-07-29
> **steveneddy said:**
> Methinks a kernel issue.

I'll bet the -20 proposed kernel.

Need to use the -19 kernel.

You bet?  Why don't you just look?

I believe the default kernel for Hardy is -19, but I have -20 and it works fine (although I had to reinstall my NVidia drivers).

---

### Post by steveneddy on 2008-07-29
> **Pro-reason said:**
> You bet?  Why don't you just look?

I believe the default kernel for Hardy is -19, but I have -20 and it works fine (although I had to reinstall my NVidia drivers).

Because the -20 kernel is wreaking havoc on lots of machines.

With the -20 kernel hibernate and sleep stopped working on my laptop, along with bluetooth file transfer.

It was a quick easy answer and will make the OP look.

If that's not it, then we've eliminated on thing that it's not.

Still wouldn't hurt to go back to -19 and see if it works there.

EDIT

I agree that a fresh install always works better than an updated installation.

---

### Post by Pro-reason on 2008-07-29
> **steveneddy said:**
> Because the -20 kernel is wreaking havoc on lots of machines.

With the -20 kernel hibernate and sleep stopped working on my laptop, along with bluetooth file transfer.

It was a quick easy answer and will make the OP look.

I apologise.  I didn't look to see who was posting.  I thought you were the original poster answering my question with "I bet the -20".

---

### Post by phidia on 2008-07-29
There's a related post on this [here]("http://ubuntuforums.org/showthread.php?t=867410").

---

