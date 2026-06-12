---
title: "Implementing a protocol: How to send passwords"
date: 2009-09-24
forum: Programming Talk
---

### Post by tom66 on 2009-09-24
I'm designing a simple protocol for communication between a server, which manages a MySQL database, and a client, which might fetch information like products/orders/customers and have limited editing permissions. This is a programming exercise for me more than anything else. The protocol requires authorisation (e.g. a login) for the staff backend parts.

However, I don't know what to do when it comes to authorisation.

There are two methods I see:

**Number 1** Store passwords in the database as plaintext. The client sends a hash of the plaintext password and salt appended together. The server can validate the password by doing the reverse, but using the plaintext password in the database. The salt is sent in cleartext to the client and is only valid for one log in. The salt is generated using a cryptographically secure random number generator, usually /dev/random on Linux (it uses /dev/urandom at the moment, because it's set to non-paranoid mode, and /dev/random blocks too often on my laptop. However, if it's under a lot of network traffic, the /dev/random file will probably not block.) Problem is, if the database is stolen, passwords are available for all users, which could be A Bad Thing.

**Number 2** Send passwords as plaintext, relying on the network interface being encrypted (e.g. over SSL or 802.1x encryption) to reduce interception chances. The passwords are stored hashed in the database, possibly with a salt. To validate, hash the password and check equality. This prevents a stolen database being a major problem.

So which is best? I can't decide.

Thanks, Tom

---

### Post by geirha on 2009-09-25
Number 3, Store hashed passwords in the database. The client hashes the password using the same salt, then sends the hash to the server, which compares the hashes.

---

### Post by MadCow108 on 2009-09-25
I'm no expert but isn't your suggestion just like number one?
if someone steals the hashes they have access to all user accounts by just logging in without hashing the hash (which requires some work but should be possible in most cases)

I'd say number 2 is the way to go, just ensure (and not hope) the password is sent encrypted.
Storing passwords as plaintext on the server is in my opinion a huge mistake because even if you did find out someone stole the database you will have to reset the password of every single user.

But again I'm no expert.

---

### Post by Zugzwang on 2009-09-25
> **geirha said:**
> Number 3, Store hashed passwords in the database. The client hashes the password using the same salt, then sends the hash to the server, which compares the hashes.

Which is technically worse than the other two cases: If the hash-code database is stolen, it can immediately used by an attacker. Since the server only wants to know the hash-code of the password, the attacker can simply provide it from the database to get access. 

Additionally, by listening to the packets sent by the client, an attacker can also obtain the hash-code of the password, which in turn is again enough to get access to the server.

---

### Post by smartbei on 2009-09-25
How about this:

Server stores a hash of the password + salt, with the salt being per user and also stored in the DB.

Client sends to server a Login request with the username.
Server sends to client the per-user salt (salt1), and another one-time salt (salt2). The client does hash(hash(password + salt1) + salt2), and sends this to the server.
Server computes the same value, and checks to make sure that is is correct.

salt1 prevents the use of rainbow tables to guess the original password. salt2 prevents replay attacks.
EDIT: This does not solve the situation where the hash DB is stolen.

This does not protect against MITM attacks. For that, I would recommend using some PKI solution (such as using this over SSL).

Note that each salt should be 8 bytes (more is fine), and the hash should be at least SHA-1.

---

### Post by MadCow108 on 2009-09-25
how does that protect against the hash database being stolen?

if i have the hash from the db I log in get the one time salt, hash the hash with that and tadaa I'm in without knowing the password.

So far I understand it the hashing must be done on the server only to prevent a stolen db from being useful

---

### Post by smartbei on 2009-09-25
You're right - my mistake.

---

