---
title: "[SOLVED] skype api - missing libdbus-1.so.0"
date: 2007-10-11
forum: Programming Talk
---

### Post by YoG%*@ on 2007-10-11
hi, 

i'm trying to send an sms through a java application using the skype api.

the skype api has a linux library (libJSA.so), which depends on libdbus-1.so.0, which i do not have and which i was not able to get a hold of by googling for half an hour... 

i have a newer version of libdbus on my system, but using that one doesn't seem to work either.

does anyone have any experience with this kind of problem and the skype api? 
are there any other prepaid - sms services which you know of that i could use instead?

thanks a lot for any advice!
mux

---

### Post by YoG%*@ on 2007-10-11
solved my problem: 
i found an rpm package containing libdbus-1.so.0.0.0 at [http://www.rpmseek.com/index.html](http://www.rpmseek.com/index.html) and extracted the library from it.

---

### Post by kenken64 on 2007-12-31
hey dude,

Mind sending me the shared library and skype4java to [email]kenken64@singnet.com.sg[/email].

I cant get mine working. the libJSA seems got problem when invoke some function on the libdbus.

---

### Post by dEeP-fRiEd on 2008-08-11
hi,

I have the same problem, I found the  libdbus-1.so.0 file in rpmseek (thanks for the link), but what do I do with it?

I tried putting it in several directories, but the Java4Skype API still crashes with an "UnsatisfiedLinkError".

I only started using Ubunto (version 8.04) recently and don't have much knwoledge of how to install anything on a linux machine.

Any help is much appreciated.

regards
dEeP-fRiEd

---

