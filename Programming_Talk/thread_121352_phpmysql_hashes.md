---
title: "php/mysql hashes"
date: 2006-01-25
forum: Programming Talk
---

### Post by grim918 on 2006-01-25
im working on a user account script. i use mysql to store the users passwords as hashes. the program will allow a user to enter their email address so that their password can be emailed to them in case they forget it. i was wondering if there is a php or mysql function that will unhash the stored password so that it can be emailed to the user. otherwise im going to have to store plain text passwords.

---

### Post by LordHunter317 on 2006-01-25
No, unless you use a two-way hash, which would be wastefull.

There are other options, however.  Change it to something reasonably strong randomly, or send them a unique URL to let them change it for a fixed period.

---

### Post by heimo on 2006-01-25
Storing passwords in plaintext or in a format that can be decrypted is not always a smart idea. :) So, rather than using something that's not one-way hash, I'd just generate a new password and send that one - or generate some kind of "new password actication" link/url (which is emailed to address user gave before) with "ticket hash" so that user may enter a new password.

EDIT: Lord, you're quick. :)

---

### Post by LordHunter317 on 2006-01-25
[QUOTE=heimo]Storing passwords in plaintext or in a format that can be decrypted is not always a smart idea. :)[/quote]If you're not using a salted hash, one-way hashes don't gain you anything anymore if the hash(es) are recovered.  Even if you are using a salted hash, you have to be careful the salting is done correctly to make rainbow-table attacks infesible.  This usually means multiple rounds of hashing.

---

### Post by grim918 on 2006-01-25
thank you . do you know of any online sites where i can learn more about passwords. im new to this area of programming, and id like to get and idea of how hashes work.

---

### Post by heimo on 2006-01-25
[quote=LordHunter317]If you're not using a salted hash, one-way hashes don't gain you anything anymore if the hash(es) are recovered.  Even if you are using a salted hash, you have to be careful the salting is done correctly to make rainbow-table attacks infesible.  This usually means multiple rounds of hashing.[/quote]

Good points to keep in mind (and I hope more software vendors would agree). It's also always good to evaluate security as a whole - keeping passwords secure is not much value if password is 'password' or it's sent insecurely through insecure networks. Best to follow best practices by security experts (and not to listen me, 'cause I'm not one). Anyway: My undestanding is that implementing secure systems is hard and using secure algorithm won't be enough - also protocols used, practices, system security and such need to be taken seriously.

---

