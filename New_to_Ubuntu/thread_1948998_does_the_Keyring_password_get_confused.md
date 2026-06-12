---
title: "does the Keyring password get confused"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by munezz on 2012-03-29
A few days ago I faced a problem with my login account for Ubuntu 11.10 (now i don't cause it got solved with the help from ABT).............but still there are doubts as I'm a mere mortal and new to Ubuntu..........................the problem started when I changed my login password and after rebooting to my surprise the login did not prompt me for a password............every time i tried to install new programs a notification prompted me to type a keyring password and later the regular pw...............what irritated me was that the keyring pw remained my old pw and the regular pw my new one.......................so I doubt the keyring pw got confused.................:confused:........................all help will be appreciated.
Thanxx

---

### Post by yetiman64 on 2012-03-29
The keyring password is set up originally the same as your login password. 

If you change a login password and have either devices or applications storing your credentials for them in the keyring, the next time you try to use them they will use the new login password but the keyring itself is still set on the old password. This causes the problem.

If you still know the old password you can go into "Passwords and Keys", search for the word password in Dash to find it, then right click on the "login" password and select "Change Password". 
Put in the old login password and then the new login password (and confirm it by typing it in again).  Once you click OK the keyring and login passwords should now match and the system behaviour should revert to normal. See attachment. Good luck.

---

