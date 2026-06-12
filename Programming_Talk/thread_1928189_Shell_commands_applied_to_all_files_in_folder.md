---
title: "Shell commands applied to all files in folder"
date: 2012-02-19
forum: Programming Talk
---

### Post by ugm6hr on 2012-02-19
I'm sure I'm being lazy, but I figured this sounds like a simple script for someone who understands these things. So I'm looking for a favour...

Basically, I'm processing image files with VIPS ( [http://www.vips.ecs.soton.ac.uk/](http://www.vips.ecs.soton.ac.uk/) )- and would prefer not to have to manually retype the name of all image files to process. Is there a simple script that will perform the following on all files named *.svs in the current folder?
```
vips im_tiff2vips 1239.svs 1239.v
vips im_shrink 1239.v 1239.tif 2 2
```
Where "1239" is the name of the image in this example (all image.svs files will be a 4-digit code).
Thanks for the help.

---

### Post by erind on 2012-02-19
You can try something like this:  

```
 for f in *.svs
  do
     vips im_tiff2vips "$f" "${f%.svs}.v"
     vips im_shrink "${f%.svs}.v" "${f%.svs}.tif" 2 2
 done
```

---

### Post by MadCow108 on 2012-02-19
you might be interested in gnu parallel to do it fast and with only very little to type:
```
ls *svs | parallel vips im_tiff2vips {} {.}.v
ls *v | parallel vips im_tiff2vips {} {.}.tif 2 2
```

or if not seperable:
```
ls -1 *svs | parallel "vips im_tiff2vips {} {.}.v && vips im_tiff2vips {.}.v {.}.tif 2 2"
```

you can do it with xargs too if you do some sed'ing for the extensions, syntax is almost the same

```
ls  *.svs | sed -e "s/.svs$//" | xargs -n 1 -I{} vips im_tiff2vips {}.svs {}.v

```

---

### Post by ugm6hr on 2012-02-20
> **MadCow108 said:**
> ```
ls -1 *svs | parallel "vips im_tiff2vips {} {.}.v && vips im_tiff2vips {.}.v {.}.tif 2 2"
```

Thank you both for the suggestions.
I like the look of this - and would like to know what I'm doing, for potential future use please... 
[LIST=1]
[*]"ls -1 *svs" presumably selects all files ending svs? 
[*]the parallel command runs the processing on each file identified by *svs, removes the "." prior to svs, then renames with .v and subsequently .tif?
[*]is parallel default installed in Ubuntu? Else, is it an apt-get install parallel? Or do I need to run it with a preceding perl command?
[/LIST]
There is what I presume a copying error from my example (im_tiff2vips then im_shrink processing, not tiff2vips for both).
Hence:
```
ls -1 *svs | parallel "vips im_tiff2vips {} {.}.v && vips im_shrink {.}.v {.}.tif 2 2"
```
Correct?

---

### Post by nothingspecial on 2012-02-20
**Edit**

See post below

---

### Post by MadCow108 on 2012-02-20
> **ugm6hr said:**
> Thank you both for the suggestions.
I like the look of this - and would like to know what I'm doing, for potential future use please... 
[LIST=1]
[*]"ls -1 *svs" presumably selects all files ending svs? 
[*]the parallel command runs the processing on each file identified by *svs, removes the "." prior to svs, then renames with .v and subsequently .tif?
[*]is parallel default installed in Ubuntu? Else, is it an apt-get install parallel? Or do I need to run it with a preceding perl command?
[/LIST]
There is what I presume a copying error from my example (im_tiff2vips then im_shrink processing, not tiff2vips for both).
Hence:
```
ls -1 *svs | parallel "vips im_tiff2vips {} {.}.v && vips im_shrink {.}.v {.}.tif 2 2"
```
Correct?

unfortunately its not in ubuntu due to a nameclash moreutils parallel which sucks compared to gnu parallel.
but its just a perl script you don't need to install. You only may need to give it execute permissions (chmod u+x file) or prepend perl.
here is also a package:
[https://launchpad.net/~jtaylor/+archive/jtaylor/+files/parallel_20110822-1~ppa1_all.deb](https://launchpad.net/~jtaylor/+archive/jtaylor/+files/parallel_20110822-1~ppa1_all.deb)

{.} interprets the input as a filepath removes the extension {} is the pristine argument, there is also {/} for the basename, [//} for the dirname and {/.} for the basename and without extension (+ a couple more see the manpage)
put an echo in front of the command to play around with it.

> Although in your particular case the second example would work, the first example is the recommended method with bash.
no, parallel is line based so it will handle spaces in filenames fine
you can also tell it to use NULL, just like xargs:
```
$ echo -e "test TEST\ntest test test" | parallel echo
test TEST
test test test

```

---

### Post by nothingspecial on 2012-02-20
> **nothingspecial said:**
> Although in your particular case the second example would work, the first example is the recommended method with bash.



> **MadCow108 said:**
> 
no, parallel is line based so it will handle spaces in filenames fine
you can also tell it to use NULL, just like xargs:
```
$ echo -e "test TEST\ntest test test" | parallel echo
test TEST
test test test

```

Ok thanks

---

### Post by sisco311 on 2012-02-20
> **MadCow108 said:**
> you can also tell it to use NULL, just like xargs

+1 for the -0 flag. :)

[http://mywiki.wooledge.org/UsingFind?highlight=%28parallel%29#Actions_in_bulk:_GNU_Parallel](http://mywiki.wooledge.org/UsingFind?highlight=%28parallel%29#Actions_in_bulk:_GNU_Parallel)

---

### Post by ugm6hr on 2012-02-21
Thanks everyone... Parallel worked as expected.

---

