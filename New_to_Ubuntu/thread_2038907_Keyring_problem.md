---
title: "Keyring problem"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by cshin9 on 2012-08-07
I changed my login password through User Account. When I restarted then logged back in, or logged out and logged back in, I got a prompt to enter a password for the login keyring, which turned out to be my old login password. After looking up the problem, I changed the login keyring password to the same one as my new login password. This still gave me the same prompt, although my login keyring password was updated.

Then I deleted my login keyring. Trying to sign into an application prompted me to create a new keyring named default. I made the default keyring password the same as my login password, but it still gave me the same prompt to enter my default keyring password when I logged in.

I don't want to leave the password blank, but I don't want to enter a keyring password every time I log in. The option to automatically unlock the keyring upon login is greyed out, so I can't choose that either. Is there a solution to this problem?

---

### Post by cshin9 on 2012-09-12
Eh, I reinstalled when I had the occasion to and recreated the account with a new password. Not the ideal solution, but a solution nonetheless. It's a good thing though that I have a separate /home partition.

---

