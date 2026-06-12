---
title: "Shared Resources"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by clementchiew on 2013-10-04
So I am just being bored and I have quite a monitors in my house but only one cpu. So I was thinking, is it possible to have several monitors hooked up to the cpu, and have several users running on it at the same time as if it were individual computers? This way, I can share the unused computer resources and save some money instead of buying more systems. Any applications to make it happen?

---

### Post by TheFu on 2013-10-04
[http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html) describes a 6 headed (heads = monitors) Linux setup. As long as your system still runs X/Windows, I think it should work.

Search for "multi-head" and "multi-seat" (with/without the dash) with Linux for more. [https://wiki.archlinux.org/index.php/xorg_multiseat](https://wiki.archlinux.org/index.php/xorg_multiseat)

Almost any device can be a remote desktop too, but they need to be some sort of network computer capable of running a remote desktop client - vnc, nx, spice and perhaps rdp.  Those tiny ARM Android devices or Raspberry Pi machines should work too, but I know that a 10" tablet that does work is still $200+ - hardly cheap.  At that point, why not get a netbook. Both of these defeat the purpose of your goal - reusing hardware for fun and profit!

In the old days, having 20 "x-terminals" connected to a single workstation happened all the time.  I attended a C and X/Windows  programming class where the entire class shared a single workstation, which had 10 "terminals" for the students.

---

