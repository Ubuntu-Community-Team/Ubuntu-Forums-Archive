---
title: "installing ubuntu from a usb ...not working!"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by shotgun sam on 2012-03-30
Hi there first post....So its been quite frustrating trying to solve this problem after following all the instruction on the web page for installing the ISO for ubuntu 11.10 onto a USB stick it just won't boot...

As I run a acer aspire one d257 which is a netbook I have no cd drive ...I used the Linux Live USB creator to make the USB pen drive which went sucessfully but when I try to boot from it ,it will just hang on a black screen with a white cursor flashing on and off in the top left corner.

I have configured the bios correctly with the usb fdd as the first boot priority and everything..usb ffd is the drive that recognizes the usb memory stick I have stuck in.

Ofcourse did some googling and someone solved a similar problem see link  post 67
[http://ubuntuforums.org/showthread.php?t=1654004&page=7](http://ubuntuforums.org/showthread.php?t=1654004&page=7)

however the type of reconfiguring doesn't seem possible in my BIOS settings because it has extremely limited functionality ...

He seemed to think it was a problem to do with the fact that his bios recognized the usb stick as a FDD,which is what mine is doing as well..

Any help with be appreciated .

In hope rather then expectation ..

---

### Post by wildmanne39 on 2012-03-30
Hi, I recommend try what is in this link to set a nomodeset option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by shotgun sam on 2012-03-30
I am not even able to get to the ubuntu boot screen.

---

### Post by kdane4 on 2012-03-30
hi,

I had the same experience before on my kingston usb. Tried unetbootin, lili,.,still same problem. I found out that certain usbs does this since I tried again on a sony usb and it worked.. Im guessing not all usb drives can boot especially cheap ones.

---

### Post by ajms1989 on 2012-03-30
Perhaps there is problem with your USB and slightly chances of unsuccessful procedure of making your USB ubuntu bootable. 

[COLOR="Black"]Try these two methods:[/COLOR]
Replace your USB with a different USB
Try different software to make your USB ubuntu bootable. 

Let us know the results.

Thanks
Oliver

---

### Post by ravinfy on 2012-03-30
I recall I had the same problem once or twice and was guessing I did something wrong. 

In addition to the ideas that other users provided here, how about 
- Using a different USB slot with each attempt? 
- Ensuring that the Boot sequence is appropriate? (I remember juggling around a few of these options and finally getting it to work for my 12.04 LTE installation) 

Hope one of these ideas work for you. 


[FONT=Tahoma]*-r@v!*[/FONT]

---

### Post by shotgun sam on 2012-03-30
I don't see how this will work but I will try to make another pendrive using a different usb stick.

The one I used before was a verbatim which was 8 GB  which I think should have been adaquat.

---

### Post by Bill Z on 2012-03-30
Hay!!  I have an Acer Aspire One NetBook that I have loaded both Ubuntu 11.10 and 11.4 using USB.  

I had seen on the forums that there are times when using USB drives (like SanDisk and Kingston) that there are problems.  The problems seem to be around any logic in the USB drive that never gets overwritten by the USB Creator.

I used a micro SD by Kingston.  Seems these don't have the logic in them.  Worked just fine.  Maybe was just a little slow but it did work.

Find a cheap USB drive.  One without any special speed packages in it and I bet it will work.

---

### Post by shotgun sam on 2012-03-30
I am glad to report that it did work after all so thats good I used a PNY USB drive which was 4G so I guess some sticks work and some don't the 8G verbatim USB stick was the one that didn't work for me.

Anyhow thanks for the advice everybody...

---

### Post by wildmanne39 on 2012-03-30
Hi, I am glad you got it working, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by dupek64 on 2012-03-30
I have 8G Sandisk and 8G Lexar. Never had any problems with. I use Unibutin. While creating, I do not specify a distro. Go down to folder with ISO. Most of the time, I do quick format with FAT32

---

### Post by shotgun sam on 2012-03-31
It seems that some USB sticks differ from others I have been wondering if performing a checksum on the disk or files in the disk is possible and if so would it help identify the reason?

---

### Post by kdane4 on 2012-03-31
Glad to hear our advice worked and you got it working. I for one also want to know how to easily determine USBs that can boot or not. In the meantime, I just avoid not so well known brands in favor of popular ones just to make sure its working. But I sure want to know the answer to that queestion!! :)

---

