---
title: "getting my backup script to run at shutdown"
date: 2015-05-30
forum: Programming Talk
---

### Post by bobbicat on 2015-05-30
At this time I am running Kubuntu 15.04 on a desktop PC, UEFI/GPT amd64. I've been managing tolerably well, for quite a number of years, without Mac or Msoft.

I use rdiff-backup to backup my /home folder to another marked /storage
I have a script which I place in /etc/cron.hourly which gives hourly incremental backups
This is working well

I also place a copy of the script in /etc/init.d with links to it labelled K10 in /etc/rc0.d and /etc/rc6.d
These used to give me an additional backup at shutdown and reboot.
This part no longer works.

I am not a coder or programmer but have been using Kubuntu exclusively for quite a few years, so I am no absolute beginner. I suspect my problem is a result of the change to systemd. Believing this I have searched the web and tried out various approaches with no success. I have tried to create various versions of a .service file, placing it in /etc/systemd/system with no result. I have navigated to systemsettings/startupandShutdown/Autostart where I added my script, unfortunately also without result.

It is beginning to look like shutdown doesn't like my script, though it does work producing hourly backups as I mentioned above. It also used to work to make a backup at shutdown.

Will hourly backups have to be all I can have for now, or is there an answer to my dilemma?
Or is this something that should be reported as a Bug? 
I am a bit out of my depth here and unsure what direction to take.

---

### Post by ian-weisser on 2015-05-30
Upstart in 15.04 no longer handles system boot/shutdown.
You can change the init from systemd back to Upstart.
Or you can create a replacement systemd .service file that runs during /usr/lib/systemd/user/shutdown.target

Personally, I think the long-term answer is the latter - to tackle the learning curve and get your new systemd .service working.
You're not alone. Lots of us learning systemd this cycle.

---

### Post by bobbicat on 2015-05-31
I tend to agree and can see that I am not alone getting to grips with the change. There is very little info for [U]buntu users on the simple level I would need.
There is info out there for non-[U]buntu implementations like Arch but their answers don't transfer in a usable way, or so it has seemed to me in my search.
There is a User folder in /etc/systems/system/ but I've no idea how to use it. There is also one in /usr/lib/systemd/. 
Hopefully at some stage there will appear some tutorials explaining to people like myself how to create, position and use the files like .services within the [U]buntu environment.

At the moment I can only find over-complicated data which does not appear to produce any useful result.
I will persevere, it is in my nature, but I think that for now my hope that eventually I will be able to get my backup at shutdown running again, will remain just a hope.

something I only just ran across whilst searching:
> Installing systemd in Ubuntu may limit the amount of help and support available to you. If you have a commercial support agreement then installing systemd would almost certainly invalidate it. Even if you rely on forums etc, you will probably have to reproduce problems on a standard Ubuntu build before anyone can help you much.
...that about sums it up really doesn't it?
...and although that did carry the caveat 'Warning outdated info' I think for an ordinary user like myself it might apply for some time.
Sadly I started out thinking I was going to get an answer in the short term...

---

### Post by bobbicat on 2015-06-11
I return with good news.
I'm pleased to report that I have successfully achieved my aim, which was to set up a backup which runs at reboot, shutdown and halt.

here is my file, backup.service:

```
[Unit]
Description=local-backup at shutdown
Before=shutdown.target reboot.target halt.target
[Service]
ExecStart=/bin/true
ExecStop=/path/to/backup/script/local-backup.sh
RemainAfterExit=yes
[Install]
WantedBy=multi-user.target
```

I saved it as /lib/systemd/system/backup.service

I then executed these two commands:

```
sudo systemctl start backup

```

```
sudo systemctl enable backup
```

my backup system thereby became operational.

I had tried variations on this unit, placed in different locations without success. It seems from trial and error that /lib/systemd/system/ is the place to go.

I am open to being better informed but now at least I have something that works.
I will look at setting up hourly backups using a .service file, next.


(...and here is a link to some info I found invaluable --> [https://wiki.archlinux.org/index.php/Systemd](https://wiki.archlinux.org/index.php/Systemd))

---

### Post by ian-weisser on 2015-06-11
Thanks for letting us know how it turned out.
And thanks for that link!

---

### Post by bobbicat on 2015-06-13
...and thank YOU for showing some interest.

---

