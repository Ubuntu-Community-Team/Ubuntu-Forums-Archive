---
title: "Browser stuttering"
date: 2019-06-24
forum: New to Ubuntu
---

### Post by axel300 on 2019-06-24
Hello all, I'm very new to Ubuntu (Kubuntu) and just installed it yesterday as a dual boot along with windows 10.

Everything works pretty good so far and all in all it's a very nice experience
My only issue (so far) is that the Firefox browser is always stuttering when I'm scrolling the web or when I watch a Video (youtube) also tried it with other browser, but still the same result.

I found this video on [reddit]("https://www.reddit.com/r/Ubuntu/comments/afzy99/scrolling_stutterlag_on_ubuntu_1804_1810/"), in which you can see pretty good what's happening. The reddit comments weren't that helpful and I bet, here is the better place to ask for advice.

Here's my output of nvidia-smi

+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.56       Driver Version: 418.56       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1080    Off  | 00000000:01:00.0  On |                  N/A |
| 36%   54C    P5    19W / 210W |    659MiB /  8118MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1124      G   /usr/lib/xorg/Xorg                           361MiB |
|    0      1299      G   /usr/bin/kwin_x11                             66MiB |
|    0      1307      G   /usr/bin/krunner                              14MiB |
|    0      1310      G   /usr/bin/plasmashell                          87MiB |
|    0      3651      G   ...el/.local/share/Steam/ubuntu12_32/steam    26MiB |
|    0      3660      G   ./steamwebhelper                               2MiB |
|    0      8884      G   ...-token=F56855A4CC4B9C4D3F25D608A114D6DF    57MiB |
|    0     10920      G   ...uest-channel-token=16440953646656553182    15MiB |
|    0     14519      G   /usr/bin/plasma-discover                      23MiB |
+-----------------------------------------------------------------------------+

sorry that the format is kinda messed up.

I'm very thankful fort every advice

If you require any additional information, just drop me a note here.

Thank you!

---

### Post by uRock on 2019-06-24
Hello and welcome to the forums.  Have you checked the box for Smooth Scrolling in Firefox's preferences?

---

### Post by axel300 on 2019-06-24
Thank you!

Yes smooth scrolling is enabled. I think it has nothing to do with the scrolling itself, seems like a Graphical Problem? As YouTube videos have the same issue
Thanks for the hint!

---

