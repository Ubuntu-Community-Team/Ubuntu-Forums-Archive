---
title: "Downloads Failing #IJustWantToUseMyComputerAlready"
date: 2018-01-08
forum: New to Ubuntu
---

### Post by letsbestrangers on 2018-01-08
TL;DR - I can't download anything from firefox 56.0 on Xubuntu 17.10.

Details: I go to download Kerbal Space Program or Drone Racing Simulator or Autodesk Inventor (Linux versions obviously) and the download gets to around 120 - 150 Mbs and then suddenly says that the download has failed. I've tried resetting firefox to default settings, i tried to download chromium to see if it was a problem with firefox, but that also failed. so then i thought "what if i got wine so  i can get chromium" but that failed too. it's like being stuck at the bottom of an empty pool and you're too short to even reach the ladder to climb up lol.

---

### Post by TheFu on 2018-01-08
Welcome to the forums.

Is the disk full?  df -h
Are all the inodes used? df -i
What are the permissions for the download location?  ls -al /path/to/directory
Have you run any programs with sudo/root which might have setup directories with permissions that prevent normal userids access?

---

### Post by Impavidus on 2018-01-08
If you installed all upgrades available for Ubuntu 17.10, you should have Firefox 57 instead of 56. So apparently you didn't do so. Maybe installing all available upgrades fixes some bug that causes this behaviour.

You could try and download stuff using wget:```
wget http://www.example.com/whatever
```However, I don't think this is a problem caused by Firefox (unless it's caused by running version 56 instead of 57).

---

### Post by wyliecoyoteuk on 2018-01-08
How much space is available in your home directory?

---

### Post by oldos2er on 2018-01-09
> **letsbestrangers said:**
> "what if i got wine so  i can get chromium"

Why would you need wine? The package *chromium-browser* is in the repositories.

---

