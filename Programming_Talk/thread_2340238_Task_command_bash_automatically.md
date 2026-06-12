---
title: "Task command bash automatically"
date: 2016-10-16
forum: Programming Talk
---

### Post by zagicien on 2016-10-16
Hi,
I would like to make a task who execute a command all ten hours.

---

### Post by papibe on 2016-10-16
Hi zagicien.

I think the easiest way would be to create a crontab entry. Read here for details: [Cron Howto]("https://help.ubuntu.com/community/CronHowto").

Hope it helps. Let us know if you need more directions.
Regards.

---

### Post by zagicien on 2016-10-17
> **papibe said:**
> Hi zagicien.

I think the easiest way would be to create a crontab entry. Read here for details: [Cron Howto]("https://help.ubuntu.com/community/CronHowto").

Hope it helps. Let us know if you need more directions.
Regards.

[COLOR=#008000][B]Thank you a lot!  
I solved my problem by doing this:[/B][/COLOR]
> $ Sudo crontab -u user -e
* */10 * * * ./backup.sh >/dev/null 2>&1

---

### Post by Habitual on 2016-10-18
> **zagicien said:**
> [COLOR=#000000]Thank you a lot!  
I solved my problem by doing this[/COLOR][COLOR=#008000]:[/COLOR]

That looks funny to me.
[http://www.dataphyx.com/cronsandbox/cronsandboxgui.php](http://www.dataphyx.com/cronsandbox/cronsandboxgui.php) didn't like it much either, I'm afraid.
See 
[RootSudo - Community Help Wiki]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo")
[Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/")

---

