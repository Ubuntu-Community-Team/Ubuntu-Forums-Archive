---
title: "Knowing the file name within a FILE structure"
date: 2011-05-05
forum: Programming Talk
---

### Post by pilas on 2011-05-05
Hello everyone, I was wondering if it is possible to know the name of a file name, after we open it with a FILE structure, for example:

#include<stdio.h>

int main(int argc, char *argv[])
{

    FILE *fp;

    fp = fopen ("file.txt", "w");

    return 0;
}

after doing this, is it possible to know the name of the file we opened, using the fp variable? 

what if we write in terminal ./program <"file.txt" , can we print the name of the file afterwards using some sort of code?? thanks!

I've tried to use printf("%s, ...); with all the fields in the FILE structure, but with no success... here are the fields I tested: (taken from [http://www.opensource.apple.com/source/gcc/gcc-937.2/libio/libio.h](http://www.opensource.apple.com/source/gcc/gcc-937.2/libio/libio.h))

struct _IO_FILE {
  int _flags;		/* High-order word is _IO_MAGIC; rest is flags. */
#define _IO_file_flags _flags

  /* The following pointers correspond to the C++ streambuf protocol. */
  /* Note:  Tk uses the _IO_read_ptr and _IO_read_end fields directly. */
  char* _IO_read_ptr;	/* Current read pointer */
  char* _IO_read_end;	/* End of get area. */
  char* _IO_read_base;	/* Start of putback+get area. */
  char* _IO_write_base;	/* Start of put area. */
  char* _IO_write_ptr;	/* Current put pointer. */
  char* _IO_write_end;	/* End of put area. */
  char* _IO_buf_base;	/* Start of reserve area. */
  char* _IO_buf_end;	/* End of reserve area. */
  /* The following fields are used to support backing up and undo. */
  char *_IO_save_base; /* Pointer to start of non-current get area. */
  char *_IO_backup_base;  /* Pointer to first valid character of backup area */
  char *_IO_save_end; /* Pointer to end of non-current get area. */

  struct _IO_marker *_markers;

  struct _IO_FILE *_chain;

  int _fileno;
  int _blksize;
#ifdef _G_IO_IO_FILE_VERSION
  _IO_off_t _old_offset;
#else
  _IO_off_t _offset;
#endif

#define __HAVE_COLUMN /* temporary */
  /* 1+column number of pbase(); 0 is unknown. */
  unsigned short _cur_column;
  char _unused;
  char _shortbuf[1];

  /*  char* _save_gptr;  char* _save_egptr; */

#ifdef _IO_LOCK_T
  _IO_LOCK_T _lock;
#endif
#if defined(_G_IO_IO_FILE_VERSION) && _G_IO_IO_FILE_VERSION == 0x20001
  _IO_off64_t _offset;
  int _unused2[16];	/* Make sure we don't get into trouble again.  */
#endif
};

---

### Post by deathadder on 2011-05-05
I misread the link I posted originally...sorry.

The easiest solution I can think off is storing the file name you use in fopen somewhere like a list.

---

### Post by r-senior on 2011-05-05
Another solution is to use a library which creates an abstraction over the basic stdio stuff. I'm thinking of GIO:

[http://developer.gnome.org/platform-overview/stable/gio](http://developer.gnome.org/platform-overview/stable/gio)

---

### Post by Arndt on 2011-05-05
The name is not stored in the FILE struct, but if you for some reason absolutely have to find the file name (and have lost it, so to speak, or some code you don't control have called you with a FILE*, you can take the file descriptor fileno(f), and use fstat to obtain the inode and device numbers. Having them, you can traverse the file system (using 'find') and look for a file with that inode number (there may be several).

Another thing which is useful sometimes is the command 'lsof'. You can use it on a running process, and it will list the open files (with names) and file descriptors.

These suggestions are more in the area of debugging or reverse engineering, of course.

---

### Post by JupiterV2 on 2011-05-05
> **pilas said:**
> Hello everyone, I was wondering if it is possible to know the name of a file name, after we open it with a FILE structure, for example:

#include<stdio.h>

int main(int argc, char *argv[])
{

    FILE *fp;

    fp = fopen ("file.txt", "w");

    return 0;
}

after doing this, is it possible to know the name of the file we opened, using the fp variable? 


Store the name of the file in a variable, as already stated. You could rewrite the above code as:
```
#include<stdio.h>

int main(int argc, char *argv[])
{

    FILE *fp;
    char *filename = "file.txt";

    fp = fopen (filename, "w");

    if (fp == NULL)
        printf ("Failed to open file %s.\n", filename);

    return 0;
}
```


> **pilas said:**
> 
what if we write in terminal ./program <"file.txt" , can we print the name of the file afterwards using some sort of code?? thanks!

In this case, the shell will handle opening the file and redirects the contents as standard input. There's no way that I know of to get the name of the file from which the contents came from. Perhaps someone with more experience can suggest something?

---

