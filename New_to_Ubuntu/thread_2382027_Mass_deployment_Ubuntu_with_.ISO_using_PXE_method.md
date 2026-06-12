---
title: "Mass deployment Ubuntu with .ISO using PXE method"
date: 2018-01-08
forum: New to Ubuntu
---

### Post by l917364825 on 2018-01-08
Hi fellows,
first of all, i want to ask how to do ./make_iso.sh like Portesu for Ubuntu 16.04 LTS?
which means in Porteus only need to use ./make command in file: /porteus/base, then can output  one overall porteus .iso file to use in USB or install another new machine. But now I have no idea how to use it in Ubuntu, help me plz.

Second, I want to mass deployment same setting, same content Ubuntu ISO to another new machine, did anyone have an idea how to do it using PXE method? 

Thx again.

Best regards.

---

### Post by sudodus on 2018-01-08
Do you want a general iso file? Then download it from the official Ubuntu web site,

[www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)

Or do you want to make a custom iso file, that contains your particular installed application programs? That is much more complicated, and there might be workarounds, for example to make

- an OEM installation, that you can clone.

- a persistent live system.

Depending on your answer, I can describe the relevant alternative with more details or other people will chip in and help.

---

### Post by l917364825 on 2018-01-08
Hi sudodus,
For example of what I want, in Porteus -> /porteus/base file, there are lots of .xzm, the only thing I have to do is edit it then package to a new .xzm, so when i ./make_iso.sh, i can get a new one overall .iso (including all  config setting and all installing tools).
It's diff. to Ubuntu, how can I do the same work in Ubuntu, make me easier to do mass deployment.

Thx for helping.

Best regards.


> **sudodus said:**
> Do you want a general iso file? Then download it from the official Ubuntu web site,

[www.ubuntu.com/download/desktop]("https://www.ubuntu.com/download/desktop")

Or do you want to make a custom iso file, that contains your particular installed application programs? That is much more complicated, and there might be workarounds, for example to make

- an OEM installation, that you can clone.

- a persistent live system.

Depending on your answer, I can describe the relevant alternative with more details or other people will chip in and help.

---

### Post by yancek on 2018-01-08
I'm not sure I'm reading your post correctly but, it seems like you want to create an iso of Ubuntu with your modifications and settings, additional software, etc.  If that's the case, either Systemback or Pinguy Builder should create that iso for you.  You would need to install anything you want before running either and that would include the Ubiquity installer.  I believe both Systemback and Pinguy are in the Ubuntu repositories.

---

### Post by l917364825 on 2018-01-08
Hi yancek,

Thank you, that's exactly want I want, I'll try it see what if work or not.
Thx again, and have a good day.

Best regards.

> **yancek said:**
> I'm not sure I'm reading your post correctly but, it seems like you want to create an iso of Ubuntu with your modifications and settings, additional software, etc.  If that's the case, either Systemback or Pinguy Builder should create that iso for you.  You would need to install anything you want before running either and that would include the Ubiquity installer.  I believe both Systemback and Pinguy are in the Ubuntu repositories.

---

### Post by Tadaen_Sylvermane on 2018-01-09
I'm interested in your workload. If it's all on a lan with full wired networking maybe LTSP could be the solution? I use it at home for media centers, works great. Single point of management vs managing 5 separate machines. It's designed for much bigger deployments than mine though.

---

