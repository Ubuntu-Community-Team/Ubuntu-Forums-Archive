---
title: "Problems installing CUDA on Ubuntu 16"
date: 2017-03-19
forum: New to Ubuntu
---

### Post by mic3 on 2017-03-19
I installed CUDA with

    > 
    `sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb`
    `sudo apt-get update`
    `sudo apt-get install cuda`

I then tried > `sudo add-apt-repository ppa:graphics-drivers/ppa` and > `sudo apt-get install nvidia-current`

After typing > `dpkg -l | grep -i nvidia`, I see `nvidia-375` and `nvidia-378`

However, I then tried "nvidia-smi" and got

    > WARNING:root:could not open file '/etc/apt/sources.list.d/osmosa-ubuntu-audio-recorder-xenial.list'
    nvidia-smi: command not found 

I also restarted, but "nvidia-smi" gave the same error

Can anyone help with this?

---

### Post by mic3 on 2017-03-20
bump

---

