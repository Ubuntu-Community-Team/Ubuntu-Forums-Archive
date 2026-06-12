---
title: "Moving files from one server to my new share"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by mrwonx on 2008-04-26
I've been building a new Ubuntu machine to just act as a simple file sharing box so that the people I work with could troubleshoot things from the gui instead of the dieing 6 year old computer we were using.

So I copied the files from one of the shares over. Just copied it (I'm assuming this was my problem), and when I switched it over - can't save over their files, bunch of various errors having to do with permissions. 

Is there a better way to move the files over to a new share that I should be looking into to, or should I be looking at how the share is set up to make sure I'm not locking people out?

---

### Post by nsilva on 2009-04-30
I think your question is not very well stated. If the problem is permissions, other users are able to write into other shares if:

[LIST]
[*]Sudo as the other user (need the other user password)
[*]The owner of the share could change the access persmissions of their shares (chmod)
[/LIST]

---

