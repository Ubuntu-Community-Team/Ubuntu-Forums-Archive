---
title: "With Regard to Home Folder Encryption Not Working and Unmounting File Systems"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by CJMacalister on 2013-05-26
I've followed the following directions to encrypt my home folder:

1. Install the encryption utilities via the terminal:

sudo apt-get install ecryptfs-utils cryptsetup

2. Create a new user account an make it an administrator account.

3. After creating this account, log out of your present account and log into the newly created one.

4. Run the following command in the terminal to encrypt your home directory, replacing user with the name of your user account:

sudo ecryptfs-migrate-home -u user

5. Log out and log back in as your original account.

6. After logging back in, click the provided "run this action now" button to create a recovery passphrase.

I have followed all these instructions and created a passphrase, and the process went fine with no indicated problems, but my home folder remains unincrypted. A more Linux-literate friend of mine told me via IM that it sounds as though I need to unmount the file system. Assuming that's the case, how do I do that, and assuming it's not, what do I do instead?

---

### Post by Dave_L on 2013-05-26
Are you sure that home folder is unencrypted? If you re-boot and log into the other user (not the user whose home folder you encrypted), can you view the files that are supposed to be encypted?

---

