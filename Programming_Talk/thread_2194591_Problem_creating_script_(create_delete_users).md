---
title: "Problem creating script (create delete users)"
date: 2013-12-19
forum: Programming Talk
---

### Post by bpanos on 2013-12-19
Hi, i would like to create a script that can create and delete users and show time and date when user created and deleted. i would like as well if it possible the script to ask me when i am deleting a user if i want to store all the files and informations about user (time and date created-deleted). Thanks in advance any help will be helpfull !!

---

### Post by Lars Noodén on 2013-12-19
You'd probably want your script to wrap around [useradd](http://manpages.ubuntu.com/manpages/saucy/en/man8/useradd.8.html) and [userdel](http://manpages.ubuntu.com/manpages/saucy/en/man8/userdel.8.html).  Then if creation or deletion is successful it can echo the action, user, and date-time to a custom log file in /var/log/

---

### Post by bpanos on 2013-12-19
Thanx for your quick response. Is it possible if its not very dificult for you to create and send me a script like this because i am trying and i cant, i ve no idea from scripts, its something that  never developed

---

### Post by Lars Noodén on 2013-12-19
What have you tried so far?

I would start with not actually creating or deleting users then but instead just making a script that prints out (using echo) the line you think you would use.  You'll want to get input from the user and use that in a variable:

[https://help.ubuntu.com/community/Beginners/BashScripting#Variables](https://help.ubuntu.com/community/Beginners/BashScripting#Variables)

---

### Post by bpanos on 2013-12-19
ill go to my home and ill post what if done so far and i hope you can help me finish this. many thanks for your quick response again !!

---

