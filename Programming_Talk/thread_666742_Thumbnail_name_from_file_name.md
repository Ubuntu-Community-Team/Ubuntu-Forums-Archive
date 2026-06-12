---
title: "Thumbnail name from file name?"
date: 2008-01-13
forum: Programming Talk
---

### Post by Yuzem on 2008-01-13
Hello, I am making a [script]("http://ubuntuforums.org/showthread.php?t=486359") and I need to know how can I get the thumbnail name from the file name.

In ~/.thumbnails/normal the names are something like:
001a54b1cd1af4c57ee9bba53949fdd7.png

I can't figure out the corresponding file name (I am a newbie).

---

### Post by ssam on 2008-01-13
looks like it could be an md5sum.

use

```
md5sum original-picture.png
```

which will give you a long hex string like that.

---

### Post by Yuzem on 2008-01-13
Thanks but there is a problem.

I did:
```
md5sum some-picture.png
```

The result is something like this:
1007ae4dbd7796f569d974ceb1c82b74

"some-picture.png" has a thumbnail but when a do:
```
cp ~/.thumbnails/normal/1007ae4dbd7796f569d974ceb1c82b74.png ~/Desktop/thumb.png
```
It tells me that it doesn't exist.
I tried twice with different pictures with no luck.

Also, when I do that with a large video file (700mb) it takes too long.
It doesn't take that much to make the thumbnail from nautilus.

---

### Post by winch on 2008-01-13
Try the method described here,
[http://library.n0i.net/graphics/th-umbs/thumbsave.html](http://library.n0i.net/graphics/th-umbs/thumbsave.html)

edit: above method works with thumbnails created by thunar.

---

### Post by kevykev on 2008-01-13
Not sure, but I think it might be the md5sum of the filename and not the file itself. I.e.
```

$ echo "filename" | md5sum

```

---

### Post by tomchuk on 2008-01-13
Correct, the thumbnail filename is an md5 of the filename. However the filename is the absolute URI to the image (without a newline).

So you need to do:
```

echo -n 'file:///home/yuzem/pics/foo.jpg' | md5sum

```

The -n argument to echo will prevent a newline from being printed after the filename (which would affect the md5sum)

You could also use a little python and the gnome python bindings to make this easy:
```

#!/usr/bin/env python

import gnome.ui, gnomevfs, os.path, sys

if len(sys.argv) < 2:
  print 'Usage: %s PATH' % (sys.argv[0])
  sys.exit(1)

path = os.path.abspath(sys.argv[1])
uri = gnomevfs.get_uri_from_local_path(path)
for type in ['normal', 'large']:
  thumb = gnome.ui.thumbnail_path_for_uri(uri, type)
  print "%8s%72s" % (type, thumb)

```

And run it like so:
```

$ ./thumbpath.py pics/t.jpg 
  normal    /home/thomas/.thumbnails/normal/89b89451402319ecaf02a5dc71075354.png
   large     /home/thomas/.thumbnails/large/89b89451402319ecaf02a5dc71075354.png

```

---

### Post by Yuzem on 2008-01-13
> **tomchuk said:**
> 
So you need to do:
```

echo -n 'file:///home/yuzem/pics/foo.jpg' | md5sum

```


Thanks a lot! That worked perfectly.

---

### Post by Yuzem on 2008-01-13
There are some problem... :(

1_If the filename contains spaces it doesn't work.

2_When I copy my thumbnail to the correct path nautilus overwrite it.
I think the problem is explained [here]("http://library.n0i.net/graphics/th-umbs/creation.html") but how can I add those png keys from the command line?
Gimp doesn't seem to show them.

---

### Post by ssam on 2008-01-14
just realised that md5summing the whole file would be too time consuming. my next guess would be the md5sum of the path, but it has already been said :-)

what language are you programming in? if it has a built in md5sum function it may fix the space problem.

---

### Post by Yuzem on 2008-01-14
I' am programming in bash.

---

### Post by ssam on 2008-01-14
i found the spec.
[http://www.freedesktop.org/wiki/Specifications](http://www.freedesktop.org/wiki/Specifications)
says it should be at
[http://jens.triq.net/thumbnail-spec/index.html](http://jens.triq.net/thumbnail-spec/index.html)
but that server seems to be in a bad mood. archive.org have a cache though
[http://web.archive.org/web/20070705050149/jens.triq.net/thumbnail-spec/index.html](http://web.archive.org/web/20070705050149/jens.triq.net/thumbnail-spec/index.html)

about the spaces. it seems that they are being url encoded. so ' ' (space) goes to '%20'. i am not sure what other characters get encoded.

or you could call the above python script from bash (i have compressed it is a way that make Guido van Rossum cry, sorry)
```

FILE_PATH='Desktop/test.png'
THUMB_PATH=`python -c "import gnome.ui, gnomevfs, os.path; print gnome.ui.thumbnail_path_for_uri(gnomevfs.get_uri_from_local_path(os.path.abspath('$FILE_PATH')), 'normal')"`
echo $THUMB_PATH

```
(also it only does the nomal size, just change where is says normal if you need)

---

### Post by Yuzem on 2008-01-14
Thanks a lot for your help!

I was able to see the tags for the thumbnail with:
```
identify -verbose some_thumb.png
```

To set the tag:
```
convert -set Thumb::URI 'path/2/original.avi' -set Thumb::MTime 1200024231 some_thumb.png some_thumb.png
```

---

### Post by Yuzem on 2008-01-21
I have a related question.
Maybe I should open a new thread but I decided to ask here first.

I have the thumbnails working with nautilus but thunar overwrites them every time.

An strange thing is that if I move the file that has the custom thumbnail to another place an then move it back from nautilus the thumbnail will work in thunar.

Comparing my thumbnail with one that does work using "identify -verbose" I found a difference.

The one that works has:
Background Color: white
The one that does not works has:
Background Color: black

Imagemagick doesn't let me to change this. Is there another way to set the correct thumbnail properties? Maybe with python? 

Searching the web I found a ROX-Filer thumbnailer and looking at the code I found this:
```
    def store_image(self, img, inname, outname, ow, oh):
        """Store the thumbnail image it the correct location, adding
        the extra data required by the thumbnail spec."""
        s=os.stat(inname)

        img.save(outname+self.fname, 'png',
             {'tEXt::Thumb::Image::Width': str(ow),
              'tEXt::Thumb::Image::Height': str(oh),
              "tEXt::Thumb::Size": str(s.st_size),
              "tEXt::Thumb::MTime": str(s.st_mtime),
              'tEXt::Thumb::URI': rox.escape('file://'+inname),
              'tEXt::Software': self.name})
        os.rename(outname+self.fname, outname)
```

But I don't know how to use it like in the example above...

---

