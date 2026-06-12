---
title: "rTorrent help &amp; questions"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-07-12
Hello, I'm trying to setup rTorrent to act in the same way that I have Deluge setup but I'm having problems. I've look over the man pages hundreds of times with still no success.

Here is a **list** of things I need rTorrent to do.
1. Watch a directory for torrents, if a torrent is found it will add it to rTorrent and move that .torrent file to another directory.
2. When a torrent is loaded in rTorrent I would like it to go into a folder called Downloading. Once it is done I would like it to go in a folder called Seeding. If the torrent is stopped, rTorrent would remove the torrent and  I would like the downloaded files to go in a folder called Completed.
3. Even if the specified ratio is not met, the torrent would end once it has ran for a time (like 2 weeks), rTorrent would stop the torrent and remove it (and from #2 the files would be moved from Seeding to Completed)

Also I cant seem to get rTorrent to work with screen. I type in > screen rTorrent and it comes up saying > [screen is terminating]


Hopefully someone can help!
Please!
Thanks.

---

### Post by hyper_ch on 2008-07-12
> **Thee_Baron_ said:**
> 1. Watch a directory for torrents, if a torrent is found it will add it to rTorrent and move that .torrent file to another directory.
Setup of watchfolder is done in the .rtorrent.rc which has to (a) either be in your user's home or (b) be specified when starting rtorrent.
The .torrent file can't be moved in a way you like it.

> **Thee_Baron_ said:**
> 2. When a torrent is loaded in rTorrent I would like it to go into a folder called Downloading. Once it is done I would like it to go in a folder called Seeding.
Setting up of a download folder is done in the .rtorrent.rc.
You can move it when it's finished. Have a look here: [http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks)

> **Thee_Baron_ said:**
> If the torrent is stopped, rTorrent would remove the torrent and  I would like the downloaded files to go in a folder called Completed.
No clue... when you "delete" the torrent, it will only delete the .torrent file and not the data files.

> **Thee_Baron_ said:**
> 3. Even if the specified ratio is not met, the torrent would end once it has ran for a time (like 2 weeks), rTorrent would stop the torrent and remove it (and from #2 the files would be moved from Seeding to Completed)
See at the common tasks page

> **Thee_Baron_ said:**
> Also I cant seem to get rTorrent to work with screen. I type in  and it comes up saying
(1) run screen
```

screen

```
(2) in screen start rtorrent
```

rtorrent

```

---

### Post by Thee_Baron_ on 2008-07-12
Thank for the help :)

Would this throttle at 4pm and 9pm everyday, making the 9pm rate last until 4pm?
> schedule = throttle_1,16:00:00,24:00:00,upload_rate=30
schedule = throttle_2,21:00:00,24:00:00,upload_rate=65
schedule = throttle_3,16:00:00,24:00:00,download_rate=100
schedule = throttle_4,21:00:00,24:00:00,download_rate=500

---

### Post by hyper_ch on 2008-07-12
no clue... I don't throttle

---

### Post by Thee_Baron_ on 2008-07-12
I have a problem loading rtorrent in screen:> rtorrent: Error in option file: ~/.rtorrent.rc:6: Could not convert string to value.

Here is the .rtorrent.rc file:> # This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
max_peers = 84.5

# Same as above but for seeding completed torrents (-1 = same as downloading)
max_peers_seed = -1

# Maximum number of simultanious uploads per torrent.
max_uploads = 12

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 500
upload_rate = 65

# Default directory to save the downloaded torrents.
directory = /media/Downloads/Active
# Move Finished (Seeding) torrent
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/media/Downloads/Seeding ;d.set_directory=/media/Downloads/Seeding"
# Move removed torrent
on_erase = move_complete,"execute=mv,-u,$d.get_base_path=,/media/Downloads/Completed ;d.set_directory=/media/Downloads/Completed"

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /media/Downloads/.session/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/media/Downloads/torrents/*.torrent

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200"

# Port range to use for listening.
port_range = 56041-56041

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
check_hash = yes

# Set whetever the client should try to connect to UDP trackers.
#use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,try_outgoing,enable_retry

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined. 
#
dht = disable


# Throttle Settings
#
schedule = throttle_1,16:00:00,24:00:00,upload_rate=30
schedule = throttle_2,21:00:00,24:00:00,upload_rate=65
schedule = throttle_3,16:00:00,24:00:00,download_rate=100
schedule = throttle_4,21:00:00,24:00:00,download_rate=500

---

### Post by shirilover on 2008-07-12
It's not feasable to have half a peer. Try either 84 or 85

---

### Post by Thee_Baron_ on 2008-07-12
*Feels stupid* haha thanks :)

---

### Post by zeezam on 2008-08-25
I got this:

sudo rtorrent
rtorrent: Error in option file: ~/.rtorrent.rc:26: Could not find '='.


**.rtorrent.rc**
```

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 120

# Same as above but for seeding completed torrents (-1 = same as 
#downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 10

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 10000
upload_rate = 50

# Default directory to save the downloaded torrents.
directory = /home/user/d/c

# Default session directory.
session = /home/user/d/s

# Watch a directory for new torrents, and stop those that have been
# deleted.
#schedule = 
watch_directory,5,5,load_start=/home/user/d/d/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=500M

#Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else 
ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# Port range to use for listening.
port_range = 6890-6999

# Start opening ports at a random position within the port range.
port_random = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

```

---

### Post by mellowd on 2008-08-25
There is an easier way with screen, this is how I use it:

I always type ```
screen rtorrent
``` (only when I first open it that day)

I then press CTRL+A then D.

Then when I want to attatch to that screen again I just type:

```
screen -x
```

If I typed screen rtorrent again I'd get the error that screen is terminating again

---

### Post by hyper_ch on 2008-08-25
zeezam:

Did you read the error message?

Actually reattaching should be done with the -r option.... -x will attach to a non-detached session.

---

### Post by zeezam on 2008-08-25
> **hyper_ch said:**
> zeezam:

Did you read the error message?

Actually reattaching should be done with the -r option.... -x will attach to a non-detached session.

That was not my problem :)

---

### Post by aimpau on 2008-08-25
I recommend using dtach. :)

---

