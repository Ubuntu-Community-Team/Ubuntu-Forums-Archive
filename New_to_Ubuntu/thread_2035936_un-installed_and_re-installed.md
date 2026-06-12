---
title: "un-installed and re-installed"
date: 2012-07-31
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-31
After facing a trouble, 2 days ago I decide to give a **BeatBox Music Player** a try
 Generally, when the it runs for the first time, it will required us a **library**... so, I lean it to my **Music Library**, which stored in **external HDD** ... this time it do the scan.
 After about 2~3 minutes, my electricity was broke-down. But it backs 1~2 minutes later.
 So, I turn on back the lapppie and re-do the scan.
 Since I found no **the Left side of Top Panel** options &#8230; so I used a "**Gear**" symbol (**placed on Top-Right**) > **Preferences** > and pointed where my **Music Library** is stored ... but this time, it do nothing.
 Why?
 And I re-checked the setting and found that my **Music Library** still set as default folder **(/home/***/Movie)**. So, I re-setting it to **External_HDD/Sounds/Lossy**.
 But it still do nothing. So I re-checked the setting and found there is no change in my library setting.
 This problem repeated on and on and on and on. Until I decide to:
 > $ sudo apt-get remove --purge beatbox
Clear all the Janitor with **Ubuntu Tweak,** **re-start the lappie**, open the terminal, type:
> $ sudo apt-get update && sudo apt-get install beatbox But the newly installed BeatBox still contains previous version's library.
 Why?
 How can I make **the newly installed BeatBox** is a **100% newly installed BeatBox**?

---

### Post by idoitprone on 2012-08-01
sudo apt-get reinstall beatbox

---

### Post by NikTh on 2012-08-01
Hi , 

maybe some file or folder hidden (from your eyes). Open nautilus and press Ctrl+H to see all hidden files & folders. Search something from BeatBox. 

Reinstall BeatBox with command @idoitprone gave you. 

Thanks

---

