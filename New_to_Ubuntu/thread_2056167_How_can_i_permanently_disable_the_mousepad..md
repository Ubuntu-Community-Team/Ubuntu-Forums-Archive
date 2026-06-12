---
title: "How can i permanently disable the mousepad."
date: 2012-09-10
forum: New to Ubuntu
---

### Post by PirateKarma on 2012-09-10
Hey guys, i have a really big problem with linux, where everytime i type the mousepad gets touched and ruins my writing process. It's driving my nuts, and I used the following command to fix it, but once i restart it goes away. Please help!!

```
killall syndaemon
syndaemon -d

syndaemon -i 4 -d
```

I'm running ubuntu 12.04.Also the option to disable the mousepad, in system settings does not work for me.

---

### Post by newb85 on 2012-09-10
Same problem here.  Would love to have a solution.

---

### Post by Hadaka on 2012-09-10
Hi, write a script with the commands you posted and
put it in  /etc/init.d   the startup file, that would disable the
mousepad on startup. and perhaps another script. "pad_activate"
to .....activate it.

---

### Post by Hadaka on 2012-09-11
Hi, here ya go...

```
 gedit off
``````
# script name =  off
# Disables mousepad while keyboard in use
#!/bin/bash
PATH=/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin/
killall syndaemon
syndaemon -d
#end
 
``````
chmod +x off 
```to activate...off......in terminal
```
./off
```you can put this in  etc/init.d  if you want, but you probably won't need to
with the defined included path

  ## gedit on
```
# script name =  on
#Enables mouse pad
#!/bin/bash
PATH=/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin/
killall syndaemon
#end
 
``````
chmod +x on
```to activate...on.....in terminal

```
./on
```I tested this and it works,  the -4 is a timmer, not needed
hope this helps.

---

### Post by dodo3773 on 2012-09-11
I use this script (taken from Arch wiki):
```

#!/bin/bash
 
 synclient TouchpadOff=$(synclient -l | grep -c 'TouchpadOff.*=.*0')

```

I map it to Windows key + M to toggle it on and off. You can probably set up an alias like mousetoggle or whatever though too if you want.

---

### Post by dodo3773 on 2012-09-11
@Hadaka 

With an if statement you should be able to convert that script to a toggle (if on / if off) if you wanted to. Save you from needing 2 commands / scripts.

---

### Post by NikTh on 2012-09-11
Hi , 

based on your Thread's title "[B]How can i [COLOR=Red]permanently[/COLOR] disable the mousepad" 

[/B]try this command first in terminal 

```
synclient TouchpadOff=1
```and see if this worked. Touchpad must be disabled.

If yes then add this command in startup applications. 

I think its not even needed to write a script . Just open startup applications and click Add then in the command box write the command 
```
synclient TouchpadOff=1
```Logout and login . 

Thanks

---

### Post by newb85 on 2012-09-11
Er...I guess I misspoke.  I really don't want to permanently disable the touchpad.  My machine has a button for disabling it manually.

Rather, I was looking for a way to have it disabled automatically when I'm typing.  The option for that in the Mouse and Touchpad dialog doesn't seem to do anything.

---

### Post by NikTh on 2012-09-11
> **newb85 said:**
> Er...I guess I misspoke.  I really don't want to permanently disable the touchpad.  My machine has a button for disabling it manually.

Then ignore everything I wrote on above post and follow what "scripters" suggested.

> **newb85 said:**
> Rather, I was looking for a way to have it disabled automatically when I'm typing.  **The option for that in the Mouse and Touchpad dialog doesn't seem to do anything**.

I have to agree with that. This option seems useless. Not doing anything for me too.

---

### Post by newb85 on 2012-09-11
And judging from the currently running threads, it's an issue that affects a lot of users and especially bothers those new to Ubuntu.  One of those small bugs with a big impact on Ubuntu's reputation.

But then, this forum might not be the place for that soapbox...

---

### Post by NikTh on 2012-09-11
Hi  , 

Ok , then the solution is simple as that.. Look the attached image.

and please change your Thread's title by edit the first post , so other people with same problem will be helped. 

> e.g : disable touchpad while use the keyboard or something like that. 

Thanks

---

### Post by newb85 on 2012-09-11
> **NikTh said:**
> Hi  , 

Ok , then the solution is simple as that.. Look the attached image.

and please change your Thread's title by edit the first post , so other people with same problem will be helped. 

 or something like that. 

Thanks

Works great for me (although I prefer the default delay of 2 seconds).  Unfortunately, I'm not the OP, so I can't change the title or mark the thread as solved.

As easy as this is, I still wonder why the option in the Mouse and Touchpad dialog didn't get the job done.  Is syndaemon not what it's using (or trying to use) under-the-hood?

---

