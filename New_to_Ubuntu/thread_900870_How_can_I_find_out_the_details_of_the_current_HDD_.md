---
title: "How can I find out the details of the current HDD and what is a good new Drive?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-08-25
What command or option can I use to find out what HDD is already installed in a PC?  
Also, how can I tell which new HDD will be able to be fully taken advantage of with my current PC?

---

### Post by iaculallad on 2008-08-25
> **curiousnoob said:**
> What command or option can I use to find out what HDD is already installed in a PC?  
Also, how can I tell which new HDD will be able to be fully taken advantage of with my current PC?

You could use:

```
sudo fdisk -l
```

or

```
sudo lshw
```

---

### Post by Gregmond on 2008-08-25
As for what you can use: There was a cut-off of about 120GB from memory. Newer BIOS' can use greater than 120GB, older ones can't. To find out what drives your motherboard can use you would need to get the BIOS type/version and the motherboard info and check on the manufacturers website at a guess. Sometimes a BIOS upgrade will allow you to use all of a drive. My understanding is that most PC's will use the newer drivers (so long as you have the right connectors) but will be limited in size to the smaller capacity.

Note from memory this happened previously and the limit was 40GB, the newer limit is 120 or 128GB and I have no idea what the next limit is, probably round the 1TB mark.

---

