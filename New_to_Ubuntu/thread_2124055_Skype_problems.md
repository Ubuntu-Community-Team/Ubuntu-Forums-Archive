---
title: "Skype problems"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by cave2596 on 2013-03-09
Hello,

i have Ubuntu 12.04 LTS and Sykpe 4.1.0.20.
It worked normaly for a few months until today.
When I open a chatroom in Skype, the new window fills the complete screen.
I can't see the top bar or something else anymore.
There is only Skype.
Because of the missing top bar, I can't even close Skype.

After a restart, it happens again.

Does someone know this problem?
Or can anyone halp me?

Thank you very much
cave2596

---

### Post by gifford on 2013-03-09
Here is a link that might help.
[http://askubuntu.com/questions/159287/skype-chat-opens-full-screen-and-i-cant-get-off-it](http://askubuntu.com/questions/159287/skype-chat-opens-full-screen-and-i-cant-get-off-it)

---

### Post by Mark_in_Hollywood on 2013-03-09
Try this:

first do the Skype Options menu under Chat deselect use default view. Then follow this steps:

If this fixes your problem, please mark the post as solved by pulling down "prefix:" to "Solved".

Close the skype.

go to /home/userfolder/ (is that maybe cave2596?)

select the show hidden files or cntr+h

rename the ".skype" folder to ".skype_backup"

open the skype

you will see the ".skype" and ".skype_backup" folders at above location.

delete the ".skype" folder and rename the ".skype_backup" to ".skype"

Close the skype

again open the skype.

then the skype will be working fine..

from:

[http://askubuntu.com/questions/159287/skype-chat-opens-full-screen-and-i-cant-get-off-it?rq=1](http://askubuntu.com/questions/159287/skype-chat-opens-full-screen-and-i-cant-get-off-it?rq=1)

---

### Post by cave2596 on 2013-03-10
Thank you for your answers!
The only problam I have:
It doesn't work.

Has someone another idea?

---

### Post by Mark_in_Hollywood on 2013-03-10
I forgot to ask you to give the make and model of the computer you have this problem on. That knowledge can be critical to finding you a solution. Otherwise, those posting here can only think in 'generic' terms.

---

### Post by cave2596 on 2013-03-11
Hello,

after i made a update on my other Linux computer, the same problem occured.
=> Mistake in the Update?

---

### Post by jsabina1 on 2013-03-11
Since I installed skype I've never been able to see the buttons to close minimize etc on the chat window. Only on the main skype window.
I had so many problems installing it that I didn't think to solve it :P

---

### Post by Mark_in_Hollywood on 2013-03-11
I forgot to ask you to give the make and model of the computer you have this problem on. That knowledge can be critical to finding you a solution. Otherwise, those posting here can only think in 'generic' terms.

---

### Post by cave2596 on 2013-03-11
One model is a Virtual Box.

But the problem occurs on very different Computers.
All since the update.

So it doesn't depend on the Computer

---

### Post by Mark_in_Hollywood on 2013-03-11
At the terminal:

sudo apt-get -f

post the results if there is a problem.

---

### Post by cave2596 on 2013-03-12
There was no problem found.

---

