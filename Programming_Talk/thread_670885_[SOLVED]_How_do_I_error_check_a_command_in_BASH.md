---
title: "[SOLVED] How do I error check a command in BASH?"
date: 2008-01-17
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-01-17
I'm writing a script to automate a few things for some new users. I already have a script that installs flash but I also want to install VLC for DVD playback.

I have the command:

```
gksudo aptitude install vlc
```

How would I go about error catching on this? I know for a command like wget I can do this:

```
wget http://blah.com/blah.jpg || echo -e "internet not working";
```

What can I do and further more, what exactly does the '||' mean?

thanks!

---

### Post by Cappy on 2008-01-18
You can use
```
sudo apt-get install vlz || echo ERROR
```
Use sudo for terminal based apps and gksudo for graphical apps.

"II" means "or". If the first argument fails it goes to the next argument.

----

You can also use something like
```

sudo apt-get install vlz
if [ $? -gt 0 ]; then
    echo "ERROR!"
fi

```

---

### Post by oodlesOfmoodles on 2008-01-18
Thanks!

It's working, though could you possibly explain:

```

if [ $? -gt 0 ]; then
    echo "ERROR!"
fi

```

Specifically : $? -gt 0

Thanks!

---

### Post by kevykev on 2008-01-18
> Specifically : $? -gt 0

$? contains the return code of the last executed process. -gt means greater than. Usually programs return zero on success or something else on failure. I would usually use -ne (not equals) instead of -gt because some programs return < 0, but you'll have to check the man pages for each executed task to be sure.

---

### Post by oodlesOfmoodles on 2008-01-18
thanks man!

---

