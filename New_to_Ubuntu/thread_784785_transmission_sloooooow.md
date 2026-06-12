---
title: "transmission sloooooow"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by eggcream on 2008-05-06
Got transmission working and everything but the download speeds are unacceptably low. Wondering how I can speed them up, and I've already opened up the proper port.

---

### Post by agim on 2008-05-06
I tried using transmission once, upon installing Hardy, it was also ubearably slow. I use deluge-torrent, great speeds, you can use random ports, and its encrypted.

Its also light on resources.

I know that doesn't answer your specific question, but if you haven't tried deluge, I would suggest it.

sudo apt-get install deluge-torrent

---

### Post by nowshining on 2008-05-06
well, these things can cause things to go slow:

RIAA, MPAA blocking downloads/slowing the download speeds (or any other company)
RIAA,MPAA forcing a slow download to distract the download of mp3s, etc.. (or any other company)
Ur downloading from a 56k modem user and or users,
Too many people downloading from one person
A user with either a 56k modem or DSL or highspeed internet capping their bandwidth to have room for browsing the net themselves, etc.. 
ur ISP is blocking a certain port & or throttling the p2p (try another port) & or try using encryption if possible.

try using ipfilters from bluetack.co.uk or blocking the bad ips with the iptables firewall :) like I did for many.

Also I do torrent + i'm on a 56k modem + i capped my uploads @ about half to not max out my bandwidth so I may browse the web, etc...@ least a bit.

---

### Post by linux phreak on 2008-05-06
Check the number of seeders for your torrent.If there aren't any,then you will have difficulty in getting the file.Also set your upload speed correctly.Deluge has this option.

---

### Post by dark_harmonics on 2008-05-06
Most likely the above posters are correct and this is specific to your torrent. There are TONS of alternatives out there like heavyweight azureus, utorrent (wine official support) and others. I find transmission to be fine for what i need. i typically  use defaults unless they really just dont meet my needs.

---

### Post by allad on 2008-05-07
I got the same problem. Transmission speeds are teally slow. And even worse, Transmission was hogging all my bandwith. It is not related to one particular torrent. So I tried azureus. And not only it was way faster but also much lighter on the bandwith.
In my opinio, Transmission sucks. And I'm appalled they've included it as the default bt client in an LTS release.

---

### Post by Vaphell on 2008-05-07
when i read about features of incoming hardy release i thought i'll try transmission in 7.10 (from gutsy repos). It had really simple interface, only files to download with progress bar, options to limit U/L and that's it. While being so surprisingly low on details it worked pretty well. In 2 minutes it maxed out bandwidth and dloaded stuff really fast. I was pretty impressed.

After installing 8.04 i couldn't recognize Transmission's interface, it was more complicated (still simple but compared to 7.10 version...) and the worst thing was it really crawled :/ 3Mbit connection and the torrent max speed was maybe 150kB and it was really rare. On average 40kB, from 20kB to occasional 100+. I tried to see if there are some hidden relations  between UL and DL but there are none (i learned one day that in utorrent there is a hidden feature: upload > 7kB unlocks unlimited download speed, otherwise DL it's restricted to max ~35kB)

utorrent in xp reaches 100-300kB easily, no pain. It is so fast that after download i have ratio 0.1 or less, in 8.04's Transmission i had 0.4-0.5

---

