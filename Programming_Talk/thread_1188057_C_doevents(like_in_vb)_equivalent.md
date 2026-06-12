---
title: "C doevents(like in vb) equivalent"
date: 2009-06-15
forum: Programming Talk
---

### Post by smkururu on 2009-06-15
Hi, I need help.
I'm working on a ncurses game. I want to put some music in it that comes from the pc speaker. The problem is, whenever I play the music, the game freeze until the music stop. I think this is because the game play the music, wait it to stop, and then resume the game. Is there any way to play the music while playing the game? I usually use doevents in vb, but this is C. Thanks

---

### Post by PmDematagoda on 2009-06-15
> **smkururu said:**
> Hi, I need help.
I'm working on a ncurses game. I want to put some music in it that comes from the pc speaker. The problem is, whenever I play the music, the game freeze until the music stop. I think this is because the game play the music, wait it to stop, and then resume the game. Is there any way to play the music while playing the game? I usually use doevents in vb, but this is C. Thanks

You probably could use process threads to achieve this, maybe [this]("http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html") tutorial could help.

---

