---
title: "Hardware failure in Ubuntu 11.10"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by tendaic on 2012-02-07
I have been using my Ubuntu (dual booting with Windows) for close to six months now on my HP ProBook 6550b and everything has been going well. Starting last week I noticed I can no longer use USB mass storage devoces or memory cards. The media or memory card would would appear in the file manager but when I click on it to display contents it would say: Unable to mount XXX. Not authorised. I have also noticed that I no longer have audio output of any kind and the WiFi toggle button no longer responds, Besides the ordinary Ubuntu updates the only applications I have added recently are Squid and Cairo Dock. Please help if anyone knows whats going on.

---

### Post by crf on 2012-02-07
I don't think my following suggestion will solve the problem. But it might rule out whether it is some mis-configuration limited to your user account.

Try creating a new user. Just for testing purposes.
[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Then log in as this new user and see if your usb stuff works.

If it does, it means that somehow (and likely not due to your fault) a user setting has changed, and is disallowing mounting and unmounting of disks.

---

