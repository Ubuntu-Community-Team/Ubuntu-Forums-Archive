---
title: "Trouble displaying images"
date: 2011-09-18
forum: Programming Talk
---

### Post by stair314 on 2011-09-18
I have a little python script where I display images by writing them to a temp file, calling eog on the temp file, and then calling rm on the temp file after the eog process closes. The relevant code looks basically like this:

```

os.popen('(eog --new-instance tmp.jpg; rm tmp.jpg)&')

```

The --new-instance flag is important; without that, if there is already an eog process, the eog call simply tells the pre-existing eog process to display tmp.jpg and returns right away. rm executes before the pre-existing eog process can open tmp.jpg. The pre-existing eog process then crashes.

Unfortunately, I don't have complete control over some of the systems I use this script on. Some of them have an outdated version of eog installed which does not support --new-instance, and I don't want to burn up my quota space building a local copy.

Is there some way I can launch eog in a way that prevents it from detecting if there are other instances? Or is there another reliable strategy for displaying images in a sophisticated viewer (ie, supports zooming, panning, etc.) that won't clutter up my directory with temp files?

---

### Post by Senesence on 2011-09-19
Can you kill the existing process?

If not, then maybe a short delay before the rm, using the sleep command?

Just a few ideas.

---

### Post by Arndt on 2011-09-19
> **stair314 said:**
> I have a little python script where I display images by writing them to a temp file, calling eog on the temp file, and then calling rm on the temp file after the eog process closes. The relevant code looks basically like this:

```

os.popen('(eog --new-instance tmp.jpg; rm tmp.jpg)&')

```

The --new-instance flag is important; without that, if there is already an eog process, the eog call simply tells the pre-existing eog process to display tmp.jpg and returns right away. rm executes before the pre-existing eog process can open tmp.jpg. The pre-existing eog process then crashes.

Unfortunately, I don't have complete control over some of the systems I use this script on. Some of them have an outdated version of eog installed which does not support --new-instance, and I don't want to burn up my quota space building a local copy.

Is there some way I can launch eog in a way that prevents it from detecting if there are other instances? Or is there another reliable strategy for displaying images in a sophisticated viewer (ie, supports zooming, panning, etc.) that won't clutter up my directory with temp files?

Is it possible to just not remove tmp.jpg? Then there will always be one temporary file there, which does not clutter up too much, perhaps.

---

### Post by stair314 on 2011-09-19
EDIT: oops, didn't see there was more than one reply. Going to reply to both at once and repost.

---

### Post by stair314 on 2011-09-19
> 
Can you kill the existing process?

No, other people use my code and that's not very nice to them. But more importantly that would mean I could never show more than one image at a time.

[QUOTE]
If not, then maybe a short delay before the rm, using the sleep command?
[/QUOTE}
I've tried that, but it has a different problem that I forgot to mention. eog also seems to be slightly buggy, and if you issue too many eog commands simultaneously without the --new-instance, not all of the images will appear. 



[QUOTE]
Is it possible to just not remove tmp.jpg? Then there will always be one temporary file there, which does not clutter up too much, perhaps.
[/QUOTE}

No, it's not literally called tmp.jpg. That was just a simple example intended to be easily readable, not my actual code. I need to be able to display an arbitrary number of images. If I just want to show one I'd use PIL.Image.show. Here's the actual code:

```

import numpy as np
from PIL import Image
import os
from tempfile import NamedTemporaryFile

def show(image):
    """
    Parameters
    ----------
    image: A PIL Image, or a numpy ndarray.
            If ndarray, integer formats are assumed to use 0-255
            and float formats are assumed to use 0-1
    """

    if hasattr(image, '__array__'):
        if image.dtype == 'int8':
            image = np.cast['uint8'](image)
        elif str(image.dtype).startswith('float'):
            image *= 255.
            image = np.cast['uint8'](image)
        try:
            image = Image.fromarray(image)
        except TypeError:            raise TypeError("PIL is whining about being given an ndarray of shape "+str(
image.shape)+" and dtype "+str(image.dtype))

    f = NamedTemporaryFile(mode='r',suffix='.png',delete=False)

    name = f.name

    f.flush()
    f.close()


    image.save(name)

    os.popen('(eog --new-instance '+name+'; rm '+name+') &')

if __name__ == '__main__':
    black = np.zeros((50,50,3),dtype='uint8')

    red = black.copy()
    red[:,:,0] = 255

    green = black.copy()
    green[:,:,1] = 255

    show(black)
    show(green)
    show(red)


```

---

### Post by Arndt on 2011-09-19
> **stair314 said:**
> No, other people use my code and that's not very nice to them. But more importantly that would mean I could never show more than one image at a time.

[QUOTE]
If not, then maybe a short delay before the rm, using the sleep command?
[/QUOTE}
I've tried that, but it has a different problem that I forgot to mention. eog also seems to be slightly buggy, and if you issue too many eog commands simultaneously without the --new-instance, not all of the images will appear. 



[QUOTE]
Is it possible to just not remove tmp.jpg? Then there will always be one temporary file there, which does not clutter up too much, perhaps.
[/QUOTE}

No, it's not literally called tmp.jpg. That was just a simple example intended to be easily readable, not my actual code. I need to be able to display an arbitrary number of images. If I just want to show one I'd use PIL.Image.show. Here's the actual code:

```

import numpy as np
from PIL import Image
import os
from tempfile import NamedTemporaryFile

def show(image):
    """
    Parameters
    ----------
    image: A PIL Image, or a numpy ndarray.
            If ndarray, integer formats are assumed to use 0-255
            and float formats are assumed to use 0-1
    """

    if hasattr(image, '__array__'):
        if image.dtype == 'int8':
            image = np.cast['uint8'](image)
        elif str(image.dtype).startswith('float'):
            image *= 255.
            image = np.cast['uint8'](image)
        try:
            image = Image.fromarray(image)
        except TypeError:            raise TypeError("PIL is whining about being given an ndarray of shape "+str(
image.shape)+" and dtype "+str(image.dtype))

    f = NamedTemporaryFile(mode='r',suffix='.png',delete=False)

    name = f.name

    f.flush()
    f.close()


    image.save(name)

    os.popen('(eog --new-instance '+name+'; rm '+name+') &')

if __name__ == '__main__':
    black = np.zeros((50,50,3),dtype='uint8')

    red = black.copy()
    red[:,:,0] = 255

    green = black.copy()
    green[:,:,1] = 255

    show(black)
    show(green)
    show(red)


```

eog seems to use 'dbus', but I know too little about dbus to give any suggestions. Maybe the best thing is to get the source code and see what it does. It doesn't seem to be a simple lock file.

---

