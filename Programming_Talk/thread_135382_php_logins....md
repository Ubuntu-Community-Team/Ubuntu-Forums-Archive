---
title: "php logins..."
date: 2006-02-23
forum: Programming Talk
---

### Post by grim918 on 2006-02-23
im working on a login script. i don't want it to be vulnerable to brute forcing attacks. Can somenone help me out and give me an idea of how to code a script that will only give a user 5 attempts to login, if unsuccesful then they will have to wait 20 minutes to try again. I don't know how to keep track of the user. Do I create a session for him and just create a counter that gives him 5 tries or do I check the IP address, or am I going about this all wrong. Thankz again for any help.

---

### Post by cwaldbieser on 2006-02-23
[QUOTE=grim918]im working on a login script. i don't want it to be vulnerable to brute forcing attacks. Can somenone help me out and give me an idea of how to code a script that will only give a user 5 attempts to login, if unsuccesful then they will have to wait 20 minutes to try again. I don't know how to keep track of the user. Do I create a session for him and just create a counter that gives him 5 tries or do I check the IP address, or am I going about this all wrong. Thankz again for any help.[/QUOTE]
I think I would keep track of that kind of state in the DB back end.  If you only try to track the session, the attcker could just start a new session and try again.

---

### Post by LordHunter317 on 2006-02-23
The only sane way to do it is to measure number of attempts in a window.  When a user first attempts to login and fails, you mark the attempt as failed in the DB and note the start time.  If they fail 'x' further attempts in the same period, you lock the account out and mark the lockout time.

Unlocking is done by comparing to the lockout time.

---

### Post by LordHunter317 on 2006-02-23
[QUOTE=cwaldbieser]I think I would keep track of that kind of state in the DB back end.  If you only try to track the session, the attcker could just start a new session and try again.[/QUOTE]You can't do it in session, you are correct.

---

### Post by grim918 on 2006-02-23
how do I keep the user from trying any further attempts. Do I ban the users IP for the specified time, and if yes then how do i check for the users IP. I'm sorry, but I just don't understand what I am supposed to lock when they fail on the 5th attempt. I can't lock any accounts because their is no way of knowing which account they are trying to access. Banning the IP for a specified time is the only thing I can think of.

---

### Post by LordHunter317 on 2006-02-23
> **grim918]how do I keep the user from trying any further attempts.[/quote]Define a DB table something like this (or integerate into your existing table, it doesn't matter):```
CREATE TABLE user_lockout (
     user text PRIMARY KEY,
     last_attempt timestamp NOT NULL,
     num_attempts integer NOT NULL CHECK (integer > 0),
     locked_out_time timestamp
) said:**
> [*]Check to see if they have a record in the table within your specified window, so something like:```
$time = SELECT last_attempt FROM user_lockotu WHERE user = $user;
$window = $now - $time 
```[*]If they are in the window, update the num_attempts record.  If it's greater then your threshold, lock them out and set the locked_out_time field to the current time.[*]If they are outside the window, create/update the record and set last_attempt to the current time and num_attempts to 1[*]If they're locked out, just ignore them.[/list]

> Do I ban the users IP for the specified time, and if yes then how do i check for the users IP.No, you cannot ban by IP.

[quote]I'm sorry, but I just don't understand what I am supposed to lock when they fail on the 5th attempt.You note they're locked out in a field.

> I can't lock any accounts because their is no way of knowing which account they are trying to access.How can you be verifying a password in the first place if you don't know what username it is for?  This makes no sense, and this exercise fruitless.

>  Banning the IP for a specified time is the only thing I can think of.It's also the wrong thing.

---

### Post by grim918 on 2006-02-24
ok now I get it. thankz again lordhunter.

---

### Post by oldmanstan on 2006-02-24
you might also try [http://www.phpfreaks.com](http://www.phpfreaks.com) for some code snippets or maybe even a complete module to do what you want.

---

### Post by simon_is_learning on 2006-02-24
maybe two session Variables, one with the numer of attempts, one with the IP .
then empty the session variable after 20 min.

---

### Post by LordHunter317 on 2006-02-24
No.  You cannot use session variables.  The attacker can spoof them.

---

### Post by Kerberos on 2006-02-25
Instead of a 20 minutes wait after 5 attempts, which can seriously inconveniance the real account owner, you can just drop it to 5 seconds between attempts - not enough to even be noticable but enough to stop any determined brute-force attempts.  I'd just store the current unix time in seconds in a field on the user database and disallow any other login attempts until that time is offset from the system time by 5 seconds.

---

### Post by simon_is_learning on 2006-02-25
[QUOTE=LordHunter317]No.  You cannot use session variables.  The attacker can spoof them.[/QUOTE]

Didn't thought of that. 
Is it more safe to use a database that stores vital information?

---

