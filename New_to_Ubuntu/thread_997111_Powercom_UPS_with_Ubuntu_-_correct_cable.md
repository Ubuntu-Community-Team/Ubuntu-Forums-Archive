---
title: "Powercom UPS with Ubuntu - correct cable?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by Berobero on 2008-11-29
Dear Friends,

I have connected Powercom UPS to IBM Netfinity 5600 using a regular serial cable, I have installed nut and upsd however cant get it work yet. Tyring it on ttyS0 and ttyS1 but both fails. Wondering whether I should use a special wired serial cable to use the device or a simple RS232 would work ?

I have also tried with apcups but it wont work. Should I use serial to usb instead ? I am just willing to shutdown the box safely on AC loss.

Thanks in advance

---

### Post by paultag on 2008-11-29
Are you sure that is a supported UPS?

Perhaps watch the output and either submit a bug report with UPSd or write your own simple daemon :)

Good Luck
Tag

---

### Post by Berobero on 2008-11-29
yes, this is a smart ups and working properly with windows. trying ttyS0 fails saying "is locked by another process" and ttyS1 says "data receiving error (-1 instead of 11 bytes).

If it is because of using a wrong cable, I am spending useless efforts on config files etc.

Pleased to hear

---

### Post by paultag on 2008-11-29
Hummm, so ttyS0 is what you want.

Another processes is doing something with the serial port...
Try hunting around for the processes and purging it, I am not sure what to tell you, but it seems like everything is working. ( except of course the issue at hand )

Anyone else have ideas for the OP?

---

### Post by Berobero on 2008-11-29
sorry bothering much but I am not so experienced on such issues, trying to improve. How can I see what is using ttyS0 ? 

ls /var/lock shows > apache2 aptitude avgd

should I kill above procs?

---

### Post by paultag on 2008-11-29
no, see this is a lock on the serial port.

tbh I am not sure how to remove a serial lock, I have not used a serial port in years.

One think you could try is to use minicom to try and talk to it manually, see if it will let you on the port.

Cheers,
Tag

---

### Post by Berobero on 2008-11-29
Thanks indeed. Now reading a bit on minicom to use it. Will report further mate.

Cheers+

---

### Post by HDave on 2009-03-16
Where did this end up?  I have inherited a Powercom UPS and am not sure how to get it to work with Ubuntu 8.10....

I did find this link however:    [http://manpages.ubuntu.com/manpages/hardy/man8/powercom.8.html]("http://manpages.ubuntu.com/manpages/hardy/man8/powercom.8.html")

Thanks

---

