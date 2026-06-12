---
title: "Hi guys, I need advice on this snapd.socket"
date: 2019-06-04
forum: New to Ubuntu
---

### Post by swangnation on 2019-06-04
Hi guys,

when i ran ```
systemd-analyze critical-chain
``` i got the following ouput :

```
graphical.target @1min 3.625s
&#9492;&#9472;multi-user.target @1min 3.625s
  &#9492;&#9472;kerneloops.service @39.410s +518ms
    &#9492;&#9472;network-online.target @39.260s
      &#9492;&#9472;NetworkManager-wait-online.service @31.671s +7.588s
        &#9492;&#9472;NetworkManager.service @23.672s +7.985s
          &#9492;&#9472;dbus.service @20.529s
            &#9492;&#9472;basic.target @20.278s
              &#9492;&#9472;sockets.target @20.278s
                &#9492;&#9472;snapd.socket @20.272s +2ms
                  &#9492;&#9472;sysinit.target @20.209s
                    &#9492;&#9472;apparmor.service @17.862s +2.327s
                      &#9492;&#9472;local-fs.target @17.860s
                        &#9492;&#9472;run-user-121.mount @34.781s
                          &#9492;&#9472;swap.target @16.816s
                            &#9492;&#9472;dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap @16.751s +64ms
                              &#9492;&#9472;dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.device @16.711s
```

After reading [https://bugs.launchpad.net/snapd/+bug/1813365](https://bugs.launchpad.net/snapd/+bug/1813365)

It's pretty alarming i think. In any case in my critical chain output the snapd.socket has started. Not sure if this info helps but my ubuntu 18.04.2 is fully encrypted and has LVM setup. What would happen if i was to disable or remove the snapd.socket? If nothing major is going to happen, what is the command to remove it or disable it altogether?

Thanks in advance guys

---

### Post by LwIh%*7 on 2019-06-04
It would be in the line of the following:

```

sudo systemctl disable snapd.socket

```

See [http://landofnightandday.blogspot.com/2018/06/disable-snap-core-service-on-ubuntu-1804.html](http://landofnightandday.blogspot.com/2018/06/disable-snap-core-service-on-ubuntu-1804.html)[FONT=&quot]
[/FONT]
Though that being said disabling snapd might remove or disable other ubuntu packages if I'm correct.

---

### Post by Rubi1200 on 2019-06-04
One should always be careful before removing major parts that are integrated into the system.

Best to try first disabling to see what side effects, if any, there are.

That being said, as a test I removed snap and snapd entirely from a test install and could not find any problems after.

However, major caveat time, that was not an LVM encrypted install and I would not suggest removing if you have any doubts.

---

