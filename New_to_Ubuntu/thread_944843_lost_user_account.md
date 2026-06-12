---
title: "lost user account"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by bohica on 2008-10-11
I've reinstalled Hardy Heron and copied the two existing accounts. I can login to mine but can't login to the other. The other account is in the home directory as expected but does not appear in the users and groups management app, ANy ideas on how to restore this account?
I can make another user and have that pointing to the old home directory but I'd prefer to keep the original user name.

TIA

Bo

---

### Post by PhoenixP3K on 2008-10-11
When you say you copied two existing account with a fresh install what you did is that you created your own account and copied the files over in your home directory.

Even if you have the home directory files of the second user you still need to create that second account so that the system knows it's there. So go in Users and Groups, "create" that second user with the name you want, then copy the files over into it. 

To make sure it does overwrite those files keep that home folder elsewhere until you created the account, then you move the files in.
Just make sure to have

---

