---
title: "Error on compile: /usr/bin/ld: cannot find -lXrandr"
date: 2009-08-29
forum: Packaging and Compiling Programs
---

### Post by Ang89 on 2009-08-29
Hi there, I've posted the same message on [ruby on rails forum]("http://railsforum.com/viewtopic.php?pid=107626#p107626"), and then I realized that this ubuntu forum is the more appropriate place.

I'm installing a program called fxri by using rubygem, and then I got a bunch of error message. The tail shows this:

```
/usr/bin/ld: cannot find -lXrandr
collect2: ld returned 1 exit status
make: *** [fox16.so] Error 1

Gem files will remain installed in /var/lib/gems/1.8/gems/fxruby-1.6.18 for inspection.
Results logged to /var/lib/gems/1.8/gems/fxruby-1.6.18/ext/fox16/gem_make.out
```

What is -lXrandr ? I can't find it in repositories. Where can I find that, or how can I fix this? I'm still using Hardy, by the way.

Thanks,
Ang

---

### Post by ad_267 on 2009-08-29
You probably need to install libxrandr-dev.

---

### Post by Ang89 on 2009-08-29
> **ad_267 said:**
> You probably need to install libxrandr-dev.

Works like a charm. Thanks!

Regards,
Ang

---

### Post by Ang89 on 2009-08-29
Successfully installed, but I can't start it. The command should be **fxri**, but it is not found. Maybe that's because I'm installing using Ruby's package manager, rubygem. Hm . . I think FXRI should be in Ubuntu's repository.

---

### Post by ad_267 on 2009-08-29
I'm not familiar with ruby applications, but usually compiling and installing an application are separate steps. Installing moves files into the system directories where they're needed.

When you run a command it searches in /usr/bin and a few other directories for the program to run. Enter "echo $PATH" to see the full list of directories. You could try searching for files named fxri to find installed files.
```
sudo updatedb
locate fxri
```

If you're in the directory where you built fxri, you could also try running ./fxri.

---

### Post by Ang89 on 2009-08-29
Ah, thanks ad_267.
Apparently, the fxri executable was put on /var/lib/gems/1.8/bin. That's because I'm not installing using aptitude (fxri is not on repository), but rubygems instead. It's a package manager for installing ruby library or programs.

Thanks,
Ang

---

### Post by ad_267 on 2009-08-30
If you like you could add that directory to your path. To do this you can edit the ~/.bashrc file and add a line to the bottom with:
```
export PATH=/var/lib/gems/1.8/bin:$PATH
```

That way you ran run the application by entering fxri.

---

