---
title: "How do I Transfer config from 11.04 to 12.04 install"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by phubert28 on 2012-06-02
An older friend has a Ubuntu 10.10 install he wants me to replace with 12.04.

He has two hard drives and I planned to install 12.04 on his other drive.

I have 11.04 in the same situation and was planning to do the same.

CAN I transfer our configurations from our OLD Ubuntu installs to 12.04 on another partition, or do I need to just do everything from scratch in the new install???

For mine, I have accumulated information on replacing Unity, as I don't care for that interface. For my older friend, Unity may be a godsend!

---

### Post by Irihapeti on 2012-06-03
It all depends on the individual programs and utilities concerned. If a program is still storing the same config files in the same place(s), then there shouldn't be a problem. But if a program's been rewritten to store things in a different place, then it needs to be configured from scratch.

I don't think it would work to transfer the configs all at one go. Enough has been changed since 11.04 to cause some problems. (Even more so with 10.10) But you can certainly transfer your Firefox profile and a few others, which can save a lot of work with setting up the new system. I did that when upgrading from 10.04 to 12.04.

I'm not sure how much of your Unity knowledge will transfer to the newer version (I've not used Unity much), but I think the general principles would still apply.

As for your friend, you could install gnome-fallback (from the repos) and then show him how to choose the desktop environment from the login screen. That way he can play with both and decide which suits him best.

---

### Post by phubert28 on 2012-06-03
Thanks, [Irihapeti]("http://ubuntuforums.org/member.php?u=346442"). Yes, Firefox profile would help considerably. And there's really not that much installed that can't be redone. The part that gets me is the LastPass transfer to a new system!! I know it shouldn't, tho. For me, tiny details are the most difficult part.

Anyway, good advice. I haven't used Unity - and from what I've seen, don't PLAN to. But I suspect Unity on 12.04 MAY be a real help to my friend who has difficulty navigating menus!

I'm an old mainframe Assembly language programmer and later sysprog, finally supporting Windows and VMware servers. Glad to be retired. A little reluctant to get into things, but I'd really like better knowledge of the innards of Linux. My upgrade to 10.10 from .04 got a little hosed in a couple of areas, and the subsequent upgrade to 11.04 didn't help, so a fresh install of 12.04 will probably be the way to go.

Recently fixed a problem with Firefox - the profile got hosed - the fix was fairly easy. Still far better than Windows!

Anyway, thanks again for the advice. I'll follow it.

---

### Post by wildmanne39 on 2012-06-03
Hi, I had one configuration file from 11.10 that I put on 12.04 and I ended up reinstalling 12.04 again because of it with out the use of the file the second time around.
Thanks

---

### Post by phubert28 on 2012-11-05
It turned out that my older friend WANTED the classic interface - I set it up for him.

My concern is having ACCESS (permissions) to my 11.04 install files FROM my new and separate 12.04 installation.

Thunderbird mail and Lightning CALENDAR files and configuration and Firefox profile are the most significant issues for me after the question of all my present folder structures and data.

My 11.04 is now off support which is awkward.

If only OSes were kept longer, and UI's LEFT ALONE!

---

### Post by black veils on 2012-11-05
if there is no encryption, you can easily access files from a live cd/dvd/usb stick, if unable to from the installed system. from my experience, managing files on an installation while using another system on that drive, is the same as doing so with a usb stick, except you will need to open the file manager with root privileges if pasting files into another system.

are you asking where to find these configuration folders/files?

---

### Post by newb85 on 2012-11-05
Make sure when you set up the new installation that you use the exact same username (case sensitive).

---

### Post by phubert28 on 2012-11-05
newb85, thanks for the username tip - I would very LIKELY have done so, but better I know it's critical! :-)

As to the location of the config/profile directories, I expect I'd have to check with Mozilla on that??

I'll have to admit that LOOKING at the file structures I seem to see duplicates of folder/directory names in different locations - THAT I find confusing.

I also find it confusing when I install fonts and want them available to all users - all their folders seem to be under my own HOME tree!

I'd LOVE to have a local Linux expert who is helping others that I could train under so I could BETTER help others!!!

---

