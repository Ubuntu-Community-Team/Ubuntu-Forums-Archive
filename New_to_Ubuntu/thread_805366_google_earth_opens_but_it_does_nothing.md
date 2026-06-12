---
title: "google earth opens but it does nothing"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-23
When I open google earth, the window opens as well as the black background of space and but nothing happens.

When I type in a location the "return" button does nothing when clicked.

Any suggestions?

---

### Post by sharks on 2008-05-24
Try reinstalling GE.

---

### Post by sharks on 2008-05-24
Or open google earth from terminal and post the error message here.

---

### Post by Steve413z on 2008-05-24
remove the following directories:

~/.config/Google
~/.googleearth

i had the same exact problem, and so is almost everybody else

---

### Post by jimv on 2008-05-24
Are you using a proxy for your internet?

---

### Post by saskatchewan on 2008-05-25
I ended up installing an earlier version and it works fine.

---

### Post by rpalyvoda on 2008-05-25
> **Steve413z said:**
> remove the following directories:

~/.config/Google
~/.googleearth

i had the same exact problem, and so is almost everybody else

Thanks, it helped!

---

### Post by Sealbhach on 2008-06-01
> **Steve413z said:**
> remove the following directories:

~/.config/Google
~/.googleearth

i had the same exact problem, and so is almost everybody else

I tried 

```
sudo rm ~/.config/Google
```

to remove but it won't let me.
> 
oliver@oliver-vaio:~$ sudo rm ~/.config/Google
rm: cannot remove `/home/oliver/.config/Google': Is a directory
oliver@oliver-vaio:~$ 

How do I get rid of them?


.

---

### Post by BlueSkyNIS on 2008-06-01
Try with ***-rf*** option, like:

```
sudo rm -rf ~/.config/Google
```

---

### Post by Sealbhach on 2008-06-02
Isn't the 

rm -rf

a fatal thing to do?

[http://blog.mypapit.net/2007/12/should-ubuntu-prevent-sudo-rm-rf-command.html](http://blog.mypapit.net/2007/12/should-ubuntu-prevent-sudo-rm-rf-command.html)


Maybe you mean

rmdir 

Thar might do it?

.

---

### Post by PmDematagoda on 2008-06-02
The rm -rf command is fatal only when you use it improperly(in the wrong path) otherwise it is just a normal and useful command which is what it is in this case.

---

### Post by BlueSkyNIS on 2008-06-02
I'm trying to help you :)


Cheers

---

### Post by Sealbhach on 2008-06-02
Thanks BlueSkyNIS. I've officially thanked you now.:guitar:

---

### Post by BlueSkyNIS on 2008-06-02
I'm glad I was able to help you.


Cheers ):P

---

