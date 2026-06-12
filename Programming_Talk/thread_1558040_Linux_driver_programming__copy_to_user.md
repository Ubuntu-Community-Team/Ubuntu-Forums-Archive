---
title: "Linux driver programming : copy_to_user"
date: 2010-08-21
forum: Programming Talk
---

### Post by bluedalmatian on 2010-08-21
Im a bit confused about how to implement a read & write system call in a Linux driver module using copy_to_user and copy_from_user.

The last argument to the read/write function is loff_t* giving the offset in the buffer where the data is to be read/written to/from.  How do I pass this into copy_to_user to ensure it reads from the correct point?

Do I just add it to the second arg to copy_to_user to advance the pointer?

Thanks
Andrew

---

### Post by xb12x on 2010-08-21
Are you writing a driver or an application?

Both 'copy_to_user' and 'copy_from_user' are "User context only".

---

### Post by bluedalmatian on 2010-08-21
A driver. The user process will call read() and write() on the /dev file and the driver will use copy_to_user and copy_from_user to transfer between the user process and the drivers internal buffer

---

### Post by xb12x on 2010-08-21
I think I understand your question now.

What you call loff_t* is the file position indicator, i.e. the offset to access within the file (or device).

---

### Post by bluedalmatian on 2010-08-22
I know it is. What Im asking is, how do I use that information to ensure copy_to_user accesses the buffer in the driver at the correct offset?

---

### Post by xb12x on 2010-08-22
copy_to_user() and copy_from_user() know about two buffers: the user-space buffer that the app has direct access to, and the kernel-space buffer that your driver has direct access to. These routines copy from one to the other so that you don't have to calculate the actual physical addresses of those two buffers. 

The file's position indicator points to the position within the file or device that your driver represents. It knows nothing of the pointers to the user-space buffer or the kernel-space buffer, or the sizes of those buffers.

Assume we're reading the entire file. The first read of 32 bytes would start at the beginning of the file, offset 0x0 within the file. Those 32 bytes would be read from the file to the kernel-space buffer. The next read of the file would be at offset 32 within the file to offset 32 within the kernel-space buffer. But if the buffer were only 16 bytes large, you would have to stop reading the file when the file's position indicator was at offset 16. Then do copy_to_user(), etc,  so you can start re-using the kernel-space buffer at offset 0x0 for the next read. But the file's position indicator will be at offset 16 for the next read of the file. This loop continues until the entire file is read and transfered, one buffer's worth at a time.

So your question has to do with pointer arithmetic based on the size of the buffers used to transfer the data from the driver to the app, etc. It will be up to you to keep track of where you are within the file (file's position indicator) and where you are within the buffers.

There is an Internet full of examples to look at. Ubuntu's sources are a good place to look.

---

### Post by bluedalmatian on 2010-08-22
OK, forget reading & writing, lets just concentrate on the read() function.  


 As I understand it, the user may request a read of say 32 bytes, but we may only transfer 16 before getting interrupted in which case its up to the user space app to check how many bytes were successfully transferred and re-issue the read() call with an updated offset? (The driver in fact updates the offset, before returning the number of bytes successfully transferred)


When read() is called again the second time, surely the driver must take the offset into account when calling copy_to_user otherwise it will transfer from the start again? Whats the point of us being passed the offset in the read function arguments if we ignore it

You talk about the 'file' and the 'driver buffer' as if they're completely separate but in actual fact the 'file' is just the userspace handle onto the driver's buffer.

Thanks for your help.  I have Googled this but all I can find are old examples based on 2.4 or verbatim copies of the O'Reilly book's 2.6 example which is what's confusing me. O'Reilly have made their example needlessly complex with "quantums" and umpteen buffers nested in umpteen structures rather than showing a nice simple example with one simple buffer.

---

### Post by xb12x on 2010-08-22
*As I understand it, the user may request a read of say 32 bytes, but we may only transfer 16 before getting interrupted *

I mentioned NOTHING about interrupts. That's an additional level of complication for you to learn about.

*You talk about the 'file' and the 'driver buffer' as if they're completely separate but in actual fact the 'file' is just the userspace handle onto the driver's buffer.*

Is the driver a device driver for hardware? Does your driver access registers on that hardware? Are the hardware's registers  memory-mapped contiguously? I use the term 'file' to represent whatever your driver is accessing. It could be custom hardware with non-contiguous registers, etc.

However, the kernel-space buffer is real memory and should be contiguous. And the size of that buffer might or might not have anything to do with the register size of the custom hardware you want to read and write.

And the size of the app's buffer is up to whoever wrote the app. 

Google "KernelHacking101_my_driver.pdf" for a simple example of how to use both copy_to_user() and copy_from_user().

Notice in that example that there are three calls to copy_to_user() to satisfy one read().

---

