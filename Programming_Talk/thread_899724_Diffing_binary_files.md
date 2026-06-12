---
title: "Diffing binary files"
date: 2008-08-24
forum: Programming Talk
---

### Post by nub nub on 2008-08-24
I'm trying to get the differences between three 1.5GB binary files. I tried comparing two at a time with diff, but all that gave me was that they differ. I tried doing it manually, with VBinDiff, but they're 1.5GB, that'd take all day.

What I need is a way to get byte ranges that differ in two files.

Well, ideally what I'm trying to do is get areas that are the same in files 2 & 3, but different in file 1. But I could do that with a list of byte ranges, if anyone knows a program.

---

### Post by mssever on 2008-08-24
> **nub nub said:**
> I'm trying to get the differences between three 1.5GB binary files. I tried comparing two at a time with diff, but all that gave me was that they differ. I tried doing it manually, with VBinDiff, but they're 1.5GB, that'd take all day.

What I need is a way to get byte ranges that differ in two files.

Well, ideally what I'm trying to do is get areas that are the same in files 2 & 3, but different in file 1. But I could do that with a list of byte ranges, if anyone knows a program.
I don't know the real answer, but you could try this kludge:
```
hd file1 > file1.hex
hd file2 > file2.hex
hd file3 > file3.hex
diff file1.hex file2.hex
```

---

### Post by jinksys on 2008-08-24
> **nub nub said:**
> I'm trying to get the differences between three 1.5GB binary files. I tried comparing two at a time with diff, but all that gave me was that they differ. I tried doing it manually, with VBinDiff, but they're 1.5GB, that'd take all day.

What I need is a way to get byte ranges that differ in two files.

Well, ideally what I'm trying to do is get areas that are the same in files 2 & 3, but different in file 1. But I could do that with a list of byte ranges, if anyone knows a program.

What kind of files are they, and do they have any internal formatting/fields/etc?

---

### Post by nub nub on 2008-08-24
> **jinksys said:**
> What kind of files are they, and do they have any internal formatting/fields/etc?

They're BitLocker encrypted NTFS volume images. They don't seem to have any structure after the bootsector.

(**My** volume images, I'm trying to figure out how it works, not break it.) 

> ```
hd file1 > file1.hex
hd file2 > file2.hex
hd file3 > file3.hex
diff file1.hex file2.hex
```

I'm going to try this, I'll let you know if it works.

---

### Post by ghostdog74 on 2008-08-24
> **nub nub said:**
> I'm trying to get the differences between three 1.5GB binary files. I tried comparing two at a time with diff, but all that gave me was that they differ. I tried doing it manually, with VBinDiff, but they're 1.5GB, that'd take all day.

what is it that you need to find? Even if diff can give you a list of what's differing between the 2 files, they are still not understandable data.

---

### Post by CptPicard on 2008-08-25
Considering these are encrypted data, if the encryption is any good, you should be getting diffs where files differ essentially as much as two files full of random bits would, that is, they are "completely different". Otherwise the encryption algorithm is a good candidate for a plaintext attack... :)

---

### Post by nub nub on 2008-08-25
> **CptPicard said:**
> Considering these are encrypted data, if the encryption is any good, you should be getting diffs where files differ essentially as much as two files full of random bits would, that is, they are "completely different". Otherwise the encryption algorithm is a good candidate for a plaintext attack... :)

Ah, yes, I realise that. These are the same volume, but file1 is "locked" (no key in the clear), but files 2&3 are "unlocked" (key in the clear *somewhere* on the disk, apparently in the "volume metadata", but not in the first 32 sectors, as they're the same).

This is the first step in making a mod for the ntfs-3g driver to open bitlocker encrypted volumes, and I'm already stuck! Maybe I'll just work on implementing the "elephant" diffuser, and come back to this later...

Oh, and that "hd" thing was no good, I don't have that much disk space :(

Maybe I should just try making something myself, if there is no such program.

Actually, maybe comparing many different unlocked volume images, all with modifications, would be a better approach. Oh well, whatever! Off to find documentation for dm, hope someone here knows a binary diff program :( See y'all later. I'll check back every five minutes :P

EDIT: In my frustration, I seem to have forgotten my manners! Thank you for your help!

---

### Post by AusIV4 on 2008-08-25
Take a look at [rdiff]("apt:rdiff").

---

### Post by nub nub on 2008-08-25
> **AusIV4 said:**
> Take a look at [rdiff]("apt:rdiff").

Thank you for the suggestion! Unfortunately, the 'delta' files it produces are completely unreadable. Am I really the first person to need a tool like this? *sigh*

*opens up C/C++ IDE*

---

### Post by EricHerman on 2009-12-29
I like to hex dump the files with one-byte-per-line; this can be a bit tedious with very large text files, but it makes for very easy viewing and diff-ing.

You might try playing with something like this:

$ hexdump -v -e '1/1 "0x%02x"' -e '"\n"' file1 > dump1.hex
$ hexdump -v -e '1/1 "0x%02x"' -e '"\n"' file2 > dump2.hex
$ diff -u dump1.hex dump2.hex > d1.diff
$ vim d1.diff

---

### Post by kwyto on 2009-12-29
what kind of differences are you hoping to find? files names? data?

---

