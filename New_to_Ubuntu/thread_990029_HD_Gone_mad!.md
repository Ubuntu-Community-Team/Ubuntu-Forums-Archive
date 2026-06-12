---
title: "HD Gone mad!"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Nutscape001 on 2008-11-22
Greetings,

Installed UE 8.1 a week ago and I am delighted with it, but for the past 12 hours my HD is constantly running (like as if I was defragging the HD, which I'm not!) Any ideas how to stop it or even find out why its running? BTW I have 150Gb of free space on the drive.

Thanks

Nutscape

Windooze2Mac2Linux

---

### Post by buyyourall3 on 2008-11-22
would u like to buy [the cheapest laptop](http://www.buyyourall.com) form china? please click [here](http://www.buyyourall.com) for more details

---

### Post by taurus on 2008-11-22
Open a terminal and see which process is accessing your harddrive constantly.

```
top
```

---

### Post by Nutscape001 on 2008-11-22
Hi Taurus

Thanks for the reply, I've gone in and typed TOP and the only programme other than system files is 'MythTV' which I can't seem to get rid off!. I did a search and found some related files but am afraid to delete in case they are important ones. It does not appear in the Add-Remove selection.

Nutscape

Windooze2Mac2Linux

---

### Post by eolson on 2008-11-22
Mythtv is in synaptic

---

### Post by hyper_ch on 2008-11-22
you could also run
```

lsof

```
that lists teh open files... if something is constantly being accessed you should be able to see that there.

---

### Post by sdennie on 2008-11-22
Just to add to the way of debugging disk activity, try:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Then:

```

tail -f /var/log/syslog

```

That should show you what processes are doing disk activity.  To turn off the log spam use:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

