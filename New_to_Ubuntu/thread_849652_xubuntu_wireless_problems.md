---
title: "xubuntu wireless problems"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by likebikes on 2008-07-04
hi
I have an old Tecra 8000 with 128mn of ram running xubuntu 8.04. i have a buffalo WLI-CB_G54L pcmia card. i have been struggling the past two years trying to get this card going with different flavours of linux. i now think i am very close but need help. The power light on the card is green (good sign!) and the link like flashes on and off. I am using ndiswrapper with xp driver from buffalo CD. I can see neighbours APs and mine. despite choosing WPA and giving correct key i still get no connection. help would be gratefully appreciated

---

### Post by braddcadd on 2008-07-14
Did you get this to work?  If not, have you tried requesting the IP address from the command line (assuming you are DHCP)?

What does this give:
```

route -n

```

This should request an ip address (substitute for wlan0 if needed):
```

sudo dhclient wlan0

```

---

