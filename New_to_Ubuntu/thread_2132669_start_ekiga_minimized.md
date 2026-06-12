---
title: "start ekiga minimized"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by oogie boogie on 2013-04-05
Hi All,
After extensive searching I cannot find a way to start Ekiga minimized.
I've added it to the startup applications but cannot get it to start in a minized state .... I've tried the -r, -m, and -systray switches however none worked.:(

If anyone has an idea then I would be very grateful.

BTW I'm currently using 13.04 and Ekiga 4.01

---

### Post by jonobr on 2013-04-05
Have you tried [this]("https://help.ubuntu.com/community/Devilspie") program, devlispie?

---

### Post by oogie boogie on 2013-04-06
Thank you Sir that was a great tip...

In case someone else has this issue here is the code required in the .ds file in ~/.devilspie

( if 
( and 
( is ( application_name ) "Ekiga Softphone" )
) 
( begin 
( minimize )
( println "match" )
)
)

Also the copy of gDevilspie that I installed from the repositries did not start at all on my system I ended up using a copy from here [http://code.google.com/p/gdevilspie/wiki/gDevilspie](http://code.google.com/p/gdevilspie/wiki/gDevilspie)

---

