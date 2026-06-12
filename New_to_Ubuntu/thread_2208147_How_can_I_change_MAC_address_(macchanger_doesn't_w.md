---
title: "How can I change MAC address? (macchanger doesn't work)"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by gerry3 on 2014-02-26
How do you guys change your mac address when using Ubuntu?

Using 12.04 fully up to date.

I installed macchanger. But can't get it to work. Are there any other options for changing mac address?

Here's what I've tried for macchanger. worked on it for hours.
sudo macchanger -r wlan0
sudo macchanger -m xx:xx:xx:xx:xx:xx wlan0
  Both of these commands produce a change as confirmed with both ifconfig wlan0 and macchanger -s wlan0.
  But after I connect to a router--or after a few minutes--the MAC address always reverts back to default.
  Anybody know how to get macchanger working?

---

### Post by Herbon on 2014-02-26
FYI

[https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses](https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses)

---

