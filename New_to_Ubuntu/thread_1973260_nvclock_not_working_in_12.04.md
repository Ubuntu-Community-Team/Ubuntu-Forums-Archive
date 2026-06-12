---
title: "nvclock not working in 12.04"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by pkjm17 on 2012-05-04
After upgrading to 12.04, I've noticed I can't get the temperature of my NVIDIA card from the terminal, or any other option to do with nvclock.

For example, if I do nvclock -t, it says segmentation fault. Does Ubuntu 12.04 not support this anymore. It is an NVIDIA 8600GT card.

---

### Post by gordintoronto on 2012-05-04
I've never used nvclock. If you run Nvidia X Server Settings and click on the Thermal Settings tab, it should display the temperature.

In Conky, I use:
${execi 60 nvidia-settings -t -q GPUCoreTemp}

In a terminal, you can run:
nvidia-settings -t -q GPUCoreTemp

---

### Post by pkjm17 on 2012-05-05
Perfect. Thank you

---

