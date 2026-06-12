---
title: "MySQL Log in trouble"
date: 2007-01-18
forum: Programming Talk
---

### Post by welshboy on 2007-01-18
Hi guys,

I'm having some trouble logging in to the mySQL server on my machine.

I've used the following command:

mysql -u emyr - p 

And then I enterred my password, and apparently it's all wrong.

Is there a way to reset the password at all?  Any help would be truly awesome.  Many thanks :D

=======================

After mucking around, I worked out a soloution, and it is as follows (maybe nothing new here but still....may help out a noob like me :) )

I ran mysql as root, 

sudo mysql

Which got me in to the data base, so I create a new user for my self by doing

Grant all on *.*  to emyr identified by "password"; (not gonna put my password up ;) )

And then logged out as root, and ran it with my own user and it worked.

Note of caution however.  You need the " "'s around the password, and don't forget the semi-colon at the end.

And be careful who you give priveleges to.  I've done this like this as I'll be the only one using the mySQL server.  You may want to think carefuly about who you allow to do what. (If others have access to your mySQL server that is)

---

