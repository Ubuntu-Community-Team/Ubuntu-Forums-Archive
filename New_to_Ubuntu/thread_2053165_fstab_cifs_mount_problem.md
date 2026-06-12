---
title: "fstab cifs mount problem"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by dvrs on 2012-09-04
Hi there,

As a newbie who's recently taken the step back into the Linux world after several years absence I've been delving into the world of home Samba and Windows networking.

I've been following this excellent guide (and related threads) in my efforts to learn how to mount windows (and samba) shares in Lubuntu 12.04:
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

I can successfully mount my windows 7 share using this command:
```
sudo mount -t cifs //MATSLUND-HP/Users/Mats\ Lund /home/mats/MATSLUND-HP -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

However, my attempt of trying get this share to mount automatically upon boot by adding the following entry to /etc/fstab has failed:
```
//MATSLUND-HP/Users/Mats\ Lund        /home/mats/MATSLUND-HP  cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0       0
```

(gives error "[mntent]: line 15 in /etc/fstab is bad").

Any ideas or pointers?

Thanks,
Mats

---

### Post by TheFu on 2012-09-04
I've never tried to mount a remote CIFS share in the fstab.  I usually just whimp out and take the exact command that is working and drop it into /etc/rc.local. That will be run as root automatically at every boot.

I probably would not use a guest user nor would I mount it with 777 permissions. That is too permissive.  Find or create a new group that all uses on the Ubuntu machine share. Mount with 770 or 775 permissions and force the group.

---

### Post by steeldriver on 2012-09-04
Not sure but I *think* that the simple backslash escape for the space (which works in the shell - when you mount at the command line) doesn't work in fstab - try using the octal code for 'space' i.e.

```
 //MATSLUND-HP/Users/Mats\040Lund        /home/mats/MATSLUND-HP ...
```

---

### Post by DogMatix on 2012-09-04
I may be completely misguided here. BUT, is it possible to discover the UUID of a Samba share to use in fstab ?

---

### Post by dvrs on 2012-09-05
Thanks for the feedback.

Please ignore the excessive permissions - at the moment it's only me who's playing around on my little home network so I've given myself some freedom ;-)

I believe I've tried replacing '\ ' with '\040' but that didn't work either. I will confirm that though.

The /etc/rc.local route sounds like an acceptable workaround - but I would still like to get the fstab approach to work (and understand why it currently doesn't).

UUID - how do I identify the UUID for the share? 

Oh and it's worth mentioning that my router is set up as a DHCP server which is why I used the netbios name rather than the IP address.

Cheers,
M.

---

### Post by Morbius1 on 2012-09-05
I took your exact line and added to my fstab changing only the mount point. After running:
```
sudo mount -a
```I got your exact error message:
> [mntent]: line 31 in /etc/fstab is badChanged the remote share using the "\040" escape:
> //MATSLUND-HP/Users/Mats\040LundAnd now my error message is:
> mount error: could not resolve address for MATSLUND-HP: Unknown errorWhich is what I expected since there is no host by that name in my network.

Try \040 again - maybe you are entering O4O instead of zero-4-zero.

---

### Post by TheFu on 2012-09-05
Many routers can be configured to provide DHCP reservations.  That is really handy for portable devices that you want to have DHCP enabled, but when at home you want a static IP.  

I've gotten to the point where I use it for everything except servers. It is just easier to manage IPs on a network that way.  OTOH, I probably have more stuff than most people ... perhaps 30-40 IPs needed.  Plus since the router is the DNS too, other machines can lookup the portable devices easily.  Nice to push certain updates to tablets or smartphones automatically instead of having to pull them manually.

---

### Post by DogMatix on 2012-09-05
> **dvrs said:**
> Thanks for the feedback.

UUID - how do I identify the UUID for the share? 

Cheers,
M.

I did a bit of digging and found this thread addressing this [here]("http://ubuntuforums.org/showthread.php?t=1471446"). It may be of help to you.

---

### Post by dvrs on 2012-09-05
Thanks all for the the helpful feedback.

Morbius1 and Steeldriver - thanks; using '\040' in the path name in /etc/fstab that did the trick :-) I think I might have used '040' earlier which obviously didn't work (sorry) :-/ 

<Problem solved>

The Fu - I cannot see that my router (Asus RT-N56U has the capability to reserve IP addresses whilst running DHCP (I guess I could always switch to fixed addresses but with lot's of mobile devices around it seems attractive to stay with DHCP if it works).

Dogmatix - thanks for the tip, I will take a look at that (especially if I run into trouble with the DHCP solution).

---

### Post by Paqman on 2012-09-05
> **dvrs said:**
> 
The Fu - I cannot see that my router (Asus RT-N56U has the capability to reserve IP addresses whilst running DHCP (I guess I could always switch to fixed addresses but with lot's of mobile devices around it seems attractive to stay with DHCP if it works).


From a quick Google it looks like it does, have another check in the menus. There's normally nothing stopping you from reserving some IPs as static while also using DHCP.

---

### Post by dvrs on 2012-09-06
Paqman - right you are! Done.

Thanks for the help with these things everyone :-)

---

