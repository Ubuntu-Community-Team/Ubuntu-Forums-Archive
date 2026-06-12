---
title: "HOWTO: Easily edit Grub's default boot"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Tomosaur on 2006-07-31
I wasn't going to put this up here, but I figure it could be useful for newbies, or indeed lazy people :P

I wrote a little script which can replace the default menu item on grub to whatever you want it to be, but which will default to the LAST menu item if you don't pass it any parameters. It was originally written to allow a guy to set his Grub to default into Windows XP, but it should work fine for anybody. On my machine, Windows XP is the last menu item in grub, so it works just fine and dandy for me. I've seen other Grub setups where XP is the last menu item, so I just assume it's the same way for everyone unless they've modified their menu by hand.

Usage is just
```

sudo sh WinBoot.sh

```

This will set your grub default boot to the last menu item. On my machine, for example, the bottom menu item (WinXP) will load by default unless I cancel the timeout.

Alternatively, you can type
```

sudo sh WinBoot.sh 2

```

And grub will now load whatever your 3rd menu item is. Yes, that's not a typo. Setting your default item to '2' will load the 3rd menu item, since grub counts from zero (therefore, it counts like this: '0, 1, 2', with 0 being the first menu item.)

For now, there's no option to alter the timeout time. This is partly for safety reasons - setting it to 0 could cause problems. If enough people want it, I may add it, or you can just script it in yourself.

Keep your grub menu trim, the script will only work properly if you have 9 or less items listed. Any more than that and you'll have to alter the script yourself, or edit your /boot/grub/menu.lst file by hand to keep things tidy.

This is primarily to make things easier than sudo nano'ing your menu.

Before using the script, reboot and check your grub menu for whichever item you want to boot into. Remember to count from zero. Also bear in mind that the 'Other Operating Systems' seperator line DOES COUNT as a menu item. If you're a bit more savvy, you can just check your menu.lst file and see which order everything's in.

Download the attached text file and save it as WinBoot.sh to use it.

As always, feel free to edit it for your own needs. If anyone makes a significantly better version, just PM me the file and I'll replace mine, edit this post, and give you all the credit :)

---

### Post by Whuggy on 2008-07-30
Hey there. This is just what I need.

I've just installed both XP and Ubuntu onto my new laptop. I'd like to have XP as the primary choise since that's where I can access the wlan so far :)

My big problem is. I do not quite get all of this. This WinBoot.sh should be placed in the Grub folder, right? How do I do that when I do not have the permission to do anything on the filesystem? :|

If anyone can explain me how I should do this I'd be very grateful :)

EDIT!:
I managed to edit the stuff by doing something else. I'd still like to know how this stuff works though :)

---

