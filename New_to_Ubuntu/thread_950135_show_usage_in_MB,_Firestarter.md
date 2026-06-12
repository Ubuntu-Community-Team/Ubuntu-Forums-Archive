---
title: "show usage in MB, Firestarter"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by bu2971x on 2008-10-16
the window that opens when you hit firestarter shows different connections
ans a bunch of other stuff. It shows how much up and down you have in that session. Can you set up Firestarter to also show how much you have
up and down for a 24 hour period..??  how do you set that up..???

---

### Post by ww711 on 2008-10-16
> **bu2971x said:**
> the window that opens when you hit firestarter shows different connections
ans a bunch of other stuff. It shows how much up and down you have in that session. Can you set up Firestarter to also show how much you have
up and down for a 24 hour period..??  how do you set that up..???


You could try the application conky for displaying this?

I'm sure there is a method to get network stats via the shell also? Can someone confirm or know how to do this?

---

### Post by Dr Small on 2008-10-16
> **ww711 said:**
> I'm sure there is a method to get network stats via the shell also? Can someone confirm or know how to do this?

Like this?

```

#!/bin/bash
netload=`ifconfig ath0 | grep bytes`

#Calculate Total Download in bytes
dl=`echo $netload | grep bytes | awk '/RX/ {print $2}' | sed 's/bytes://'`

## Convert each to Megabytes
dlmb=$(($dl / 1048576))

echo -e $dlmb "MBs"

exit 0
```

---

### Post by ww711 on 2008-10-16
> **Dr Small said:**
> Like this?

```

#!/bin/bash
netload=`ifconfig ath0 | grep bytes`

#Calculate Total Download in bytes
dl=`echo $netload | grep bytes | awk '/RX/ {print $2}' | sed 's/bytes://'`

## Convert each to Megabytes
dlmb=$(($dl / 1048576))

echo -e $dlmb "MBs"

exit 0
```

yeah, like that.

---

### Post by bu2971x on 2008-10-17
that looks interesting..will that show for a 24 hr period?? what part of the code is for the time period so I can change it..??
DO I run this in the terminal..??? thanks much
I tried it , it says syntax error...

---

### Post by Kevbert on 2008-10-17
The other thing you could try in the Net Monitor screenlet which you can get from [[COLOR="Red"]here.[/COLOR]]("http://gnome-look.org/content/show.php/Net+Monitor+Screenlet?content=64719"). You'll also need the Screenlets Manager which you can get from screenlets.org

---

### Post by Dr Small on 2008-10-17
> **bu2971x said:**
> that looks interesting..will that show for a 24 hr period?? what part of the code is for the time period so I can change it..??
DO I run this in the terminal..??? thanks much
I tried it , it says syntax error...
That's a bash script. Save it as 'net' in your Home Folder. Give it executable permissions:
```
chmod +x net
```

Then run it:
```
./net
```

It is not doing a time period, but rather from boot time (when networking started) or from the last time your restated networking. If you didn't reboot (or restart networking) for 5 days, this would be outputting the total amount of download (in Megabytes) from over the past 5 days.

Dr Small

---

