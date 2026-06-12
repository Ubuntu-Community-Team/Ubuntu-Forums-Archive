---
title: "Installation type 4 partitions max"
date: 2018-12-09
forum: New to Ubuntu
---

### Post by blu422 on 2018-12-09
Hello,
So first off I'm sorry if this has already been discussed but I have spent at least the last hour searching but to no avail.

Here's the problem so, I am attempting to dual boot ubuntu studio 18.10 with windows. So I shrank my data partition and made over 100 GB of space. Then I made the installation USB (I tried two different USBs to be sure that wasn't the problem). After booting from the installation USB I began to install ubuntu studio. When I got to the screen where I select how my partitions are going to be I click on the free space and then click on the plus to make a new partition, but when I do, all the buttons on the installer gray-out and then it stalls indefinitely (and I left it for about a half an hour) (I have an SSD). So after some searching, I thought that maybe the problem was that I already had 4 primary partitions because of some mystery 16mb windows partition that I think might be there for managing other partitions, but that can't be the problem because my hard drive is formatted GPT, which can have up to 128 primary partitions with no problems. So now I don't know what the problem is. Maybe the installer doesn't realize that with GPT you can have more than 4 partitions? maybe the installer doesn't realize that my hard drive is GPT? Maybe the problem is another entirely? What do you guys think?

---

### Post by yancek on 2018-12-09
While booted to the Ubuntu install usb, open a terminal and run the command below and post the output here.  That will give partition info and tell whether it is GPT.  Do you have your windows 10 hibernated?

```
sudo parted -l
```

That's a Lower Case Letter L in the command.

---

### Post by blu422 on 2018-12-10
Hey so I fixed the problem. I used easeus partition manager to just partition the free space and then when I ran the installation I was able to delete that partition and make more primary partition. I guess the installer just had to see that 5 partitions were possible to be willing to do it?

---

### Post by blu422 on 2018-12-10
And the output of the command you told me to do told me that I was using gpt I don't know how to post the exact output

---

### Post by blu422 on 2018-12-10
Thanks for your help though

---

