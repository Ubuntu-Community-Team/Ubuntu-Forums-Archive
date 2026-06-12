---
title: "How to test permissions of current working directory"
date: 2014-11-22
forum: Programming Talk
---

### Post by SagaciousKJB on 2014-11-22
How can I use stat() to test if the current working directory has proper write permissions?  I tried using some of the example code from the manual page but it didn't work as expected.

```
           switch (sb.st_mode & S_IFMT) {
           case S_IFBLK:  printf("block device\n");            break;
           case S_IFCHR:  printf("character device\n");        break;
           case S_IFDIR:  printf("directory\n");               break;
           case S_IFIFO:  printf("FIFO/pipe\n");               break;
           case S_IFLNK:  printf("symlink\n");                 break;
           case S_IFREG:  printf("regular file\n");            break;
           case S_IFSOCK: printf("socket\n");                  break;
           default:       printf("unknown?\n");                break;
           }

```

They use this switch to print what type of file it is.  Couldn't I make a similar switch with st_mode and the S_IRWXU to test which permissions the user has in the folder?  So like...

```
           switch (sb.st_mode & S_IRWXU) {
           case S_IWUSR:  printf("Owner has write permission\n");            break;
 .....................................
           }

```

The problem is the switch loop doesn't seem to read the S_IWUSR flag and will just go to the default option.  Haven't tired it with group or other permissions yet, seems like I'm doing something wrong.

---

### Post by ofnuts on 2014-11-22
That doesn't work because unlike Dir/Link/File types, the authorisations can happen together. So sb.st_mode & S_IRWXU==S_IWUSR is true only if the user has write access and nothing else (no read, no execute). To test for your own read access you just need to test sb.st_mode&S_IWUSR != 0.

---

### Post by SagaciousKJB on 2014-11-22
> **ofnuts said:**
> That doesn't work because unlike Dir/Link/File types, the authorisations can happen together. So sb.st_mode & S_IRWXU==S_IWUSR is true only if the user has write access and nothing else (no read, no execute). To test for your own read access you just need to test sb.st_mode&S_IWUSR != 0.

So if I did if(sb.st_modes&S_IWUSR != 0) is that true if I *do* have permissions or *don't*?

---

### Post by ofnuts on 2014-11-22
My money on the fact that you have the permission. But easy to test...

---

### Post by SagaciousKJB on 2014-11-22
> **ofnuts said:**
> My money on the fact that you have the permission. But easy to test...

Eh I'm sorry, I don't understand

---

### Post by ofnuts on 2014-11-23
I don't know, it is a lot more likely that a bit set indicates that access is granted. You can check the doc or experiment (see how the flag value changes when you do a chmod on the file).

---

### Post by SagaciousKJB on 2014-11-23
> **ofnuts said:**
> I don't know, it is a lot more likely that a bit set indicates that access is granted. You can check the doc or experiment (see how the flag value changes when you do a chmod on the file).

Yeah, the manual wasn't making too much sense of it for me.  Think I'm gonna try that experimenting idea.

---

