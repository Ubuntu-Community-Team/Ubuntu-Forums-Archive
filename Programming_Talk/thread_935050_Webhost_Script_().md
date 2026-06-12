---
title: "Webhost Script (?)"
date: 2008-10-01
forum: Programming Talk
---

### Post by JohnSearle on 2008-10-01
I'm looking for a short script that would work on a generic webhost (assumed Apache) that would run a PHP page once a day automatically.

The reason I'm asking for this, is that I'm setting up a daily game, where a PHP / MySQL combination stores turn information, and then at the end of the day it plays all the information out.

I know I could set it up to detect the date on a user load, and then if it's the next day it could run a processing function (playing the turns)... But I would rather have this run independently of people accessing the game.

Any thoughts? Is this possible?

- John

---

### Post by themusicwave on 2008-10-01
If your webserver is Linux based, you could set up a cron job.  Many of the sites that run using the Cpanel web hosting have a wizard for setting it up.  If you have SSH access you can use cron yourself to do it.

Basically, you just schedule a Cron Job to run every day at a specific time.

I used this to have a Python script e-mail me daily to let me know who RSVPed for my wedding on my website.  Each night at 8pm the script was run.  It went into the Database pulled out the new RSVPs and e-mailed them to me.

You could use a similar concept.

---

### Post by JohnSearle on 2008-10-03
Thanks for the information.

I'll have to go read up on RCon and such, since I'm not very familiar with it currently.

- John

---

