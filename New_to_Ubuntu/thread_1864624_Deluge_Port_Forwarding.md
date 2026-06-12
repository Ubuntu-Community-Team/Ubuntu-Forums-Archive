---
title: "Deluge Port Forwarding"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by fractalman on 2011-10-19
Ok, i have recently re-installed 11.04 and since doing so i canot get my torrents to download.   previously i forwarded the ports on my router and set deluge to the same and everything was fine.  I have tried with 2 different routers

Thompson mini livebox - orange
invedel livebox - orange

and i cant get anything through either of them

So here's my deluge and router configs as i normally set them up,  i never usually have to alter the firewall at all, but i tried it allowing deluge with the preconfigured settings option but still nothing, see attachment,

Could there be a glitch on my computer, or is there any software i can use to check if my isp or the authorities are blocking all my ports?  i have spoke my isp this morning and they claim they are not blocking any ports.   

Am i being completely stupid and missing something obvious?  everything is set the same as before
the trackers for a couple of torrents i tried either timed out or the connection was refused, i tried different torrents from different sites to eliminate as many possibilities as i could
I have tried using ports in a higher range as well, 50000-50007
i rebooted the router and/or the pc everytime i made changes
I have tried a million different google results before posting this as well

any ideas please?  if you need outputs just post the commands

thanks

---

### Post by lovinglinux on 2011-10-19
Your configuration looks good. Could be the tracker.

Try downloading an Ubuntu ISO using torrent. Most likely that their tracker will be online.

Also check [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It has some questions to help narrow down the issue.

It has been a long time since I used Deluge. Now I mostly use qBittorrent and Ktorrent.

BTW, I would recommend using different ports. Those you use are standard for torrent and can be easily blocked. See my tutorial for more information. But before doing anything, I would check if there is anything in your ISP contract about not being allowed to download using BitTorrent. If not, as long as you download only legal torrents, they cannot legally block or cap your speed.

---

