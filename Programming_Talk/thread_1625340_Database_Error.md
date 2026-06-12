---
title: "Database Error"
date: 2010-11-18
forum: Programming Talk
---

### Post by cboxhero on 2010-11-18
I'm making a website, and I needed to test out my log in form.
I put all the info into my database and when I put it in, I got this
"Warning: #1265 Data truncated for column 'password' at row 1"
I encrypted my password with MD5. What's the problem?

---

### Post by amauk on 2010-11-18
MD5 hashes are 32 characters long
is your password column set to less than 32 chars?

Also, MD5 is quite vulnerable to collision attacks
you may want to consider using at least SHA1 (which incidentally is 40 chars)

---

### Post by cboxhero on 2010-12-02
That's not the problem. When I set it at the correct number of characters, it just makes the password into the encryption. It's not even an encrypted password. It's just a bunch of random numbers and letters.

---

### Post by amauk on 2010-12-02
> **cboxhero said:**
> That's not the problem. When I set it at the correct number of characters, it just makes the password into the encryption. It's not even an encrypted password. It's just a bunch of random numbers and letters.

Err, what?
MD5 (or other hashing function) hashes an arbitrary byte sequence into a fixed length "digest"

With the input as
"The hash of this sentence is..."

The outputs from the various hashing functions are as follows:

MD5
c26fc459238ff781ce31213c29a0434b

SHA1
bea26fa153d77206c13a064d9445776a76307d37

SHA256
59a87b4e9e8f47d77ece62be819ed86e78f520f74392027ab5d97b83d38bd644

SHA512
b3bb038849f24b6812a2753978c0af8e0bda0aa58db798aa0dbc4d8939633f684ae2c42d8c6c36b337304aaf57a7146a188b8a38f18d7c7e26306297ef03716b

---

### Post by amauk on 2010-12-02
Just to elaborate,
One-way hashing functions are used to eliminate the need to store user's passwords in plain text (among other uses, but storing password hashes is the most common usage)

Imagine a database table with 3 columns,
userid, username, password

When a new user registers, their details get added to the database

User AndyPandy registers a new account with the password "this_is_my_password"

Storing the password details in plain text, the table now looks like this

```
userid	username	password
1	AndyPandy	this_is_my_password
```

When AndyPandy logs in, it's simple to check if he has the correct password

His password gets sent over the wire in plain text,
arrives at your server in plain text,
a simple```
if (user_supplied_pass == db_stored_pass)
```
will tell you if he's entered the correct password

However, the password is sent over the wire in plain text, so anyone monitoring his network will see the password.
Also anyone with access to your database can see this user's stored password

Both of these things make this method very insecure

If you run all passwords through a one-way hash, and store the hash, our table now looks like this

```
userid	username	password
1	AndyPandy	a851308387ed93a0548c48b6150429aa
```

Anyone with access to the database now cannot see the actual password, only the hash
This is a lot more secure

The password check now becomes```
if ( hash_of(user_supplied_pass) == db_stored_pass )
```
Nowhere in the site's workings is the user's actual password stored

---

