---
title: "Lynx won't run from php"
date: 2008-01-09
forum: Programming Talk
---

### Post by tatacalu on 2008-01-09
Hello!!!

I have a very nasty problem: 
I cannot run lynx from PHP anymore.
Until a few days ago everything was OK... but when I tried today to run 

lynx -dump http://www.~~~whatever~~~.com/file.php

with exec() nothing happened.

That file was on my server and if it was executed inserted a row in a Database table [it is just a test file so that I can see that lynx ran].

I ran 

exec('whoami');

and I saw that the user was "apache" [I did that to see if I can execute system calls through exec() ... obviously I can].

So ... the question is: what can I do about this problem ? I have absolutely no ideea what caused that and how to solve it.

Thanks !!!

---

### Post by tatacalu on 2008-01-28
I dug a little bit into apache's error logs and realised that every time I tried to run:
[PHP]exec ( 'lynx -dump http://www.google.com' );[/PHP]
In my apache httpd error log appeared a new line:
```
/root/: No such directory
```
I tried to run from the linux command shell:
```
sudo -u apache lynx -dump http://www.google.com
```
and the same error message appeared in the command shell.
Then I changed the attributes of my /root/ directory to 777... surprise, everything went OK - in PHP the exec() went fine, in the command prompt the sudo -u apache lynx .... went fine.

Thinking a little bit about security issues, I changed the attributes of /root/ as they were (to 750 = read/write/exec by owner, read/exec by group).

Given this situation, what options do I have to fix this problem ?? First of all, I don't understand why would lynx require full access to /root/ if it would be running as apache ...

Does anybody have any ideas on this?

Thanks!

---

