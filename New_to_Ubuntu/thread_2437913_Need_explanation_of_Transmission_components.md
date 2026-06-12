---
title: "Need explanation of Transmission components"
date: 2020-03-03
forum: New to Ubuntu
---

### Post by freonpsandoz on 2020-03-03
I'm new to Ubuntu, and I need an explanation of how the various Transmission components work (or don't work) together. I have the Transmission GUI app on the Ubuntu 16.04 launcher. I have also installed transmission-cli, transmission-common and transmission-daemon. I understand that there is also a Transmission web UI, but haven't used it. I added a torrent in the Transmission GUI app, but when I list Transmission daemon torrents using "transmission-remote -l" no torrents are shown. Do the GUI app and the daemon maintain separate lists of torrents? If so, can those lists be synched somehow? I'm trying to migrate a large number of completed torrent downloads from Windows to Ubuntu, so I was hoping to write a script that uses the CLI to add the existing torrents and then use the GUI app to add new torrents, view torrents, view and add trackers, etc. Is this possible? Thanks.

---

### Post by guiverc on 2020-03-03
Have you looked through any documentation?

[https://help.ubuntu.com/community/TransmissionHowTo](https://help.ubuntu.com/community/TransmissionHowTo)

Sorry I'm not very familiar with`transmission` , but that showed up first item on a startpage.com search for me (along with many of the `man` pages; ie. `transmission site:*.ubuntu.com`, I use the site: to restrict to official documents only)

---

### Post by mastablasta on 2020-03-03
> **freonpsandoz said:**
> I'm trying to migrate a large number of completed torrent downloads from Windows to Ubuntu, so I was hoping to write a script that uses the CLI to add the existing torrents and then use the GUI app to add new torrents, view torrents, view and add trackers, etc. Is this possible? Thanks.


if they are completed, then why would you need to move torrent? just move the downloads.

also decide on one and sue that. i am not quite sure they are connected. i used transmission in webgui and GUI. but not on the same machine.

---

### Post by SeijiSensei on 2020-03-03
Transmission's GUI, transmission-gtk is a snap to use. Click on a .torrent link in a browser, and Transmission will launch and ask you where to put the downloaded files.  I prefer it to KTorrent though I'm using Kubuntu with the KDE desktop.

---

### Post by mastablasta on 2020-03-04
> **SeijiSensei said:**
>  I prefer it to KTorrent though I'm using Kubuntu with the KDE desktop.


ktorrent seems heavy to me (slows down my old box). qbittorrent is a lot lighter and qt based. i used it on windows as well as it was giving me less issues than utorrent.

---

### Post by freonpsandoz on 2020-03-05
> **mastablasta said:**
> if they are completed, then why would you need to move torrent? just move the downloads.

I'm not moving anything; I'm trying to *migrate* over 1500 torrent downloads from uTorrent on Windows to a BitTorrent client on Ubuntu. I have a Perl script to make a list of download folders and the .torrent file associated with each. I need a way to automate the process of getting a BitTorrent client set up to share those torrents. I'm not going to manually load all of those torrents into a client using a GUI.

> **mastablasta said:**
> also decide on one and sue that. i am not quite sure they are connected. i used transmission in webgui and GUI. but not on the same machine.

According to the documentation, they were apparently connected at one time; I'm trying to find out whether they still are, or at least whether their databases of loaded torrents are compatible. If they're at least compatible, I should be able to automate the process of loading the torrents into the transmission daemon's list and then transfer that list to the Transmission GUI app, right?

---

### Post by ipv on 2020-03-10
> **SeijiSensei said:**
> Transmission's GUI, transmission-gtk is a snap to use.

true that.

> **SeijiSensei said:**
> Click on a .torrent link in a browser, and Transmission will launch and ask you where to put the downloaded files.

does transmission ask you to pick a download location every time you add a torrent? on ubuntu it selects the default downloads folder by itself.

> **mastablasta said:**
> qbittorrent is a lot lighter and qt based. i used it on windows as well as it was giving me less issues than utorrent.

for windows i totally recommend tixati. 100% ad-free, also available as portable & .debs available too.

> **freonpsandoz said:**
> I'm not moving anything; I'm trying to migrate over 1500 torrent downloads from uTorrent on Windows to a BitTorrent client on Ubuntu.

i too often move torrents from windows to ubuntu but i prefer magnets to torrents.

b.t.w. have you guys tried this :

[ATTACH=CONFIG]285201[/ATTACH]

---

### Post by TheFu on 2020-03-10
Google found this: [https://github.com/transmission/transmission/wiki/Transmission-Architecture](https://github.com/transmission/transmission/wiki/Transmission-Architecture)
**Transmission bt architecture** was my search.

---

