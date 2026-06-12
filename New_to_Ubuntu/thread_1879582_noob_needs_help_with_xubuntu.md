---
title: "noob needs help with xubuntu"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by colorado_rubin on 2011-11-11
I have installed the latest xubuntu os on my chomium cr-48 laptop and all went mostly well, including more space for the sata drive.

all solutions online for connecting to a windows homegroup is based on ubuntu which seems way different then xubuntu, or have so much code talk that it reminds me of "basic" back in the day. I have spent 2 days looking with no luck. please, just looking for simple directions like step 1, step 2,etc..

thanks to any and all suggestions, I will continue to look.

fyi: we have to have a windows based system to run my wife's university programs and the kodak printer.

---

### Post by cwa on 2011-11-11
what guides are you looking at? have you tried the samba project?

---

### Post by The Cog on 2011-11-12
I think Samba is for sharing files **to** windows, not for accessing files shared **by** windows. So I don't think it's what's needed here.

I often connect to windows shares from Xubuntu. I use Gigolo (menu System->Gigolo) and enter the server details in there. This is fine for occasional server access. You may have to install package gvfs-backends first - this command will do it:
> sudo apt-get install gvfs-backends

For permanent mounting of shares, you will probably have to make an entry into /etc/fstab, but I doubt you want to do that on a laptop.

---

