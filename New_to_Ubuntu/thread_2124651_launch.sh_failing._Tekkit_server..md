---
title: "launch.sh failing. Tekkit server."
date: 2013-03-11
forum: New to Ubuntu
---

### Post by Eyeball114 on 2013-03-11
My .sh is set to executable. I double click on the .sh to launch the server and the terminal opens and closes instantly. Am I forgetting something?

---

### Post by Cheesemill on 2013-03-11
Try launching the sh file from a terminal, it should give some error messages which will help us diagnose the problem.

---

### Post by Eyeball114 on 2013-03-11
newb here depending on gui to much :( 

In terminal, I get to the folder where ther .sh is located. How should I finish out that line in terminal to launch it?

---

### Post by Cheesemill on 2013-03-11
Once you are in the folder containing the sh file just do...
```
./filename.sh
```

---

### Post by Eyeball114 on 2013-03-11
Like this?

```
/media/zach/6e6209ee-a84e-4ba4-8398-2e4f3be6d421/Tekkit-Server/.launch.sh


```

Result:
```
bash: /media/zach/6e6209ee-a84e-4ba4-8398-2e4f3be6d421/Tekkit-Server/.launch.sh: No such file or directory
```

incase I misunderstood I ran it without the .in ./launch.sh, same results. File name is correct.

---

### Post by Cheesemill on 2013-03-11
Change to the directory first then run the file...
```
cd /media/zach/6e6209ee-a84e-4ba4-8398-2e4f3be6d421/Tekkit-Server
./launch.sh
```

---

### Post by Eyeball114 on 2013-03-11
I figured it out, and I feel so stupid haha. .sh was written tekkit.jar trying to execute Tekkit.jar 

All came down to one letter...Thanks for all the help, I was wracking my head over this for about 3 days.

---

