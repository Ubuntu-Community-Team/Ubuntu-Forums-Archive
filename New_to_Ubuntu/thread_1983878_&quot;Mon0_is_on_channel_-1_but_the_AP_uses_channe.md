---
title: "&quot;Mon0 is on channel -1 but the AP uses channel X&quot;"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by SebastianWeigman on 2012-05-20
So I am a total been when it comes to Linux.. But I am using a burned to disc 12.04 for aircrack as backtrack on VMware didn't work with my adapter, or burn to disk correctly.  So now I am using my atheros card within my laptop regularly.  All works well besides the mon0 error.  I tried ALL of the patch fixes but whenever I try to 'make' or 'sudo make install' on the compat-wireless updated versions, I get multiple 'make' errors.. Is it because aircrack-ng is read only?  Please help.. Note that all patches (maxim and the like) will not successfully install..

---

### Post by sam_delta on 2012-05-20
as far as i remember you set the channel you want to hear to when launching airodump (after you set the interface to monitor mode).

e.g.
```
  airodump-ng -c <channel> -w <out_file> --bssid <AP_MAC> mon0 
```

sam

---

### Post by cariboo on 2012-05-20
Aircrack is no longer in the repositories, so we no longer support it here. Your best bet for support is the [BackTrack Forum]("http://www.backtrack-linux.org/forums/forum.php?"). Thread Closed.

---

