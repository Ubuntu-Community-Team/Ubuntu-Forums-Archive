---
title: "cmd line when i load ubuntu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by bawbz on 2008-06-18
g'day
so heres my problem; 
i just installed
ubuntustudio-8.04-alternate-i386.iso

i load it in grub, it loads and all i get is a cmd line?????
where/how do i get the gui?
or do i have to download that seperately?
thanks

---

### Post by iaculallad on 2008-06-18
While in your terminal:

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by hyper_ch on 2008-06-18
but first you have to login with your username and password before you enter those commands.

---

### Post by iaculallad on 2008-06-18
Yap, be sure to authenticate your login first before issuing those commands :)

---

### Post by kesman on 2008-06-18
And don't worry if your password isn't shown when you type it, it's a security thingy, just keep typing and hit enter.

---

### Post by bawbz on 2008-06-18
thanks all! :-D

---

### Post by bawbz on 2008-06-18
ok now im getting: 
"
The package 'xserver-xorg' is not installed and no info is available.
"

or something along those lines. i swear i didn't have to do any of this sorta stuff last time i install ubuntu. very odd.!

---

### Post by kesman on 2008-06-18
That's odd, I'm sure xorg comes with ubuntu studio :O
Well, you can always install it with
```

sudo apt-get install xserver-xorg

```
If you wan't the normal ubuntu desktop, you could try
```

sudo apt-get install ubuntu-desktop

```
but I'm not sure if this works in ubuntu studio.

---

### Post by bawbz on 2008-06-18
apparently it can't find either of those 'packages'.
i'll try reinstalling!

---

### Post by hyper_ch on 2008-06-18
what error do you get? do you have an internet connection?

---

### Post by bawbz on 2008-06-18
ok now ive reinstalled i am able to 
perform "sudo dpkg-reconfigure xserver-xorg"
and play with keyboard settings
then when i go to type "startx"

i get this:

"Fatal server error: No valid Fontpath could be found.

giving up.

xinit: connection reset by peer (errno104): unable to connect 
xinit: No such process (errno103): Server error"

>________>

---

### Post by kesman on 2008-06-18
Are you sure your CD's not broken? Did you verify the md5sum of the downloaded ISO-file and the burned CD afterwards? Why did you download Ubuntu Studio instead of the normal "Ubuntu"?
Did something go wrong during the installation process?
What happens if you type:
```

sudo /etc/init.d/gdm restart

```

---

### Post by bawbz on 2008-06-18
still being a prick
guess the cd is dodgy
downloading regular ubuntu -_-
cheers

---

