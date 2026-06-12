---
title: "Using ieee80211_radiotap.h fails"
date: 2010-10-08
forum: Packaging and Compiling Programs
---

### Post by fecjanky on 2010-10-08
Hi,

My problem is that I can't compile successfully the following code .(I use gcc compiler)
The used include directories   (because net/ieee80211_radiotap.h doesn't exist in /usr/include as so these architecture dependent headers) :
- /usr/src/linux-headers-2.6.32-24-generic/arch/x86/include
- /usr/src/linux-headers-2.6.32-24-generic/include

```

#include <stdio.h>
#include <stdlib.h>
#include <net/ieee80211_radiotap.h>

int main()
{   
    return 0;
}



```I get the following errors and warnings:
```

/usr/src/linux-headers-2.6.32-24-generic/include/linux/kernel.h|664|warning: #warning Attempt to use kernel headers from user space, see http:|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|7|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_le16’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|12|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_le32’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|17|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_le64’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|22|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_be16’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|27|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_be32’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|32|error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘get_unaligned_be64’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|37|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|42|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|47|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|52|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|57|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/linux/unaligned/access_ok.h|62|error: expected ‘)’ before ‘val’|
/usr/src/linux-headers-2.6.32-24-generic/include/net/ieee80211_radiotap.h|65|error: expected specifier-qualifier-list before ‘u8’|
/usr/src/linux-headers-2.6.32-24-generic/include/net/ieee80211_radiotap.h||In function ‘ieee80211_get_radiotap_len’:|
/usr/src/linux-headers-2.6.32-24-generic/include/net/ieee80211_radiotap.h|258|warning: implicit declaration of function ‘get_unaligned_le16’|
/usr/src/linux-headers-2.6.32-24-generic/include/net/ieee80211_radiotap.h|258|error: ‘struct ieee80211_radiotap_header’ has no member named ‘it_len’|
||=== Build finished: 14 errors, 2 warnings ===|

```The last error message is also quite interesting, because the function is where the it_len member is accessed is right after the definition of ieee80211_radiotap_header, so I don't have any idea what could be wrong.
Could someone please help? 
Thanks in advance!
Regards,
Ferenc

---

