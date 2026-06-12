---
title: "Most of the apps aren't working T.T"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by DarknessEnemy on 2008-07-02
Im still pretty noob in linux, so I dont understand much of the things.

I wanted to talk to my friends using aMSN, and didn't worked (never started the app: so I had to use pidgin), I tried to run Limewire but said that wasn't allowed to use the directory that always used. I started firefox and I cannot see my bookmarks (besides, my google search bar doesn't work). I never had problems with Amarok, Now starts a little bit awkward, starts with a very tiny window and an other normal window, Tried to close, and the window is gone, but music still on.

(The last thing I did was Installing supertuxkart and updating my system)

I hope you can help me. Ive used a lot this forum and I don't want to disturb anymore, but I don't want to use windows again either.

Thank you in advance.

---

### Post by kuja on 2008-07-02
> **DarknessEnemy said:**
> I never had problems with Amarok, Now starts a little bit awkward, starts with a very tiny window and an other normal window, Tried to close, and the window is gone, but music still on.
a) Maybe you enabled the xmms-like player window, check in settings->configure, in the general tab, look for a "show player window" option, if it's on and you don't want it then turn it off. Amarok runs in the system tray. If you close it it will just minimize to system tray. To really make it quit you have to go to Engage->Quit or hit Ctrl+Q.

---

### Post by DarknessEnemy on 2008-07-02
Well, I don't know if thats the problem with amarok, but it did not minimized to system tray. I checked (Or at least, didn't had a tray Icon). But there are not answers about my other problems? Well, maybe I just screwed up on something.

---

### Post by kuja on 2008-07-02
I don't really use aMSN, Pidgin, Limewire, or Firefox ... soooooo I don't really have any ideas for those.

As per amarok, I do use it, I use it a lot :) I'd say that it's still probably running in the background, pretending it has a tray icon, and when you close it it minimizes to tray, except there's no tray icon, so there's no way you can get it back up ... I don't even think there's a dcop command for bringing it back.Maybe if you have a shortcut key for launching amarok, then that would work though ... I'll google around and see if I can't find a solution for your problem in the morning ... As for now, I'm going to bed.

---

### Post by DarknessEnemy on 2008-07-02
Thank you. I appreciate it. XD. Well, if it not works I was planning to install Ubuntu Studio anyway . Of course meanwhile every answer is welcome.

Ill be waiting.

---

### Post by clive littlewood on 2008-07-02
Hi

With Amarok if you close with the X it only closes to the sys tray, to close use the quit in file menu.

I have found Frostwire to be much better than Limewire in Linux.

I would suggest a new install of the program, it will then allocate it,s own files.

Hope this helps a bit

Clive

---

### Post by jflarm on 2008-07-02
For amsn:
Start a terminal and type amsn (press Enter)
Maybe you could see an error message that could help you.

For LimeWire:
Find out if the directory you want to share is owned by you user. If it is owned by root, you won't be allowed to share it.
You can do this also on a terminal doing: "ls -l" on the directory or just opening the Nautilus (your file browser) and looking at the column Owner for the directory.

Hope this helps..

---

### Post by strongboww on 2008-07-02
i have got kind of the same problem today, suddenly firefox went crazy

no bookmarks
google search in upper right corner doesnt function
no cookies saved and so on

edit: amarok also doesnt start up

gives an error message with dcop server
```

There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read network connection list.
/home/longbow/.DCOPserver_heimdall_0

Please check that the dcopserver program is running!

```

edit2:
also music keeps playing after close, worked perfectly yesterday... i suppose it was the update today which screwed everything up

---

### Post by kuja on 2008-07-02
This thread is really old, but it may be of use: [http://forums.gentoo.org/viewtopic-t-463567-highlight-.html?sid=4a91e1bde8991806415bced27f0be669](http://forums.gentoo.org/viewtopic-t-463567-highlight-.html?sid=4a91e1bde8991806415bced27f0be669)

---

### Post by DarknessEnemy on 2008-07-02
I have noticed that I can see bookmarks, until I try to use limewire. Then it says that doesn't has premission to use /home/user/limewire/shared.

aMSN works but with lots of error messages.

Amarok doesnt work at all now, and it comes out an error message:

```
there was an error setting up inter process communications for KDE. the message returned by system was:

Could not read connection list.
/home/user/.DCOPserver_user-laptop_0

Please check that "dcopserver" program is running
```

Oh yeah. and Comix doesn't work. XD

I also think that was the update that screw everything up, because I had ubuntu before like 1 month ago. so I think that I was doing something that I should not while it was upadting, but as long I can remember, I was just watching Daria on VLC.

Sorry about my bad english.

---

### Post by kuja on 2008-07-02
I wonder if [this](http://ubuntuforums.org/showthread.php?t=622563) will help with the amarok problem.

---

### Post by DarknessEnemy on 2008-07-03
Im giving up, but thanks. Thanks a lot.

---

