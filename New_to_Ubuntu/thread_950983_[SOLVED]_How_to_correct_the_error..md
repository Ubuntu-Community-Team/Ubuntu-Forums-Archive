---
title: "[SOLVED] How to correct the error."
date: 2008-10-17
forum: New to Ubuntu
---

### Post by ellalan on 2008-10-17
Hi
I have done something wrong and now I am unable to get in to sources.list to delete the last entry which produced this error message.
I was trying to add the medibuntu to the sources list. Could someone tell me how can I get in to sources list please.
OS-Hardy 8.04.

---

### Post by ezramorris on 2008-10-17
> **ellalan said:**
> Hi
I have done something wrong and now I am unable to get in to sources.list to delete the last entry which produced this error message.
I was trying to add the medibuntu to the sources list. Could someone tell me how can I get in to sources list please.
OS-Hardy 8.04.

Hi,
It looks like you have typed a terminal command into sources.list. Please post your sources.list file. Thanks.

---

### Post by sisco311 on 2008-10-17
open a terminal and post the output of:
```
cat /etc/apt/sources.list
```

EDIT: i'm slow:)

---

### Post by cariboo on 2008-10-17
Can't you press Alt-F2, then type:

```
gksu gedit /etc/apt/sources.list
```

and then edit /etc/apt/sources.list, or did you break sudo also.

Jim

---

### Post by ellalan on 2008-10-17
Thank you all, its all fine now. I followed the cariboo907's instructions and edited. Thanks again.

---

### Post by sisco311 on 2008-10-17
cool.
to add the medibuntu repos run:
```
sudo apt-get update
```
and:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```type "yes" (without the quotes) to accept the package.

---

