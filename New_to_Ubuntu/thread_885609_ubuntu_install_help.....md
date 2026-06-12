---
title: "ubuntu install help...."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by tomdlgns on 2008-08-10
i downloaded the ISO off of the [www.ubuntu.com](www.ubuntu.com) homepage and burned it onto a CD...i put it in my pc, and it booted up to the ubuntu splash screen, which was fully functional...i could use the arrow keys, etc...

then i highlighted install ubuntu and pressed enter, nothing happens...

what am i doing wrong?

---

### Post by gjoellee on 2008-08-10
you may need to click on the button on the screen and not enter, check out the video here to how you install Ubuntu: [http://www.polishubuntu.piczo.com/howtoinstallubuntu/?cr=2](http://www.polishubuntu.piczo.com/howtoinstallubuntu/?cr=2)

---

### Post by WRDN on 2008-08-10
If you can't navigate the immediate selection screen after booting from the CD, then it sounds like a bad burn.

---

### Post by tomdlgns on 2008-08-10
> **WRDN said:**
> If you can't navigate the immediate selection screen after booting from the CD, then it sounds like a bad burn.

i can navigate the selection screen, that is why i posted saying i can use the arrow keys to go up and down....i can also press f1 f2 f3 f4 f5 f6, etc....and the proper screens pop up.


when i press enter, i can hear the CD starting to spin faster...nothing happens on the screen, that's all.

for the first reply...i think i tried to move the mouse around and nothing, but i am not sure...should the mouse move?

i will try that when i get home.

thanks guys.

---

### Post by WRDN on 2008-08-10
> **tomdlgns said:**
> i can navigate the selection screen, that is why i posted saying i can use the arrow keys to go up and down....i can also press f1 f2 f3 f4 f5 f6, etc....and the proper screens pop up.


when i press enter, i can hear the CD starting to spin faster...nothing happens on the screen, that's all.

for the first reply...i think i tried to move the mouse around and nothing, but i am not sure...should the mouse move?

i will try that when i get home.

thanks guys.

Sorry, I misread your original post.
When you boot from the CD, press the relevant key to edit the boot parameters, and remove the words "quiet splash" from the line that appears. Now, try booting again. Rather than a splash screen appearing, text will appear, and you will be able to see what errors appear and where it stops.

---

### Post by tomdlgns on 2008-08-10
what about the first option that says something along the lines of...

try ubuntu without installing it...

or something similar...

---

### Post by Sycron on 2008-08-10
You can use the first option if you want to try Ubuntu as if it would be installed on your HDD. This is posible by running ubuntu on your RAM memory. After you restart the settings that you've made will be lost.

---

### Post by tomdlgns on 2008-08-10
that is what i thought...so when i pressed enter on that option, nothing happened.

---

### Post by Sycron on 2008-08-10
How much ram do you have ?

---

### Post by tomdlgns on 2008-08-10
ok, this is confusing me...

i am at home so i can try any other suggestions that anyone might have.

when i press f4, 4 options come up, Enter doesnt seem to do anything.  the only place enter works is if i get into the launguage options, i can highlight English and press enter...then it taks me back to this splash screen.

the f buttons seem to be working, but i already posted that, it's not new information.

also, when i press enter on boot from first hard disk, that works, but obviously it isn't the OS i want...my drive does contain another OS, which i dont want, should i wipe the drive then try this again?

i was planning on wiping the drive with the unbutu install.

thanks.

---

### Post by tomdlgns on 2008-08-10
512mb

---

### Post by tomdlgns on 2008-08-10
test memory doesnt work
check CD for defect doesnt work

this is strange becuase when i highlight the option i want, i can hear the CD starting to spin faster.

hmmm

---

### Post by Sycron on 2008-08-10
It is possible that your CD wasn't burned corectly. You mush try it on other computer.

---

### Post by Inane_Asylum on 2008-08-10
[This page]("https://help.ubuntu.com/community/UbuntuHashes") has the md5 hashes for the Ubuntu .iso's.  Check your downloaded .iso against that list to see if it was a good download.  Bad downloaded .iso = bad burn = bad install

---

### Post by tomdlgns on 2008-08-10
yup, that what i tried after my last post....same problem on another PC...

boots to the splash screen, does nothing when i press enter.

do you think the download was bad or the burn was bad?

---

### Post by Sycron on 2008-08-10
> do you think the download was bad or the burn was bad?     YES, it have to.

---

### Post by tomdlgns on 2008-08-10
i am going to download from another server and i am going to burn it again.

---

### Post by WRDN on 2008-08-10
It sounds like a bad burn, but it could have been a bad download. As Inane_Asylum said, check the iso against the md5 hash list.
When downloading, its often best to do so using torrents, because, aside from the convenience of stopping/ starting them, once the file has downloaded, they will be checked against hashes. If part of the file is corrupt/ missing, those parts can be downloaded again. In contrast, if you downloaded a corrupt file from an FTP, you would have to download it all again.

---

### Post by Inane_Asylum on 2008-08-10
Make sure to compare hashes before you burn.  I've gotten a couple of bad downloads before...saved me a couple of CDs

---

### Post by tomdlgns on 2008-08-10
where do i find the md5 hashes for the downloaded .iso?

i probably need to extract it to a folder first?

---

### Post by tomdlgns on 2008-08-10
not sure if the first cd was a bad burn or a bad download...

i downloaded from another source and burned it again and it took me to the memory test when i pressed enter...last time it didnt do that.  i already deleted the old .iso, so i cant check the hash files for that .iso.

---

### Post by Inane_Asylum on 2008-08-10
Check [this page]("https://help.ubuntu.com/community/HowToMD5SUM#md5sum") for instructions.  You don't need to extract the .iso to check its hash, it checks the actual .iso file.

Depending on which OS you're using to download/burn the .iso, the instructions will be different.  From what I read, Linux usually comes prepackaged with md5sum.  I had to install it on windows, so that's all I know.

---

