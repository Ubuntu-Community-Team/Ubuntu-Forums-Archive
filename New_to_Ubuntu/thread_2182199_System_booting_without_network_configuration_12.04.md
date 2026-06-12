---
title: "System booting without network configuration 12.04 lts"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by 884kmFE on 2013-10-20
Hi, this is my first post here.
So I'm not a complete noob but ubuntu managed to beat the **** out of me.

I installed ubuntu yesterday and configurated my internet through pppoeconf, the whole thing was very much straightforward.
Today I boot ubuntu because I have some work to do and see "system booting without network" and to my funny surprise there really is no network any where to be found!! I followed some "instructions" changing /etc/network/interfaces (actually getting to the file but not having a clue what to do) nothing really helped I'm not familiar with the system and the concept and right now am desperately reinstalling the system from CD. I'm pretty sure the problem will reappear itself cuz I'm using broadband internet and I'll try to set it up with pppoeconf again.

Please help!

EDIT: and yeah plz tell me how to return to GUI view after clicking ctrl+alt+f1 and how should input a file name if it has 2 word (cd word1 word2  => "word1 not found")

---

### Post by varunendra on 2013-10-22
Hi, and Welcome to the forums !

> **884kmFE said:**
> I installed ubuntu yesterday and configurated my internet through pppoeconf
You can also add and configure your PPPoE connection in Network Manager's gui, under "DSL" tab. That is usually the recommended method for Ubuntu. Although I personally prefer to save it in the dsl/adsl modem itself, thus keeping it 'always on'.

Be aware that "Network Manager" and the "/etc/network/interfaces" are two different methods to manage connections. Either one or the other should be used, not both for the same connection or else there may be problems due to conflicting settings.

Also, none of the 'Methods' would work if somehow your Ethernet interface goes down (driver or other problems). So did you make sure it is physically and 'logically' connected? If not, you'd need to fix that first.

> EDIT: and yeah plz tell me how to return to GUI view after clicking ctrl+alt+f1 and how should input a file name if it has 2 word (cd word1 word2  => "word1 not found")

press **Ctrl-Alt-F7** to return to the gui, and names with spaces should be supplied within double-quotes - "word1 word2". It can be either only the filename, or the whole path within the double-quotes. For example - **cat Desktop/"word1 word2.txt"** or **cat "Desktop/word1 word2.txt"**.

---

