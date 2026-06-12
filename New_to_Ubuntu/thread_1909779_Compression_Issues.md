---
title: "Compression Issues"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by justmott on 2012-01-15
I am trying to work through the terminal to compress all my files on my numerous USB flash drives.  I used the "zip -r file.zip ~/USB" but the produced .zip was only about 60mb smaller than the 305mb file that I started with.  Also the files in the .zip archive all appeared as regular files, so I could open them without unzipping them.  I also tried the tar command which produced similar results.  What am I overlooking?

---

### Post by mcduck on 2012-01-16
What types of files are you trying to compress?

If the data is already in compressed format, you can't compress it any more. The original copression has already removed as much of the data as possible. (this is especially true for files that are already compressed using highly effective lossy compressions like with most audio & video formats)

For this reason trying to compress things like MP3 audio, JPG images, pretty much any video file, OpenOffcie docments and so on only gives you minimal reduction in file size (and can actually in some cases even result in archive that's larger than the original files).

---

### Post by justmott on 2012-01-16
Bingo! Thanks

---

