---
title: "can you construct and absolute file path from an inode and nameidata?"
date: 2008-04-13
forum: Programming Talk
---

### Post by keeler1 on 2008-04-13
I am working on a project for a class of mine and have a couple question about the two data structures mentioned.

I need to recreate the absolute file path given an inode and an instance of nameidata.

From what I have been able to collect thus far, it seems as though the inode will not be used for this but it is still available if need be.

What I have so far is that the nameidata contains a dentry struct which has a field d_name.  It also contains a pointer to the parent directory of this dentry which is another dentry.

Does the d_name field contain the name of the current directory of file with no path prepended?

If so then I could recreate the absolute path by following the parent pointer back to the root directory and use all the names with '/' put in between.

Is this correct or would it not work?

I have been unable to find any specification for what the d_name field actually holds.

---

### Post by keeler1 on 2008-04-13
Ok, I feel pretty dumb now.  After looking through the kernel source a bit more, it turns out there is a function to do this already.

```
char * d_path(struct dentry *dentry, struct vfsmount *vfsmnt, char *buf, int buflen)
```

Now this seems pretty easy.  Simply use the dentry inside the nameidata structure and the vfsmount object inside the nameidata structure to get the path.

The only comment in the kernel for the function is 

/* write full pathname into buffer and return start of pathname */

From this I take it that I need to create some buffer, and pass the dentry, vfsmount, pointer to the buffer and the size of the buffer and it should return a pointer into the buffer to the beginning of the path.

One last thing a call to d_path would look like

```
nameidata nd;  //this is already initialized
int bufferSize = <some size>
char *buffer = <get memory of bufferSize with kmalloc or other function>;
char *pathPtr = d_path(nd.dentry, nd.mnt, buffer, bufferSize);
```

Now what do I have?  How can I read the absolute path from this pointer not knowing the length of the string?  Does the function fill from the end of the buffer forward?  This would make sense to fill the last then move back as you get the parent dentry.  If this is correct I could subtract my orignal pointer from my new one to get how many characters in my buffer are not full.  Then I would also have the length.

How does the function work?

---

### Post by supirman on 2008-04-13
You can check the length using strlen.

Here's an example from drivers/usb/gadget/file_storage.c in a kernel version I have laying around...

[PHP]
 if (backing_file_is_open(curlun)) { // Get the complete pathname
    p = d_path(curlun->filp->f_dentry, curlun->filp->f_vfsmnt,
        buf, PAGE_SIZE - 1);
    if (IS_ERR(p))
      rc = PTR_ERR(p);
    else {
      rc = strlen(p);
      memmove(buf, p, rc);
      buf[rc] = '\n';   // Add a newline
      buf[++rc] = 0;
    }
  } 
[/PHP]

---

### Post by keeler1 on 2008-04-13
So I am assuming that the buffer from the pointer passed back to the end is null terminated, or else strlen would not work.

This is good news.  Thank You

---

### Post by kulpsterdaman on 2008-05-09
```
char * d_path(struct dentry *dentry, struct vfsmount *vfsmnt, char *buf, int buflen)
```

What does buf represent? Given inode, mask, and nameidata how do you initialize it?

---

### Post by keeler1 on 2008-05-09
Buffer is the buffer to put the filepath in.  You initialize it like every other char array.  Its where d_path puts the name of the path.

---

### Post by kulpsterdaman on 2008-05-10
thanks for the reply. i like how your Post says you posted in May 2007...time travel is wicked.

---

