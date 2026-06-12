---
title: "PythonMagick: Convert image to gray scale (black &amp; white)"
date: 2010-03-23
forum: Programming Talk
---

### Post by moma on 2010-03-23
Hello,

I want to use PythonMagick to convert an image to gray scale. PythonMagick is a Python wrapper to ImageMagick++ library. PythonMagick has no documentation on its own but Magick++ is documented here [http://www.imagemagick.org/Magick++](http://www.imagemagick.org/Magick++) 

I cannot figure how to access the GrayscaleType attribute in PythonMagick. Can you help?

Sample code:
[PHP]import PythonMagick

filename = "test1.png"
img = PythonMagick.Image()
img.read(filename)

img.type = GrayscaleType

#img.quantizeColorSpace(?)
#img.quantize()
#img.channel(PythonMagick.ChannelType.RedChannel ??)

img.write("test2.png")[/PHP]

The PythonMagick package:
$ apt-cache search PythonMagick
python-pythonmagick - Object-oriented Python interface to ImageMagick
----
ps. I do not want to use PIL. I prefer ImageMagick.

---

### Post by moma on 2010-03-24
Is this forum dead or what? No answers, no comments, nada!

Hi,
Never mind people.

I've started to use PythonMagickWand.py which is a ctypes binding to MagickWand. Ref.: [http://www.procoders.net/index.php?s=pythonmagick](http://www.procoders.net/index.php?s=pythonmagick)

Very nice solution because it reveals all MagickWand fucntions to Python. The manual: [http://www.imagemagick.org/script/magick-wand.php](http://www.imagemagick.org/script/magick-wand.php)

I've earlier used MagickWand in Gscreendump
[http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_imagemagick.c](http://code.google.com/p/gscreendump/source/browse/trunk/src/sd_imagemagick.c)

One thing though,
PythonMagickWand.py lacks a definition for PixelSetColor() function so I added it to my local copy.

[PHP]# bool PixelSetColor( PixelWand pxl_wnd, string imagemagick_col_str )
# Ref: http://www.magickwand.org/PixelSetColor.html

try:
    _magick.PixelSetColor.restype = MagickStatusType
    _magick.PixelSetColor.argtypes = (PixelWand, ctypes.POINTER(ctypes.c_char), )
except AttributeError,e:
    print e
else:
    PixelSetColor = _magick.PixelSetColor[/PHP]

Here is a prototype how I use the MagickWand binding from Python.

[PHP](FLIP_VERTICAL,
 FLIP_HORIZONTAL) = range(2)

def get_str(ctypes_str):
    if ctypes_str == None: return ""
    i = 0
    s = ""
    while 1:
        c = ctypes_str[i]
        if ord(c) == 0: return s
        s += c
        i += 1

def magickwand_get_err_msg(img):
    severity = MagickGetExceptionType(img)
    err = MagickGetException(img, severity)
    s = get_str(err)
    MagickRelinquishMemory(err)
    return s

def magickwand_flip_image(wand, direction):
    # Image name 
    filename = get_str(MagickGetImageFilename(wand))

    if direction == FLIP_VERTICAL:
        status = MagickFlipImage(wand)
    else:
        # direction == FLIP_HORIZONTAL
        status = MagickFlopImage(wand)

    if status.value != True:
        err = magickwand_get_err_msg(wand)
        err_msg = "ImageMagick: Cannot flip the image %s. %s.\n" % ( filename, err,)
        raise ImageMagickException(err_msg)

    return wand


def magickwand_call_function(filename_from, filename_to, func_cb, *args):
    ret = False

    try:
        # Open the image
        wand = NewMagickWand()
        status = MagickReadImage(wand, filename_from)

        if status.value != True:
            err = magickwand_get_err_msg(wand)
            MagickClearException(wand)
            err_msg = "ImageMagick: Cannot open image %s. %s.\n" % (filename_from, err,)
            raise ImageMagickException(err_msg)


        # Call the MagickWand function.
        func_cb(wand, *args)

        MagickClearException(wand)

        # Save the image

        # This seq faults if the file is write protected.
        # status = MagickWriteImage(image, filename);  

        if filename_from == filename_to or filename_to == None:
            filename = filename_from
        else:
            filename = filename_to 

        # This is more manageable
	    status = MagickWriteImages(wand, filename, MagickTrue)

        if status.value != True:
            err = magickwand_get_err_msg(wand)
            MagickClearException(wand)
            err_msg = "ImageMagick: Cannot write to %s. %s.\n" % (filename, err,)
            raise ImageMagickException(err_msg)

        ret = True

    except Exception, e:
        import sys
        sys.stderr.write("%s\n" % (e.msg,))

    finally:
	    DestroyMagickWand(wand)

    return ret 

ret = magickwand_call_function("test1.png", "test2.png", magickwand_flip_image, FLIP_VERTICAL)
print "ret=", ret

ret = magickwand_call_function("test1.png", "test3.png", magickwand_flip_image, FLIP_HORIZONTAL)
print "ret=", ret[/PHP]
--------------

Many thanks to those who developed PythonMagickWand.py!

Kindly
  Osmo (Moma) Antero
  Grønland
  [http://www.futuredesktop.org](http://www.futuredesktop.org) ([http://www.futuredesktop.com](http://www.futuredesktop.com))

---

