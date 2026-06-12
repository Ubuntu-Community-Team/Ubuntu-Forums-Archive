---
title: "Automatic torrent downloader"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by androssofer on 2012-03-09
here is what i would like:

have a folder called 'torrentFiles' or something.

where i can put torrent files in there, and a torrent client will open up a certain time, and automatically download any torrents in that folder. then remove them when they are complete.


At the moment i run vuze using cron overnight to download. However when i want to download something, i have to find the torrent, download it, then open vuze and load in the torrent. then shut it down again. then it runs at night for me.. but i'm quite lazy, so want the computer to do the work :-).

can anyone think of a way to do this?

I had the idea that if there was a cli based torrent client. i could write a script that gets all the torrent files in a folder and loops through them all opening each of them using the cli. then remove them when it completes.. but its messy and might not be the easiest way...

regards

Andy 


ps: i'm fine with using bash scripts and cron jobs...

---

### Post by idoitprone on 2012-03-09
transmission-cli

commandline torrent client

---

### Post by papibe on 2012-03-09
transmission-daemon (run in the background, web interface) can be set to "watch" a directory for torrents. When found, it load them and start downloading them. It can be also be set to delete the original torrent file from the watch directory.

Hope it helps.
Regards.

---

### Post by androssofer on 2012-03-13
> **papibe said:**
> transmission-daemon (run in the background, web interface) can be set to "watch" a directory for torrents. When found, it load them and start downloading them. It can be also be set to delete the original torrent file from the watch directory.

Hope it helps.
Regards.

ok, papibe's advice and transmission made it all too easy..

so i decided to go super lazy!

so i made a perl script that checks the download folder on my laptop, and if it finds any torrent files copies them to my 'server' for downloading. so now all i have to do is download a torrent file on the laptop and its on my media server by the next day..

```
#!/usr/bin/perl
  use 5.010;
  use strict;
  use warnings;


  my $checkForTorrents = `ls /home/username/Downloads | grep .torrent`;
  my @fileNames = split(' ',$checkForTorrents);
  my $fileNum = scalar @fileNames;
  if($fileNum > 0)
  {
    my $checkConntection = `ifconfig`;
    if($checkConntection =~ m/inet addr:192.168/)
    {
        my $outcome = `scp /home/username/Downloads/*.torrent serverAddress:TorrentFiles/`;
        my $delete = `rm -f /home/username/Downloads/*.torrent`;
    }
  }
```

and i run it every hour using a cronjob.

isnt the best script, but does the trick :-)

---

