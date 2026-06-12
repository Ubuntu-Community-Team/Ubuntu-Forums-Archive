---
title: "How to convert from pdf to djvu (2 methods)"
date: 2012-03-05
forum: Outdated Tutorials &amp; Tips
---

### Post by starplex on 2012-03-05
One of the main reasons to convert a pdf file into djvu is to save space. I've seen 577MB PDF file become 95MB DJVU after conversion. But a lot depends on the converter chosen and of course, the settings.

[B]Method 1: The easy pdf2djvu
[/B]

Installed by ```
sudo apt-get install pdf2djvu
```

After it's done just open a terminal and type ```
pdf2djvu -o output_file input_file
```

input_file being the pdf you want to convert.

**Method 2: The harder way djvudigital**

Step 1: ```
sudo apt-get install djvulibre-bin djvulibre-desktop djvulibre-plugin
```

Step 2: download the latest GSDJVU from here [http://sourceforge.net/projects/djvu/files/GSDjVu/](http://sourceforge.net/projects/djvu/files/GSDjVu/)

Step 3: Extract it somewhere and inside create a new directory named BUILD

Step 4: download latest
[LIST]
[*]Ghostscript [http://sourceforge.net/projects/ghostscript/files/GPL%20Ghostscript/9.05/ghostscript-9.05.tar.bz2/download](http://sourceforge.net/projects/ghostscript/files/GPL%20Ghostscript/9.05/ghostscript-9.05.tar.bz2/download)
[*]Ghostscript fonts [http://code.google.com/p/ghostscript/downloads/detail?name=ghostscript-fonts-std-8.11.tar.gz&can=2&q=](http://code.google.com/p/ghostscript/downloads/detail?name=ghostscript-fonts-std-8.11.tar.gz&can=2&q=)
[*]JPEG src [http://www.ijg.org/files/jpegsrc.v8d.tar.gz](http://www.ijg.org/files/jpegsrc.v8d.tar.gz)
[*]LIBPNG [ftp://ftp.simplesystems.org/pub/libpng/png/src/libpng-1.5.9.tar.gz](ftp://ftp.simplesystems.org/pub/libpng/png/src/libpng-1.5.9.tar.gz)
[*]Zlib [http://zlib.net/zlib-1.2.6.tar.gz](http://zlib.net/zlib-1.2.6.tar.gz)
[/LIST]

Put these files in the BUILD directory you created in step 3. **Do not extract them**

Step 5: download [http://sourceforge.net/tracker/index.php?func=detail&aid=3485919&group_id=32953&atid=406585](http://sourceforge.net/tracker/index.php?func=detail&aid=3485919&group_id=32953&atid=406585) and put it in the GSDJVU directory.

Step 6: ```
sudo apt-get install patch
```. In terminal go to the GSDJVU dir and type ```
patch -p1 < 0001-Upstream-removed-gserror.h-in-gs905-commit-8f2ecf4.patch
```

Step 7: RUN the shell script ```
build-gsdjvu
```. **USE FULL PATHNAME**. eg /home/sam/gsdjvu/build-gsjvu

Step 8: Wait

Step 9: ```
sudo cp -r BUILD/INST/gsdjvu  /usr/local/lib
```
        ```
sudo cd /usr/local/bin
```
        ```
sudo ln -s ../lib/gsdjvu/gsdjvu gsdjvu
```


You are now ready to run djvudigital. Just type ```
djvudigital input_file output_file
``` and all should be well.

For more info consult the manuals:
```
man pdf2djvu
man djvudigital
```

---

