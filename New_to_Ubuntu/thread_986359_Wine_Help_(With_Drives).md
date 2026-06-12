---
title: "Wine Help (With Drives)"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by flinstonex on 2008-11-18
Okay, so. Ive got wine. When i go to Applications > Wine all i see is Programs, Browse C:/ drive,Configure Wine, and Uninstall wine software. In Programs, all i have is notepad. Heres a picture.
[IMG]http://i62.photobucket.com/albums/h93/x0_naz/Picture1.jpg[/IMG]

Now. I want to be able to open my Windows C: and D: Drives on Ubuntu (I'm dualbooting). My C: Drive is windows etc, and my D: Drive is all my games, applications, etc.

So I go to Configure wine, then i click on the 'Drivers' tab. I click AutoDetect and get this:
[IMG]http://i62.photobucket.com/albums/h93/x0_naz/Picture2.jpg[/IMG]

Notice how my D: drive is just a / ? I want to be able to access my files from windows and be able to open them through wine. So i tried another way. I attatched myself onto the D: drive.
[IMG]http://i62.photobucket.com/albums/h93/x0_naz/Picture3.jpg[/IMG]

When i try to run wow i get an error.
[IMG]http://i62.photobucket.com/albums/h93/x0_naz/Picture4.jpg[/IMG]

Is it because i do not have the game installed onto Ubuntu, but rather the windows drive?

Anyway, the only thing ive tried so far and worked was ventrilo, and some other programs. Maybe its cause i barley have anything on my windows drives (im at a fresh format). Photoshop opens then closes quickly, but its a portable version so idk bout that. Uhm..

So basically, can i work around the Browse C: drive just by mounting the drives and running it from there? And why wouldn't WoW work?

Also, my uhm Ubuntu partiton is only 20 gigs because at first i didnt think i would like it, but i fell in love, and now i regret giving it so little space. So, soon enough, i will reformat again and this time give ubuntu 50 or 100 gigs, and the rest to windows. Dont hate me for that. I need windows incase something wont work or i cant get something in ubuntu, so i need some backup. I also use windows to game for now seeing as im having trouble with wine.

Any help is greatly appreciated.
Thanks :D


PS - UNRELATED: How do i get my 'recordmydesktop' to work smoothly. When i recorded a video and played it back, it was really choppy and laggy. Can someone give me the best performance settings for recordmydesktop.
Also could it just be that the player for it lags, but the video itself is fine?

---

### Post by txcrackers on 2008-11-18
The problem with trying to run stuff off of your Windows partition is that it's **not** installed "in" Wine - your configuration and pseudo-registry files only "know" about stuff that you installed through Wine. You might get away with pointing drive_c to your mounted Windows partition, but there's no bets on that.

The other thing is that when you installed WoW in Windows, you probably put it on the C: drive, which means that *it's* configuration is expecting it to be on C:, not D:

---

### Post by Kellemora on 2008-11-19
Hi Flins

For something to WORK on Wine it must be installed in Wine!

Most windows programs write information to the Windows Registry during installation, and this points to where those required files are.

Then there is another problem, Wine is NOT WinDOZE, it's not even an emulator of windows.  Thus the name Wine Is Not an Emulator!

Many Games and some power programs make API calls, therefore they cannot be run on Wine at all.
It's sorta like looking under the hood of your neighbors Ford car to see a part number for what your Chevy car needs.
Early Apples called these Peeks, Pokes and Calls!

TTUL
Gary

---

