---
title: "Force password change NIS"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by TJCIB on 2008-08-15
I am running NIS for the login in our school's computer lab.

It is the beginning of the school year, all of the user accounts and brand new.

I have read that I can force users to change their password on first login (with a generic password or preassigned) by using 
```
chage -d 0 *username*
```

Will this work when they log in on an NIS client, or do they need to do their initial login on the NIS server?

Thanks

---

### Post by bab1 on 2008-08-15
Hi TJCIB,

A quick check of the man pages shows no first login option.  The "-d" option is > -d, --lastday lastday
    With this option the date when the password was last changed can be set to another value. lastday has to be specified as number of days since January 1st, 1970. The date may also be expressed in the format YYYY-MM-DD. If supported by the system, a value of zero forces the user to change the password at next login.
not what you want.  Most of this deals with expiration or listing of the data and not new account config.

A SUN description of the new user process can be found [[COLOR="Red"]here[/COLOR]]("http://docs.sun.com/app/docs/doc/806-1387/6jam692ck?a=view")

---

### Post by TJCIB on 2008-08-15
> a value of zero forces the user to change the password at next login.

This is exactly what I would like to do.  I know how to add/delete users.  And NIS is already set up and working for many users.

My my question is, do they need to do their "next login" on the NIS server for their password change to work properly?  

I don't want them to be prompted for a new password on a client machine, then the changes be entered on the /etc/passwd file on the client rather than the server.

---

### Post by bab1 on 2008-08-15
Test it out.  Make a test user and try it.  :D

Edit1: I missed the last line on the man page.  My bad.  :-(

Edit2:  I would try logging in to a client.

---

### Post by TJCIB on 2008-08-15
Yeah...I'll test it.  I just wanted to see if any red flags would come up from people.

I don't think I can mess too much up.

---

### Post by bab1 on 2008-08-15
I'm pretty sure that the test user idea will work.  Don't even think of having students near your server.  :D

---

### Post by TJCIB on 2008-08-16
Tried a test user "guest" with password "password"
ran ```
sudo chage -d 0 guest
``` on the server
then remapped the NIS server
I logged into a client machine with the old password...No prompt.
Tried a second machine...no prompt
Went to the server and logged into "guest"...instant prompt for new password

It appears the "chage -d 0 *username*" works only on the machine you run it on.

Any suggestions?

---

### Post by bab1 on 2008-08-16
Not a clue.  That does not sound like the way a client/server should act.  You sohuld be able to manage the server and the clients should respond.  I'll do some reading myself.  Try a google search on "chage -d 0 +NIS".

---

### Post by bab1 on 2008-08-16
You bring up the term locally.  I believe you should NOT have the guest account on the local machine (the server in this case).  If the account is local then NIS will not work.  See [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=890753&goto=newpost").  Read the part on NIS interaction.

---

### Post by bab1 on 2008-08-16
I just had a thought.  We have talked about other topics.  You mentioned that your client machines are XP.  Is this right?  If so, I wonder if this is another Windows/*nix interoperability problem.

---

### Post by TJCIB on 2008-08-16
my NIS network is totally Linux.  It is for the computer lab at the school.

I plan on doing some more reading and tweaking.  I just wanted to be cautious since school has already started.  If this were June I would be breaking my system left and right since a full reinstall would be happening in July...

---

