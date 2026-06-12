---
title: "keyring password"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by ZootHornRollo on 2008-05-24
hi,

i am acomplete linux noob.  just installed ear os today.

its askig for a password to unlock the kyring.

where do i get the password?

cheers.

---

### Post by vrangforestillinger on 2008-05-24
Have you tried your login-password? The default keychain usually uses that one.

If you have changed your password after the installation, it might be that the keychain didn't update and is still using the old password. (This is a known bug.)

---

### Post by ZootHornRollo on 2008-05-25
i managed to get it thanks,

it was in lower case and i had forgot i had turned caps lock on to type the WEP password for the router.

my stupid fault.

---

### Post by ZootHornRollo on 2008-05-25
i managed to get it thanks,

it was in lower case and i had forgot i had turned caps lock on to type the WEP password for the router.

my stupid fault.

---

### Post by jmodigb on 2008-07-07
I am also having this problem, however, I never reset my password, it is the same as it was when i installed ear os.  Is there a default password for default keyring?

---

### Post by ZootHornRollo on 2008-07-07
> **jmodigb said:**
> I am also having this problem, however, I never reset my password, it is the same as it was when i installed ear os.  Is there a default password for default keyring?

the default password is 'earmusic'

---

### Post by jmodigb on 2008-07-07
I see, thought that was just for the LiveCD.  Found another fix though.

Running ear os, my password was not accepted at all. So, I went into Applications..Accessories..Passwords and Encryption Keys and deleted the login keyring. Then created a new one named default. Connecting to my wireless access point no longer requires a password for nm-applet.

Cheers.

---

