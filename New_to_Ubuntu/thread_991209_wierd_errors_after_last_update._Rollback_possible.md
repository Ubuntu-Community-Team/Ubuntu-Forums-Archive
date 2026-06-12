---
title: "wierd errors after last update. Rollback possible?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by mormor on 2008-11-23
> Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.

ALso Compi* fusion seems to pull tricks on me. As it free*es.

Any way to do a rollback?

ubuntu 8.10 64 bit.

---

### Post by Michael.Godawski on 2008-11-23
Is this the error message when you run this in terminal:
```
gksudo synaptic
```

What gives you
```
ls -la .Xauthority 
```

Also try this

```
sudo chown username:username .Xauthority 			 		
```
and repleace userename with your username.

---

### Post by diablo75 on 2008-11-23
When does this error appear?  What are you doing when it occurs?  What kind of video card do you have?

... and are you typing * instead of the letter z on purpose?

---

### Post by mormor on 2008-11-23
THe synapticerror just disapeared magically.

> When does this error appear? What are you doing when it occurs? What kind of video card do you have?

... and are you typing * instead of the letter z on purpose?

THe error with compi* apears all the time. Browsing. Switching desktops. Cant find a spesific trigger to it. Dont know the videocard. But it has never been a problem untill last compi*-update. ( i have a acer travelmate 6291 laptop.)

The reason i use * is becouse the letter it replaces is not working on my keyboard, thanx to a coffee-spill some time back. : )

---

