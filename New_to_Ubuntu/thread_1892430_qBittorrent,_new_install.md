---
title: "qBittorrent, new install"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by McTwitch on 2011-12-08
I have the program qBittorrent installed on an Ubuntu 11.04 installation. I'm reinstalling 11.04 over it. I was wondering if I'd be able to find a file with the status of a current download, and be able to continue downloading on the new install. It's an ISO of Stoner Edition, for those of you wondering.

---

### Post by beew on 2011-12-08
> **McTwitch said:**
> I have the program qBittorrent installed on an Ubuntu 11.04 installation. I'm reinstalling 11.04 over it. I was wondering if I'd be able to find a file with the status of a current download, and be able to continue downloading on the new install. It's an ISO of Stoner Edition, for those of you wondering.

If you have kept a separate /home partition then yes. Otherwise if you save its configuration file (either .qbittorrent or something in .config) and the data file (of course) and copy them to the same places (as before) in  your new  home  after reinstall then it should be able to resume. Of course you have to reinstall qbittorrent.

---

### Post by McTwitch on 2011-12-08
I do not have a seperate /home partition, sadly. On the new install I plan to though. So all I have to do is find the file in .config?

---

### Post by searchfgold6789 on 2011-12-08
Most torrent clilents will check the data first. This means that if you add a new torrent, and the file and folder names are all correct and are unchanged, and some of the downloaded data is there, then it will automatically take off from where it was interrupted and continue downloading. I do not know if qBittorrent had thi feature disabled by default or not, although it would seem funny for a torrent client to totally skip data checking.

---

### Post by beew on 2011-12-08
Well there are two folders that seem to be relevant. Unless you have changed it, qbittorrent saves its downloads to the folder QBT-dir in your home, so you need to save this and replace the new QBT-dir with the old one in your new install. Then there is a folder called qBittorrent which is inside .config. .config is a hidden file in your home so you have to open the file manager in your home and go to View > Show Hidden Files to see it. You may want to save that before you reinstall and replace the new one with this for your old settings.

I just tried to move both these files and start qbittorrent but it still resumes download so there must be another piece somewhere to keep track of downloads. You can try experiment a bit.

---

### Post by McTwitch on 2011-12-08
I moved both of the folders over to a test install, but the new qBittorrent doesn't resume the download. Would importing the account onto a new install work?

---

### Post by beew on 2011-12-08
You can try importing your account since you have a test install.  

I have moved these two files, purged qbittorrent, used bleachbit to do one more clean up, rebooted, reinstalled qbittorrent and it still resumes!! So there is something else other than the two pieces that I mentioned above that enables qbittorrent to 'remember'. You have to move the settings of this unknown piece to the new install to ensure that it will resume correctly.

At the moment I am stumped. I have checked that all the qbittorrent files in /usr/lib has been removed when  I uninstalled qbittorrent so I don't really know what it is, sorry.

Maybe you can do what searchfgold says, simply copy the folder QBT-dir over and then restart qbittorrent and just readd the torrent.

---

### Post by McTwitch on 2011-12-08
Moving the qbt-file didn't help. I can try just popping over that and a torrent, though. I found some more qBittorrent related files in .local/share/data/qBittorrent. I moved those over to the test install, but after doing that, the program refused to open at all. Also, all of these problems stem from another post of mine; my regular harddrive won't boot. It comes up with an error, and the "grub rescue>" screen. Any suggestions on that post would circumvent quite a few hassles.

update: At one time I did find the torrent file in some obscure folder on my system, but now I can't seem to repeat it. I still can't get qBittorrent to resume the old download on the new install. It's just not something that's working. I'm still trying, though, and I'll keep updates coming as I attempt them.

update2: Importing accounts isn't working, either. I click the import accounts button while installing, and point it at the correct account, everything. But when I boot onto the new install, and log in, there isn't anything from the old account.

---

