---
title: "can't login after installation, ubuntu 13.04"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by 4md1t on 2013-05-09
hi ,   i have installed ubuntu 13.04  through dual booting  windows 7 premium . 

after i choose ubuntu on dual booting page ,next  Log in page appear, I entered USErname and password correctly , but it does not accept .  it just can  enter through guest mode , i even can not access to the internet ,  it ask me permission  .. and still it does not accept my root pass .

what is the main problem here ? 
how can i access to recovery mode ? to find out the username and reset password ...


My notebook is AMD APU A8-35000M 
6GB RAM  , 
AMD RAdeon HD 6740 G2 , 

OS : ubuntu 13.04 amd64.


**[SIZE=4]Solution found  : [/SIZE]**

[FONT=Book Antiqua][SIZE=3][B]This is a bug in the latest 13.04 Wubi diskimage... which can get installed by running an out of date wubi.exe from 12.04 or 12.04.1 (another bug).

You need to get the latest Wubi for 12.04.2 from here: [http://releases.ubuntu.com/12.04/wubi.exe](http://releases.ubuntu.com/12.04/wubi.exe)

Or the 12.10 Wubi from here: [http://releases.ubuntu.com/12.10/wubi.exe](http://releases.ubuntu.com/12.10/wubi.exe)[/B][/SIZE][/FONT]

---

### Post by Impavidus on 2013-05-09
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You may have to hit shift repeatedly. Just holding doesn't always work.

---

### Post by _sluimers_ on 2013-05-09
Why not reinstall Ubuntu? 

I'm sorry if that takes a lot of time, but trying to crack your password is probably more difficult.

---

### Post by 4md1t on 2013-05-09
i was holing all the time .. 

ill try now , thank you .

---

### Post by 4md1t on 2013-05-09
i re-installed two times ,   still same case ..

---

### Post by 4md1t on 2013-05-09
i tried a lot ,   i couldn't access to recover mode .. 

is there any solution ?

---

### Post by Impavidus on 2013-05-09
Ah, wubi, that changes things.

Anyway, glad you solved it.

---

### Post by UltimateCat on 2013-05-10
There is another approach but I honestly have not tried "root password recovery"

I realize that these instrustions are for a Debian sys but these steps should be able to be applied as well-
Unless I am mistaken-- Just trying to help-


[http://debian-bits-and-snips.blogspot.com/2011/07/root-password-recovery.html](http://debian-bits-and-snips.blogspot.com/2011/07/root-password-recovery.html)

---

