---
title: "[SOLVED] webbrowser module question in python"
date: 2008-07-19
forum: Programming Talk
---

### Post by seventhc on 2008-07-19
Hello everyone,
I have a question about the webbrowser module.

A friend of mine wrote a small script that uses the webbrowser module, but to close it the code uses killall like so.
[php]
if (count % 20)== 0:
        commands.getoutput('killall firefox')
[/php]So basically after 20 tabs are open Firefox closes.
It's fine and does close but when you close it that way the next time you open Firefox it wants to know if it should restore the session.
Is there a way that would close it properly, as if I just closed it by clicking on the x in the top corner?
I have read the documentation and although I can find everything about opening a browser, I can't find anything about closing them.
Is this possible to do?
Any help is appreciated.
Thank you.

ps. It isn't super important, the script is more of a project done for fun, but I would still like to know if there is a way to do it.
Thanks again.

---

### Post by mssever on 2008-07-19
> **seventhc said:**
> Hello everyone,
I have a question about the webbrowser module.

A friend of mine wrote a small script that uses the webbrowser module, but to close it the code uses killall like so.
[php]
if (count % 20)== 0:
        commands.getoutput('killall firefox')
[/php]So basically after 20 tabs are open Firefox closes.
It's fine and does close but when you close it that way the next time you open Firefox it wants to know if it should restore the session.
Is there a way that would close it properly, as if I just closed it by clicking on the x in the top corner?
I have read the documentation and although I can find everything about opening a browser, I can't find anything about closing them.
Is this possible to do?
Any help is appreciated.
Thank you.

ps. It isn't super important, the script is more of a project done for fun, but I would still like to know if there is a way to do it.
Thanks again.
I'm guessing you need to figure out which signal gets sent when you click the close button, then send that signal. But it might not be that simple. Firefox doesn't seem to do a very good job at handling signals.

---

### Post by seventhc on 2008-07-19
Yeah, I think thats what I need..but no luck in finding anything. I tried running Firefox from the terminal in hopes it would give some output when I closed it..again no luck. :(
I also think even if that did work, I'll also need a way for it to exit without asking if I really want to close all these tabs.
 At this point I am more curious if it's possible and less concerned about the actual script.

---

### Post by mssever on 2008-07-19
> **seventhc said:**
> Yeah, I think thats what I need..but no luck in finding anything. I tried running Firefox from the terminal in hopes it would give some output when I closed it..again no luck. :(
I also think even if that did work, I'll also need a way for it to exit without asking if I really want to close all these tabs.
 At this point I am more curious if it's possible and less concerned about the actual script.
Have you looked at documentation for all the signals listed by [FONT=Courier New]kill -l[/FONT]? That's the first place I'd look. Failing that, I guess it would probably be necessary to read up on X11 documentation. Since I know virtually nothing about X internals, I'm afraid I can't help too much there.

I don't know whether it's possible to do this without Firefox's cooperation. Oh, one more thought. As a long shot, it might be worthwhile to read up on XUL, Firefox's GUI toolkit. But that's probably the last thing I'd try.

---

### Post by seventhc on 2008-07-19
Thanks for that advice, I haven't even thought about that. I will try that.

---

### Post by ghostdog74 on 2008-07-19
> **seventhc said:**
> 
Is there a way that would close it properly, as if I just closed it by clicking on the x in the top corner?

you can change the restore options. see [here](http://kb.mozillazine.org/Session_Restore)

---

### Post by seventhc on 2008-07-19
> **ghostdog74 said:**
> you can change the restore options. see [here]("http://kb.mozillazine.org/Session_Restore")
Thanks for the reply :)
That would work but I want Firefox to have the restore feature as is and somehow have the script perform all the necessary actions.
But if it isn't possible I'll use this method for when the script is running.

---

### Post by nanotube on 2008-07-20
> **seventhc said:**
> Thanks for the reply :)
That would work but I want Firefox to have the restore feature as is and somehow have the script perform all the necessary actions.
But if it isn't possible I'll use this method for when the script is running.

after you do the "killall firefox", also have the script delete any "sessionstore.js" files in your firefox profile dir. that will kill the old "session", and firefox won't ask you to restore the session next time.

kind of a hack, but this will allow you to do what you want: no session saving when using the script, but you can still save sessions when using normally.

another idea (a better one, i think): when using the script, have firefox use a different profile, and in that profile, disable sessionrestore, and "ask before closing multiple tabs". so, when using from script, it won't bother you with crap, but when using interactively, things will work as you want (and as a benefit, you won't be nuking your sessionstore).

you can even have two copies of firefox running, one each with a different profile, so you can run your script just fine, even while you are using firefox interactively doing something else. (look at the "-no-remote" cli arg for firefox).

if you need help setting that up, just post back here.

---

### Post by seventhc on 2008-07-20
Thanks for that answer, I think that's probably the way to go. I won't be able to try it until later but looks like it will do what I need.
Thank you.

---

