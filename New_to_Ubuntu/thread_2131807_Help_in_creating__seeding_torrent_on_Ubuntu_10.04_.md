---
title: "Help in creating / seeding torrent on Ubuntu 10.04 Server / Transmission-Daemon 1.93"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by wowiesy on 2013-04-02
[COLOR=#000000]I am running Ubuntu 10.04 Server (although installed desktop components already) as a torrent server mostly to download files. [/COLOR]

[COLOR=#000000]Now I have a need to share huge files to particular people and I thought of using torrents to do this. [/COLOR]

[COLOR=#000000]Have transmission-daemon and [/COLOR][COLOR=#417394]transmissioncli[/COLOR][COLOR=#000000] installed 1.93 (10621) version... [/COLOR]

[COLOR=#000000]i use the command: [/COLOR]


```
[COLOR=#417394]transmissioncli[/COLOR] -n <<FILE TO SHARE AS TORRENT>> -a [u]("http://open.tracker.thepiratebay.org/announce")dp://tracker.openbittorrent.com:80/announce <<OUTPUT.TORRENT>>
```
[COLOR=#000000]
Output is:[/COLOR]
[COLOR=#000000]
[/COLOR]```
.Transmission 1.93 (10621) - http://www.transmissionbt.com/
[09:49:14.448] Transmission 1.93 (10621) started
[09:49:14.449] RPC Server: Adding address to whitelist: 127.0.0.1
[09:49:14.449] DHT: Generating new id
creating torrent "OUTPUT.TORRENT"
[09:49:14.783] Port Forwarding (NAT-PMP): initnatpmp succeeded (0)
[09:49:14.783] Port Forwarding (NAT-PMP): sendpublicaddressrequest succeeded (2)

```

[COLOR=#000000]
[/COLOR]
[COLOR=#000000]FILE TO SHARE AS TORRENT as well as OUTPUT.TORRENT are all on my default download folder (where all my other earlier downloads are)[/COLOR]

the OUTPUT.TORRENT isn't created.  I am not sure why... earlier when I was using a different tracker, the output.torrent file was generated although when I use the torrent file to download (whether from the same server machine or from a Mac on the office network) the download isn't started and 0 seeders/leechers even when I have left it for a couple hours... 

using this particular tracker, the output.torrent isn't created... 


[COLOR=#000000]reading on some threads over the internet... I was pointed to possible network / routing issues...[/COLOR]

[COLOR=#000000]I use port 51413 and this is forwarded from my router to this particular machine, the machine itself has a fixed ip, and my ISP doesn't give me a fixed IP, but I am signed up with DynDNS.... no firewall on the router itself.. no firewall on the torrent machine itself... my router also has a port forwarded (from router default 6881:6889 i think... also forwarded to my machine at port 51413...  [/COLOR]


[COLOR=#000000]am I missing something to make this work? from the [/COLOR][COLOR=#417394]transmissioncli[/COLOR][COLOR=#000000] side? or config on transmission-daemon? network side? is it possibly my ISP is blocking port 51413? How should I test this? [/COLOR]

[COLOR=#000000]I leave this particular machine pretty much on 24/7.. I am about 3 - 4 timezones away from the people who needs the file I am sharing... so I think sharing through torrent is quite a good way under this circumstances... Please help! =)


[/COLOR]

---

### Post by wowiesy on 2013-04-03
UPDATE:

finally able to create the torrent by using [http://tracker](http://tracker) address   instead of the udp:// tracker address...   it seems that the listed public trackers use udp.. but if I use it.. there's an error in creating the torrent file (although transmissioncli doesn't report the error in the console)...  I found this out by creating the torrent using transmission gtk client..  errors popped out while using udp.. but if I use http.. the torrent creation process finished and the actual torrent file was created... 


so now that the torrents are created... I needed to seed... first I tried seeding on the transmission gtk client... it seemed it couldn't seed...  when I added the torrent file to the torrent client, it can not download (i think it is still finding the seeders through the tracker list).. however.. when i checked the status of the torrent, it is yet unable to announce... so most likely (from my understanding).. I can not download since the torrent client doesn't know where to look for the seeders yet (even if the file is just sitting there beside it on the same folder on the same computer).... 

I tried using transmission client on Mac, on the same network, to download the torrent.... so the setup at this point is the actual file to be shared through torrent is in a server within a LAN...  but still my Mac torrent client can't find any seeders so it is unable to start download...  

I now tried uploading the torrent file itself into the transmission-daemon i have setup on the same box i created the torrent in (using the gtk client)...   and the transmission-daemon was able to verify the file (since it is there in the same folder as all my other torrent downloads)... so now the torrents are being seeded, courtesy of transmission-daemon....   

checking on the status of the announce on the transmission-daemon, it is yet unable to connect to the public tracker...  perhaps this is the reason why even if it is now seeded on my transmission-daemon box, I still can't start downloading from my Mac torrent client, even if both machines are on the same LAN...  

I now decided to just let the seed go on through the day.. and try again later tonight if I can download from a different machine... 

not sure if I am doing the right thing here.. or how can this be explained...

---

### Post by wowiesy on 2013-04-05
From some resources over the Net, it seems that public trackers have switched to UDP protocol.. however, since my setup is still using 10.04 / Transmission 1.93.. most likely (I am not sure about this) the version I have doesn't support UDP protocol... 

How do I update my transmission-daemon / transmission to the latest version, even though I want to keep my environment at 10.04?

---

