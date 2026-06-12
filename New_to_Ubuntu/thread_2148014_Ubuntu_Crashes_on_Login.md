---
title: "Ubuntu Crashes on Login"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by prasa043 on 2013-05-23
I've been using Ubuntu for a while now and recently have been trying to learn Ubuntu/Linux better; anyways, I was trying to figure out how to make Ubuntu open terminal on startup. I looked online a little bit and (not being too careful) I entered ```
sudo startx
``` in the terminal, and I've been having problems. Whenever I try to login as my user, it crashes almost immediately and returns to the login screen. (I can log in as a guest fine) If I open terminal from the login, I can log in fine but if I try sudo startx again, I get what appears to be a completely blank desktop, and I don't think I can do anything. A similar thing happens if I try ```
sudo stop lightdm   and 
sudo start lightdm
```. 
 
I did look online I didn't find any solutions to my particular problem except for a suggest clean install; is there any other way out of this?

Thanks.

---

### Post by grahammechanical on 2013-05-23
When you get what seems to be a completely blank desktop, can you still get to a terminal? Ctrl+Alt+T = terminal. Ctrl+Alt+F2 = tty.    Try

```
dconf reset -f /org/compiz/
```
```
setsid unity
```

If you do not have dconf-tools installed
```
sudo apt-get install dconf-tools
```

I am assuming 13.04. These commands will reset Compiz and restart Unity. I am guessing that you crashed Compiz. For the information of anyone who is interested, it is not good to try to start the xserver when it has already been started during the loading of Ubuntu and we are at a desktop.

Regards.

---

### Post by prasa043 on 2013-06-14
Sorry I responded so late - I ended up following your advice but I forgot to post back here. 
Thank you for your help!

---

