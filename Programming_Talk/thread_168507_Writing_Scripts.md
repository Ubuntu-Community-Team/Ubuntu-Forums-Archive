---
title: "Writing Scripts"
date: 2006-04-30
forum: Programming Talk
---

### Post by ricardo141 on 2006-04-30
Hi guys and gals,

Im new to Linux and Ubuntu and am just trying to get my head round how scripting works 8) 

Iam trying to get some basic scripts to work and am finding it a little difficult, if anybody out there can help with the following two problems I will be extremely grateful :-D 

Write a script that reads a list of names (found here) and creates a user account for everyone on the list. You will have to think carefully about the usernames and their uniqueness. Remember, they need home directories.

Write a script that creates useful .profile files for each user. What other login initialisation files are there? Why are they useful? Why are there different initialisation files (e.g., .login, .cshrc). 

Rich

---

### Post by drachir on 2006-04-30
Me thinks someone needs help with homework.

---

### Post by aysiu on 2006-04-30
Why don't you post what code you've tried, and people can point out what you might be missing?

---

### Post by ubuntu_demon on 2006-04-30
I moved this thread to programming talk.

---

### Post by ricardo141 on 2006-04-30
All i have managed to do is read a file in, but ive not been able to create a user account for each person:

#!/bin/sh
echo "Please type in your filename"
read ENTRY
echo "Here is your list"
sort -u $ENTRY

This opens a file with a list of names contained, and i know how to create user accounts: 

useradd john

but i really dont know hw to do the scripting part of it

any ideas??

---

### Post by sphinx on 2006-04-30
You'll need to use some sort of loop. Here is a pretty good reference page for the bash shell, have a look at the 'for' loop:

[http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html]("http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html")

---

### Post by yaaarrrgg on 2006-04-30
[QUOTE=ricardo141]All i have managed to do is read a file in, but ive not been able to create a user account for each person:

#!/bin/sh
echo "Please type in your filename"
read ENTRY
echo "Here is your list"
sort -u $ENTRY

This opens a file with a list of names contained, and i know how to create user accounts: 

useradd john

but i really dont know hw to do the scripting part of it

any ideas??[/QUOTE]

I don't think calling useradd will work, since it it an interactive program.  

There's two ways  to approach this problem.  First, you can use a program called "Expect" which allows you to automate the interaction with an interactive program.  

The second approach is to manually append a user to the /etc/passwd file.  If you do this, you will have to encrypt the password  and check uniqueness maunally.

Personally, I think Expect is probably the easier route.

---

