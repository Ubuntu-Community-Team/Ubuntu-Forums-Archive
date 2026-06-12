---
title: "[python] Restart yourself!"
date: 2009-10-28
forum: Programming Talk
---

### Post by Pyro.699 on 2009-10-28
Hey,

I was wondering how i would go about telling a python program to restart it's self. Here's the situation.

I created a BATCH file to upload a RAR folder containing new source.
I also created a BATCH file to download, extract, and replace the existing *.py files with updated ones & remove all *.pyc files.
What i would then like to do is send a signal over a socket to the program (who is still running all this time) to 'restart its self' meaning that all variables, objects and methods would be erased and it would start from line one again; re-importing all the modules.

Hope that made sense

Thanks
~Cody

---

### Post by Arndt on 2009-10-28
> **Pyro.699 said:**
> Hey,

I was wondering how i would go about telling a python program to restart it's self. Here's the situation.

I created a BATCH file to upload a RAR folder containing new source.
I also created a BATCH file to download, extract, and replace the existing *.py files with updated ones & remove all *.pyc files.
What i would then like to do is send a signal over a socket to the program (who is still running all this time) to 'restart its self' meaning that all variables, objects and methods would be erased and it would start from line one again; re-importing all the modules.

Hope that made sense

Thanks
~Cody

I don't know if you can do it inside Python, but how about calling the program in a loop in a shell script. Then, if the program simply exits, it will then be restarted.

---

### Post by benj1 on 2009-10-28
fork a process to call the program then exit the parent,(look in the os module) you wouldnt be able to control it from the shell, but from what i understand you dont need to.

---

