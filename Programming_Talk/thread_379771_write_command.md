---
title: "write command"
date: 2007-03-08
forum: Programming Talk
---

### Post by finer recliner on 2007-03-08
im not sure if this works in bash, but in the c shell there is a "write" command in which you can chat with anyone logged into that server like so:

```

write username hello, how are you?

```
(where username is the person you want to chat with)

however my friends at work like to mess with each other by doing something like:
```

spam.pl |write username

```
where spam.pl is a script that generates rediculous amounts of random text. this will flood the users screen and it executes so quickly, you wont even have time to see who the user was that sent it to you. hehehe

```

cat etc/passwd | write username

```
this is another fun one if you go to a large university like i do and there are thousands of users that exist.



so thats the fun part on how to mess with you friends, but now im looking for a way to stop it. the easy way is to use the command
```
mesg n
```
this will simply turn off your ability to receive messages from other people.
if you get a spam attack, i also found that ^D will close the shell altogether. but what im really looking for is a way to leave messages on, but be able to stop it if i get spammed by a friend.

---

### Post by Mr. C. on 2007-03-08
This sure goes back to the good 'ol days.

The write command is two way.  If you want to write others, you will be write-able.

MrC

---

