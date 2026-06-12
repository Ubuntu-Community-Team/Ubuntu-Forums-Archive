---
title: "New motherboard, old windows doesn't boot, need the files on the HD"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by joker0205 on 2013-11-30
So, just finished building my computer, using my old HD and new mobo, graphics card, CPU and RAM, and Windows isn't starting. So I have booted Ubuntu 12.04.3 from an USB and I want to recover my files (mostly pics and vacation videos) from my HD, but I'm kinda stuck.. Used gparted to check out the partitions and this comes up: 

So I looked it up and I read that I had to write "sudo ntfsclone --save-image --rescue --output image_file.img /dev/sda2" in the terminal, but then it seems to want to create the image on the USB, and then cancels due to lack of space. I thought that maybe I could redirect it to and external drive, but I don't know how to do that. Confused about what it really does too..

Basically, I want to know if I can get to the files from windows and copy them to the external drive so I can wipe my HD and reinstal windows and Ubuntu.

Any suggestions?

Thankful for answers!

---

### Post by coffeecat on 2013-11-30
First thing: please don't drag and drop images into the message editor. It doesn't work &#8211; all you do is to trigger a firefox bug and insert masses of base64 code into your post. Please use the manage attachments button under the advanced message editor or the paperclip icon to upload images to your post. I've edited out the base64 code because its presence can cause some people's browser to freeze.

Second. If you only want to copy files, you don't need to clone the Windows partition. You should be able to mount it from the file manager in the live session and drag and drop copies to a USB drive. But maybe gparted is saying something about the health or otherwise of the partition. See if you can post that image and we'll take it from there.

---

### Post by joker0205 on 2013-11-30
Oh, sorry! I think I figured the problem out, did what you wrote about mounting and it worked! Thanks!

---

