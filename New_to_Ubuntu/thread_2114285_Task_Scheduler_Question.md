---
title: "Task Scheduler Question"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by butt3rs84 on 2013-02-09
Good day all,

   I've been browsing a bit and trying get a grasp on how to install and set up a task manager application for lubuntu. I can't seem to get anywhere unfortunately. Ideally I just want it to turn my computer off and on every day. Can anyone offer me some help with this? Does this all have to be run from the terminal or is there an application that allows you to configure this?

Regards,
butt3rs84

---

### Post by TOMBSTONEV2 on 2013-02-09
There is a program available in the software centre called "Scheduled Tasks" I believe it will make things easier for you.

---

### Post by Lars Noodén on 2013-02-09
Depending on the machine, you should be able to set it to turn on in the BIOS, if your version allows it.  You might have to adjust your time to UTC if the hardware clock is set to UTC, which is common for many OSes.

---

### Post by tgalati4 on 2013-02-09
```
man crontab
man shutdown
crontab -e
```

You would put a shutdown command in crontab and have your BIOS boot it in the morning at a given time.

```
sudo shutdown -h now
sudo shutdown -h 23:00
```

---

### Post by Lars Noodén on 2013-02-10
There are two man pages for crontab, one for the program, one for the file format.   The latter you can find with [man 5 crontab](http://manpages.ubuntu.com/manpages/precise/en/man5/crontab.5.html)

For the shutdown, it is good to have some lead time so that if you are logged in and using the computer, you have time to abort the shutdown.  You could have something like the following in root's cron to shutdown at 23:00, but start getting warnings at 22:30.

```

30  22  *   *   *   /sbin/shutdown -h 23:00

```

That will give you half an hour to cancel the shutdown, if so needed.

To get to root's crontab, use sudo.

```

sudo crontab -e

```

There are probably ways to do it with graphical interfaces, but doing it with text is the same across all systems.

---

