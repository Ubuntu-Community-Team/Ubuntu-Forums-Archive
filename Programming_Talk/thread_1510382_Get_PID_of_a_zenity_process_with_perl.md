---
title: "Get PID of a zenity process with perl"
date: 2010-06-15
forum: Programming Talk
---

### Post by carandraug on 2010-06-15
Hi

I'm writing a perl script (to resize a bunch of images) and I'm giving a go with zenity to have a progress bar and icon. However, I can't get the process PID of the icon to kill it in the end. With some options I get the right one, with others, I don't.

Here's an example script (see $icon_zen at the end)

```
$pid_icon = open ICON, "|-", $icon_zen;
say "PID is $pid_icon\n";

## To flush ICON immediately
select (ICON);
$|++;
select(STDOUT);

say `ps aux | grep zenity`;
say ICON "message: start.";
sleep 3;
say STDOUT "back from sleep";
kill 15, $pid_icon;
say STDOUT `ps aux | grep zenity`;

```

Depending on the command I use, I get the right or the wrong PID

```
## This doesn't work
$icon_zen = "zenity --notification --listen --window-icon=info --text='image_resizer is running'";
##Here's its output
PID is 10373

1000     10373  0.0  0.0   1748   488 pts/2    S+   17:42   0:00 sh -c zenity --notification --listen --window-icon=info --text='image_resizer is running'
1000     10374  0.0  0.0   1748   484 pts/2    S+   17:42   0:00 sh -c ps aux | grep zenity
1000     10375  0.0  0.4  15312  3340 pts/2    S+   17:42   0:00 zenity --notification --listen --window-icon=info --text=image_resizer is running
1000     10377  0.0  0.0   3300   760 pts/2    S+   17:42   0:00 grep zenity

back from sleep
1000     10375  3.3  0.8  71044  6736 pts/2    S+   17:42   0:00 zenity --notification --listen --window-icon=info --text=image_resizer is running
1000     10378  0.0  0.0   1748   484 pts/2    S+   17:42   0:00 sh -c ps aux | grep zenity
1000     10380  0.0  0.0   3300   764 pts/2    S+   17:42   0:00 grep zenity

## This works fine
$icon_zen = "zenity --notification --listen";
##Here's its output
PID is 10344

1000     10344  0.0  0.4  15312  3340 pts/2    S+   17:40   0:00 zenity --notification --listen
1000     10345  0.0  0.0   1748   484 pts/2    S+   17:40   0:00 sh -c ps aux | grep zenity
1000     10347  0.0  0.0   3300   764 pts/2    S+   17:40   0:00 grep zenity

back from sleep
1000     10344  3.0  0.0      0     0 pts/2    Z+   17:40   0:00 [zenity] <defunct>
1000     10348  0.0  0.0   1748   480 pts/2    S+   17:40   0:00 sh -c ps aux | grep zenity
1000     10350  0.0  0.0   3300   764 pts/2    S+   17:40   0:00 grep zenity

```

What am I doing wrong to get the wrong PID? Thanks in advance

---

### Post by kerry_s on 2010-06-15
try:
```
$(pidof zenity)
```
instead of
```
`ps aux | grep zenity`
```

---

### Post by shawnhcorey on 2010-06-15
The pid returned by open is the pid of the shell running zenity, not zenity itself.  Try using the list variant of open:
```
my @icon_zenity = (
  'zenity',
  '--notification',
  '--listen',
  '--window-icon=info',
  q(--text='image_resizer is running'),
);
my $pid_icon = open my $icon_fh, '|-', @icon_zenity;
die "could not pipe to zenity: $!\n unless $pid_icon;
```

---

### Post by carandraug on 2010-06-17
> **shawnhcorey said:**
> The pid returned by open is the pid of the shell running zenity, not zenity itself.  Try using the list variant of open:
```
my @icon_zenity = (
  'zenity',
  '--notification',
  '--listen',
  '--window-icon=info',
  q(--text='image_resizer is running'),
);
my $pid_icon = open my $icon_fh, '|-', @icon_zenity;
die "could not pipe to zenity: $!\n unless $pid_icon;
```

Thanks. This solved my problem. I'll read more on the differences between calling open with an array and a string. I knew about using one and about having the arguments after the first element, but I thought it was just another way to do the same thing. Again, thank you very much

---

