---
title: "Unison (file syncing) in a crontab help"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by tippx1 on 2012-06-25
I need to synchronize a few folders on my system, and from googling I've read that Unison is the best program to do that. I set it up in unison, calling the profile 'Sync', and added ```
*/10 * * * * unison "Sync"

``` to the root crontab (I entered 'sudo crontab -e' into terminal).

Unfortunately, this hasn't worked. Am I making a huge mistake somewhere that I don't see yet? I've noticed if I enter 'unison "Sync" ' into terminal, unison will only preview the sync, so I'm assuming my problem is just something I need to add to the line to make it run.

---

### Post by cariboo on 2012-06-26
I haven't used unison for years, but if I remember correctly it is only a front-end for [rsync]("http://en.wikipedia.org/wiki/Rsync").

Check out this howto [here]("http://www.linuxbasement.com/content/backups-using-rsync-bash-cron"), to help you accomplish what you want to do.

---

