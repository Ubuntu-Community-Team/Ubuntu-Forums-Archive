---
title: "cannot upload or download in Teams unbuntu 22.04"
date: 2022-05-20
forum: New to Ubuntu
---

### Post by smallville1979 on 2022-05-20
brand new install, brand new user not good on coding. 
there is a bug fix for this that just worked I found the code on this forum but cant remember. 
I just installed microsoft teams now back to the same problem, cant upload or download or work with email attachments. 
have u got the bug code sudo command line fix please? 
its a basic bug fix that should solve it.

---

### Post by Tadaen_Sylvermane on 2022-05-20
do you remember anything about the thread you found it on? did you post on it? anything at all? the search can be used quite well by anyone. i just did a search for your name and only got 2 posts. if you can't remember any of the content then the rest of us are just shooting in the dark to help you.

---

### Post by #&amp;thj^% on 2022-05-20
sniped see post below

---

### Post by #&amp;thj^% on 2022-05-20
> **Tadaen_Sylvermane said:**
> if you can't remember any of the content then the rest of us are just shooting in the dark to help you.

+1
There has been a lot of complaints over this.
Is it installed as a snap?
Ubuntu 22.04 uses a newer version of this core library, that the current .deb version of the teams client does not like.
They recommend "snap install/run teams"
Also another tip was said to work.


For a lot of people, snaps may solve this particular issue, but introduce a ton of other issues (drag/drop not working,copy/paste not working, inability to reach needed parts of the filesystem for attaching files etc).

Until a new deb release fixes the glibc issue og snaps are fixed on a very foundational level, safest bet is probably running teams in a browser like Chrome. Not ideal by any means, but it works.

---

### Post by smallville1979 on 2022-05-21
Ii already downloaded teams then it stopped working again.

---

### Post by smallville1979 on 2022-05-21
are u saying uninstall teams or what exactly?

---

### Post by #&amp;thj^% on 2022-05-21
No I merely point out Teams is just not working in Jammy ATM.
_Until a new deb release fixes the glibc issue_, you'll have to use a Browser like Chrome to upload or download.

---

### Post by smallville1979 on 2022-05-21
it doesnt work in chrome.

---

### Post by #&amp;thj^% on 2022-05-21
I don't need teams or want teams, but here again: [https://docs.microsoft.com/en-us/answers/questions/785952/ms-teams-crashes-in-ubuntu-2204.html](https://docs.microsoft.com/en-us/answers/questions/785952/ms-teams-crashes-in-ubuntu-2204.html)
out of advice for you now.

---

