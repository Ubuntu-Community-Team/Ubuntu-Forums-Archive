---
title: "Thunderbird mail from XP - permissions"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by markling on 2008-05-27
Hello

encountered a prob transferring thunderbird mail from xp to ubuntu.

here's what happened:

created mozbackup in windows
copied backup to external usb hard disk and deleted from C:
installed ubuntu 8.04 + thunderbird
discovered there isn't a version of mozbackup for ubuntu
extracted mozbackup file on external hd
tried to copy mail folder from external hd to profile folder in ubuntu
got this error:
"The folder "Mail" cannot be copied because you do not have permissions to create it in the destination."
tried to change permissions - didn't work.

thanks

markling.

---

### Post by quelx on 2008-05-27
What do you have in the mozbackup archive?

is there some **xXxXxXxX.default** file?

Try launching Thunderbird on your Ubuntu box and setup your email as you normally would.

Then **ALT-F2** > **nautilus ~/.mozilla-thunderbird**

in there is some random direcectoy.default

Copy the **Mail** contents of your old xxxxxxxx.default into the new **Mail** directory in xxxxxxxx.default

Fire up thunderbird

---

### Post by markling on 2008-05-28
thanks, but that's not quite worked and appears to have complicated matters.

i copied the files as you suggested, and took the 'merge' option that ubuntu gave me.

but the emails haven't appeared in the folders list in thunderbird. there's one from march and a few from the other day, but nothing else at all. today's mail has downloaded.

i wonder now that if i *did* manage to import my thunderbird emails from my windows file, whether i would be able to keep the ones that have since downloaded, since thunderbird's import facility appears to be nothing but a crude over-copy.

there are other thunderbird settings that it would be useful to keep as well - e.g. filters.

and i still have this issue of ubuntu telling me that i don't have permission to copy a file, which i created, from my own external drive to my own hard drive. if i don't have the permissions, then who does!?!-)

thanks

markling.

---

### Post by markling on 2008-05-28
ok, i've bitten the bullet and read through mozilla's painfully finicky instructions for copying files individually from one profile folder to another. it appears to have been fairly successful.

but there are problems: it has not maintained the same mail folders, losing subfolders and bunging all the mail in the same one. bizzarely, its managed to keep the subfolders for a secondary account that's no longer used, but from which the mail must also be kept.

its lost the starred items and message filters. i wonder if it has it lost anything else? i'm not filled with confidence.

it's not good enough, really. i've had a lot of faffing about to get unsatisfactory results regarding some of my most important data. i would not normally hesitate to recommend thunderbird to someone else, but i'm not sure i can until mozilla does something to make the transfer of mail and settings a little more reliable and navigable by common or garden computer users.

markling.

---

