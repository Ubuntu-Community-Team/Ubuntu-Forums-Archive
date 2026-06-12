---
title: "[SOLVED] Can I use .bash_login like this?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-12
I want to use is like Sessions. So have it load up a script every time I log in. I currently only have one command in .bash_login, and that is ./Scripts/StartScript. Now I know that command works in the terminal, but when I log in it doesn't work how I was expecting. I was expecting it to work like Sessions. In Sessions I have it execute the StartScript and it works perfectly. I think the .bash_login is just trying to boot it up too soon. Any clue how to do what I am trying to? Am I making any sense?

---

### Post by KIAaze on 2008-09-12
Mmh, I'm not sure, but first of all, I think .bash_login is only called when you "log in" on a terminal using bash.
So it would only be called when you open a terminal.

Next, try using the full path like this:
```
/home/user/Scripts/StartScript
```
or
```
~/Scripts/StartScript
```

> When  bash is invoked as an interactive login shell, or as a non-inter active shell with the --login option, it first reads and executes  commands  from  the file **/etc/profile**, if that file exists.  After reading that file, it looks for **~/.bash_profile**, **~/.bash_login**, and **~/.profile**, in  that order, and reads and executes commands from the first one that  exists and is readable.  The --noprofile option may be  used  when  the shell is started to inhibit this behavior.

man bash: [http://linux.die.net/man/1/bash](http://linux.die.net/man/1/bash)

Usually, I just put stuff I want to run when I launch a terminal in **~/.bashrc**
I don't know where it's called from, but it's called. :)

---

### Post by sdennie on 2008-09-12
Is there a reason you can't just use System->Preferences->Session?  My guess from your description is that it's not working from .bash_login because your script depends on having the DISPLAY variable set properly (which in turn requires your X session to be started).  In that case, using .bash_login isn't appropriate but System->Preferences->Session is.

---

### Post by KIAaze on 2008-09-12
There's also /etc/rc.local to run stuff at startup.
However, everything in there is run with root permissions and before even logging in.
Not sure if this is what you want.

Note: /etc/rc.local exits as soon as an error is encountered, so make sure your scripts exit successfully (exit 0) before putting them in there.

---

### Post by ibuclaw on 2008-09-12
I agree with vor.

For logging in, there is also the gdm config directories to consider too.

/etc/gdm/PreSession/Default

Then put the full path to the script and arguments at the bottom there.

Regards
Iain

---

### Post by slughappy1 on 2008-09-12
The reason I didn't want to use Sessions, is because I have a script that I use when installing to a new system. I have asked before, but no one has been able to answer how to add stuff to the Sessions menu using the terminal ( or at least ME not having to do it personally ).

I see that I am using the .bash_login wrong. I wasn't sure when it loaded, but vor is right when he said that I need X to be started. 

I have never heard of the gdm config directories. Would I be right in assuming that they are called when the login screen comes up?

---

### Post by KIAaze on 2008-09-12
> **slughappy1 said:**
> I have never heard of the gdm config directories. Would I be right in assuming that they are called when the login screen comes up?

Not 100% sure, but I suppose so. Only found this concerning it:
>  this is the PreSession script, which is run before the session is started
[http://ubuntuforums.org/showpost.php?p=4620556&postcount=2](http://ubuntuforums.org/showpost.php?p=4620556&postcount=2)

> The reason I didn't want to use Sessions, is because I have a script that I use when installing to a new system. I have asked before, but no one has been able to answer how to add stuff to the Sessions menu using the terminal ( or at least ME not having to do it personally ).

_For Gnome >= v2.14:_
Just add a .desktop entry in .config/autostart/ ;)
In a script, you could do this either by simply copying over a prepared desktop file or you can write the desktop file dynamically from the script using cat as follows:
```
cat > file.desktop < EOF
line 1
line 2
line 3
EOF

```
Details about this method: [http://forums.devshed.com/other-programming-languages-139/what-does-eof-do-328074.html](http://forums.devshed.com/other-programming-languages-139/what-does-eof-do-328074.html) (I didn't even know I could use something else than EOF... ^^ )

_For Gnome < v2.14:_
cf gentoo wiki link below.

_Links:_
How to autostart stuff in different desktop environments: [http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)
Why the Gentoo wiki is wrong concerning Gnome: [http://linux.derkeiler.com/Mailing-Lists/GNOME/2008-04/msg00027.html](http://linux.derkeiler.com/Mailing-Lists/GNOME/2008-04/msg00027.html)
Official specifications: [http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

---

