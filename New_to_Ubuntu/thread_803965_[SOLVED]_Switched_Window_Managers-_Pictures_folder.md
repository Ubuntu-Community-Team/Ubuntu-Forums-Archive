---
title: "[SOLVED] Switched Window Managers- Pictures folder and Contents Gone!"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by randy78 on 2008-05-22
Hey all...

Strange thing happened just now...

I booted into Ubuntu, Let the system load and decided to do a couple things...

First I deleted a couple of items from my Desktop and I noticed that the SHIFT key on the right hand side of the keyboard was stuck down... so I unstuck it and then I right clicked on the Compiz Fusion Icon and changed window managers, from Metacity back to Compiz.

Immediately after switching, my wallpaper disappeared (the black-green Hardy Heron wallpaper, if anyone knows where I can find it again I'd appreciate it!), my Skydome background disappeared and so did my Pictures folder, which is located within a folder on my desktop (I don't use the Pictures folder in the Home directory, I have a folder that I store stuff in on my Desktop, for quick access).

The Pictures folder and all pictures inside of it were removed, and I don't know what happened.

I then checked the Pictures folder in the Home directory to see if, by chance, the contents may have been transferred to it, but no luck.

It seems that something happened when I switched back to Compiz (Which runs great and has been working flawlessly since Gutsy on my machine).

Any way to see what happened?

I'm experienced with data recovery, so I'll probably end up using the Testdisk suite to try and recover the files, but this is crazy!

Any suggestions and ideas are appreciated!

Thanks and Take Care
Randy

HP Pavillion a1104x
P4 3.06 Ghz
2GB ram
Integrated graphics (Intel)
Ubuntu 8.04 Hardy

---

### Post by Xiong Chiamiov on 2008-05-26
It may seem like a stupid question, but did you check your trash?  And, I'm assuming that the folder doesn't show up when you do an ls in the directory?

---

### Post by sayakb on 2008-05-26
Are you sure that you didn't accidentally delete it? Since your shift key was stuck, you might have Shift+deleted them which bypasses trash and deletes them completely.

---

### Post by randy78 on 2008-05-26
Thanx for the replies!

I wasn't in the Directory with the Pictures folder when this occured...

As stated, I had deleted two other files that were on the Desktop, and didn't enter the directory where the Pictures folder resides at all.

It was deleted almost instantly after I switched back to Compiz from Metacity.

Thanx for the tip about the Shift-Delete though!
Handy :D

Take Care

---

### Post by randy78 on 2008-05-29
Alright...

I think I figured out what was doing it, and I believe it was a Secure-File-Delete Nautilus script that I was using...

I just downloaded another file and when I was done extracting it, I used the Secure-File-Delete script to erase the file, but this time I had my storage folder open, and sure enough, it was deleting other files as well as the file that I selected for removal!

I caught it early though and hit Ctrl+Alt+Backspace too break the operation before too much was erased...

I had a ton of stuff in that folder, so I don't know what's missing yet, but needless to say I won't be using that script anymore!

;)

Take Care

---

