---
title: "swap"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by sutibun on 2012-07-20
Hi.

I have 1 GB ram and 120GB hdd i currently have set my swap to 10 is that ok?what you suggest?

---

### Post by FatFrog on 2012-07-20
Swap space should be set to around 1.5 to 2x the amount of physical RAM in your system
Large swap spaces can negatively impact performance. Unless you are using a lot of resource intense software, i would recommend making it 2GB and sticking with it...

---

### Post by papibe on 2012-07-20
Hi sutibun.

FatFrog's suggestion is sound. If you want to do read a little further on the matter, check this [article]("https://help.ubuntu.com/community/SwapFaq/").

Regards.

---

### Post by lukeiamyourfather on 2012-07-20
> **FatFrog said:**
> 
Large swap spaces can negatively impact performance.


Other than losing that disk space what negative impact is there?

---

### Post by sutibun on 2012-07-20
Hi. 
So you guys suggest what FatFrog said? 2GB? what i should put on the x mark tho?
vm.swappiness=X
Thanks

---

### Post by papibe on 2012-07-20
2Gb sounds a reasonable value.

Regarding swappiness: I would leave the value as it is, and test how the system behaves for a couple of days. If you are OK with your performance, there's no need to change it.

Just a thought.
Regards.

---

### Post by sutibun on 2012-07-20
> **papibe said:**
> 2Gb sounds a reasonable value.

Regarding swappiness: I would leave the value as it is, and test how the system behaves for a couple of days. If you are OK with your performance, there's no need to change it.

Just a thought.
Regards.

Its currently at 10.Default was 60 but now that i set it to 10 i see better performance. Ok i will and i will give some feedback in 2 days.
Thank You

---

### Post by anewguy on 2012-07-20
Also - IF it's a notebook, and IF you plan to hibernate, you'll need a little over twice your physical memory size.  Since you're being recommended to set the swap size to 2gb, it should probably do it for hibernation as well.

---

### Post by LordEager on 2012-07-20
[...]The only downside to having more swap space than you will actually use is the disk space you will be reserving for it.[...]

previous words describe excellently what they were saying in the Swap Faq page about "Linux ancient legends"  :-)

---

### Post by sutibun on 2012-07-21
Swap is set to 10 and it works fine :) 

Thanks anybody for the help this thread will close now :)

---

