---
title: "MythTV won't delete files"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-10-18
Hi MythBuntu Community:

I'm having trouble with deleting recorded shows from MythTV...

When I hit "d" on Recorded Shows, and then look in my default storage directory, the show is still there...

The permissions of all of the files in the default storage are mythtv:mythtv and have read and write privileges.

How do I get MythTV to delete files so that I don't run out of space in the default storage?

Old Jimma from the Old Country

---

### Post by Old Jimma on 2012-12-28
Y'all:

[COLOR="Red"]If you can't delete programs using on mythfrontend, try adding yourself to the mythtv group:[/COLOR]

> [COLOR="Red"]sudo usermod -a -G mythtv USERNAME[/COLOR]

as per the instructions at: [https://help.ubuntu.com/community/MythTV/Install/mythtv-group]("https://help.ubuntu.com/community/MythTV/Install/mythtv-group")

Although the documentation doesn't seem to say that you need to do this, I've scoured the web and found that this works... if you cannot deltete them easily using mythfrontend.

So many tiny things you've gotta take care of with myth!

However, it is very worthwhile... since Myth is SO GREAT! :)

The Older than Rocks Jimma
From the Oldest Part of the Old Country

---

