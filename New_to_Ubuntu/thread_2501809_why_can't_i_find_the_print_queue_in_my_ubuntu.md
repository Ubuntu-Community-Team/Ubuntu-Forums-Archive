---
title: "why can't i find the print queue in my ubuntu?"
date: 2024-10-21
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2024-10-21
i don't have it in the apps list.
where is it?

tnx

---

### Post by 1fallen on 2024-10-21
I'm  just guessing but will this still work:
```
bash -c "/usr/share/system-config-printer/system-config-printer.py --show-jobs $(lpstat -d | sed 's/.*: //')"
```
As for why you can't find it, someone else might need to chime in. I'm just NOT a Gnome fan.
Or even this:
```
system-config-printer

```

---

### Post by yancek on 2024-10-21
If you can't find it in your apps list, try opening a terminal and running the command below which will shows print jobs.

```
lpq
```

---

### Post by 1fallen on 2024-10-21
> **yancek said:**
> If you can't find it in your apps list, try opening a terminal and running the command below which will shows print jobs.

```
lpq
```

```
 lpq
lpq: Error - no default destination available.

```

---

### Post by grahammechanical on 2024-10-21
I have not had a printer connected to my machine for decades. So, I am not speaking from experience but with the Gnome desktop environment we open System Settings>Printers and add a printer. It may be that after adding a printer other settings may appear in System Settings>Printer including information on the progress of print jobs. I doubt that there is a separate app for print jobs.

Regards

---

### Post by TheFu on 2024-10-21
You can use lpq, the CUPS webpage (localhost:631), or the system printer config applet off the top of my head to see queues.

If the output isn't helpful, then more details about how to access the specific print queue you want is spelled out in detail inside the command manpage.
> NAME
       lpq - show printer queue status

SYNOPSIS
       lpq  [  -E ] [ -U username ] [ -h server[:port] ] [ -P destination[/in&#8208;
       stance] ] [ -a ] [ -l ] [ +interval ]

DESCRIPTION
       lpq shows the current print queue status on the  named  printer.   Jobs
       queued  on the default destination will be shown if no printer or class
       is specified on the command-line.

       The +interval option allows you to continuously report the jobs in  the
       queue  until  the  queue is empty; the list of jobs is shown once every
       interval seconds.


From that, I knew to use:
```
$ lpq  -h hadar
laser is ready
no entries
```
to get the queues managed by my CUPs print server, hadar.  "laser" is the default queue which connects to my laser printer. The queue for "laser" is empty.  'hadar' is the DNS name for the print server.  An IP or mDNS name can be used, if you need that.

---

### Post by ronjjjg8885 on 2024-10-22
> **grahammechanical said:**
> I have not had a printer connected to my machine for decades. So, I am not speaking from experience but with the Gnome desktop environment we open System Settings>Printers and add a printer. It may be that after adding a printer other settings may appear in System Settings>Printer including information on the progress of print jobs. I doubt that there is a separate app for print jobs.

Regards

thank you all
it was in the settings......

i do need a printer from time to time.......

---

