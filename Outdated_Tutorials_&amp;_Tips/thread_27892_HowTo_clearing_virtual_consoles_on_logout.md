---
title: "HowTo: clearing virtual consoles on logout"
date: 2005-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by soul_rebel on 2005-04-18
edit /etc/bash.bashrc for all users or ~/.bashrc for single user

add in the end

```
alias logout='clear && logout'
```

done!

you won't leave any trace of you console session when you log out.
bye

---

### Post by TravisNewman on 2005-04-18
[QUOTE=soul_rebel]edit /etc/bash.bashrc for all users or ~/.bashrc for single user

add in the end

```
alias logout='clear && logout'
```

done!

you won't leave any trace of you console session when you log out.
bye[/QUOTE]
 Just curious-- what are the benefits of doing this?

---

### Post by soul_rebel on 2005-04-18
let's say your box is shared between 20 users and some of them work from the command line, editing files and reading their mail, then with this you prevent someone to read the last commands of the user just before him, wich may contain some personal or valuable info.

I would make this the default behaviour of logout.

And it is cool too.

---

### Post by remmelt on 2005-04-18
Isn't that obvious? When you are in a virtual console and just did some stuff as root that other users do not need to see, you don't have to "clear" by hand. Also, it looks tidy.

Say, I cat'd a file, as root, that only root has read permission on. Now I type exit, and the contents of the file are still in plain view, for any user to see.
If you are running a one-user desktop system, this won't be a problem ofcourse. 

I edited the alias to trigger on 'exit', because that's what I always type, but it works either way.

---

### Post by Mike Douglas on 2005-04-18
couldn't you just put "clear" in .bashlogout?

---

### Post by soul_rebel on 2005-04-18
is there a global bashlogout? i don't have that file nor it works creating /etc/bash.bashlogout

---

### Post by TravisNewman on 2005-04-18
nice, didn't think about that. Very handy! I'm on a one-user system, so no benefit here, but very good idea!

---

### Post by soul_rebel on 2005-04-18
> I edited the alias to trigger on 'exit', because that's what I always type, but it works either way.

sometimes you use exit for other things than logout, so i don't recommend that setup.
for example after exiting a root session with "sudo su" I like to keep the output.

That's because I am not adding it to the first post.

---

### Post by remmelt on 2005-04-18
I didn't think of that... Good one. I like to still type exit instead of logout though... Here is my long-way solution:

Go in your /etc/inittab and add to the "1:2345:respawn:/sbin/getty 38400 tty1" lines the following code: "-I '\033[2J\033[f'".

Like so:
```
1:2345:respawn:/sbin/getty 38400 tty1 -I '\033[2J\033[f'
2:23:respawn:/sbin/getty 38400 tty2 -I '\033[2J\033[f'
... (etc)
```

This sends a clear console code on exit. An old modem thing (or something, I got this of some website too, OK ;))

Need to check out the .bashlogout.

---

### Post by soul_rebel on 2005-04-18
nice alternative! do you know if it's the best way of doing it? is there any human-readable option for getty that does the trick? Have you tested it.

Maybe I'll add this one on the first post.

---

### Post by Golovko on 2005-04-18
I've always added:
"trap clear 0"

to /etc/profile.

---

### Post by soul_rebel on 2005-04-18
>  	I've always added:
"trap clear 0"

to /etc/profile.

seems clean! what this is supposed to do?

---

### Post by remmelt on 2005-04-18
I'm sure it works, that's the way my Debian server is set up. As said, I got it off some website, it worked, so I didn't fiddle with it further.

---

### Post by hreker on 2005-04-19
Using "clear" is not really the best solution. On some platforms, the next person to log in can still use Shift-PageUp to scroll backwards (see also [this message](http://www.monkey.org/openbsd/archive/bugs/0402/msg00096.html), found on an OpenBSD list). A better way to do this is to append something like ```
# Make sure shift-pageup does not reveal anything for console logins
for ((i = 0; i < 200; i++)); do echo ''; done
clear

``` to your "~/.bash_logout" (not "~/.bashlogout", BTW). Or if you have root access, you can use the [approach described here](http://www.openbsd.org/faq/faq7.html#ConsoleClear).

---

### Post by soul_rebel on 2005-04-20
[http://www.openbsd.org/faq/faq7.html#ConsoleClear](http://www.openbsd.org/faq/faq7.html#ConsoleClear)
I think this applies only to OpenBSS. We do not have a /etc/gettytab...

I am testing all the solutions:
clear && logout does not work
trap clear 0 does not too
 -I '\033[2J\033[f' I think i need a reboot for this to work... cant reboot now
~.bash_logout is the dirty one, i don't like it at all.

---

### Post by soul_rebel on 2005-04-20
ok tested everything
I '\033[2J\033 this does not work too! scrollback buffer is accessible with shift + pgUp.

this is my hybrid solution:
add to /etc/bash.bashrc:

alias logout='for ((i=0; i<200; i++)); do echo ; done; logout'

I still have an idea to try...

---

### Post by hreker on 2005-04-21
> We do not have a /etc/gettytab... You're right soul_rebel, I should have checked that before posting. I did some Googling, and it [turns out](http://lists.debian.org/debian-security/2001/01/msg00098.html) that temporarily changing to another virtual terminal will clear the [scrollback buffer](http://www.monkey.org/openbsd/archive/misc/0208/msg00514.html). [This thread](http://lists.debian.org/debian-security/2001/01/threads.html#00097) addresses exactly the issue we're talking about. The "fix" [they propose](http://lists.debian.org/debian-security/2001/01/msg00147.html) is to use chvt 63; clear; chvt 1.

Of course we still need to modify that to switch back to whatever the current virtual terminal is, instead of to VT 1 regardless. One can use fgconsole to find out the current VT. Finally, the statements above should be executed only if we're actually in a virtual terminal, not when in a "normal" terminal in X. So I'd propose to put the following in ~/.bash_logout:
```
 # Clear the screen and the scrollback buffer when in a VT.
case "`tty`" in
  /dev/tty[0-9]*)
    CUR_CONSOLE=`fgconsole`
    clear
    chvt 63
    chvt "$CUR_CONSOLE"
    ;;
esac
``` To make this available for all users, you could put the code above in /etc/skel/.bash_logout, so that newly added users automatically get it copied into their home directory. Another alternative is to put it in a separate script, say /etc/bash.clear (that may not be the most appropriate location, though). Then you could modify your hybrid solution to source that script, by adding this to /etc/bash.bashrc:
```
 alias logout='source /etc/bash.clear; logout'
``` It's still a bit of a hack, but less ugly than the "for loop"-method, IMHO.

---

### Post by soul_rebel on 2005-04-21
this is the best we have so far. Thanks hreker.

What is needed it's a command to clear the scrollback buffer, which I suppose is a kernel feature, so .... any kernel hacker?

---

