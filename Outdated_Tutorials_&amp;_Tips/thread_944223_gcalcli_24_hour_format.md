---
title: "gcalcli 24 hour format"
date: 2008-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by hofa on 2008-10-11
There was just one thing I didn't like about gcalcli, and it was that I couldn't specify which time format I want to use. I live in Belgium where we're used to using the 24 hour format. So after some research, I got gcalcli to display in 24 hour format.

I made a diff file from the original and edited file so I could share it here:

```
391c391
<                 tmpTimeStr = eventStartDateTime.strftime("%l:%M") + meridiem
---
>                 tmpTimeStr = eventStartDateTime.strftime("%H:%M")
605c605
<         timeFormat = '%l:%M'
---
>         timeFormat = '%H:%M'
621c621
<             tmpTimeStr = eventStartDateTime.strftime(timeFormat) + meridiem
---
>             tmpTimeStr = eventStartDateTime.strftime(timeFormat)
859c859
<             tmpTimeStr = eventStartDateTime.strftime('%l:%M') + meridiem
---
>             tmpTimeStr = eventStartDateTime.strftime('%H:%M')
```

If you put this in a file called gcalcli.diff in your home folder, you can patch the file like this:

```
sudo patch /etc/usr/gcalcli ~/gcalcli.diff
```

Maybe I'll try and set it up so you can specify it in ~/.gcalcli when I've got some time to spare

---

### Post by xrat on 2008-11-16
Thanks a lot. I was wondering whether I missed some option of the configuration but apparently the time format is hard coded. Thanks for the diff.

---

### Post by ddaavviidd on 2009-01-22
thanks a lot for the patch! but...

```
sudo patch [COLOR="Red"]/etc/usr[/COLOR]/gcalcli ~/gcalcli.diff
```

should really be

```
sudo patch [COLOR="SeaGreen"]/usr/bin[/COLOR]/gcalcli ~/gcalcli.diff
```

right?

---

