---
title: "ubuntu 19 can't see my uefi installed windows 10"
date: 2019-05-08
forum: New to Ubuntu
---

### Post by pugtm on 2019-05-08
I've gone through all the steps in the uefi guide, I've turned off all the secure boot and hibernation. 
mint and ubuntu both refuse to even see the SSD that windows 10 is installed on. I'm using a Rufus made key set to UEFI mode. I can boot in fine to try Ubuntu it runs no problem, I just can't make it install alongside windows. 
any help would be greatly appreciated

---

### Post by Rubi1200 on 2019-05-08
Hi,

from the liveUSB please create a boot summary to post here (link in my signature). No repairs please just the summary. This will help us diagnose what is going on so we can offer advice on next steps.

Thanks.

---

### Post by pugtm on 2019-05-08
sorry how do i do that?

---

### Post by Rubi1200 on 2019-05-08
Boot the computer using the liveCD/USB you created and choose to Try Ubuntu.

You need to be connected to the internet for the next part.

Open a terminal on the desktop with CTRL+ALT+T and then run the following commands and wait for each one to finish before the next one:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

```
sudo apt-get install -y boot-info && boot-info
```

When the app opens choose the option Online report.

Paste the link here in a new post.

---

