---
title: "rtorrent issue"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Inxsible on 2008-07-27
If I use the selective download of files from within a torrent, my stop_on_ratio parameter doesn't work.

For eg, Out of a 2 GB torrent of different files, I wanted only about 500 MB worth of files. Once all 500 MB worth of files were downloaded my stop_on_ratio did NOT actually stop the torrent once the ratio was reached, probably because it still counted as the whole 2GB as the complete size of the torrent instead of what I wanted/downloaded.

Is there a way to correct this so that it will use the amount I downloaded as opposed to the total actual size of the torrent?


I hope I was clear enough in explaning the problem.

---

### Post by 505 on 2008-07-27
I don't think so. I saw this behaviour too in rtorrent. I suppose it's just a bug. You might want to file a bug report on the rtorrent web site (if not already there).

---

### Post by zeezam on 2008-08-05
I have this problem when I start rtorrent with my .rtorrent.rc I got this error message:

rtorrent: Error in option file: ~/rtorrent.rc:16: Invalid start of name

Here is the content of .rtorrent.rc:

```

# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.
#
# Based on original .rtorrent.rc file from http://libtorrent.rakshasa.no/
# Modified by Lemonberry for rtGui http://rtgui.googlecode.com/
#
# This assumes the following directory structure:
# 
# /Torrents/Downloading - temporaray location for torrents while downloading (see "directory")
# /Torrents/Complete - Torrents are moved here when complete (see "on_finished")
# /Torrents/TorrentFiles/Auto - The 'autoload' directory for rtorrent to use.  Place a file 
#           in here, and rtorrent loads it #automatically.  (see "schedule = watch_directory")
# /Torrents/Downloading/rtorrent.session - for storing rtorrent session information
#

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 100

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 15

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 50

# Default directory to save the downloaded torrents.
directory = /Torrents/Downloading

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /Torrents/Downloading/rtorrent.session

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/Torrents/TorrentFiles/Auto/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low. */
schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000

execute_log = /home/shs/rtorrent.log

# When the torrent finishes, it executes "mv -n <base_path> ~/Download/"
# and then sets the destination directory to "~/Download/". (0.7.7+)
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/Torrents/Complete/ ;d.set_directory=/Torrents/Complete/"

# The ip address reported to the tracker.
ip = 127.0.0.1
ip = johnnyh.homelinux.net

# The ip address the listening socket and outgoing connections is
# bound to.
bind = 127.0.0.1
bind = johnnyh.homelinux.net

# Port range to use for listening.
port_range = 55556-55560

scgi_port = 127.0.0.1:5000

# Start opening ports at a random position within the port range.
port_random = no

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
check_hash = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

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
encryption = allow_incoming,enable_retry,prefer_plaintext

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
hash_max_tries = 10

# Max number of files to keep open simultaniously.
max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets = <no default>


# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
#schedule_remove = "ip_tick1"

```

Something that is wrong in the .rtorrent.rc file?

---

### Post by hyper_ch on 2008-08-05
I think it's a bug. You might want to submit a bug report on [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no)

---

### Post by zeezam on 2008-08-26
> **hyper_ch said:**
> I think it's a bug. You might want to submit a bug report on [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no)

Changed my .rtorrent.rc to this:
```

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 120

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 20

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 6000
upload_rate = 100

# Default directory to save the downloaded torrents.
directory = /home/user/d/d

# Default session directory.
session = /home/user/d/s

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,5,5,load_start=/home/user/d/t/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=100M

#Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,"stop_on_ratio=200,200M,2000"

# Port range to use for listening.
port_range = 6890-6999

# Start opening ports at a random position within the port range.
port_random = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

```

Now it's working

---

