---
title: "Slow rTorrent"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by HornedBeast on 2008-05-21
Hi.

I am running Rtorrent from a Screen session on Ubuntu Server 8.04. I am having trouble with slow download speeds. When I run Transmission on my Ubuntu desktop machine my torrents download very quickly with no problem at all. When I run the same torrents in rtorrent on the server machine, they download very slowly!

**Server IP:**

```
192.168.1.2
```

**Iptables -L output:**

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:51414 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51413 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:51414 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```


**My rtorrent config:**

```
# Default directory to save the downloaded torrents.
directory = /torrents/Unfinished

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = /torrents/Session

# Watch a directory for new torrents, and stop those that have been deleted
schedule = watch_directory,10,10,load_start=/torrents/Torrents/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

# Move completed downloads
on_finished = rm_torrent,"execute=rm,$d.get_tied_to_file="
on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/torrents/Finished/ ;d.set_directory=/torrents/Finished/"

# Close torrents when diskspace is low.
schedule = low_diskspace,5,60,close_low_diskspace=1024M

# Stop torrents when reaching upload ratio in percent.
schedule = ratio,60,60,"stop_on_ratio=100"

# Check hash for finished torrents.
check_hash = yes

# Encryption options. This can be useful when using an ISP that uses traffic shaping.
#encryption = allow_incoming,try_outgoing,enable_retry
encryption = enable_retry,require_rc4
#encryption = allow_incoming,enable_retry,prefer_plaintext

# Port range to use for listening.
port_range = 51414-51414

# Start opening ports at a random position within the port range.
#port_random = yes

# IP or Domain to Use
ip = <HIDDEN TO PROTECT THE INNOCENT!!>
bind = 192.168.1.2

# Enable DHT support for trackerless torrents or when all trackers are down.
# May be set to "disable" (completely disable DHT), "off" (do not start DHT),
# "auto" (start and stop DHT as needed), or "on" (start DHT immediately).
# The default is "off". For DHT to work, a session directory must be defined.
dht = auto

# UDP port to use for DHT.
dht_port = 51413


# rTorrent should try to use UDP trackers
use_udp_trackers = yes
```

I have also opened ports 51413 and 51414 for both TCP and UDP on my router. Any ideas as to what might be causing this?

Does Ubuntu Server 8.04 even use Iptables? Is it just using UFW (Uncomplicated Firewall) instead? If so, how do I go about opening up the correct ports in UFW?

Thanks in advance.

HB!

---

### Post by hyper_ch on 2008-05-21
(1) you have no max. upload rate...
```

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 0
upload_rate = 140

```
Set it to this value:
You max. upload speed in kilobytes/second - 10 (for DHT) - [5-10] (for normals surfing).
So, if you have a max upload speed of 80 kb/s then set it to about 60-65.

(2) test how you're doing with no encryption - might be you have bad peers right now

if that doesn't help, explicitly forward the dht and rtorrent port from your router to your computer and make sure your firewall does not interefere there (why did you install ufw anyway?)

If that does not help, try chaning ports to some standard ones.

---

### Post by HornedBeast on 2008-05-21
My upload seems to be fine set to "Off" (IE. No limits). It maxs out my connection at 50k up a second. Its my download thats not very good. But when I try running the same torrents inside Transmission, they download really quick (over 500kb a second), but in rtorrent they download at about 20k a second in total.

I use encryption with Transmission and it generally produces faster speeds for me. I've tried Rtorrent with no encryption and I get the same problem.

The reason for the high port number is because I know Transmission on my desktop uses that port and I know it isnt being blocked or throttled by my ISP.

I did not install UFW, I beleive its installed by default on Ubuntu Server 8.04.

---

