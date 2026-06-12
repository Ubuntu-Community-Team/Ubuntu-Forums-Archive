---
title: "PyQt: Exiting Process"
date: 2011-03-04
forum: Programming Talk
---

### Post by Sailor5 on 2011-03-04
Greetings!

So I've been trying to track down an answer to this question for some time now. I did receive some solutions but when I put them into practice in my own script they didn't work. I'm posting my script below in hope someone can find a working solution to my problem.

So what is the 'problem' well currently when you exit PyQt's window the process carries on. Which I'm not wanting. So  I simply need to call quit() or raise SystemExit when the window has been called and everything will be hunky-dory. But I can't figure out how and that's where you the reader come in.

[http://pastebin.com/cSeSDcyp](http://pastebin.com/cSeSDcyp)

Please post your witty responses below.

---

### Post by cgroza on 2011-03-04
This is the third thread I see on this topic.
[http://ubuntuforums.org/showthread.php?t=1155388](http://ubuntuforums.org/showthread.php?t=1155388)
He solved it.

---

### Post by Sailor5 on 2011-03-04
> **cgroza said:**
> This is the third thread I see on this topic.
[http://ubuntuforums.org/showthread.php?t=1155388](http://ubuntuforums.org/showthread.php?t=1155388)
He solved it.

I've tried adding```

QtCore.QObject.connect(Form, QtCore.SIGNAL('triggered()'),
            self.Exit)

def Exit(self):
  raise SystemExit
```To my script but it still did not solve the problem. It defently does not exit the entire process.

** I think the problem is. I'm spawning a separate thread for the window GUI and thus when I call quit or raise SystemExit it doesn't close the main thread. Why am I such an fool?

---

### Post by cgroza on 2011-03-04
Did you try sys.exit(0)?

---

