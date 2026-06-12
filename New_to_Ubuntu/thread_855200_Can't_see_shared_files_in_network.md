---
title: "Can't see shared files in network"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Michl on 2008-07-10
I'm not sure what or when this happened, but this wasn't a problem but
now it is.  Using Hardy.

I have four computers on a network and they all show up in
Places -> Network, but for some of the computers the
shared files do not show up and mount. All that shows up is a
print$ folder.  I have tried to do everything the same
way as I did on the computer whose shared files do show
up in setting-up file sharing, but without success.

Thanks.

---

### Post by fatality_uk on 2008-07-10
I know you don't know when, but have you upgraded Ubunt recently? As in from Gutsy to Hardy for instance?

---

### Post by Michl on 2008-07-10
Yes, I upgraded from Gutsy, but I was following the Alpha and
Beta paths and then did a clean install of the final version.
I think along this way something happened.  I vaguely remember
that I had it working before the clean install.

In any case, the following worked.  I installed system-congif-samba
and saw with that gui that only the printer files were shared and none
of the other files I had marked for sharing.  This is odd, because
in 'sharing options' and properties -> share in nautilus they
are marked as shared.  In any case, when I added these files in
the system-config-samba gui, everything worked as before.

So it is solved for me, but I hope that this is not the official
path for sharing files because it should work from within
nautilus as designed in 8.04.

---

