---
title: "uninstalling programs and/or multiple installations"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by nycap on 2012-11-27
i have been using ubuntu for like 2 weeks now.  still having a helluva time getting acclimated to the terminal and debugging process.  to learn as i go i have just kept trying different things until something compiles and installs with out errors.  i still have not been successful in getting the program working that i want to use so its going on and on.

my question is can i uninstall a program that was successfully installed in order to use an earlier version?  can i do multiple installs of same programs?  is my file system so polluted that i should just make a new partition and start over?

thanks in advance.

---

### Post by drmrgd on 2012-11-27
From what I recall, most of the stuff you've been installing is from source (i.e. you're getting a package, making it, and installing it).  Those packages are difficult to install as it often requires a bit of finesse to make sure you have all the dependencies met and have everything set up correctly to compile.  So, don't feel bad!  Many of us who have been doing it for a while still run into problems from time to time.

The uninstall method is just as tedious in a way.  To uninstall, you'll have to delete all of the files that the package created when you built it.  Some just keep everything in a neat, tidy place.  Some put some extra files here and there so that they work with the system a bit better.  That's another reason why most prefer to use package managers and install strictly from the Software Center.

I would say that unless you have a space problem on your drive, you don't really have to worry about deleting the packages you don't want, and you certainly don't have to re-partition and re-install.  Each package should be its own entity, and should run when you explicitly ask for that program to run (sometimes you might have to launch a program with exact name or path of the binary just to make sure you get the version you want).  

So, in short, you don't have to worry about removing the extra packages.  But, if you decide you want to, just look for the files that make up the package and manually delete them.

---

