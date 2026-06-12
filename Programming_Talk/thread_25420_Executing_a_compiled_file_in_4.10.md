---
title: "Executing a compiled file in 4.10"
date: 2005-04-10
forum: Programming Talk
---

### Post by drchatty on 2005-04-10
I took a graphics class once (all theory, very little programming) and I'd like to get back into that.  I may have OpenGL set up correctly, but I'm not sure.  I have an old program from the class (done on Solaris) and it compiles.  I try to run it, and I just get 'commend not found'.  I'm in the same folder as the file, and it is an executable.  Can anyone tell me why this isn't working?  

Matt

---

### Post by toojays on 2005-04-10
It would've helped if you posted how you compiled it and how you tried to run it, but I can guess.

If your program is called "foo", and you are in the directory where it lives, you execute it by typing "./foo".

If you just type "foo", the bash shell will only execute foo if it can find it in the PATH. This is kind of a security feature to stop sysadmins being tricked into running programs they didn't mean to run. The "./" tells bash, "yes I really do want to run the program in the current directory."

Is this what happened?

---

### Post by drchatty on 2005-04-10
That did it, thanks.

---

