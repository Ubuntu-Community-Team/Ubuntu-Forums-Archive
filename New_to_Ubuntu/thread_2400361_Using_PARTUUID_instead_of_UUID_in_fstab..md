---
title: "Using PARTUUID instead of UUID in fstab."
date: 2018-09-05
forum: New to Ubuntu
---

### Post by rocco.martinello on 2018-09-05
[FONT=arial][SIZE=2]Hi to all,


in order to see UUID of my swap partition I used the command [COLOR=#000000]*sudoblkid | grep 'TYPE="swap"'*, [/COLOR][COLOR=#000000]but it only shows PARTUUID and not UUID for my [/COLOR][COLOR=#000000]/dev/sda5 partition.[/COLOR]
[COLOR=#000000]If I use *sudo file -s /dev/sda5* I see an incorrect UUID (UUID=00000000-0000-0000-0000-000000000000 [thisUUID doesn&#8217;t work in /etc/fstab]).[/COLOR]
[COLOR=#000000]I needed to know UUID to enable swap partition in /etc/fstab.[/COLOR]
[COLOR=#000000]Now I put PARTUUID [/COLOR][COLOR=#000000]in /etc/fstab and the swap partition is enabled.
Now my questionsare:
[/COLOR][COLOR=#000000]1[/COLOR][COLOR=#000000])I know that it is necessary to use UUID instead of [/COLOR][COLOR=#000000]/dev/sda5 [/COLOR][COLOR=#000000]in /etc/fstab [/COLOR][COLOR=#000000]to avoid problems adding another hard drive (/[/COLOR][COLOR=#000000]dev/sda5 [/COLOR][COLOR=#000000]can change, but UUID cannot): is this problem avoided anyway using PARTUUID?[/COLOR]
[COLOR=#000000]2)Can using PARTUUID instead of UUID cause problems?[/COLOR][/SIZE][/FONT]

---

### Post by oldfred on 2018-09-05
The partuuid or GUID is new with gpt partitioned drives.
See this that shows fstab can use partuuid.
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

To see both UUID & partuuid. You have to widen terminal screen to see on one line.
lsblk  -o name,label,partlabel,size,mountpoint,uuid,partuuid

New versions of Ubuntu use a swapfile. But will use a swap partition if one is found when installing.

---

