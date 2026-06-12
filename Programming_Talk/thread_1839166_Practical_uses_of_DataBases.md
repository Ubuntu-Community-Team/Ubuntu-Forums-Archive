---
title: "Practical uses of DataBases?"
date: 2011-09-05
forum: Programming Talk
---

### Post by hakermania on 2011-09-05
Hello, I've made a couple of useful programs and I really cannot think what databases could be useful for. I know that programs like  'locate' do use a database, and I understand the reason, but except from that I cannot think a use of it in 'normal' (ordinary) programs.

My teacher was always insisting that a language that doesn't support database handling isn't language, so it must be very important but I don't get the reason.
Thanks for any tip. :confused:

---

### Post by ofnuts on 2011-09-05
> **hakermania said:**
> Hello, I've made a couple of useful programs and I really cannot think what databases could be useful for. I know that programs like  'locate' do use a database, and I understand the reason, but except from that I cannot think a use of it in 'normal' (ordinary) programs.

My teacher was always insisting that a language that doesn't support database handling isn't language, so it must be very important but I don't get the reason.
Thanks for any tip. :confused:As soon as you start handling more than a couple hundreds of pieces of data, you want to be able to retrieve/update them according to some criteria. This very forum is backed by a database... 

I don't agree that all languages should have database access built-in (if only because it locks you up on a specific database architecture)

---

### Post by doobrie on 2011-09-05
A database can be any collection of data - it doesn't necessarily have to be something as large as Oracle or Postgres etc.

I would say that any application that maintains lists of data uses a database.  Depending on the functionality you need, you need a  more feature rich database.  For example if you are maintaining a list of your contacts you may need a very simple database that only allows you to add, delete and iterate through contacts.

If you then needed to send out emails to certain people in you contact list based upon certain criteria, then you may start to need more SQL-type features.

Eitherway, you're using a database.

---

### Post by jhonan on 2011-09-05
Most business systems sit on top of databases - Accounts systems, Order processing, Revenue reporting etc. Banking systems, use databases (that's where your account data is stored)

Air traffic control systems, Hospital patient records, Supermarket scanners...

Ebay, Paypal, Amazon

Google... When you do a Google search, where do you think Google is storing all its data?

In fact, it's more difficult to come up with a list of programs that *don't* use some form of database than these that do! - Games, perhaps (although you could argue that scores are stored in a table, and things like configurations and levels etc.) - Utility programs, maybe.

---

### Post by Lars Pensjö on 2011-09-05
And then, the file system is really just another data base. Because of that, I would say all languages that support file input/output has some kind of DB support (counting standard library as part of the language).

---

### Post by Bachstelze on 2011-09-05
> **Lars Pensjö said:**
> And then, the file system is really just another data base. Because of that, I would say all languages that support file input/output has some kind of DB support (counting standard library as part of the language).

Well, no. The low-level filesystem operations are handled by the filesystem driver in the OS kernel. All the language needs (at least on UNIX systems) is a way to call the read and write system calls, then the kernel handles the rest. And that's a good thing because having to add filesystme supprt in every language when a new filesystem is added would not be fun...

---

