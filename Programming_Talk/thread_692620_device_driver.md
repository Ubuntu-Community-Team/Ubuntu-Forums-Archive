---
title: "device driver"
date: 2008-02-09
forum: Programming Talk
---

### Post by g3k0 on 2008-02-09
So... I'm supposed to write a program to read disk geometry info of a CD.  From what I understand I should just use basic read calls like I would a file.  So, I am just trying to dump the first 512 bytes or so to the screen to see if I am getting what I want to.  I get 0's.  I downloaded a kHexEdit and opened /dev/scd0 .... still nothing.  But the cd is mounted! I type mount and it has /dev/scd0 mounted to /media/cdrom0. what am I doing wrong!  Here is my code currently.  Very basic, just trying to get a response I want.

```

unsigned char buffer[512];
int cd = open("/dev/scd0", O_RDONLY);
lseek(cd,0,SEEK_SET);
int n=read(cd, buffer, 512);
for (int i = 0; i < 512; ++i){
	printf("%02X ", buffer[i]);
}

close(cd);
```

---

### Post by LaRoza on 2008-02-09
Why are you "supposed" to write this?

---

### Post by Zugzwang on 2008-02-10
> **g3k0 said:**
> So... I'm supposed to write a program to read disk geometry info of a CD.  From what I understand I should just use basic read calls like I would a file.  So, I am just trying to dump the first 512 bytes or so to the screen to see if I am getting what I want to.  I get 0's.  I downloaded a kHexEdit and opened /dev/scd0 .... still nothing.  But the cd is mounted! I type mount and it has /dev/scd0 mounted to /media/cdrom0. what am I doing wrong!  Here is my code currently.  Very basic, just trying to get a response I want.


Please verify that:
[LIST]
[*]You unmount your CD before trying to read from /dev/scd0
[*]Your rights are sufficient to read from that device
[/LIST]

---

### Post by g3k0 on 2008-02-10
I tried unmounting it and it did the same thing,  It did cause the drive to spin though,  Maybe I am just misunderstanding how to do this whole thing.  As far as rights go I run the program with sudo and it doesn't change anything.

---

### Post by Zugzwang on 2008-02-11
Have you tried using the "dd" utility of Linux for copying the beginning of the CD to a file? Maybe it's just that the first 512 bytes of your CD *are* 0's?

---

### Post by g3k0 on 2008-02-11
haha yeah they are 0s.  A friend of mine said he gets the same thing on that part of the CD.  The geometry is on sector 16 or something like that.  Thanks for the help.  I just gotta figure out how the cd is set so I know where to read =/

---

