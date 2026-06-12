---
title: "Ardentryst"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by Edwardj. on 2011-12-04
So, Playing the game mentioned, and would up manually shuting down my computer. Before this time Ardentryst ran fine. Now, The program won't start. Basically, I click on the app, and a grand total of nothing happens. The only thing I did between it working, and it not working, was shutting down my computer. Thoughts?
Thanks!

---

### Post by MG&amp;TL on 2011-12-04
Could you open a terminal and run:

```
ardentryst
```

so we can see the debugging output?

---

### Post by Edwardj. on 2011-12-04
The code line follows as such:

An error has occurred.
Traceback (most recent call last):
  File "/usr/share/games/ardentryst/ardentryst.py", line 4718, in <module>
    main()
  File "/usr/share/games/ardentryst/ardentryst.py", line 3835, in main
    raise Exception("** Please remove your options.dat file (in your ~/.ardentryst/ directory) and run Ardentryst again. **")
Exception: ** Please remove your options.dat file (in your ~/.ardentryst/ directory) and run Ardentryst again. **
Traceback (most recent call last):
  File "/usr/share/games/ardentryst/ardentryst.py", line 4722, in <module>
    handleException(e)
  File "/usr/share/games/ardentryst/ardentryst.py", line 683, in handleException
    open("bugreport.txt", "w").write(open(os.path.join(SAVEDIRECTORY, "log.txt"), "r").read())
IOError: [Errno 13] Permission denied: 'bugreport.txt'

I'm assumeing that I have to remove the "Options.dat" file, but I have no Idea where that is. Thanks!

---

### Post by MG&amp;TL on 2011-12-04
To remove that, open a terminal and type:

```
cd .ardentryst
rm options.dat
```

Then try it again.

---

### Post by Edwardj. on 2011-12-04
Bless you sir. Works Great. Thank you so much for the help, and your time!

---

### Post by MG&amp;TL on 2011-12-05
> **Edwardj. said:**
> Bless you sir. Works Great. Thank you so much for the help, and your time!

No problem, hope it keeps you amused. :)

Never mind, done.

---

