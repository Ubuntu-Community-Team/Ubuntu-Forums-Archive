---
title: "I really need some help with Ubuntu Crashing"
date: 2020-06-07
forum: New to Ubuntu
---

### Post by h0lyt0ast on 2020-06-07
It seems to be random, but generally 10 or so minutes of up time in (Ubuntu fresh 20.04 install as of 6-7-2020) it hard locks and does not log anything. I'm not sure how to go  about looking in to this as I'm new to Linux. Google said check the log application but nothing stands out.
I thought it might be the hardware, but after playing games and streaming it in windows for 4-5hours I don't get any hard locks/bsod. 

My only other concern is I have a 5700xt, do i need to install something for it to work properly ? Additional drivers, the application, and some googling say no. 

Im on regular ol ubuntu 20.04
gpu is 5700xt
cpu amd ryzen 7 2700x
32g ram @ 3000


Any help would be appreciated and thanks in advance

-Toast

---

### Post by h0lyt0ast on 2020-06-07
I solved my own issue, and wish i would have seen this on friday. 

I kept playing around with my system and noticed that it kept crashing with things related to vulkan. 

i removed the installed vulkan drivers from Ubuntu and added in oibaf's 


sudo apt purge mesa-vulkan-drivers vulkan-utils
sudo apt-add-repository ppa: oibaf/graphics-drivers
sudo apt update && sudo apt install mesa-vulkan-drivers vulkan-utils

this fixed my issue for now.

---

### Post by daniewicz on 2020-06-07
Glad you are up and running!

---

