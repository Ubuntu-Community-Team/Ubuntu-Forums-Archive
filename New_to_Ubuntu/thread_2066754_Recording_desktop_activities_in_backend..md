---
title: "Recording desktop activities in backend."
date: 2012-10-05
forum: New to Ubuntu
---

### Post by pmohankumar on 2012-10-05
Hi friends,
*i need a screen recording software that should run without knowledge of user ie. backend in system.
*It should start with OS booting
*Only admin can control.

kindly update the name of software.

Thanks,
Mohan

---

### Post by androssofer on 2012-10-05
> **pmohankumar said:**
> Hi friends,
*i need a screen recording software that should run without knowledge of user ie. backend in system.
*It should start with OS booting
*Only admin can control.

kindly update the name of software.

Thanks,
Mohan

there is screen recording software, you can get it by using:

```
sudo apt-get install gtk-recordmydesktop
```

however running it as root in the background may be an issue... 

is there a reason for this? perhaps there is another solution?

as a guess:

you might be able to add the command to the rc.local script, however i'm not sure it would work.. work a try though:

open rc.local 

```
sudo gedit /etc/rc.local
```

then add this to the bottom (after installing gtk-recordmydesktop as mentioned above..)

```
export DISPLAY=:0 && sleep 60 && gtk-recordmydesktop
```

***note, this command has not been tested, nor do i know what it will do.. It might not even work..

---

### Post by Lars Noodén on 2012-10-05
There is also x11grab in the package ffmpeg and a package called kazaam.

---

