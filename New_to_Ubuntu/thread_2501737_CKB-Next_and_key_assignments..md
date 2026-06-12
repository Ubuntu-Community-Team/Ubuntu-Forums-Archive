---
title: "CKB-Next and key assignments."
date: 2024-10-18
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-18
Heyo guys,

So I have done amazing things with CKB!  I love this software, but what I want to know how is this.

I was to assign discord to G3, calculator to G1, Brave to G2 etc, but idk where to find anything and what do to.  Help please?

---

### Post by bobunderwood99 on 2024-10-19
Hello,

Does this help: [https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-shortcuts-set.html.en)

---

### Post by shadowtabby on 2024-10-19
Heyo,

No because its not using the [COLOR=#000000]CKB-Next and it is not telling me how to fet the things I need to make it work for G1 - 6 with assigning it to software.[/COLOR]

---

### Post by grahammechanical on 2024-10-19
If you are like me, wondering what this thread is all about, then here is the answer:

[https://github.com/ckb-next/ckb-next](https://github.com/ckb-next/ckb-next)

I am still noe-the-wiser.

Regards

---

### Post by 1fallen on 2024-10-19
Two choices, build from source:
```

sudo apt install build-essential cmake libudev-dev qtbase5-dev zlib1g-dev libpulse-dev libquazip5-dev libqt5x11extras5-dev libxcb-screensaver0-dev libxcb-ewmh-dev libxcb1-dev qttools5-dev git libdbusmenu-qt5-dev
```
Then:
```
git clone https://github.com/ckb-next/ckb-next.git
cd ckb-next
./quickinstall
```

Or add the PPA Good up to 24.04
```
sudo add-apt-repository ppa:tatokis/ckb-next
sudo apt install ckb-next
```

Not what you asked about, but it works for those who have that board.
And it runs as deamon I would have to guess:
```
sudo systemctl start ckb-next-daemon
```

---

### Post by shadowtabby on 2024-10-19
Heyo,

I'm with you, I am thinking where is the info on how to do this, I see the keyboards etc that it will work with etc.  I look at this and think, I already have this installed.   Point is I want to get the apps on the G1 - G6 buttons, and I am not sure how to get the apps locations to put it in the mapping in the software which is what the question was.  Then I look in places being dyslexic and think, where is the information for this that I am asking about clearly and gave examples in my first post?

---

### Post by 1fallen on 2024-10-19
I don't have the device, I'm just trying to help you: [https://github.com/ckb-next/ckb-next/wiki/CKB-Daemon-Manual](https://github.com/ckb-next/ckb-next/wiki/CKB-Daemon-Manual)

---

### Post by shadowtabby on 2024-10-19
Heyo,

Ik ik.  I wasn't being nasty or anything... Let me read this other link you sent.

---

### Post by shadowtabby on 2024-10-19
heyo,

I need the path for apps.  So I can assign them to the key.  HOW do I get THE PATHS for the software??

So in other words.  To asign a software launch to G1 like the calc or discord I NEED THE PATH TO THE SOFTWARE to assign to the key.  HOW do I get the PATH?

---

### Post by bobunderwood99 on 2024-10-19
grahammechanical: 
this thread is a continuation of "icue app?"

1fallen2:
It's in the Ubuntu repositories.

shadowtabby:
I've never used ckb-next and have no Corsair peripherals. 
If you do not see a way to assign a key to open a program (open the Bindings tab) ckb-next may not support that.
So try the method linked to in post #2.

---

### Post by 1fallen on 2024-10-19
> **shadowtabby said:**
> Heyo,

Ik ik.  I wasn't being nasty or anything... Let me read this other link you sent.

I did not think that for second, I just did not want to over sell myself in this thread.
> **shadowtabby said:**
>  I NEED THE PATH TO THE SOFTWARE to assign to the key

Just an example for mine and we use a different system all together.
```
[FONT=monospace][COLOR=#000000]which kcalc [/COLOR]
/usr/bin/kcalc

[/FONT]
```
You get the idea now....

---

### Post by shadowtabby on 2024-10-19
Heyo,

I would show a screen shot but this forum stops me at times from it with this firewall thing and says I am doing everything wrong basically.  It seems like no one is getting what I am asking.  I just will give up on this subject.

---

### Post by shadowtabby on 2024-10-19
OOOOOOOOOOOOOOOOOOOOOOOOOOOOOOO progess.  Okies what about other apps?  Discord etc?  Where are they?

This is the type of thing I am needing:  [COLOR=#000000][FONT=monospace]/usr/bin/kcalc[/FONT][/COLOR][FONT=monospace]

Um calc as in the one that is in the "start menu" of Ubuntu 24.4.1 LTE.

I get overwhelmed so easy with new things.[/FONT]

---

### Post by shadowtabby on 2024-10-19
[QUOTE=1fallen2;14210172]  Just an example for mine and we use a different system all together.
```
[FONT=monospace][COLOR=#000000]which kcalc [/COLOR]
/usr/bin/kcalc

[/FONT]
```

IT WORKS!!!!  But with the calc it's [FONT=monospace]/usr/bin/[/FONT]gnome-calculator for me.

Thank you so much thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you, thank you!!!!

I cannot find brave and spotify in the bin folder, do you know where else it could be?

---

### Post by bobunderwood99 on 2024-10-19
Look in```
 /snap/bin
```
[https://www.baeldung.com/linux/snaps-flatpak-appimage](https://www.baeldung.com/linux/snaps-flatpak-appimage)

---

### Post by 1fallen on 2024-10-19
> **shadowtabby said:**
> 

I cannot find brave and spotify in the bin folder, do you know where else it could be?

I don't know about spotify but brave would be the same method, if it isn't a snap package EDIT or a Flatpak....
```
[FONT=monospace][COLOR=#000000] which brave [/COLOR]
/usr/bin/brave
[/FONT]
```
Or for you it might be:
```
[FONT=monospace][COLOR=#000000] which brave-browser[/COLOR]
[/FONT]
```
Flatpak:
```
[FONT=monospace][COLOR=#000000]which com.brave.Browser [/COLOR]
/var/lib/flatpak/exports/bin/com.brave.Browser

```


[/FONT]

---

### Post by shadowtabby on 2024-10-19
Heyo.

I looked in /var/lib/flatpak/exports/bin/ and [COLOR=#000000][FONT=monospace]/usr/bin/brave and I cannot see brave there and ik it's on here cause I am using it currently.  

I just checked, I installed it through the app store.[/FONT][/COLOR]

---

### Post by 1fallen on 2024-10-20
It's a snap then, and I won't be of much use on that>>>>NO Snaps here>>>YUCK!

 EDIT: bobunderwood99 post #15 now that he edited it makes more sense

---

### Post by bobunderwood99 on 2024-10-20
Look at post #15.

---

### Post by shadowtabby on 2024-10-20
> **bobunderwood99 said:**
> Look in```
 /snap/bin
```
[https://www.baeldung.com/linux/snaps-flatpak-appimage](https://www.baeldung.com/linux/snaps-flatpak-appimage)


YOU LEGAND!!!!

Thank you very much.  Thank you.

---

### Post by shadowtabby on 2024-10-20
Everyone that replied to this post.

Thank you heaps!!  Thank you heaps for the help of this.  Thank you.

---

