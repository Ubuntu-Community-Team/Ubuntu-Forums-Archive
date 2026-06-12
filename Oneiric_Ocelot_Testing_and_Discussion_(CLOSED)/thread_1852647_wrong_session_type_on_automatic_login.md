---
title: "wrong session type on automatic login"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lprofil on 2011-09-30
Hello,

i would like to log in automatically when i typed in my passphrase for encryption.
My default session should be "GNOME Classic (no effects)" but where i get is the Unity Desktop. 
Where or how to change that?

Thanks in advance!

/lprofil

---

### Post by cariboo on 2011-09-30
What session is set in /etc/lightdm/lightdm.conf, I boot to Unity when logging in, so my lightdm.conf looks like this:

> cat lightdm.conf

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
allow-guest=false


You should be able to change the user-session to what you need.

---

### Post by lprofil on 2011-09-30
Thanks mate,

of course, wh changed to lightdm, i forgot about that.
That seems to be the right config file, but which types 
of session options can i choose?

can i try:

[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu-[COLOR="Red"]classic[/COLOR]
autologin-user=myusername

---

### Post by cariboo on 2011-09-30
If you do make a change, make a backup copy of lightdm.conf first, that way if something breaks you can get back to a working lightdm.

---

### Post by lprofil on 2011-09-30
Thanks Cariboo,

i just found this post:

[http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-lightdm-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-lightdm-when-using-auto-logins)

and will give it a try.

/lprofil

---

