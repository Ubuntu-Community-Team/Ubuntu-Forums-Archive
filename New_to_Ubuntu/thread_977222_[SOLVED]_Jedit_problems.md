---
title: "[SOLVED] Jedit problems"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by DavidMP on 2008-11-10
Hello,

I'm new to ubuntu and so far all has being going well, however, I'm trying to install jedit (I use it to write music with the lilypond tool) and all seems to go well until I try to use it and then it freezes.
Attached are the screen-shots of the frozen state and the java files installed in my computer.

Any help is greatly appreciated

---

### Post by Pro-reason on 2008-11-10
Can you use Java successfully for other things?

Is there any particular reason why you need to use jEdit instead of gedit, kate, kwrite, nano, vim, emacs, mousepad...?

---

### Post by DavidMP on 2008-11-11
Yes, I write musical scores using using the lilypond language. I have recently tried the denemo front end but feel it is not quite there yet; under windows XP I used the lilypond tool for jedit. I would like to keep working under Ubuntu; it seems other people are using jedit and have fixed their problems but I tried the same things and it still hangs.

---

### Post by DavidMP on 2008-11-15
Solved.

It was a bug between compiz-fusion and java as reported [here]("http://marc.info/?l=jedit-users&m=122452033600347&w=2") and [here]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6632124").
This has been fixed by Sun in Java 6.10 which is not available in the Hardy repositories. I upgraded to Intrepid (I was going-to anyways) and installed Java 6.10 and then jEdit 4.3pre15 from its SourceForge page (The repository has only jEdit 4.2 stable). Lilypond tool seems to be working again.

Cheers

---

