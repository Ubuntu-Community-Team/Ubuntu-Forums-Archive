---
title: "a beginner setting up systemd service and timer files in [k]ubuntu"
date: 2016-05-15
forum: Programming Talk
---

### Post by bobbicat on 2016-05-15
I have been using 'rdiff-backup' for some years as a simple backup method for my computers.
Since the beginnings of the use of systemd here on [k]ubuntu I have been struggling to write services which will control the timing of my backup routine.

I have finally managed to set something up that works but I would like to know if what I have is 'correct', also whether I have put my files in the 'correct' areas.
Most of my method comes from examining files exhibited on the Linux Arch forums. Although that did give me pointers, quite a lot does not work in exactly the same way in [k]ubuntu.
I have searched in vain for simple tutorials with methods to create and use service files in [k]ubuntu but I think they are yet to be written.

The following are my timer routines. If you know how systemd works and could give me a critique of my method I would appreciate any comment.


----------------------------------------------------------------------------------
local-backup.sh
----------------------------------------------------------------------------------

a simple script calling rdiff-backup to make a backup
[I can expand and define this further if more detail is required]

---------------------------------------------------------------------------------

```
kdesudo kate
```
copy the following code into kate
and save as /lib/systemd/system/backup.service

----------------------------------------------------------------------------------
backup.service
----------------------------------------------------------------------------------
```
[Unit]
Description=runs local-backup.sh at shutdown
Before=shutdown.target reboot.target halt.target
[Service]
ExecStart=/bin/true
ExecStop=/path/to/backup/script/local-backup.sh
RemainAfterExit=yes
[Install]
WantedBy=multi-user.target

# save as /lib/systemd/system/backup.service
# its the only place I could find where the routine would work
```

then execute these two commands:

```
sudo systemctl start backup.service
sudo systemctl enable backup.service
```

```
kdesudo kate
```

copy the following code into kate
and save as /lib/systemd/system/local-backup.service

----------------------------------------------------------------------------------
local-backup.service
----------------------------------------------------------------------------------
```
[Unit]
Description=local-backup made hourly

[Service]
Type=simple
ExecStart=/path/to/backup/script/local-backup.sh

# save as /lib/systemd/system/local-backup.service
# again, its the only place I could find where the routine would work
# local-backup.timer starts this service, so no need to start/enable this now

```

```
kdesudo kate
```

copy the following code into kate
and save as /lib/systemd/system/local-backup.timer

----------------------------------------------------------------------------------
local-backup.timer
----------------------------------------------------------------------------------
```
[Unit]
Description=runs local-backup.service every hour

[Timer]
# Time to wait after booting before first run
OnBootSec=10min
# Time between running each consecutive time
OnUnitActiveSec=1h
Unit=local-backup.service

[Install]
WantedBy=multi-user.target

# save as /lib/systemd/system/local-backup.timer
# again, its the only place I could find where the routine would work
```

then execute these two commands:

```
sudo systemctl start local-backup.timer
sudo systemctl enable local-backup.timer
```

After a computer restart the routines begin to run.
The following confirms the routine's activity.

```
sudo rdiff-backup -l /route/to/backup/storage/
```

----------------------------------------------------------------------------------

All the above produces the intended backup, both hourly and when the computer shuts down.

I am seeking corroboration that I am putting my files in the correct location and that their syntax is optimal.

If you need more info I would be pleased to give it.

---

