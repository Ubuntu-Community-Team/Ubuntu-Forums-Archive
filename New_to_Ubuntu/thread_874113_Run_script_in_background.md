---
title: "Run script in background"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by DBrocks on 2008-07-29
Hey guys. How can i run my SH script in the background, like a daemon. Thanks in advance!

---

### Post by unutbu on 2008-07-29
If the script is called myscript.sh, then run
```

myscript.sh &
```

---

### Post by sdennie on 2008-07-29
If you run it from a terminal you will also need to use disown to keep it running after you close the terminal:

```

my_script.sh &
disown
exit

```

---

### Post by unutbu on 2008-07-29
Vor, thanks for pointing out the 'disown' command -- I didn't know about that. I've always used nohup. Is that the same?

Also, just out of curiosity, I saved this script as 'test.sh':
```
#!/bin/sh
while true ; do
    echo "Hi!" >> ~/test/a;
    sleep 2
done
```
And ran it from a gnome-terminal like this:
```

test.sh &
```
I then closed the gnome-terminal, and looked inside ~/test/a. It was still printing 'Hi!'s! 

Then I logged out of my GNOME session, got to the GDM window, pressed Ctrl-Alt-F2, and logged in at a text terminal. The tesh.sh script was still printing more 'Hi!'s in ~/test/a!

Is this the effect of some configuration option I don't know about, or is this normal?

---

### Post by bodhi.zazen on 2008-07-29
or nohup ...

```
nohup script.sh &
```

---

### Post by DGortze380 on 2008-07-29
alt+f2 if you don't want to open a terminal to do it.
add it to /etc/init.d and update init.d to run it on login

---

### Post by bodhi.zazen on 2008-07-29
> **unutbu said:**
> Vor, thanks for pointing out the 'disown' command -- I didn't know about that. I've always used nohup. Is that the same?

[http://playingwithsid.blogspot.com/2007/10/disown-nohup-bash-commands.html](http://playingwithsid.blogspot.com/2007/10/disown-nohup-bash-commands.html)

---

### Post by sdennie on 2008-07-29
> **unutbu said:**
> Vor, thanks for pointing out the 'disown' command -- I didn't know about that. I've always used nohup. Is that the same?

Also, just out of curiosity, I saved this script as 'test.sh':
```
#!/bin/sh
while true ; do
    echo "Hi!" >> ~/test/a;
    sleep 2
done
```
And ran it from a gnome-terminal like this:
```

test.sh &
```
I then closed the gnome-terminal, and looked inside ~/test/a. It was still printing 'Hi!'s! 

Then I logged out of my GNOME session, got to the GDM window, pressed Ctrl-Alt-F2, and logged in at a text terminal. The tesh.sh script was still printing more 'Hi!'s in ~/test/a!

Is this the effect of some configuration option I don't know about, or is this normal?

It must be a configuration option.  I just tried your script and it stopped printing when I closed the terminal.

---

### Post by unutbu on 2008-07-29
Any ideas where I should look to find out why my terminal has nohup/disown always on?

I checked with pstree and found that when I run test.sh its parent starts as bash (spawned by gnome-terminal), but when gnome-terminal is closed, test.sh's parent jumps to init. 

I checked my .bashrc and .profile, and nothing jumped out at me as the culprit -- though I'm not great at understanding shell stuff.

I also am researching shopt, but I'm having trouble even finding documentation on what all the options mean.

---

