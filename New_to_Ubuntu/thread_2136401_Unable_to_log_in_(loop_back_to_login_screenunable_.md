---
title: "Unable to log in (loop back to login screen/unable in prompt)"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by ItsAllWorthIt on 2013-04-17
Hi all,

When attempting to login to ubuntu 12.10 i correctly enter the password (also changed the pw so i know its correct) but it loops back to the login prompt. When I ctrl/alt/F1 to the prompt screen and attempt to login I get:

Signature not found in user keyring.
Perhaps try the interactive 'encryptfs-mount-private'

Well, from here i'm totally lost.

Can anyone attempt to walk me through fixing this issue, if its fixable?

Thanks!

---

### Post by Krextyl on 2013-04-17
First did you check capslock/numlock?

---

### Post by sandyd on 2013-04-17
Have you selected 'encrypt your home folder' when installing?

If yes, you willl have to decyrpt your home directory using
```
encryptfs-mount-private
```
when logged in via a TTY (only applies to terminal sessions).

---

### Post by ItsAllWorthIt on 2013-04-18
Thanks for the help guys.

No issues with num/caps lock, so thats not it i don't believe.

Sandy - I see ubuntu prompting me to use that but honestly i'm so new to this that i'm unsure how to manipulate anything using that file, can you assist/would you mind giving me some advice please? :)

---

