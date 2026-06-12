---
title: "Intel WLAN blinking mode with kernel 2.6.39"
date: 2011-05-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-05-02
Just a FYI: With kernel 2.6.39 the option to change the blinking mode of your Intel wireless LED needs to be set for the *iwlagn* module instead of the *iwlcore* module. However, if you do this, then kernel 2.6.38 will refuse to load the modules necessary for WLAN (as it doesn't understand the *iwlagn* module option).

Edit:

I just added these few lines to /etc/rc.local to reload the *iwlagn* module with the option I want (always on) in case I boot with 2.6.39.
```

# reload iwlagn with led_mode=1 for 2.6.39
ver=$(uname -r)
ver=$(echo $ver | cut -b 1-6)
if [ "$ver" = "2.6.39" ]; then
  modprobe -r iwlagn
  modprobe iwlagn led_mode=1
fi

```

---

