---
title: "Script for Font DPI Calculation"
date: 2009-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by samjh on 2009-05-02
Ubuntu defaults to 96 dpi for font rendering.  If you're using Gnome, font settings can be changed in System -> Preferences -> Appearance -> Fonts -> Details.

96 dpi is not the correct setting for most systems.  Having the correct dpi will render fonts on screen using correct sizes, the way typographers intended for them to be rendered.  If you do desktop publisher or similar work, it may be advantageous to find the correct font dpi.

Attached is a Python script to calculate the correct dpi for your system.  Input the horizontal resolution, vertical resolution, and screen size as parameters, and the script will calculate the dpi for you.  The code is self-explanatory.

```
#! /usr/bin/env python

import sys, math

def calculatedpi():
	hres = float(sys.argv[1])
	vres = float(sys.argv[2])
	dsize = float(sys.argv[3])
	hdpi = hres / (hres / math.sqrt(hres**2 + vres**2) * dsize)
	print "Your screen's dpi =", int(hdpi)

def main():
	argerror = False

	if len(sys.argv) < 4:
		argerror = True
	else:
		for arg in sys.argv[1:]:
			if arg.isdigit() == False:
				argerror = True

	if argerror == True:
		print "DPI calculator\n"
		print "Usage: dpi hres vres size\n"
		print "Where:"
		print "  hres = horizontal resolution in pixels"
		print "  vres = vertical resolution in pixels"
		print "  size = size of screen in inches\n"
		print "Example:"
		print "  dpi 1280 1024 19"
		print "  Your screen's dpi = 86\n"
	else:
		calculatedpi()

if __name__ == "__main__":
	main()
```

This is also posted at my blog:
[http://www.xessnet.com/2009/05/02/script-for-font-dpi-calculation/](http://www.xessnet.com/2009/05/02/script-for-font-dpi-calculation/)

---

