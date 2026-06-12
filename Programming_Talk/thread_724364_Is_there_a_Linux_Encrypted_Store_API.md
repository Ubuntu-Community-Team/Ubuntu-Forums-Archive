---
title: "Is there a Linux Encrypted Store API?"
date: 2008-03-14
forum: Programming Talk
---

### Post by twokswine on 2008-03-14
Anybody know a quick/easy way to store private data (e.g. a password) on Linux (cross-distro) *without* having the application store a separate private key? That is, on Windows, one can use CryptProtectData() which uses the currently-logged-on user's credentials (and presumably other information) to encrypt data for storage and retrieval. Anything like that on Linux?

---

### Post by Jessehk on 2008-03-14
I don't quite understand the question (and I don't know much about encrpytion), but this *might* help somehow: [http://www.gnu.org/software/libc/manual/html_node/crypt.html#crypt](http://www.gnu.org/software/libc/manual/html_node/crypt.html#crypt) .

You didn't mention language, but C is standard on Linux.

---

### Post by twokswine on 2008-03-17
Thanks Jessehk... I'm doing C/C++ and I'm looking for a method that uses the current process user credentials to encrypt/decrypt application data.  The crypt() function you mention requires the application provide a key to do crypto functions, thus the application either has to embed a key (very insecure), or prompt the user for the key (unworkable for services and impractical since the user has already provided credentials).  What I need is crypto functions that use the credentials the user has already provided for the logon to do encryption/decryption.  Thus the application doesn't do addition key management.  In Windows one would use CryptProtectData... you just give it raw data and you get be encrypted data... no keys.  Didn't know if Linux had such a thing...

---

### Post by mssever on 2008-03-17
I think that gnome-keyring is supposed to be usable for this sort of stuff, although it's quite immature. Also, I don't know much about libpam, but maybe there's something useful there.

---

### Post by dempl_dempl on 2008-03-17
You can find three libs on my site:

[Ansi C++ ciphering libs]("http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,132/Itemid,99999999/")

Cheers!

---

### Post by twokswine on 2008-03-18
> **mssever said:**
> I think that gnome-keyring is supposed to be usable for this sort of stuff, although it's quite immature. Also, I don't know much about libpam, but maybe there's something useful there.

Thanks, I don't know much about either... but at first glance, it appears gnome-keyring is some kind of gui-password management thingy and that libpam seems to deal more with authentication.  I'm looking more for "encrypt using currently authenticated user stuff".

---

### Post by twokswine on 2008-03-18
> **dempl_dempl said:**
> You can find three libs on my site:

[Ansi C++ ciphering libs]("http://www.stosha.net/component/option,com_mtree/task,listcats/cat_id,132/Itemid,99999999/")

Cheers!

Ok, but your libraries seem to encapsulate various ciphers... I'm looking for "encrypt arbitrary data using currently authenticated user info", not "encrypt with this key" or "digest data".

---

### Post by mindwarp on 2008-03-18
It sounds like maybe you want to use the user's name as a salt for encryption?  You really need to define what 'currently authenticated user info' is, because to me that means they entered a username / password, and the password correctly matched the md5 entry in /etc/shadow.

---

### Post by mssever on 2008-03-18
> **twokswine said:**
> Thanks, I don't know much about either... but at first glance, it appears gnome-keyring is some kind of gui-password management thingy and that libpam seems to deal more with authentication.  I'm looking more for "encrypt using currently authenticated user stuff".

What I was thinking of is that gnome-keyring is supposed to be able to handle encryption keys. A couple of releases back, when nm-applet wanted to connect to a secured wireless network, it would have to prompt the user for the key to the encryption it was using. So there's some sort of per-user encryption there. Now, as to how that works, I don't know. And I don't even know if you can make it work for you.

I'm pretty sure that there isn't a system-wide facility such as I gather there is in Windows (I know absolutely nothing about Windows programming).

---

### Post by pmasiar on 2008-03-18
I am not sure what you want, but "use current user's default" looks like security designed by MSFT to me :-)

If I bother with security, I would go for little inconvenience to provide some kind of passphrase, so I can access same encrypted archive from other computer where my username etc might be different, no? 

I am not sure how I feel about security what is convenient and transparent. How can I detect it is there?

---

### Post by twokswine on 2008-03-21
> **mindwarp said:**
> It sounds like maybe you want to use the user's name as a salt for encryption?  You really need to define what 'currently authenticated user info' is, because to me that means they entered a username / password, and the password correctly matched the md5 entry in /etc/shadow.

Thanks, yeah that's in the right direction of what I intended.  Using the username as a salt with a static key is better than just using a static cipher key linked into the executable, but it's still not great security.  I could use the password hash too, but of course if they change their password, I can no longer decrypt data.  It's a step better than where I'm at though.  At least you can't transport encrypted data to another box and super-easily have it decrypt.  The more I think about this the more I wonder what *exactly* CryptProtectData() is doing on Windows...

---

### Post by twokswine on 2008-03-21
> **pmasiar said:**
> I am not sure what you want, but "use current user's default" looks like security designed by MSFT to me :-)

Well, I question what Microsoft has implemented in the afrementioned CryptProtectData() API, but in principal, strong security can be applied using a combinarion of several mechanisms.

> **pmasiar said:**
> If I bother with security, I would go for little inconvenience to provide some kind of passphrase, so I can access same encrypted archive from other computer where my username etc might be different, no?

Thanks, but this is exactly what I'm trying to avoid.  1) I can't have a passphrase for a service I expect will run unattended because I can't have it wait for a manual password entry during reboot/restart.  2) I want the encrypted data tied to the system/installation and don't want other means of decrypting.  The data I want to protect is authentication information for a different remote system...

---

