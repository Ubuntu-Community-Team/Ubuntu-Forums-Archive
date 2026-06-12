---
title: "Python - image histogram"
date: 2010-08-10
forum: Programming Talk
---

### Post by ApEkV2 on 2010-08-10
Hello, I'm writing a little script to print the colors histogram of an image and also the number of occurrences.
However, the way I'm doing it currently is so slow for anything over 200x200 or many colors.
Is there a faster method than what I'm doing?

```
#!/usr/bin/env python

from PIL import Image
from optparse import OptionParser
import sys, gtk, pygtk, time

def Pixbuf2Image(pb, opt):
    '''convert gtk Pixbuf to PIL Image'''
    width, height = pb.get_width(), pb.get_height()
    return Image.fromstring(opt,(width,height),pb.get_pixels())

if __name__ == '__main__':
    parser = OptionParser()
    parser.add_option("-m","--mode",dest="Pal",type="str",default="RGB",metavar="MODE",help = 'Palette')
    parser.add_option("-l","--min" ,dest="Min",type="int",default= 1, metavar="MIN", help = 'Threshold')
    clipboard = gtk.clipboard_get(gtk.gdk.SELECTION_CLIPBOARD)
    (options, args) = parser.parse_args()

# monitor clipboard and wait for an image

    while True:
        data = clipboard.wait_for_image()
        time.sleep(500 / 1000.0)
        if data: break
    try:
        Pass = True; Ltot = []
        Lpix = list(Pixbuf2Image(data, options.Pal).getdata())

# iterate through pixels, loading them into a list and calculating totals

        for INX, x in enumerate(Lpix):
            for INC, y in enumerate(Ltot):
                if x == y[0]:
                    Pass = False
                    Ltot[INC][1] += 1
                    break
                else:
                    Pass = True
                    continue
            if Pass:
                Pass = False
                Ltot.append([x,1])

# print the results

        for z in Ltot:
            if z[1] > options.Min:
                print z[0],"\t\t",z[1]
    except Exception, error:
        print "\Failed:\n%s\n" % error
```
```
# sample output mode RGB

(0, 0, 254) 		490
(0, 0, 255) 		5980
(1, 0, 254) 		12
(0, 0, 253) 		430
(255, 255, 0) 		20983
(254, 254, 0) 		45
(254, 255, 0) 		5467
(1, 0, 1) 		3
(0, 0, 0) 		1098
(1, 1, 0) 		3
(1, 0, 0) 		1090
(0, 1, 0) 		868
(0, 0, 1) 		394
```

---

