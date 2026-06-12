---
title: "How to choose the best salts for password hashes"
date: 2011-11-11
forum: Programming Talk
---

### Post by Mezzoforte on 2011-11-11
I've created a MySQL database and I'm planning to add a table which keeps track of user details for a website.

I'm not a pro, so it would be nice to hear your opinions on security issues here. I've been reading a little about user management, and what I've gotten so far is that passwords should never (ever) be stored in plain text. It's been suggested that a better way to handle user authentication is the following: 

1. The user submits username and password.
2. The code takes the password and appends a salt.
3. Password + salt is hashed using md5 or similar, and this hash is what's stored in the table containing user details.

This is all well, but I also read that it's a bad idea to use the same salt for all users, which makes it a little more complicated. So, I want to use a different salt for every user's password. Let's say every user is associated with an id, then this id could be used as a salt. But it's too simple, isn't it? Any ideas on what would make a good salt? Does it matter if the salts for different user passwords are related? And what about size (or length), does that make a big difference?

Now let's consider a worst-case scenario. A (jubilant) hacker hacks my website and gains access to all the PHP files on the server, as well as everything in the MySQL database. In such a case, the hacker would see from my PHP files which salts I use, and in the database tables the hashes would be found. I guess the hacker could try to find out user's passwords by brute force, generating all md5 hashes possible and comparing to the hashes found in my database table. Is this feasible? And can this be made significantly more difficult by adding longer salts or more random salts or something like that? I guess there's little point in that, if the hacker also has gained access to the salts though. I'm new to this, so maybe I'm just exaggerating the possibility that somebody might gain access to the files containing the salts.

Ideas and opinions appreciated!

---

### Post by MadCow108 on 2011-11-11
first of all:
do _**not**_ use md5, that hash is broken. sha-2 should be good.

you only need to make sure as many users as possible user gets a unique salt
the salt is no secret information, you can save it in plaintext together with the password.
it should be long enough so a salt+weak password does not appear in general purpose rainbow tables but there is no point in making it longer than the hash used.
the hash of the username would be a choice.

there are standard functions for password hashing, like crypt, be sure to use them (with right settings) instead of doing it youself.
another thing you might want to consider is to make your password verification slow, e.g. by doing multiple rounds of hashing or using bcrypt.

---

### Post by Mezzoforte on 2011-11-12
Making password verification slow seems like a good idea. I was reading a little about bcrypt, and it looks a lot more secure than other those other hashing methods. Either I will go with bcrypt, or I'll just let someone else take care of authentication using OpenID. I guess most OpenID providers should have good security standards.

---

### Post by shubham1 on 2011-11-13
> **Mezzoforte said:**
> Making password verification slow seems like a good idea. I was reading a little about bcrypt, and it looks a lot more secure than other those other hashing methods. Either I will go with bcrypt, or I'll just let someone else take care of authentication using OpenID. I guess most OpenID providers should have good security standards.
what about this
create two rows password and salt key
suppose this is the array of salt keys in your php script
a[1] = "some salt";
a[2] = "!@#$%&^*()_+||";
and so on
store the key 1 or 2 or other in that row 
when you check login of a user
just see the id from row and use the salt

---

### Post by shubham1 on 2011-11-13
at the time of sing up just use random numbver alogirthm to get salt key and choose the salt

---

