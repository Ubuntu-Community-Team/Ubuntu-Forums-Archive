---
title: "SimpleCV - getting traceback errors running 1st 'hello world' script"
date: 2013-09-03
forum: Programming Talk
---

### Post by memilanuk on 2013-09-03
So... fully up to date version of Ubuntu 13.04 on my laptop (Lenovo ThinkPad T530), downloaded the SimpleCV 1.3 superpack .deb file and installed it.  When I open up an interactive interpreter, either regular python 2.7 or ipython, I get various errors as shown below:

```
    In [1]: from SimpleCV import Camera, Display, Image
    In [2]: cam = Camera()
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    VIDIOC_QUERYMENU: Invalid argument
    
    In [3]: display = Display()
    ---------------------------------------------------------------------------
    IOError                                   Traceback (most recent call last)
    <ipython-input-3-026b8c705ca8> in <module>()
    ----> 1 display = Display()
    
    /usr/lib/pymodules/python2.7/SimpleCV/Display.pyc in __init__(self, resolution, flags, title, displaytype, headless)
        156         if not displaytype == 'notebook':
        157             self.screen = pg.display.set_mode(resolution, flags)
    --> 158         scvLogo = SimpleCV.Image("simplecv").scale(32,32)
        159         pg.display.set_icon(scvLogo.getPGSurface())
        160         if flags != pg.FULLSCREEN and flags != pg.NOFRAME:
    
    /usr/lib/pymodules/python2.7/SimpleCV/ImageClass.pyc in __init__(self, source, camera, colorSpace, verbose, sample, cv2image)
        785                     self._bitmap = cv.LoadImage(self.filename, iscolor=cv.CV_LOAD_IMAGE_COLOR)
        786                 except:
    --> 787                     self._pil = pil.open(self.filename).convert("RGB")
        788                     self._bitmap = cv.CreateImageHeader(self._pil.size, cv.IPL_DEPTH_8U, 3)
        789                     cv.SetData(self._bitmap, self._pil.tostring())
    
    /usr/lib/python2.7/dist-packages/PIL/Image.pyc in open(fp, mode)
       1986     if isStringType(fp):
       1987         filename = fp
    -> 1988         fp = builtins.open(fp, "rb")
       1989     else:
       1990         filename = ""
    
    IOError: [Errno 2] No such file or directory: '/usr/lib/pymodules/python2.7/SimpleCV/sampleimages/simplecv.png'
    
    In [4]: 
```

...as well as a blank (black) pygame window.  It looks like all of this goes back to one missing .png file?!?  

Any ideas or suggestions welcome.

TIA,

Monte

---

### Post by memilanuk on 2013-09-04
Someone (on another forum) pointed me to the solution here:

[https://github.com/sightmachine/SimpleCV/issues/213](https://github.com/sightmachine/SimpleCV/issues/213)

Appears its an open issue (for over a year now) with the deb package...

---

