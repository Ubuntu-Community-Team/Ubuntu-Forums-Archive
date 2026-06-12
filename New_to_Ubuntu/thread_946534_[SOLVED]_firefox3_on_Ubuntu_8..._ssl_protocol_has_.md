---
title: "[SOLVED] firefox3 on Ubuntu 8... ssl protocol has been disabled"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by renepotvin on 2008-10-13
Hello, I'm new to this forum. I'm using Ubuntu 8.04.

My problem started when I allowed the update system to update my Firefox 2 to 3.

While installing Firefox 3 the updater simply let me hang with a disabled ssl protocol.

Now whenever I start Firefox ...
1- I get a message that some security measure could not be installed 
2- and whenever I encounter an ssl link I get a popup telling me my ssl protocol has been disabled. Then Firefox freeze.

I imagine this is not a feature as much as a bug. I've done some extensive search for an answer but I could not find anything recent on the matter. The help provided to users with this exact problem years ago mention files that either do not exit or I cannot find them on 8.04. Anyway nothing works.

BTW should I disable the update manager? Am I going to run into problems all the time? What do super users do?

Rene

---

### Post by aysiu on 2008-10-13
Maybe this might help?
[http://support.mozilla.com/en-US/kb/Firefox+cannot+connect+securely+because+the+SSL+protocol+is+disabled](http://support.mozilla.com/en-US/kb/Firefox+cannot+connect+securely+because+the+SSL+protocol+is+disabled)

If it's an issue of your profile changing ownership (perhaps you ran the command *sudo firefox* instead of *gksudo firefox* to update it?), then close Firefox, paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.mozilla
``` and then start Firefox again.

---

### Post by renepotvin on 2008-10-13
OMG, this totally did it! Thank you!
I simply had to get rid of cert8.db! 

Although finding it on the "byzantine" Nautilus that simply ignores the presence of files that i'm looking for (something I took for granted, duh) was an adventure. I now know to ignore the search option (you learn something new every day and today it was something about that file system).

This is the link that worked for me
[http://support.mozilla.com/en-US/kb/Could+not+initialize+the+browser+security+component](http://support.mozilla.com/en-US/kb/Could+not+initialize+the+browser+security+component)

---

