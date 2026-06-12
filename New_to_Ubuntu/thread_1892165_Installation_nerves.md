---
title: "Installation nerves"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by joshswain123 on 2011-12-07
I'm running Lubuntu (11.10) off a live CD to try it out, and I'm having trouble installing software (lubuntu-restricted-extras) using both Terminal or Synaptic. My question is, is this just a LiveCD issue, or will it carry over into a permanent installation?

---

### Post by nothingspecial on 2011-12-07
Did you update your live system first?

```
sudo apt-get update && sudo apt-get install lubuntu-restricted-extras
```

---

### Post by bluexrider on 2011-12-07
it will not carry into permanent installation.

---

### Post by 2F4U on 2011-12-07
And what problems did you have? Error message?

---

### Post by seawolf167 on 2011-12-07
> **joshswain123 said:**
> I'm running Lubuntu (11.10) off a live CD to try it out, and I'm having trouble installing software (lubuntu-restricted-extras) using both Terminal or Synaptic.

As posted above, first try updating the lists, then installing the package (ensure you are connected to the internet)

```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```

If you are receiving a specific error message, please post that here so we can see it and further help.

> **joshswain123 said:**
> My question is, is this just a LiveCD issue, or will it carry over into a permanent installation?

Any changes you make in the LiveCD environment will have no effect on a clean installation of LUbuntu from said LiveCD environment.

---

### Post by joshswain123 on 2011-12-09
Thanks for the help, all! I went ahead with the installation because I wasn't worried so much about things not working off the CD. My intent was to only test off the CD, and then do a permanent install. Thanks again!

---

