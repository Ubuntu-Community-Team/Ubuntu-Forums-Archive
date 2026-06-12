---
title: "Can't install Ubuntu?!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by lockdown1097 on 2008-06-12
After loading and getting on successfully with Ubuntu on my laptop. I recommended it to a friend.
 The problem is with my friends computer. It went wrong and they decided formatting it was the best option. But now they don't have an operating system on the desktop! When you start it up it goes to the login screen and when you try and login it asks you to validate windows, but they don't have the windows cd so I mentioned Ubuntu.
I made a live iso cd using my laptop, booted up the other comp using the live cd. I've got to the main screen of Ubuntu. The one that asks you if you want to install, test etc.
When you try and do anything a box pops up and says I/O error, Error reading boot CD. The only option it gives me in this box is reboot. After clicking reboot I loads back up to the same screen and I have the same problem.
Can anyone help here please?!

---

### Post by bumanie on 2008-06-12
Check the integrity of the live cd with 'check cd for errors' and do a md5 checksum on the download to ensure it downloaded correctly. You could otherwise try the 'alternate install cd' which is text based rather than a live cd and often installs if the live cd doesn't.

---

### Post by forger on 2008-06-12
you say you made a live iso cd.. how? maybe that's the problem, you could try downloading the ubuntu live cd

---

### Post by avtolle on 2008-06-12
And, given the difference between drives, burn the iso for your friends' desktop on a CD-R, at the lowest possible speed (4x is what I use).

---

### Post by lockdown1097 on 2008-06-12
I downloaded the live cd from ubuntu and burnt it on to a cdr as an iso image. Same way I did it on my laptop and it worked fine.
I tried the "check cd for defects" option but it just tells me to reboot again? I am very confused:confused:

---

### Post by forger on 2008-06-12
you could try and burn another cd/dvd at very low speeds (1x or 4x recommended)

---

### Post by Tomatz on 2008-06-12
Does the pc you are installing to have less than 512 ram?

If so you will need to download the "alternate iso" (text based like the xp installation cd) you can get it from the main ubuntu download page.

If you do have enough ram you may want to try it anyway as using it solves most problems when the live cd installation fails.

;)

---

### Post by melrom on 2008-06-12
> **bumanie said:**
> Check the integrity of the live cd with 'check cd for errors' and do a md5 checksum on the download to ensure it downloaded correctly. You could otherwise try the 'alternate install cd' which is text based rather than a live cd and often installs if the live cd doesn't.

Here's some more info about the md5 sum:

Here is Ubuntu documentation that explains what checking the MD5 sum is:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


also, here are the hashes for the different isos:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by lockdown1097 on 2008-06-12
> **Tomatz said:**
> Does the pc you are installing to have less than 512 ram?

If so you will need to download the "alternate iso" (text based like the xp installation cd) you can get it from the main ubuntu download page.

If you do have enough ram you may want to try it anyway as using it solves most problems when the live cd installation fails.

;)
I can't find the text based "alternate iso" do you have a link?

---

### Post by Tomatz on 2008-06-12
Go here:

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Then under the **green text** saying *"start download"* **check the check box** with the text next to it that says:

> Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

;)

---

