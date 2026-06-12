---
title: "String Manipulation - Azureus Stats"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by tinners on 2008-05-25
Hello all, my first real post here. Am new to Ubuntu but just built a home server running it and finding it superb !

Anyhow, I have a question. I want to be able to output the status of torrents in Azureus into my conky screen. All I need is the name of the torrent, size, how much downloaded and download speed.

All the data is in the Azureus_Stats.XML file (attached)

I got this far
```

egrep -A1 "NAME|SIZE|DOWNLOAD_SPEED|DOWNLOAD_STATUS|DOWNLOADED" /home/home-server/.azureus/Azureus_Stats.xml | egrep "NAME|TEXT" | cut -f 2 -d '<' | cut -f 2 -d '>'

```
which ouputs the information 

[I]119.7 kB/s
ubuntu-8.04-alternate-amd64.iso
696.00 MB
53.45 MB
67.4 kB/s
ubuntu-8.04-desktop-i386.iso
699.11 MB
36.72 MB
52.2 kB/s[/I]


but what I want it to display as is

[I]Total D/L speed: 119.7 kB/s
ubuntu-8.04-alternate-amd64.iso         696.00 MB    46.40 MB    68.8 kB/s
ubuntu-8.04-desktop-i386.iso         699.11 MB    30.93 MB    50.8 kB/s[/I]

The other thing I am not sure of is that there could be any number of torrents on the go, so how can I get it to output 3 if there are 3 torrents on the go, or 10 times when there are 10 ?

Thanks

---

