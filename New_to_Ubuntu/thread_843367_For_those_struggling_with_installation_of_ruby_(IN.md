---
title: "For those struggling with installation of ruby (INCLUDING OPENSSL PROBLEM)!"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by mcbgun on 2008-06-28
Right I hope this reaches as many people as possible...

I spent hours trying to set up Ruby, Ruby Gems, Ruby on Rails and MYSQL only to be thwarted by an OPENSSL problem when trying to run WEBrick.

Don't worry there is a solution!

Ok from the ground up, here is what you do:

1) Install Ubuntu 

2) To be on the safe side DO NOT INSTALL ANY UPDATES THAT FLASH UP when you first load up the system (follow this guide first to make sure ruby works before you update everything else...that way you know what the culprit is if you update everything after and ruby fails to work!)

This may seem like a rather silly thing but to be honest...after hours of trying and failing...I didn't want to take any chances whatsoever!



3) Follow the instructions given at [http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu)       (MAKE SURE YOU START FROM "The recommended way" SECTION).

I think the main issue for the open ssl webrick problem is not editing the database.yml file properly. 

A book I'm using "Beginning Ruby on Rails E-Commerce" DID NOT tell me to include the host: localhost part in there.

This I think caused the main problem but like I said just follow what I've said here and you shouldn't have any problems.


Conclusion
-----------

Whilst you might have more success than I did using the synaptic package manager to install rails etc...personally I think it mucked up things for me.

I know its more of a quiz to type everything yourself in a terminal but hey...it worked for me!


If anyone has a simple noobie guide to get ubuntu working on a raid drive please let me know!


GOOD LUCK!

---

