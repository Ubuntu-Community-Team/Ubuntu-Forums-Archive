---
title: "[SOLVED] Starting a SSH Server With Keys"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Chrissd on 2008-11-02
Hi, I've got a SSH server started, however, I've got completely lost with the understanding of keys to secure it. I've a few questions.

1) How do I generate keys?
2) How do I use these to secure the SSH?

Thanks.

---

### Post by Peter09 on 2008-11-02
The easiest way is to use seahorse.

Accessories->Passwords and Encryption Keys

Click on the create key button and select ssh key. If you have ssh already working it will do the rest for you.

---

### Post by Chrissd on 2008-11-02
Thanks.

I've that, created a key, but from my other computer, I didn't need to do anything, I just needed to log in with the username and password, is this correct? :confused:

---

### Post by Peter09 on 2008-11-02
Yes, you create a key from the 'client'. If you select the correct option seahorse will do the rest, you need to tell seahorse how to login to the server (password etc). Next time you login in to the server it will ask for your passphrase - it tends to fail the first time, after that you should not need to use user name and password at all.

---

