---
title: "Check Temperature of Hard Drives"
date: 2009-10-27
forum: Programming Talk
---

### Post by EMCGFX on 2009-10-27
This is just small bash function to check all hard drives for temperature. I thought I will share it, it might help some one. You need to install hddtemp for this to work.

```
# Check Hard Drives Temperatures
function temp() {
  echo ''
  echo '-----------------------------------'
  echo '----- (Ubuntu)'
  sudo hddtemp /dev/sda
  echo '-----------------------------------'
  echo '----- (HD2)'
  sudo hddtemp /dev/sdb
  echo '-----------------------------------'
  echo '----- (HD3)'
  sudo hddtemp /dev/sdc
  echo '-----------------------------------'
  echo '----- (HD4)'
  sudo hddtemp /dev/sdd
  echo '-----------------------------------'
  echo '----- (HD5)'
  sudo hddtemp /dev/sde
  echo '-----------------------------------'
  echo ''
}
```

Note change and modify this function for your hard drives. Enjoy.

---

