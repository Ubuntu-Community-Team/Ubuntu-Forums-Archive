---
title: "Upgrade from 12.04.05 to 14.04 (LTS) via terminal doesn't allow me to log in"
date: 2014-12-20
forum: New to Ubuntu
---

### Post by v9003360 on 2014-12-20
Good morning everybody,

I am a newbie user regarding Linux OS so please forgive me if I cannot explain some things correctly. I will try though to explain you in details what I tried to do and and what was the result.

1. By using the following command on the terminal I tried to upgrade my system:

do-release-upgrade -p ([http://askubuntu.com/questions/502886/ubuntu-12-04-4-lts-to-14-04-1-lts-upgrade-no-new-release-found](http://askubuntu.com/questions/502886/ubuntu-12-04-4-lts-to-14-04-1-lts-upgrade-no-new-release-found))

2. The process started successfully. During the time that it was running some questions came up on the terminal asking mainly if I had to install something
new regarding a feature (e.g one of the them was the Samba file) or to keep the old one (old one = default action). For all questions like the previous I follow
the default action.

3. The process completed and at the end he proposed me to reboot the system to finilise the upgrade. After reboot, my system boots and reaches up to the log in
screen but when I am trying to enter my creds it doesn't log in.

As I have mentioned in the begging of my post I very new user in the Linux OS and now I do not know what exactly to do.

Thank you in advance

I would like to add some additional info

Before the upgrade I created a user (recovery as super user). By press Ctrl+Alt+F1 on the keyboard this is only user that is able to log in (neither root nor my usual logging in user). The detailed screen below appears:

Ubuntu 14.04.01 LTS computername tty1
computername login: recovery
Password:

Welcome to ubuntu 14.04.01 LTS (GNU/Linux 3.13.0-43-generic x86_64)
#

Thanks

---

### Post by DuckHook on 2014-12-21
If you had more experience with Linux, then there some things we could try involving some complexity. But since you are a new user by self admission, then I strongly, strongly suggest the following:

1. Using another computer, perhaps a friend's, download and burn the LiveDVD/USB from the Ubuntu site. The best way to download is by torrent, which has great error correction and has the best chance of giving you an error-free image.
2. Start up your computer with the LiveDVD/USB and backup the whole /home directory on your HDD to an external USB stick/disk. Make sure that the backup is good by checking if it is readable.
3. Reinstall a pristine 14.04 on you computer and then recover your important data from your backup.

This is the easiest and most painless way for a new user. It takes a little longer but has the huge advantages of simplicity and being well nigh foolproof.

*****IMPORTANT*****
In future, do **NOT** create a superuser or activate the superuser account. Ubuntu is based on *sudo*, which temporarily elevates you to superuser status only for the occasion needed to do your privilege-required command. By activating the superuser account, you not only compromise Ubuntu's security model, but you introduce wonky behaviour into the system, which may in fact be what caused your current difficulties.

Learn about *sudo* [here]("https://help.ubuntu.com/community/RootSudo").
Learn about the larger issue of security [here]("https://wiki.ubuntu.com/BasicSecurity").

PS. Do not use the -p flag for *do-release-upgrade*. In general, do not use flags unless you fully understand what they are supposed to do. In your upgrade case, you did not want "proposed" but the *standard* release.

---

