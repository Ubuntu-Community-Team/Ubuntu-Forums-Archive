---
title: "Reseed torrents with Transmission"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Apurvam on 2013-03-03
How can I reseed torrents I downloaded in Windows now in Linux? What is the procedure?

I use Xubuntu 12.10.

---

### Post by Cheesemill on 2013-03-03
Just open the relevant .torrent files with Transmission, and point the download location to where the completed files live.

Transmission will verify the files to check that they are complete and then start seeding.

This is exactly the same process you would use when switching torrent clients in Windows, it doesn't matter that you are now using a different OS.

---

### Post by Apurvam on 2013-03-03
OK, I got seeding status, let's see if Transmission actually will seed those files.

---

### Post by Cheesemill on 2013-03-03
There is a problem with the tracker you are trying to connect to, you will have to wait until they sort out the problem at their end.

---

### Post by Apurvam on 2013-03-03
I got bunch of these errors:
> Tracker gave an error: "Connection limit exceeded! You may only leech from one location at a time." - Stalled

In Transmission's preferences I set 'Maximum active downloads' to 15 which is higher than amount of torrents I've added to Transmission.

---

### Post by Cheesemill on 2013-03-03
The tracker is telling you that you are downloading from more than one location at the same time, a lot of private trackers don't allow this which is why they are giving you an error message.

If this isn't the case then contact the admins of the tracker, they are the only people that can sort out your issue.

This isn't a problem with Transmission or Ubuntu, it's the tracker itself that is giving you these errors.

---

### Post by Apurvam on 2013-03-04
"The tracker is telling you that you are downloading from more than one location at the same time.."
Hmm.. So I need to delete those torrents in uTorrent (Windows)?

---

### Post by Hodevah on 2013-03-04
No. That is not neccessary. You are using Ubuntu when you are using Transmission, not Windows right?
So no need to delete them. Go on their IRC if you feel you want to and telll them what is going on. That you are using a different operating system after booting out of Windows. It takes a bit of time for an automatic recognition from an operating system usage change to occur on the tracker side. I had the same thing once.

---

