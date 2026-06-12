---
title: "keyring unlock for ssh private key?"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by iansane on 2012-05-13
Hi,

I just generated a ssh key and uploaded the pub key to my server and am now trying to ssh connect.

The keyring prompt pops up and asks for password, I type it in and hit enter and it pops up again.

I tried changing the password and get no errors so it seems I've changed it but I don't think this is the problem. It still continues to popup over and over and won't take my password. I even tried setting the password to blank and nothing changes.

Any suggestions?

On a side note, isn't it my responsibility to protect my home directory to keep other users and hackers from getting my private key? This is just a major irritation.

Thanks

---

### Post by iansane on 2012-05-13
Ok, setting the password to blank did work. It just required a log off and log back in which I didn't see mentioned anywhere in info I found on the subject.

I'd still like to know why it would not work with the correct password before I set it blank.

Is there a limit on password characters, alpha-numeric, uppercase/lowercase that might make my password not work? I ran into such an issue once doing something with Oracle. Can't remember what it was but when I set the password it took it but then when logging in, it wouldn't work because there was a character limit. That's why I ask.

Other than that I have no idea why setting it to blank works but setting it to a known password wouldn't.

---

