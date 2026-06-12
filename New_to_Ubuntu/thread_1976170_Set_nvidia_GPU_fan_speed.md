---
title: "Set nvidia GPU fan speed?"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-08
Does anyone know of a way to do this in 12.04? By default it is really low (like 40%) so it runs pretty hot so I'd like to turn up the GPU fan to 80% for example. On 11.04 and 11.10 I was able to use nvclock to do it, but that package is broken on 12.04.

Can anyone suggest a different method to change my GPU fan speed at login to 80%?

Thanks in advance!

---

### Post by cmont899 on 2012-05-08
I don't think it's possible if you are using the nouveau driver, look here if using the nvidia driver:

 [http://ubuntuforums.org/showthread.php?t=1678374](http://ubuntuforums.org/showthread.php?t=1678374)

---

### Post by d4m1r on 2012-05-08
Thanks! That did the trick...Basically, now I get the below option in my nvidia settings and it does seem to get set automatically at boot :mrgreen:

[IMG]http://i.imgur.com/HAJoXl.png[/IMG]

---

