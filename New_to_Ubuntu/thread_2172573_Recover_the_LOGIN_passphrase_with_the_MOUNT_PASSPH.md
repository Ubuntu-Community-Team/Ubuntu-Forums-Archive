---
title: "Recover the LOGIN passphrase with the MOUNT PASSPHRASE"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by Xavinovic on 2013-09-05
Hi everybody,

First steps with Ubuntu... after holidays, I forgot my password. HOURA ! So I used GRUB to change my password, it was a success. But... rebooting the computer, arriving on the launch screen... I wrote my new password, "enter", then black screen, then going back to the launch screen, without any message.

Then I started the console, login, password, youpee it works... My new password is correct. But «signature not found in user keyring»

Then I followed some tutorials to decrypt my home directory, but I'm stuck.

I tried this : [http://unixtitan.net/main/2010/11/16/annoyance-changing-password-with-ecryptfs/](http://unixtitan.net/main/2010/11/16/annoyance-changing-password-with-ecryptfs/)
But I forgot my LOGIN passphrase, the original one...

And when I want to recover my LOGIN passphrase, using my MOUNT passphrase, I do this :
[HTML]ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase[/HTML]
Whatever I do, I arrive on «unwrapping passphrase failed [-5]».

When the console asks me the "old wrapping passphrase", what is it ? The mount or login passphrase ?
And then, when it asks me the new wrapping passphrase.... what the hell is it ? How can I generate one ? Need I to generate one from my new password !?

I can't find any clear step-by-step tutorial (for newbie like me) which explains how to access to my computer with my new password and my old ecryptfs mount passphrase !

Thank you.

---

### Post by Alan_Mason on 2014-03-10
Hi, did you find a solution to this? I have same problem.

---

