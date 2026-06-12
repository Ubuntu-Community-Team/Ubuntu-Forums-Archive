---
title: "nvidia driver cannot get correct resolution"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-11-06
I'm currently running Ubuntu 8.10 with an nVidia Geforce 9500 GT. According to the latest drivers released by nVidia, it should support the Geforce 9500 GT. It sort of does. I can get the compiz effects working (though I don't care for it) but all the resolutions I can get from the nvidia-settings are:

1360x768
1152x864
1024x768
800x600


and other irrelevant resolutions. I need a resolution of 1680x1050. No, changing the resolution in System -> Preferences -> Screen Resolution does not work.

My xorg.conf is in the file below:

[http://www.zantherus.com/xorg.conf](http://www.zantherus.com/xorg.conf)

Modeline, if necessary:

```
Modeline "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
```

Every time I run the nvidia-settings in the terminal, I get an 'out of range' error. I am 100% sure that my monitor can handle a 1680x1050 resolution; Hardy worked just fine and I was able to get the 1680x1050 quite easily there.

Any thoughts? Help? Thanks.

---

### Post by Tamlynmac on 2008-11-06
Read this and hope it helps.

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

---

