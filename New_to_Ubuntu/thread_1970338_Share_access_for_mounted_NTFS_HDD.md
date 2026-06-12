---
title: "Share access for mounted NTFS HDD"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by HandTowel on 2012-05-01
I'm running my main desktop PC on Ubuntu 12.04 and then have 3 x Windows 7 laptops and 1 x Mac running on the network (combination of wired and wireless).
What I want to do is share two 2TB NTFS HDD (containing movies, TV Shows, musci, etc.) to everyone - a bit like the idea of Windows 7 Homegroup sharing.

At this stage I've got one of my laptops able to connect and access (read+write) files on these two HDD. This laptop is using the same username that I'm logged into on Ubuntu (pantau) and it doesn't seem to matter that the windows password is different between systems, so long as I enter the one that is being used in Samba.

The other 3 PC's (using different usernames - mel, kel and (mac UID???)) are able to see my desktop PC (MediaPC) and drill through to the two shared HDD, but are unable to access anything further.

At this stage I've been mounting the HDD once logged in as UID 'pantau'. I get the feeling that I need to make this HDD mount as part of a startup script (?) prior to the PC logging in and in the same instance, allow all users to access them.

At this stage, security is not a huge problem for me.

Lastly, it is possible for me to re-format these drives, I have backups, so if alternative FS formats are advisable, let me know.

Cheers.


Just created a new user account on one of the laptops that wasn't letting me in - UID = 'pantau' the same as my working laptop - and it's allowed me access to the HDD. Also allows me to access the HDDs while logged in as the original users - just have to specify the UID - pantau - details when I connect with my desktop PC.

---

