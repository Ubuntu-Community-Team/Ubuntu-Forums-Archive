---
title: "Cannot read correct file-access time"
date: 2011-01-12
forum: Programming Talk
---

### Post by Minsky on 2011-01-12
I'm new to C programming and I'm writing a utility that displays a file's attributes. I've got a problem in that the st_atime member of a file does not get updated and just shows the same value as st_mtime. I've Googled around and read that this might have something to do with (atime) not being enabled when the file systems are mounted. However, if I go to the Desktop and right-click on the same file and select Properties, the correct access time is displayed. Can anyone explain why this is, and how I can read the correct access time (as the Gnome Properties Window can) without having to edit fstab?

---

### Post by gmargo on 2011-01-12
Try the **stat(1)** command to display the inode attributes.

Most filesystems these days are mounted with the **relatime** attribute.  So "access time" does not get updated on every access.  See the **mount(8)** man page for a fuller explanation.  In the olden days, the "access time" attribute was updated on every access, but this turns out to be really wasteful.  (What's the point of updating the access time on the /bin/ls binary every time you type "ls"?)

You can determine if you're using the **relatime** attribute by looking at **/proc/mounts** (not /etc/fstab).

If you really really want the traditional behavior of access time, you can use the **strictatime** attribute on your filesystem.

---

### Post by Minsky on 2011-01-12
Thanks for replying Gmargo, typing:-

```
stat --printf='%x\n' /path/to/file
```

in a BASH shell produces, near enough, the required result. Can an equivalent code be written in C without using the 'system' function?

---

### Post by gmargo on 2011-01-12
> **Minsky said:**
>  Can an equivalent code be written in C without using the 'system' function?

You can see the **stat(1**) source code, in C, by downloading the source to the **coreutils** package: run "**apt-get source coreutils**" to get the source code.

---

### Post by Minsky on 2011-01-13
Thanks Gmargo, I'll have a look at that.

---

### Post by slavik on 2011-01-14
stat uses the stat syscall.

also, sometimes there is noatime specified for a mount point. ;)

---

### Post by fct on 2011-01-14
Edit: sorry, didn't read that the problem wasn't about relatime.

---

### Post by rnerwein on 2011-01-15
> **Minsky said:**
> I'm new to C programming and I'm writing a utility that displays a file's attributes. I've got a problem in that the st_atime member of a file does not get updated and just shows the same value as st_mtime. I've Googled around and read that this might have something to do with (atime) not being enabled when the file systems are mounted. However, if I go to the Desktop and right-click on the same file and select Properties, the correct access time is displayed. Can anyone explain why this is, and how I can read the correct access time (as the Gnome Properties Window can) without having to edit fstab?

hi 
just for a hint.
it's a matter for performanc reasons what you will get on this filesystem.
if you ain't will retrive only informations from it then mount it without noatime. this will cause the system that the "time" isn't update by only read access.
on huge system that will give you a much bigger performance.
why --> no overload for nothing.
ciao

---

### Post by Minsky on 2011-01-16
Thanks for all the replies, I've figured out what was going wrong, and it was with the way that I was referencing 'st_atime' and 'st_mtime'. The problem I had was that I couldn't figure out why 'st_atime' and 'st_mtime' both displayed the same value; 'st_atime' does contain a file's last access date but I was trying to reference it as in the example below:-

```
int main(void)
{
    char *accessed_time,*modified_time;
    struct stat stbuf;
    stat("/home/minsky/Documents/example.txt",&stbuf);
    accessed_time=ctime(&stbuf.st_atime);
    modified_time=ctime(&stbuf.st_mtime);
    printf("\nAccessed Time = %s\n",accessed_time);
    printf("Modified Time = %s\n",modified_time);
    return 0;
}
```
The error, as you can probably notice, is that the pointers 'accessed_time' and 'modified_time' are both pointing to the result of the ctime() function so when I called ctime() the second time, they were both pointing to the value of 'st_mtime'. This was corrected by modifying the code as shown below:-

```
int main(void)
{
    char *accessed_time,*modified_time;
    accessed_time=malloc(30*sizeof(char));
    modified_time=malloc(30*sizeof(char));
    struct stat stbuf;
    stat("/home/minsky/Documents/example.txt",&stbuf);
    strcpy(accessed_time,ctime(&stbuf.st_atime));
    strcpy(modified_time,ctime(&stbuf.st_mtime));
    printf("\nAccessed Time = %s\n",accessed_time);
    printf("Modified Time = %s\n",modified_time);
    free(accessed_time);
    free(modified_time);
    return 0;
}
```

By allocating a separate memory area for each pointer to point to and copying the result of each call of the ctime() function into their respective areas, 'accessed_time' and 'modified_time' now point to the correct values.

---

