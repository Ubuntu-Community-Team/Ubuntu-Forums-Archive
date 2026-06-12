---
title: "oops need help"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by stormchas2000 on 2008-06-29
I was downloading limewire,  it needed some dependencies so it was downloading them   then it froze up.   since then I have been getting a message stating    E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

when i try to do this it tells me i need     
dpkg: requested operation requires superuser privilege


please help if you can    I am a newbie  so bekind

---

### Post by crashovaride on 2008-06-29
You may need to do the following:

su root {password}
dpkg --configure -a

if you can't get into root with a password, you may need to change your root password. If you need help with that. Let me know. I'll give you some instructions.

---

### Post by hyper_ch on 2008-06-29
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Troll_the_Great on 2008-06-29
I would suggest ```
sudo dpkg --configure -a
```.
Tell me if it worked.
Cheers!

---

### Post by stormchas2000 on 2008-06-29
Ok I will remember to be more specific in the title      
I tried the command but my password is either not working or something else is wrong

su: Authentication failure



thanks

---

### Post by Troll_the_Great on 2008-06-29
Try with my post.Use "sudo" instead of "su root" and then tell me if it worked.

---

### Post by hyper_ch on 2008-06-29
are you logged in as "first" user that you setup when you installed ubuntu?

---

### Post by stormchas2000 on 2008-06-29
yes i am the only user,    sudo command tells me i need

dpkg: requested operation requires superuser privilege

and su command tells me

su: Authentication failure

---

### Post by Troll_the_Great on 2008-06-29
Man, try sudo instead of su root!!!See my first post and run that command!

---

### Post by stormchas2000 on 2008-06-29
OK  thanks guys   I think it is working      Troll you had it thanks again

---

### Post by Dutch70 on 2008-06-29
> **Troll_the_Great said:**
> I would suggest ```
sudo dpkg --configure -a
```.
Tell me if it worked.
Cheers!

+1 You should be able to just use the above, and then put in your password, and hit enter! 
you wont see your password or the fact that it is doing anything. just hit enter.

Edit: guess I was too slow :)

---

### Post by Troll_the_Great on 2008-06-29
Glad I could help.Root is the super user in linux, and root account is disabled by default in linux.That's why it said " Authentication failure".If you want (but I wouldn't recommend) you could type:
```
passwd
``` 
and then type a root password.But you can do anything with "sudo".When it tells you that you need super user privileges just type "sudo" and then your command.
Cheers!

PS:Also remember to mark the thread as "solved" so others to benefit from it.You can do it from "Thread Tools" from the top of the page.

---

### Post by Dutch70 on 2008-06-29
You may want to check this thread on runnung as root!:)

[http://ubuntuforums.org/showthread.php?t=765414&highlight=telling+people+run+root](http://ubuntuforums.org/showthread.php?t=765414&highlight=telling+people+run+root)

---

