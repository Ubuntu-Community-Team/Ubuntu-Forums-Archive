---
title: "Postgresql with synaptic?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by mlemily on 2008-07-23
Hi all,

I'm trying to get postgresql running and have a few questions...
I'm on Hardy, 8.04

I found this page useful:
[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

My main question is, when I open up the synaptic package manager, and search for 'postgresql' I return an entry for pgAdminIII but not for postgresql; however, the above page seems to indicate one can use synaptic to install postgres:

"Or you can use synaptic/adept to install the postgresql package."

Do I need to add software repositories to be able to get postgresql?

In my infinite foolishness I then proceeded to install postgres from the command line, using the following (again, from the page above)

sudo apt-get install postgresql

I then proceeded to 'Basic Server Setup' and ran:

sudo -u postgres psql postgres

ALTER USER postgres WITH ENCRYPTED PASSWORD ' <***password***> ';
 \q

Then I went back to synaptic and installed pgAdminIII

Now for my second question:

pgAdminIII doesn't seem to register that I have postgresql installed (I'm told by my boss that I should show an entry under Servers for Postgresql 8.3, and I don't)

Is there a way to get pgAdmin to register I have postgresql installed?

My guess is that because one was installed from the command line and one from synaptic they are not seeing each other.

Thanks for all your help!
Emily

---

### Post by roquefilipe on 2008-07-24
Add/Remove, Synaptic, apt-get and aptitude are all just frontends to the [APT]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool"). So you can use any of them to install software. That is also why you can only use one at a time. 

I did a search for postgresql in synaptic and it returned a list with 234 items. What kind of search did you do?

About pgAdminIII, I believe it's not supposed to register any postgresql server. You have to tell it what server to use. I assume it will be the localhost so ip 127.0.0.1. I just followed the instructions from the help page and had no problem. So if you still encounter problems redo all your steps.

---

### Post by Seisen on 2008-07-24
You need to enable the Universe Repository in order to pull the postgresql server package.

---

### Post by mlemily on 2008-07-24
Hmmm....
I do have the universe repository enabled (its checked, along with the multiverse, when I check my 'Software Sources)

and 

I'm searching for postgresql in synaptic using the Search field in the upper right of the 'Add/Remove Applications' window.
I have Show: All Available Applications, selected

I return 6 results:
OpenOffice.org Database
Glom
TOra
Gambas2
ferret
pgAdminIII

Thanks for your suggestions, obviously I'm still missing something here.... 
:)

Emily

---

### Post by roquefilipe on 2008-07-24
Oh, I believe you are confusing something. 

Add/Remove (under Applications menu) in fact only shows those 6 packages. This program only displays programs that have a Graphical User interface, GUI, which is why postgresql is not listed. postgresql doesn't have a GUI and is more like a service than an application, just like the apache server, although everything is software.

The Synaptic Package Manager, available under System->Administration, is more complete, with more features like version freezing, etc, but more important it displays all available packages. This is what you should use to check for postgresql.

---

### Post by mlemily on 2008-07-25
Ah!  Thank you!
You were correct, I had missed the Package Manager under the Administration menu.  It is indeed a much more complete and precise tool!

That solves my problem, now on to setting up my server.

Thanks again for your prompt replies, I just knew it was something simple I was overlooking!

Emily

---

