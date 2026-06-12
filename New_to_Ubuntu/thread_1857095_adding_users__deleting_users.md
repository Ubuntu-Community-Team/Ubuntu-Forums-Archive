---
title: "adding users / deleting users"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by bagzli on 2011-10-09
so I am doing this assignment for Linux course and I screwed up so now trying to fix my mistakes.

I need to add users and I started like this:

useradd – c George Jetson
I honestly don't even have an idea what that did.  I need to delete this home user along with his home diretory so I can add him properly with a command like this.

useradd –sbin/bash  –pjetson –d/home –m jetsong

I tried userdel -r George  (doesn't work)
I tried userdel -r Jetson  (still doesn't work)

So can somebody help out the newby?

basically my user needs to have following parameters:

username and password both are jetsong
user has to have valid home folder under /home
set their SHELL to /bin/bash
user has to change their password on first log in
password has to be changed every 60 days
and his account must expire in 90 days

so basically the rest of options I was going to modify the account later.  But problem is I can't recreate the account to start over and I have no idea how to delete the current one nor what is the username set to that account I have just created.

---

### Post by spiky001 on 2011-10-09
have a look in /etc/passwd

---

### Post by bagzli on 2011-10-09
when i did sudo su  seems to of allowed me to delete it.

I do have another question, when I add a new user and i want to ad a comment to that user i know the command is -c but can you give me an example of lets say adding a username test123 and i want in his comment to have Its a nice Day.  How would I do that?

useradd -c "Its a nice Day" test123

something like that?

---

### Post by azmyth on 2011-10-09
try:

userdel &#8211;r 'George Jetson'

---

### Post by mikejonesey on 2011-10-09
lol just to complicate things...

deluser --remove-home username
instead of...
userdel -r username

(you can configure deluser to auto remove homedirs, groups and check a couple a things like fstype or even backup the users files somewhere before deletion...)

---

