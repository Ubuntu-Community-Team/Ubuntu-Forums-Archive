---
title: "Update from 18.10 to 19.04"
date: 2019-06-21
forum: New to Ubuntu
---

### Post by grenic on 2019-06-21
Good morning everyone. What is the best and safest way to upgrade my Ubuntu from 18.10 to 19.04?

---

### Post by mastablasta on 2019-06-21
backup your data files and click to upgrade. make sure you are on wired internet connection.

---

### Post by garvinrick4 on 2019-06-21
Materablaster gave you the easiest way to upgrade as you are a new user so
Upgrading as Mastablaster states it works fine or a fresh install.
i prefer to keep 18.04 for it still is the LTS until 20.04 so i would preferably make another partition
on drive to install 19.04 so you always have that LTS version as main install. You can also make
a /home partition to keep files that way all installs can access one /home instead of having a separate
/Home on every install. Is not hard according to how drive partitioned now just ask if you want to learn.
  If you want to wait until you are more comfortable with Ubuntu that is fine also. On these forums and you can
ask about anything and will find a user who will help you. Enjoy the Ubuntu Forums.

---

### Post by TheFu on 2019-06-21
Definitely begin with a full, know-you-can-restore, backup.
I'm not big on the GUI stuff, so next, I'd
sudo apt update
 - only continue if that worked without any warnings/errors
sudo apt dist-upgrade
 - only continue if that worked without any warnings/errors
reboot
 -  - only continue if that worked without any warnings/errors
sudo do-release-upgrade
 - Run this from a console, not over the network.  If there ar any errors before the do-release-upgrade command, STOP. Fix those first.  No upgrade has ever made a problem get fixed.

Or you can wipe the system completely and start fresh.

Like others have said, I much prefer to stay on LTS releases. I don't like having to upgrade the OS every 6 months.  New is the enemy of stable.

---

### Post by Impavidus on 2019-06-22
18.10 will reach end of life next month, so it's indeed time to upgrade. Install all available upgrades for your current release. Make sure you've got backups of your important files, but you should have those at all times anyway. Make sure you've got enough free space on your hard drive. You need several GB temporary storage. If you've got separate partitions for /boot, /var or whatever, make sure all of them have enough free space. It's best to have an Ubuntu 19.04 live disk ready, just in case something goes wrong. If something really bad happens (never happened to me, but the forum is full of stories about failed upgrades), use the live disk for a fresh install. Use the live disk to test 19.04 on your computer, just to make sure graphics and wifi work.

Read the [release notes]("https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes") and pay attention to known bugs, so you won't be surprised. Make sure you've got a reliable internet connection and power supply. Third-party sources have to be disabled, but this is done automatically. The upgrade will be fully downloaded before installation begins, so if your network fails halfway through, there isn't much of a problem. On my laptop I use power from the wall outlet, but have my battery fully charged, so even if power fails (happens here once per five years), installation can continue. Then start the release upgrade. I always use the GUI from the update manager. Read a book or watch a race on television, whatever you like. You may have to answer a few questions during the upgrade, so don't walk away for too long. It should take about an hour, multiplied or divided by a factor 3.

---

