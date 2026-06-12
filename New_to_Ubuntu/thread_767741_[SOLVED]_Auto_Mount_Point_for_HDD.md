---
title: "[SOLVED] Auto Mount Point for HDD"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by stalkier on 2008-04-25
I am having the same trouble many people are with the new upgrade. I would like to have my NTFS partition mount automatically when the system boots. How would I go about doing this? I am still a semi-noob. (I have zero retention with commands etc) Thanks for the help.

---

### Post by crjackson on 2008-04-25
> **stalkier said:**
> I am having the same trouble many people are with the new upgrade. I would like to have my NTFS partition mount automatically when the system boots. How would I go about doing this? I am still a semi-noob. (I have zero retention with commands etc) Thanks for the help.

```
sudo apt-get install ntfs-config
```

If that doesn't install the configuration program you need then look in the synaptic package manager for ntfs config and install it from there.

---

