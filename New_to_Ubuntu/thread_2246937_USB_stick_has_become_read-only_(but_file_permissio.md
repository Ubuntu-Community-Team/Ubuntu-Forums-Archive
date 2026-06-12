---
title: "USB stick has become read-only? (but file permission is read+write)"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by amanchesterman on 2014-10-04
Hi all, I have used various flavours of Ubuntu for several years now and I'm currently using Xubuntu 14.04.1. I have run into a problem with a USB memory stick from which I cannot delete files, and since I'm a little confused about file permissions I'm posting this in the 'new to Ubuntu' section. I hope someone can help to explain what is going on.

The situation is that I have Xubuntu running as the sole OS on a laptop on which I am the sole registered user. Roughly once a week I copy various data files on to a couple of USB memory sticks as one way of keeping a handy backup. (I also use a backup program.) I use Thunar to do the copying, dragging and dropping the files. When I want to back up later versions of the files I delete (shift+del) the former versions from the USB stick first.

I've just done that with one memory stick and it worked fine, as usual. With the other, when I came to delete the files I got an error message: 'error removing file: read-only file system'. I've tried repeatedly and I keep getting the same error. This memory stick has behaved perfectly in the past and does not appear to be damaged.

What has got me puzzled is that Thunar says that I, as owner, have read+write permission for all the data files on the USB stick, and the terminal output says the same. What's more, if I drag and drop the files back from the memory stick into a vacant folder on my hard disk, I can delete them without problem: it's only while they are on the USB stick that they can't be removed.

So my questions are:
1) If Thunar and the Terminal think that I have read+write permission for the files, why does Thunar say that the file system on the memory stick is read-only?
2) Is this a symptom that the memory stick is failing and should not be used any more?
3) If the answer to (2) is yes, how can I delete the files from the stick before throwing it away?

Thanks in advance for your help!

---

### Post by buzzingrobot on 2014-10-04
If you need the files on the USB, copy them off and use Gparted to repartition and reformat the stick.  Getting read-only notices can be a response to filesystem damage.

On the other hand, I've had USB's just crawl away and die, beyond repair.  Last week, one came physically apart.

---

### Post by Impavidus on 2014-10-04
I once had your symptoms too. When opening a particular file on the usb stick I got an I/O error and the stick was remounted read only. Permissions are independent of that, so there were still write permissions, but I couldn't use them. Remounting as read-write worked fine, but as soon as I accessed that particular file I got a new I/O error and it was read-only again. I managed to delete the problematic file and the usb stick resumed normal operations for a while. Then I stored another big file on the drive and as soon as I tried to read it, the I/O errors returned. I could read 213 pages of the document and then it always stopped. Just leaving the file there and never touching it ensured reliable operation. Clearly a case of broken hardware. Of course, I bought a new (and 16 times bigger) usb stick.

---

### Post by amanchesterman on 2014-10-05
Thanks guys. I hadn't realised that file permissions are independent of the I/O state of the disk. I'll wipe the disk and bin it, it's obviously reached EOL.

---

