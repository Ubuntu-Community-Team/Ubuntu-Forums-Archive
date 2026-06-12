---
title: "How do I run a terminal application through Alacarte?"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by ConchX on 2012-02-13
I bought a game online called Trauma, It's a folder and if I set it to execute in the properties, I can execute it from the terminal or without the terminal, but I want to run it from my "Games" menu, using alacarte, but nothing is working. So far I've tried.

"/home/username/trauma/runtrauma"
"/home/username/trauma/ ./runtrauma"
"sudo /home/username/trauma/ ./runtrauma"

Nothing is working, I either get permission denied, or nothing happens.
I also tried to chmod 777 the whole dir, doesn't seem to make much difference.

Please help me guys :popcorn:
Thank you :KS

---

### Post by ptn107 on 2012-02-13
Something's amiss.  Check your permissions once more:
```
chown -R $USER /home/$USER/trauma/
chmod -R 755 /home/$USER/trauma/
```

I would avoid setting 777 on anything.  If the above isn't working then it's not a permissions issue.

---

