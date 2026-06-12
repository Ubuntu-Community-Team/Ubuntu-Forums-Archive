---
title: "[SOLVED] Quick ssh question"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-07-09
I want to have multiple computers have the ability to log in to my website through ssh. On my computer I used```
ssh-keygen -t rsa
``` to create a unique key. I then copied the id_rsa.pub file to my websites as .ssh/authorized_keys. My question is, how do that for another computer so that I can have two computers have a passwordless login.

---

### Post by apswartz on 2008-07-09
Just create a key on the other computer and append the id_rsa.pub file to your  .ssh/authorized_keys.

---

### Post by kevdog on 2008-07-09
To append to the authorized_keys file use the >> symbol.  The > symbol creates/erases the file and starts from the first line.

So

cat id_rsa.pub > authorized_keys  (This would create the file authorized_keys and add the contents of id_rsa.pub)

cat id_rsa2.pub >> authorized_keys  (This would append the contents of the id_rsa2.pub file to the existing authorized_keys file)

I prefer to use these commands as above, since the authorized_keys file is very sensitive to spaces, CR etc.  This takes out the confusion.

---

### Post by slughappy1 on 2008-07-09
To append to the authorized_keys file use the >> symbol. The > symbol creates/erases the file and starts from the first line.

So

cat id_rsa.pub > authorized_keys (This would create the file authorized_keys and add the contents of id_rsa.pub)

cat id_rsa2.pub >> authorized_keys (This would append the contents of the id_rsa2.pub file to the existing authorized_keys file)

So what you are saying is:
Step 1 -> create a new key on said computer
Step 2 -> copy id_rsa2.pub to .ssh on website server
Step 3 -> inside .ssh use cat id_rsa2.pub >> authorized_keys

After doing this it will allow my two computers to login to my website without a password? So would I be right in assuming that the cat id_rsa2.pub >> authorized_keys just adds the second key to the authorized_keys file?

---

### Post by inteluser on 2008-07-09
Yes, cat id_rsa2.pub >> authorized_keys does just that.

Another option is to copy id_rsa (your private key) to the second computer.  This has the nice property of helping maintain a single "identity" for yourself, represented by that one keypair.

---

