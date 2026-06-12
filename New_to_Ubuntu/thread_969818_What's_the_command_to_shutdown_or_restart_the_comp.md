---
title: "What's the command to shutdown or restart the computer when in shell?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-11-03
I'm trying to get Ibex working, but I need to login via the shell. I know the commands I need to type, but after I do that, how can I log out of the shell, and either restart my computer or take me back to the login screen? Thanks.

---

### Post by shifty_powers on 2008-11-03
```
sudo shutdown -r
```

---

### Post by FrostyFlames on 2008-11-03
"exit" or "logout" will take you back to a login screen.

"sudo shutdown -r now" will reboot when run.
"sudo shutdown -h now" will shut the system down completely.

---

### Post by Joeb454 on 2008-11-03
> **shifty_powers said:**
> ```
sudo shutdown -r
```

What's wrong with a good old ```
sudo reboot
``` and ```
sudo poweroff
```

---

### Post by shifty_powers on 2008-11-03
pfft that's just being picky :P

they both do the same thing, don't they? :D

---

### Post by anewguy on 2008-11-03
Depending, you might also need:

shutdown -r now

(really showing my age now, huh?)

---

### Post by AndyCooll on 2008-11-03
> **Joeb454 said:**
> What's wrong with a good old ```
sudo reboot
``` and ```
sudo poweroff
```
Or indeed
```
sudo halt
```
:cool:

---

### Post by Dr Small on 2008-11-03
```
sudo shutdown -h now
```

But I like my alias :)
```
alias sd='figlet -c '\''system shutdown'\'';sudo shutdown -h now'
```

---

### Post by kerry_s on 2008-11-03
i'll do few not mentioned:

just press> ctrl+alt+delete

sudo reboot

sudo shutdown -rf now

sudo halt

sudo shutdown -hf now

---

