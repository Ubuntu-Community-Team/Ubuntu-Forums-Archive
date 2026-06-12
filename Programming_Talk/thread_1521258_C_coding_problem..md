---
title: "C coding problem."
date: 2010-06-30
forum: Programming Talk
---

### Post by kemiko on 2010-06-30
I am porting a C application from RedHat 7.0 to Ubuntu 8.04 LTS

I am getting a SIGSEGV on the following line:

```
490                while( fgets ( istring, 100, hSort_File ) != NULL ) {
```

The code makes it paste this line for first time...the FILE *hSort_File gets screwed up a few lines later, but okay now:

```
(gdb) p *hSort_File
$6 = {
  _flags = -72539000, 
  _IO_read_ptr = 0xb7fde053 "0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 20050501 0010 b D 0 0000779 2726476 0002706 07005 00000\n0 00000 11 203672 20061401 2006240"..., 
  _IO_read_end = 0xb7fdf000 "y", 
  _IO_read_base = 0xb7fde000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_write_base = 0xb7fde000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_write_ptr = 0xb7fde000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_write_end = 0xb7fde000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_buf_base = 0xb7fde000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_buf_end = 0xb7fdf000 "y", 
  _IO_save_base = 0x0, 
  _IO_backup_base = 0x0, 
  _IO_save_end = 0x0, 
  _markers = 0x0, 
  _chain = 0x815b010, 
  _fileno = 11, 
  _flags2 = 0, 
  _old_offset = 0, 
  _cur_column = 0, 
  _vtable_offset = 0 '\0', 
  _shortbuf =     "", 
  _lock = 0x815fab0, 
  _offset = -1, 
  __pad1 = 0x0, 
  __pad2 = 0x815fabc, 
  __pad3 = 0x0, 
  __pad4 = 0x0, 
  __pad5 = 0, 
  _mode = -1, 
  _unused2 =     '\0' <repeats 39 times>
}
```

After the following line the FILE *hSort_File get messed up:

```
502                        if( nSkip = ( err = isread ( fd, (char *)&susidx, ISEQUAL )) < 0 ) {

(gdb) p *hSort_File
$3 = {
  _flags = 135657528, 
  _IO_read_ptr = 0x4 <Address 0x4 out of bounds>, 
  _IO_read_end = 0x3754534d <Address 0x3754534d out of bounds>, 
  _IO_read_base = 0x0, 
  _IO_write_base = 0x0, 
  _IO_write_ptr = 0x169 <Address 0x169 out of bounds>, 
  _IO_write_end = 0xfbad2488 <Address 0xfbad2488 out of bounds>, 
  _IO_buf_base = 0xb7f84053 "0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 20050501 0010 b D 0 0000779 2726476 0002706 07005 00000\n0 00000 11 203672 20061401 2006240"..., 
  _IO_buf_end = 0xb7f85000 "y", 
  _IO_save_base = 0xb7f84000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_backup_base = 0xb7f84000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _IO_save_end = 0xb7f84000 "0 00000 11 202890 20122000 20010501 0010 b D 0 0000779 2211518 0002046 07005 00000\n0 00000 11 203371 20061902 20071802 0010 b D 0 0000779 2506019 0002423 07005 00000\n0 00000 11 203649 20042301 2005050"..., 
  _markers = 0xb7f84000, 
  _chain = 0xb7f84000, 
  _fileno = -1208463360, 
  _flags2 = 0, 
  _old_offset = 0, 
  _cur_column = 0, 
  _vtable_offset = 0 '\0', 
  _shortbuf =     "", 
  _lock = 0x0, 
  _offset = 51675246608, 
  __pad1 = 0x0, 
  __pad2 = 0x0, 
  __pad3 = 0x0, 
  __pad4 = 0x815fab0, 
  __pad5 = 4294967295, 
  _mode = -1, 
  _unused2 =     "\000\000\000\000&#65533;&#65533;\025\b", '\0' <repeats 12 times>, "&#65533;&#65533;&#65533;&#65533;", '\0' <repeats 15 times>
}
```

**I have no idea why this is happening!**

---

### Post by wmcbrine on 2010-06-30
I don't think anyone can help you without seeing more of the code. Forget the gdb stuff.

---

### Post by trent.josephsen on 2010-06-30
Something else in your code appears to be trampling on your memory.  It's almost certain that the line you posted isn't at fault.

---

### Post by Can+~ on 2010-06-30
Either the istring is not long enough, or hSort_file is pointing to a wrong direction (or nonexistant).

And the later, could be a result that a previous instrunction overwrote the hSort_file pointer, etc. We need more code, or you should debug better.

---

### Post by soltanis on 2010-07-01
Yup, you pretty clearly have a pointer straying outside of memory but it doesn't trigger the fault until the line you posted. More likely than not your problem code was executed several statements back.

---

