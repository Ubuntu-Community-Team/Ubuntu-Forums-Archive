---
title: "Request to a high level programmer"
date: 2008-04-04
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-04-04
How can I make a pop-up gtk window say "Backup time" Mondays and Fridays on my desktop?:guitar:

---

### Post by LaRoza on 2008-04-04
You can use zenity to make simple GUI widgets.

```

#!/bin/bash
zenity --info --title="Backup" --text="Time to Backup"

```

(Install zenity and make this executable)

Now you will have to use cron to make it run at certain times, research that independantly, or wait for another response. I have no experience using it.

/etc/crontab

---

### Post by Sockerdrickan on 2008-04-04
Awesome

If anyone knows how to use cron then please submit an example here.

---

### Post by LaRoza on 2008-04-04
> **Tux0r said:**
> Awesome

If anyone knows how to use cron then please submit an example here.

It seems simple enough, but I am not going to give examples unless I am sure it would work. [http://en.wikipedia.org/wiki/Cron](http://en.wikipedia.org/wiki/Cron)

---

### Post by AnRa on 2008-04-04
You may use [gnome-schedule](apt://gnome-schedule) to configure cron easily. :)

---

