---
title: "some times restarting ubuntu does help"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by 20aty48 on 2008-07-05
i am very new to ubuntu (about 10hrs ago) and learning a lot :) 

what i just learn is; after installing a program or making some changes on ubuntu we may have to restart ubuntu. (hope i'm right?)

here is my experience i wanted to listen mp3 on my new ubuntu on first try i failed, after some research i find out i have to enable **ubuntu-restricted-extras** by doing

 
  [LIST]
[*]Go to Applications &#8594; Add/Remove...
[/LIST]

      [LIST]
[*]Set Show: to All available applications
[/LIST]
     [LIST]
[*]Search for ubuntu-restricted-extras and install it
[/LIST]

and tryed mp3 on default program but after this.  i still failed to listen mp3 so i installed [COLOR="Blue"]Rhythmbox[/COLOR] music player i still failed to listen mp3. 

i have began to research every think about ubuntu including sound card and hardware on my pc and pulling my hairs out :)

than i thought " i did lots of changes on ubuntu maybe i need to restart it to activate the changes" soo it did work well, now i can listen mp3...

[COLOR="Black"][SIZE="2"]reason i send this thread is advice new beginners like me, after making some changes you may need to restart ubuntu

 
as a new user i do not want to give up easy on ubuntu a specially remembering to spend over 6 years and hundreds of formatting on win xp and still getting no where :)[/SIZE][/COLOR]

---

### Post by Sam Lars on 2008-07-05
Yes, even on Linux restarting does some helpful things and is a good place to start for some issues.

---

### Post by llamakc on 2008-07-05
Other than a new kernel there is no reason to ever reboot, provided your system is not hard-locked up and you can still ssh in (or gain access to one of the TTY's).

But yes, for newbies it may be easier to just reboot instead of figuring out which service needs restarting. Frankly I recommend learning how to use the commands `ps`, `pstree`, and `top` to investigate issues.

---

### Post by 20aty48 on 2008-07-05
Thanks for the replies.
 i will check out commands to get to root of the problems :)

---

