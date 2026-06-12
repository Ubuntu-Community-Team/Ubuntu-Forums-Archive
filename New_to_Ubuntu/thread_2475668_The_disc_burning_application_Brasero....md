---
title: "The disc burning application Brasero..."
date: 2022-06-03
forum: New to Ubuntu
---

### Post by Innernet on 2022-06-03
Good day.
When burning a file to a DVD;  this Brasero software does its thing displaying the track being burned and the percentage of completion.
Then, the 100% done ! shows up.  Yeeeeaaaah !
If you remove or turn off the compfuser, the disc will get screwed up to say the least.  So the 100% done is a lie. Then starts another 10 minutes of checking, or whatever it does, still, with the same prompt of 100% done. Same lie.     And then starts another 10 minutes of the checksum, always with the same "100% done", then another 5 minutes "finalizing"  with the same wrong prompt until the 'successfully burned" prompts and ejects the media.
How can a sharp brain that creates the software goofs misleading the user with WRONG prompts ?   It is not done until it is done !  Can anyone explain ?  Or not even the developer gives a sheet ?
By the way; the 'fast blanking' option seems to be reversed. Not checking it seems to be the fast option.  And, after blanking, it self ejects.  Not exactly the process to start burning after erasing :(

---

### Post by poorguy on 2022-06-04
I recommend installing and using Xfburn you can install using the terminal or using the Muon Package Manager.

Open the terminal and copy and paste this command then press enter and then enter your password if ask and pres enter.

```


sudo apt install xfburn


```

Restart the computer and look in the menu under*** accessories ***or*** sound and video.***

---

### Post by guiverc on 2022-06-04
You haven't provided any release details, but Lubuntu [doesn't provide any DVD burning software on the latest release]("https://discourse.lubuntu.me/t/dropping-trojita-k3b-fcitx-from-lubuntu-jammy-22-04-seed/3044") (Lubuntu 22.04 LTS) and even before that provided `k3b` and thus was tested mostly with that, and not `brasero`, eg. you can read the Lubuntu 20.04.4 LTS' [manifest]("https://cdimage.ubuntu.com/lubuntu/releases/20.04.4/release/lubuntu-20.04.4-desktop-amd64.manifest") ti see what is included, but in your case I'd check how you installed it & look for clues (*it's not included with Lubuntu*).

I'm assuming Lubuntu given you've put this in the Lubuntu *flavor* area of UF, and 20.04 based on your stated *distro*.  I would expect `brasero` to work, but I rarely use it (*for sure can't remember the last time, I rarely write DVD/CDs but I'd normally use `k3b` or `xfburn`)*

---

