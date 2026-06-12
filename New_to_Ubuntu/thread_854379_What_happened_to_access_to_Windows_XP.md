---
title: "What happened to access to Windows XP?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Ray Shive on 2008-07-09
OOPS! I think. I Installed Ubuntu 8.04 with the understanding that it would be set up alongside my Windows XP and so that I could ease into Linux by being able to switch back and forth. Alas I find no way to get to my XP desktop. Is all lost? If so, please let me down easy. If not, how do I get to XP? Thank you

---

### Post by mikewhatever on 2008-07-09
Can you post the output of <sudo fdisk -l>. Which partitioning option did you use?

---

### Post by avtolle on 2008-07-09
Yes, post the output of ```
sudo fdisk -l
```. 

Wondering whether the OP is wanting to switch between the two OS without a restart?

---

### Post by stchman on 2008-07-09
> **Ray Shive said:**
> OOPS! I think. I Installed Ubuntu 8.04 with the understanding that it would be set up alongside my Windows XP and so that I could ease into Linux by being able to switch back and forth. Alas I find no way to get to my XP desktop. Is all lost? If so, please let me down easy. If not, how do I get to XP? Thank you

Did you dual boot?  Did you use wubi?  Let us know.

If you chose to use entire disk when installing Ubuntu then I am afraid that XP is gone.  Let us know HOW you installed Ubuntu.

---

### Post by Ray Shive on 2008-07-09
> **mikewhatever said:**
> Can you post the output of <sudo fdisk -l>. Which partitioning option did you use?
I have no idea. It was all automatic. I downloaded Ubuntu 8.04 and then made an install disk as directed. Istallation proceeded smoothly. I was given no options. An article in PC World had led me to believe that it automatically went into a folder or something that would ba accessed when needed. I would also be able to delete Ubuntu from my system just like any Windows application if I decided I didn't want it.

---

### Post by Ray Shive on 2008-07-09
> **stchman said:**
> Did you dual boot?  Did you use wubi?  Let us know.

If you chose to use entire disk when installing Ubuntu then I am afraid that XP is gone.  Let us know HOW you installed Ubuntu.
Can you tell me where to find the output of <sudo fdisk-1>?

---

### Post by Ray Shive on 2008-07-09
> **Ray Shive said:**
> Can you tell me where to find the output of <sudo fdisk-1>?
Yes I chose to use the entire disk. I thought it was automatically using Wubi - again tht's the way the PC World article sounded. In any case I was given no real options - the Use Entire Disk option was already selected. I assumed that it would be clear especially in view of the dire consequences of choosing the wrong option(s). Looks pretty bad.

---

### Post by avtolle on 2008-07-09
To choose to install through Wubi one must choose the option to "install within Windows" or words to that effect which I believe is option 3 in the menu that comes up on boot of the Live CD. If you said to use the entire disk, well, you weren't using Wubi. From what I perceive, you have formatted over your XP install.

To use the command (sudo fdisk -l) open a terminal (Applications>>Accessories>>Terminal) and type the command at the prompt, enter your password when requested (there will be no visual feedback), hit Enter, and the output should appear. Cut and paste it into your post.

---

