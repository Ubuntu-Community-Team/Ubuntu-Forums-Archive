---
title: "Unattended upgrades and third party repositories"
date: 2022-11-02
forum: New to Ubuntu
---

### Post by sash5 on 2022-11-02
Why unattended upgrades doesn't follow apt configuration and third party repositories need to be added in Allowed-Origins separately?
Because this makes the problem, that when you set apt priorities, to make an update from third party repository, unattended upgrades will ignore third party repository, and overwrite your packages. Is there a way configure unattended upgrades that it always use all apt repositories.

---

### Post by ian-weisser on 2022-11-02
No. You must configure each third party with an Allowed-Origins string.

Allowing every third-party to randomly update your system silently is considered risky. You won't have any warning before your system fails, and no idea what was recently updated. That makes troubleshooting harder and adds to the community support workload. 

That's why the developers who wrote Unattended Upgrades deliberately made adding/enabling new sources non-trivial.

A stock install of Ubuntu has enabled Unattended Upgrades ONLY for the -security pocket. If your packages are being overwritten, it's to mitigate a CVE.

---

### Post by sash5 on 2022-11-02
The reason why i wanted to change the priority was that there is a lot of snap packages, like firefox and keepassxc, and others that are not working correct because of the snap restrictions.
[https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22](https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22)

---

### Post by ian-weisser on 2022-11-02
Keepass and Gnome Extensions not working on Firefox snap is due to lack of native messaging support. It's a known issue.

See [https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/](https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/) for a proposed fix and how you can help test it.

Since it's a fix for the snap, implementation is not tied to Ubuntu release cycles. When it's ready, it can ship immediately. More testers = Ready sooner.

---

### Post by ian-weisser on 2022-11-03
> **ian-weisser said:**
> See [https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/](https://discourse.ubuntu.com/t/call-for-testing-native-messaging-support-in-the-firefox-snap/29759/) for a proposed fix and how you can help test it.

Update: The developer reported that the fix is now in Firefox Stable. Simply refresh the snap to get it.

---

