---
title: "Bakit nag-'crash'?"
date: 2008-06-30
forum: Philippine Team
---

### Post by rjmdomingo2003 on 2008-06-30
For 2 days, na-notice ko na while using nautilus and running deluge, pag nag load ako ng dvd sa laptop ko eh nawawala 'tong dalawang 'to (nag-crash?). Pero nakakagamit pa rin ako ng kazehakase (web browser). Di ko pa sure kung sa ibang programs eh pareho ang behavior.

Na-notice nyo na ba 'to?

Appreciate your help on this. Thanks in advance.

---

### Post by loell on 2008-06-30
may error prompt ba kung enexecute mo silang dalawa sa terminal pagkatapos nag-crash tuwing may dvd insertion?

---

### Post by rjmdomingo2003 on 2008-06-30
> **loell said:**
> may error prompt ba kung enexecute mo silang dalawa sa terminal pagkatapos nag-crash tuwing may dvd insertion?
That I have to check.

As a remedy, tuwing mag-buburn or browse a dvd, hinahayaan ko na lang munang 'killed' 'tong 2 'to until I finish. Then, I run them by a 2-finger salute:

windows + d for deluge
windows + n for nautilus

Wala naman sigurong relevance sa WM ko, palagay nyo?

---

### Post by rjmdomingo2003 on 2008-06-30
Weird talaga!

Kapag DVD-R ang sinalpak ko eh walang crash na nangyayari. Di ko lang mahanap yung DVD-RW ko para ma-verify kung wala na yung problema.

Siguro, pinagbabawalan na ko ng laptop ko na bawasan na yung pag-buburn.;)

---

### Post by loell on 2008-06-30
heheh, ayaw nyang kumopya nang copyrighted stuff :lolflag:

---

### Post by rjmdomingo2003 on 2008-07-09
> **loell said:**
> may error prompt ba kung enexecute mo silang dalawa sa terminal pagkatapos nag-crash tuwing may dvd insertion?

Eto yung error prompt for deluge:
```

[~] deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin Scheduler
Initialising plugin DesiredRatio
Initialising plugin WebSeed
Initialising plugin TorrentPeers
Initialising plugin EventLogging
Initialising plugin NetworkHealth
Initialising plugin BlocklistImport
Initialising plugin FlexRSS
Initialising plugin Search
Initialising plugin NetworkGraph
Initialising plugin MoveTorrent
Initialising plugin TorrentCreator
Initialising plugin TorrentNotification
Initialising plugin WebUi
Initialising plugin TorrentFiles
Initialising plugin SpeedLimiter
Applying preferences
Starting DHT...
Showing window
no old fastresume to delete
Found TorrentFiles plugin...
Found TorrentPeers plugin...
Found MoveTorrent plugin...
Segmentation fault
```

for nautilus:

```
[~] nautilus --no-desktop
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault

```

This time, CD-R naman ang insert ko for burning the Arch installer..honest..:guitar:

---

### Post by rjmdomingo2003 on 2008-07-10
Did some research on this 'bug', and checked out Launchpad. Sabi dun i-eject na lang daw yung dvd or cd para gumana ulit yung Nautilus. Nagpapatawa?!

Another resolution daw is to downgrade Nautilus. Haay.

Anyways, chance na siguro 'to para ma-try ko Thunar, and hope that the deluge problem goes away.

Susubukan ko rin mamaya kung PCManFM ay ganun din ang behavior.

---

### Post by loell on 2008-07-10
heheh, kahit nga sa gnome, pcman na lang ang ginagamit ko. :)

transmission kaya gamitin mo, pampalit sa deluge. :D

---

### Post by rjmdomingo2003 on 2008-07-10
> **loell said:**
> heheh, kahit nga sa gnome, pcman na lang ang ginagamit ko. :)

transmission kaya gamitin mo, pampalit sa deluge. :D
Tignan ko muna kung nagwowork pa ang deluge kung Thunar or PCManFM ang default file manager. If not, then, I'll try X'mission.

---

