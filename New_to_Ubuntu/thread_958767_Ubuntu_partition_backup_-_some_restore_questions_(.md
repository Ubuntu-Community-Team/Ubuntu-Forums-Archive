---
title: "Ubuntu partition backup - some restore questions (using Ghost)"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by mingle on 2008-10-25
Hi,

I'd like to create an image backup (using Norton Ghost 11.0) of my Ubuntu partition, which I'm fine with, but I have a couple of questions regarding what I need to do to restore the image with the correct swap-partition, etc.

I'm moving my system to a bigger hard drive and I currently have Win XP on the first partition, my data files on the next (extended NTFS) partition, then Unbuntu 8.04 on the third partition and finally a small partition for the Linux swap-file.

When I restore my Unbuntu image, is there anything special I need to do to make sure it ends up on the correct partition and can find the swap file partition correctly?

Would it be possible to put the swap file on the same partition as my main Ubuntu install, or is this a big no-no?

Cheers,

Mike.

---

### Post by jerome1232 on 2008-10-25
You can make a swap file, you essentially create an image full of zeros with dd then format the image as swap. Then tell Ubuntu to mount the disk image as swap.

[https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file](https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file)

edit: It looks like you can't hibernate the computer when using this method for swap. And it's better explained above the spot I linked initially [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by Duck2006 on 2008-10-25
Not use Norton Ghost 11.0, with linux part image will do what you want for backing up. If you want a swap partition in your ubuntu / root partition use a swap file to do this with.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

