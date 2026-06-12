---
title: "synaptic package manager no longer working"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by shoup on 2008-06-28
I am very new to using linux, and tried to load medibuntu.  I didn't do something right, and now when I try to use synaptic package manager I get the following message:

E: Type '<!DOCTYPE' is not known on line 3 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I am not sure what I messed up trying to use medibuntu, but right now I just want to get everything else up and running normally.  Is it possible to re-load the ubuntu package from the cd I have without messing everything else up?  Or is there a way to correct this problem more easily?  Any help and advise I can get will be greatly appreciated.  

A confused but still a happy non-windows user, shoup.

---

### Post by bettlebrox on 2008-06-28
There must be some wrong with the format of the file, post the contents of /etc/apt/sources.list.d/medibuntu.list . It should be a plain text file and not start with something like "<!DOCTYPE" (that looks like XML or HTML).

Also, have a look at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) for instructions on how to add the Medibuntu repositories to your system.

---

### Post by pytheas22 on 2008-06-28
If you go to System>Administration>Software Sources, unselect the medibuntu repositories, then close the utility.  You'll be prompted to reload the packages list; agree to do it and after that you should be up and running again.

If this doesn't work, please post the output of:
```

cat /etc/apt/sources.list
```

EDIT: sorry, I read your post too quickly.  The output of:

```
cat /apt/sources.list.d/medibuntu.list
```

would be more useful than the first command.

---

### Post by shoup on 2008-06-28
I went back and tried to reload the medibuntu software, and now everything works great.  I must have not typed something in correctly last night.  Thanks for the suggestions, this was my first time with a problem using linux, and just a little work solved everything.

---

