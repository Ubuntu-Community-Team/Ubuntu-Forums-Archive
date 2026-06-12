---
title: "[SOLVED] Managing multiple versions of java?"
date: 2008-11-25
forum: Programming Talk
---

### Post by talkingcomet on 2008-11-25
Hi guys,
I'm new to ubuntu!!!
Just migrated from windows last day..
And this forum has been a big help
Now this is a problem I need to solve..
Back in windows I could use multiple versions of java for my development.
It was a simple matter of changing the path..
Is there any way in ubuntu I could use that?
Install java 1.4 and java 5.0 and use either one of them as the need arises?
I hope this is the correct place to post this query!!!!

---

### Post by doyouhas on 2008-11-25
Yes it is the right place to post the question. 
For the JRE you can use
```

sudo update-alternatives --config java

```
Fyi, try searching for the answer to your question first. I found this answer with one search through the Ubuntu Forums.

---

### Post by talkingcomet on 2008-11-25
hmmm.. really?
have been searching since last night..:(:(
may be am not using the right key words..:confused:
can u please post the link to the thread..

---

### Post by talkingcomet on 2008-12-01
dont bother..
got the answer..
i was looking for some command through which i can manage environment variables like path in windows..
and at last i found the
 # export set PATH=/opt/j2sdk1.4.2/bin:$PATH
command.. 
:)

---

### Post by jespdj on 2008-12-01
The update-alternatives command only works when you installed Java from the Ubuntu repository (e.g. using Synaptic or apt-get), it does not work when you installed Java manually by downloading it from Sun's website (which you seem to have done, since you have it installed in /opt, which is not the standard place where Java is installed on Ubuntu).

---

