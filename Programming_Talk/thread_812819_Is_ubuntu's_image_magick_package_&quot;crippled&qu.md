---
title: "Is ubuntu's image magick package &quot;crippled&quot; ?"
date: 2008-05-30
forum: Programming Talk
---

### Post by skelooth on 2008-05-30
[sort-of_SOLVED]
I installed from source and I'm just going to spawn processes with system(). For now it's a better option than fighting with Image::Magick all day long.



Hello, I'm working on a piece of dam software and would like to use perlmagick for thumbnail generation and info extraction. The problem I've run into is that the ubuntu package of image magick does not seem to read psd and ai files as advertised on the website.

Has the package in the repository been crippled to exclude non-free file formats? 

Thanks.

---

### Post by skelooth on 2008-05-30
I just noticed that libmagick is part of the ubuntu-desktop package. Am I going to regret compiling image magick from source? I'm scared.

---

### Post by Lau_of_DK on 2008-05-30
> **skelooth said:**
> I just noticed that libmagick is part of the ubuntu-desktop package. Am I going to regret compiling image magick from source? I'm scared.

I'm not sure, I think you should read from the official site to get some definitiy info, but I've had many tasks that ended up being side-tracked because Imagemagick do as it was supposed to.

Gdlib however, did the job.

/Lau

---

### Post by skelooth on 2008-05-30
I installed it from source and it works GREAT ..... but only from the command line! I get no error when I run perl scripts with

use Image::Magick

but it produces no output and throws no errors. It just.... happily pretends to read files, and write nothing.

---

### Post by pdwerryhouse on 2008-05-31
> **skelooth said:**
> I just noticed that libmagick is part of the ubuntu-desktop package. Am I going to regret compiling image magick from source? I'm scared.

If you installed it in the same location where the package was installed, then you might have some problems further down the track.

Reinstall the package with:

apt-get --reinstall install libmagick

And then if you still need to install imagemagick from source, make sure you install in somewhere else on the filesystem (eg, /usr/local).

---

