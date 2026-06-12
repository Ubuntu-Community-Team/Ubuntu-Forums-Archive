---
title: "Access Windows 10 Network Share"
date: 2016-08-12
forum: New to Ubuntu
---

### Post by martymcfly2 on 2016-08-12
Hello everyone,

I'm trying to access a folder of my Windows 10  laptop from my Ubuntu desktop (with Gnome.) I am very new to this and I  don't understand what I'm doing. Googled the last few evenings and  always ended up with the message "Unable to access location. Failed to  mount Windows share: Invalid argument."

I'll just write everything in a list to keep it quick:

- I logged in to my laptop with Windows Live login and I want to keep it that way.
-  I right-clicked on the folder on my Windows 10 laptop, clicked on  "Properties," then "Sharing," then "Advanced Sharing" and then "Share"
- Sharing worked with my Windows 10 desktop
-  Opened up "Places" in Gnome, clicked on "Other Locations," "Network,"  my network, my laptop, entered my Windows Live login data, didn't know  what to set on "Domain" so I just left it at the default which was  "WORKGROUP", unfortunately clicked on "Remember forever"
- The error "Unable to access location. Failed to mount Windows share: Invalid argument." popped up
- Installed cifs-utils, same error
- Edited /etc/samba/smb.conf and added my network name under "workgroup =", same error

A few ideas I have:
-  When I have to enter the login data for accessing the Windows 10 share,  I should have changed the "Domain" to the domain of my email address,  so "Places" would have to forget my login data so that I can re-enter  them, but I don't know how to make it forget these.
- Maybe I have to add a different user on my Windows 10 laptop and share it with that one?

I'm  sorry for the question, this probably has been asked a million times. I  mostly just don't understand the tutorials that I found that well,  since I'm completely new to this.

Thanks in advance!

---

