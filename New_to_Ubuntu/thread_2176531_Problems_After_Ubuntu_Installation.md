---
title: "Problems After Ubuntu Installation"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by christian3 on 2013-09-24
I recently installed Ubuntu on my laptop as my second operating system after Windows 7. To do so I deleted the HP_TOOLS partition on my hard drive. I did not realize that deleting this partition would disallow my access to BIOS settings from Windows. After installing I have had some strange behavior with my computer. Video from the internet has become incredibly slow to buffer, especially HD. I have also had problems with having multiple tabs of internet explorer open. Windows comes up with a graphics card error and shuts my computer down to avoid damage. Windows suggests accessing the BIOS setting to see if something is wrong. I believe it was something about ghosting? I really can't remember. I was hoping someone could help me with this as I am unhappy with the performance of my laptop now that I have Ubuntu on it. If anyone could tell me how to access BIOS another way to solve the problem that would be great. I also heard that I can somehow download HP_TOOLS again? I couldn't figure that one out. If anyone can offer any help it would be greatly appreciated, I want my laptop back.

---

### Post by mastablasta on 2013-09-25
you might be able to get the tools (search using your model or ask on HP forums. 

you've mentioned your problems appear in windows. why would they be ubuntu problem then? you should ask on windows forums. but here is what i would do in your place:
restore windows to factory settings. if this is even still possible since you can't get in the BIOS menu - but you might be able to restore it using recovery disk you created before messing with partitions. if you created image of the whole system you can just restore that.

otherwise it is easier to use mini partition tool and change the windows partition into secondary. then you can create primary at the end of where you put  ubuntu.

---

### Post by whitesmith on 2013-09-25
According to [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/Where-can-I-Download-HP-Tools-for-DV6-2113TX/td-p/288293](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-e-g-Windows-8-and-Software/Where-can-I-Download-HP-Tools-for-DV6-2113TX/td-p/288293) there is no available download for HP_TOOLS. Maybe you could find someone with the same make & model and copy from that machine. Or try the vendor. Or try this as a search query: "download hp tools host:hp.com". The horses are out of the corral, but making a backup is really the first thing to do with a new computer. Since you probably didn't do that, did a CD/DVD come with the PC? If so, what you need may be on that. Wish I could be of more help.

---

### Post by mastablasta on 2013-09-25
@whitesmith read the link you posted further down. they do have tools for download only they might indeed be called service diagnostics or similar.

---

### Post by christian3 on 2013-09-25
Thanks for the responses guys, I appreciate it. I think I will just have to restore my computer using a backup I have from quite a while ago. I wish I could have Ubuntu on my computer without having to delete HP_TOOLS

---

### Post by mastablasta on 2013-09-26
you don't need to delete hp tools. as i wrote you can transform the main partition (windows) into logical/secondary with that free tool. then you don't need to delete anything. i did it like that on an HP notebook i bough last year (though i admit i do not have UEFI laptop).

also hp tools should be available for download. they can also be installed (moved) to main disk, but that could be a bit more complicated.

also before doing anything i got my self a USB external disk and made bare metal bit by bit backup using redo backup (just in case something went wrong i could image the whole thing back)

---

