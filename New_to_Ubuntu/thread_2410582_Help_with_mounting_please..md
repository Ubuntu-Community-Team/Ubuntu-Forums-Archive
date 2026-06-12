---
title: "Help with mounting please."
date: 2019-01-17
forum: New to Ubuntu
---

### Post by mrfdes on 2019-01-17
Hi, 
I installed lubuntu 18.10 recently, but there seems to be a problem.
Whenever I click on the name of my HDD in the file manager I get "Can't mount file" and when I shut that another window says "The path is not mounted".

I have taken 2 screenshots, one to show what lsblk says, and the other one to show what is in file manager.
When I click on "File System", it does open, but what about my HDD itself?

Any help will be much appreciated.
[ATTACH=CONFIG]282223[/ATTACH]

[ATTACH=CONFIG]282224[/ATTACH]

---

### Post by TheFu on 2019-01-17
Please delete the image in the post above.

Please run **sudo fdisk -l** and post the TEXT output using "code tags".

I don't know of any GUI that properly mounts storage inside Linux.  There are GVFS mounts, which leave much to be desired using GUI tools.  Friends don't let friends use gvfs unless it is an emergency and used for 2 minutes.

If you google "ubuntu fstab" a how-to guide should be a top result for modifying the fstab file. Use this if you are in a hurry.

---

### Post by slickymaster on 2019-01-17
@mrfdes:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

