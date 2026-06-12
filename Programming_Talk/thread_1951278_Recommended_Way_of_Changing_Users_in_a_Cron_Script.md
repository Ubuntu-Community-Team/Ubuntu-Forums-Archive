---
title: "Recommended Way of Changing Users in a Cron Script"
date: 2012-04-02
forum: Programming Talk
---

### Post by kazza on 2012-04-02
Hi, today ive been attempting to write a daily cron script. I require running the script from a given user for a couple of reasons.

After a bit of playing round I settled on placing 
```

if [ $USER != "kazza" ] ; then
    su kazza -c $0
    exit
fi
```
at the head of the script. Much of the advice ive found on the internet seems to recommend writing a second script that is called by the first after a user switch. This just seems a bit messy as having to maintain an extra script.

I was just wondering what the recommended method is? I understand that the above solution has the potential to not terminate.

Thanks,
kazza.

---

### Post by Lars Noodén on 2012-04-02
Why not just run the cron job as that user?

```

sudo -u kazza crontab -e

```

Or 

```

su kazza -c "crontab -e"

```

---

### Post by kazza on 2012-04-02
Ah that is true. 

Would you suggest adding a user specific cron to a start up script so that it works automatically after a reboot without having to manually run a cron deamon?

kazza

---

### Post by Lars Noodén on 2012-04-02
The cron daemon is running anyway.  It's one of the services that Ubuntu starts automatically for you.  Once the cron table is set up for that user, it will be running when the computer is running so there is no need to mess with startup scripts.  But otherwise, yes, the user-specific cron job is the way to go.

---

### Post by kazza on 2012-04-02
Thanks, that is pretty neat.

---

