---
title: "Calling All Pythoneers!!"
date: 2005-10-23
forum: Programming Talk
---

### Post by kudu on 2005-10-23
I need your help, please.

I'm trying to learn this blasted language, reading "Game Programming with Python."

When I try to run the example code I get these errors:

kudu@ubuntu:~/python/gpwp/chapter4$ python main.py
Traceback (most recent call last):
  File "main.py", line 48, in ?
    run()
  File "main.py", line 42, in run
    core.init(width, height)
  File "/usr/lib/python2.4/site-packages/pyui/core.py", line 65, in init
    from renderers.openglPygame import OpenGLPygame
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglPygame.py", line 25, in ?
    from pyui.renderers import openglBase
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglBase.py", line 49, in ?
    from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC
  File "/usr/lib/python2.4/site-packages/OpenGL/WGL/__init__.py", line 2, in ?
    from WGL__init__ import *
ImportError: No module named WGL__init__

Can anyone please help me sort this out ?? I seem to have everything but it just doesn't work. Thanks!

---

### Post by ssam on 2005-10-23
looks like you are missing a python module.

in synaptic search for python. it will list hundreds of modules, install the relevent ones and try again.

it looks like you have got quite a complicated example to start with. maybe you should find a beginners tutorial and learn the basics first. then move on to advanced stuff.

sam

---

### Post by kudu on 2005-10-23
No doubt you're right, but nevertheless, the example should run. I double-checked synaptic and I have just about every python2.4 package installed.

I have PyUI-0.95 and PyGame installed. My /usr/lib/python2.4/site-packages/ directory seems to contain all the files referred to by the error messages.

So why the heck doesn't it fly ??

I tried importing OpenGL.WGL to see if I could run dir() on it and got this:

>>> import OpenGL.WGL
Traceback (most recent call last):
  File "<input>", line 1, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/WGL/__init__.py", line 2, in ?
    from WGL__init__ import *
ImportError: No module named WGL__init__

Now in /usr/lib/python2.4/site-packages/OpenGL/WGL is this:

__init__.py
__init__.pyc
__init__.pyo

and that's it.

__init__.py consists of:

"""Minimal wrapper for the OpenGL.WGL module"""

from WGL__init__ import *



# now import all the "special" names that got skipped...

__api_version__ = WGL__init__.__api_version__

__author__ = WGL__init__.__author__

__date__ = WGL__init__.__date__

__doc__ = WGL__init__.__doc__

__version__ = WGL__init__.__version__



So, is there something missing from the python2.4-opengl package in synaptic??

---

### Post by cwaldbieser on 2005-10-23
[QUOTE=kudu]I need your help, please.

I'm trying to learn this blasted language, reading "Game Programming with Python."

When I try to run the example code I get these errors:

kudu@ubuntu:~/python/gpwp/chapter4$ python main.py
Traceback (most recent call last):
  File "main.py", line 48, in ?
    run()
  File "main.py", line 42, in run
    core.init(width, height)
  File "/usr/lib/python2.4/site-packages/pyui/core.py", line 65, in init
    from renderers.openglPygame import OpenGLPygame
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglPygame.py", line 25, in ?
    from pyui.renderers import openglBase
  File "/usr/lib/python2.4/site-packages/pyui/renderers/openglBase.py", line 49, in ?
    from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC
  File "/usr/lib/python2.4/site-packages/OpenGL/WGL/__init__.py", line 2, in ?
    from WGL__init__ import *
ImportError: No module named WGL__init__

Can anyone please help me sort this out ?? I seem to have everything but it just doesn't work. Thanks![/QUOTE]

Looks like the last line ought to be
```

from WGL.__init__ import *

```
Looks like the period is missing.  That is why it is saying there is no module named "WGL__init__".  There is an "__init__" module under the "WGL" package, though.

---

### Post by lrmall01 on 2005-10-23
Well, I too am a fledgling python programmer, and I have also been learning the language messing around with simple games.  I haven't read the book your referring to, but maybe I can help.

I have run into problems before trying to get the livewires and pygsear packages to install.  It seemed that all my problems went away once I installed the python-dev package.  However, it doesn't appear your trying to install anything, so this may not help you.  

I notice that it mentions Pygame, so be sure to install that and maybe the python-opengl package.

Hope this helps!
==========

Oops - looks like you guys have advanced well beyond my suggestions in the time that it took me to type it up! :-)

---

### Post by thumper on 2005-10-23
Do you have pyopengl installed?

A quick google showed this as the base package for WGL__init__.  I didn't see PyUI in the Breezy repositories, did you install that manually?

---

### Post by kudu on 2005-10-23
[QUOTE=cwaldbieser]Looks like the last line ought to be
```

from WGL.__init__ import *

```
Looks like the period is missing.  That is why it is saying there is no module named "WGL__init__".  There is an "__init__" module under the "WGL" package, though.[/QUOTE]

Well, I added a "." to it thus "WGL.__init__.py" but it still doesn't work. Same error message as before. Did I do that right ?

---

### Post by kudu on 2005-10-23
[QUOTE=thumper]Do you have pyopengl installed?

A quick google showed this as the base package for WGL__init__.  I didn't see PyUI in the Breezy repositories, did you install that manually?[/QUOTE]

Yes I have PyGame and python2.4-opengl installed from synaptic, and I manually installed PyUI-095 as per directions in the Python doc tutorial regarding importing modules. PyUI is in, I can import pyui and run dir() on it. Works fine as far as I can tell.

I just now also installed python-opengl package, but it STILL doesn't work.

---

### Post by thumper on 2005-10-23
Tried **import OpenGL.WGL**?

My guess is that it will fail (from your previous post's error message).

No idea what this package does exactly, but I think it is where the problem is.

---

### Post by thumper on 2005-10-23
Another quick google took me to this page [http://pyopengl.sourceforge.net/pydoc/OpenGL.WGL.html](http://pyopengl.sourceforge.net/pydoc/OpenGL.WGL.html) which suggests that WGL is windows specific.

Seems to be a bug somewhere...

---

### Post by kudu on 2005-10-23
[QUOTE=thumper]Tried **import OpenGL.WGL**?

My guess is that it will fail (from your previous post's error message).

No idea what this package does exactly, but I think it is where the problem is.[/QUOTE]


Tried it, failed. All same error message.

---

### Post by kudu on 2005-10-23
[QUOTE=thumper]Another quick google took me to this page [http://pyopengl.sourceforge.net/pydoc/OpenGL.WGL.html](http://pyopengl.sourceforge.net/pydoc/OpenGL.WGL.html) which suggests that WGL is windows specific.

Seems to be a bug somewhere...[/QUOTE]


Hmmm...so much for cross-platform, eh ? :)

Thanks for the help though, appreciated. Weird that WGL is onboard if it's Windows specific. Why bother ?

---

### Post by kudu on 2005-10-23
I tried an experiment. This is the openglBase.py file in the renderers folder in pyui with the bit about OpenGL.WGL commented out. Specifically this line:

#from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC


And this is the entire file:

# PyUI

# Copyright (C) 2001-2002 Sean C. Riley

# 

# This library is free software; you can redistribute it and/or

# modify it under the terms of version 2.1 of the GNU Lesser General Public

# License as published by the Free Software Foundation.

# 

# This library is distributed in the hope that it will be useful,

# but WITHOUT ANY WARRANTY; without even the implied warranty of

# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU

# Lesser General Public License for more details.

# 

# You should have received a copy of the GNU Lesser General Public

# License along with this library; if not, write to the Free Software

# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA



""" GL portions of pyui

"""





TEXTURE_ROTATE_90 = 1

TEXTURE_ROTATE_180 = 2

TEXTURE_ROTATE_270 = 3

TEXTURE_MIRROR_H = 4

TEXTURE_MIRROR_V = 5



USE_TRUETYPE_FONTS = 0



import sys

import time



import pyui



if USE_TRUETYPE_FONTS:

    try:

        import win32ui

    except:

        print "UNABLE TO IMPORT win32ui. Using GLUT text renderering"

        USE_TRUETYPE_FONTS = 0

    



from pyui.renderer3d import Renderer3DBase

from pyui.desktop import getDesktop



from OpenGL.GL import *

from OpenGL.GLU import *

from OpenGL.GLUT import *



#from OpenGL.WGL import wglUseFontBitmaps, wglGetCurrentDC



######################################################

## Utility functions

##

######################################################



class OpenGLBase(Renderer3DBase):

    """ OpenGL pyui renderer functionality. This is incomplete - it requires a wrapper of

    either GLUT or PyGame which are implemented as seperate renderers that derive from this

    renderer. All common functionality lives here though.



    #TODO:  fix clipping

    """



    name = "GL"

    

    def __init__(self, w, h, fullscreen, title):

        Renderer3DBase.__init__(self, w, h, fullscreen, title)

        self.frame = 0

        self.last = time.time()

        self.width = w

        self.height = h

        self.fontId = 50000

        self.fonts = {}

        self.textures = {}

        

        pyui.locals.K_SHIFT     = 304

        pyui.locals.K_CONTROL   = 306

        pyui.locals.K_ALT       = 308



        pyui.locals.K_PAGEUP    = 280

        pyui.locals.K_PAGEDOWN  = 281

        pyui.locals.K_END       = 279

        pyui.locals.K_HOME      = 278



        pyui.locals.K_LEFT      = 276

        pyui.locals.K_UP        = 273

        pyui.locals.K_RIGHT     = 275

        pyui.locals.K_DOWN      = 274        



        pyui.locals.K_INSERT    = 277

        pyui.locals.K_DELETE    = 127



        pyui.locals.K_PAD0      = 256

        pyui.locals.K_PAD1      = 257

        pyui.locals.K_PAD2      = 258

        pyui.locals.K_PAD3      = 259

        pyui.locals.K_PAD4      = 260

        pyui.locals.K_PAD5      = 261

        pyui.locals.K_PAD6      = 262

        pyui.locals.K_PAD7      = 263

        pyui.locals.K_PAD8      = 264

        pyui.locals.K_PAD9      = 265



        pyui.locals.K_PADDIVIDE = 267

        pyui.locals.K_PADTIMES  = 268

        pyui.locals.K_PADMINUS  = 269

        pyui.locals.K_PADPLUS   = 270

        pyui.locals.K_PADENTER  = 271

        pyui.locals.K_PADDECIMAL= 266



        pyui.locals.K_F1        = 282

        pyui.locals.K_F2        = 283

        pyui.locals.K_F3        = 284

        pyui.locals.K_F4        = 285

        pyui.locals.K_F5        = 286

        pyui.locals.K_F6        = 287

        pyui.locals.K_F7        = 288

        pyui.locals.K_F8        = 289

        pyui.locals.K_F9        = 290

        pyui.locals.K_F10       = 291

        pyui.locals.K_F11       = 292

        pyui.locals.K_F12       = 293



        self.keyMap = {

            100: pyui.locals.K_LEFT,

            101: pyui.locals.K_UP,

            102: pyui.locals.K_RIGHT,

            103: pyui.locals.K_DOWN

            }



        if not USE_TRUETYPE_FONTS or sys.platform != "win32":

            print "Using GLUT fonts"

            self.createFont = self.createFont_OLD

            self.getTextSize = self.getTextSize_OLD

        else:

            print "Using True-Type fonts"



        self.drawBackMethod = self.clear

        

    ###############################################################################

    ### Draw Primatives functions

    ###############################################################################



    def drawRect(self, color, rect):

        """Fills a rectangle with the specified color."""

        glBegin(GL_QUADS)

        glColor4ub( color[0], color[1], color[2], color[3] )

        glVertex2i(rect[0], rect[1])

        glVertex2i(rect[0] + rect[2], rect[1])

        glVertex2i(rect[0] + rect[2], rect[1] + rect[3])

        glVertex2i(rect[0], rect[1] + rect[3])

        glEnd()



    def drawText(self, text, pos, color, font = None):

        """Draws the text on the screen in the specified position.

        """

        if USE_TRUETYPE_FONTS:

            self.do_text(text, (pos[0], pos[1]), color, font)

        else:

            self.do_text_OLD(text, (pos[0], pos[1]), color, font)            

        

    def drawGradient(self, rect, c1, c2, c3, c4):

        """Draws a gradient rectangle"""

        glBegin(GL_QUADS)

        glColor4ub( c1[0], c1[1], c1[2], c1[3] )

        glVertex2i(rect[0], rect[1])                        # top left

        glColor4ub( c2[0], c2[1], c2[2], c2[3] )        

        glVertex2i(rect[0] + rect[2], rect[1])              # top right

        glColor4ub( c4[0], c4[1], c4[2], c4[3] )

        glVertex2i(rect[0] + rect[2], rect[1] + rect[3])    # bottom right

        glColor4ub( c3[0], c3[1], c3[2], c3[3] )

        glVertex2i(rect[0], rect[1] + rect[3])              # bottom left

        glEnd()

        

    def drawLine(self, x1, y1, x2, y2, color):

        """Draws a line"""

        glBegin(GL_LINES)

        glColor4ub( color[0], color[1], color[2], color[3] )

        glVertex2i(x1, y1)

        glVertex2i(x2, y2)

        glEnd()

        

    def drawImage(self, rect, filename, pieceRect = None):

        """Draws an image at a position."""

        textureCoords = [[0.0,1.0],[1.0,1.0],[1.0,0.0],[0.0,0.0]]



        if not self.textures.has_key(filename):

            self.loadTexture(filename)

        texture = self.textures[filename]



        glColor4ub( 255, 255, 255, 255 )

        glEnable(GL_TEXTURE_2D)

        glBindTexture( GL_TEXTURE_2D, texture)



        glBegin(GL_QUADS)

        glTexCoord2f(textureCoords[0][0], textureCoords[0][1])

        glVertex2i( rect[0], rect[1])

        glTexCoord2f(textureCoords[1][0], textureCoords[1][1])

        glVertex2i( rect[0] + rect[2], rect[1])

        glTexCoord2f(textureCoords[2][0], textureCoords[2][1])

        glVertex2i( rect[0] + rect[2], rect[1] + rect[3])

        glTexCoord2f(textureCoords[3][0], textureCoords[3][1])

        glVertex2i( rect[0], rect[1] + rect[3])

        glEnd()



        glDisable(GL_TEXTURE_2D)



    def drawImageRotated(self, rect, filename, rotDegrees=0, textureEffect=0):

        """Draws an image at a position."""



        if textureEffect == TEXTURE_ROTATE_90:

            textureCoords = [[0.0,0.0],[0.0,1.0],[1.0,1.0],[1.0,0.0]]

        elif textureEffect == TEXTURE_ROTATE_180:

            textureCoords = [[1.0,0.0],[0.0,0.0],[0.0,1.0],[1.0,1.0]]

        elif textureEffect == TEXTURE_ROTATE_270:       

            textureCoords = [[1.0,1.0],[1.0,0.0],[0.0,0.0],[0.0,1.0]]

        elif textureEffect == TEXTURE_MIRROR_H:

            textureCoords = [[1.0,1.0],[0.0,1.0],[0.0,0.0],[1.0,0.0]]

        elif textureEffect == TEXTURE_MIRROR_V:

            textureCoords = [[0.0,0.0],[1.0,0.0],[1.0,1.0],[0.0,1.0]]

        else:

            textureCoords = [[0.0,1.0],[1.0,1.0],[1.0,0.0],[0.0,0.0]]



        if not self.textures.has_key(filename):

            self.loadTexture(filename)



        texture = self.textures[filename]



        glColor4ub( 255, 255, 255, 255 )

        glEnable(GL_TEXTURE_2D)

        glBindTexture( GL_TEXTURE_2D, texture)



        halfwidth = rect[2] / 2

        halfheight = rect[3] / 2



        glPushMatrix()

        glTranslate(rect[0] + (halfwidth), rect[1] + (halfheight), 0.0)

        glRotate(rotationDegrees, 0.0, 0.0, 1.0)      # Rotate



        glBegin(GL_QUADS)

        glTexCoord2f(textureCoords[0][0], textureCoords[0][1])

        glVertex2i( -halfwidth, -halfheight)        

        glTexCoord2f(textureCoords[1][0], textureCoords[1][1])

        glVertex2i( halfwidth, -halfheight)

        glTexCoord2f(textureCoords[2][0], textureCoords[2][1])

        glVertex2i( halfwidth, halfheight)

        glTexCoord2f(textureCoords[3][0], textureCoords[3][1])

        glVertex2i( -halfwidth, halfheight)



        glEnd()

        glPopMatrix()



        glDisable(GL_TEXTURE_2D)

        

    def loadImage(self, filename, label = None):

        if not filename:

            return

        self.loadTexture(filename, label)



    def setClipping(self, rect = None):

        """set the clipping rectangle for the main screen. defaults to clearing the clipping rectangle.

        NOTE: isn't working..."""

        return

        if rect:

            offsets = glGetIntegerv( GL_MODELVIEW_MATRIX )

            corrected = (offsets[3][0] + rect[0], getDesktop().height - offsets[3][1] - rect[3] - rect[1], rect[2], rect[3])

            self.clip_stack.append( corrected )

        elif len( self.clip_stack ):

            self.clip_stack = self.clip_stack[0:-1]



        if len( self.clip_stack ) and self.clip_stack[-1][2] > 0 and self.clip_stack[-1][3] > 0:

            glEnable(GL_SCISSOR_TEST)

            apply( glScissor, self.clip_stack[-1] )

        else:

            glDisable(GL_SCISSOR_TEST)

        pass

        



    ###############################################################################

    ### methods to be implemented by GL wrappers

    ###############################################################################

        

    def draw(self, windows):

        """To be implemented by GLUT or PyGame

        """

        raise

        

    def update(self):

        pass



    def getModifiers(self):

        raise

    



    def quit(self):

        raise

    



    def clear(self):

        glClear(GL_COLOR_BUFFER_BIT|GL_DEPTH_BUFFER_BIT)

        self.clip_stack = []





    def packColor(self, r, g, b, a = 255):

        """pack the rgb triplet into a color

        """

        return (r, g, b, a)



    def dirtyCollidingWindows(self, inRect):

        """Dont do dirty rects in 3D"""

        return



    def setup2D(self):

        """Setup everything on the opengl Stack to draw in 2D in a way that can be torn down later.

        """

        glMatrixMode(GL_PROJECTION)

        glPushMatrix()

        glLoadIdentity()

        glOrtho( 0, getDesktop().width, getDesktop().height, 0, -1, 1 )



        glMatrixMode(GL_MODELVIEW)

        glPushMatrix()

        glLoadIdentity()



        glDisable(GL_DEPTH_TEST)

        glEnable(GL_SCISSOR_TEST)



        glEnable(GL_BLEND)

        glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA)



    def teardown2D(self):

        """tear down the 2D stuff to revert to the previous state.

        """

        glPopMatrix()    

        glMatrixMode(GL_PROJECTION)

        glPopMatrix()

        glEnable(GL_DEPTH_TEST)

        glDisable(GL_SCISSOR_TEST)



    def ReSizeGLScene(self, Width, Height):

        # Prevent A Divide By Zero If The Window Is Too Small     

        if Height == 0:	

            Height = 1



        # Reset The Current Viewport And Perspective Transformation

        glViewport(0, 0, Width, Height)		

        glMatrixMode(GL_PROJECTION)

        glLoadIdentity()

        gluPerspective(45.0, float(Width)/float(Height), 0.1, 100.0)

        glMatrixMode(GL_MODELVIEW)

        self.width = Width

        self.height = Height



    def getScreenSize(self):

        """ Returns (width, height) of the scene viewport

        """

        return (self.width, self.height)



    def loadTexture(self, filename, label = None):

        pass

    

    def setWindowOrigin(self, winX, winY ):

        glMatrixMode(GL_MODELVIEW)

        glLoadIdentity()

        glTranslatef(winX, winY, 0)

        

    ######################################################

    ## 2D drawing functions.

    ##

    ## These assume that we are in a 2D state as setup by the

    ## setup2D() function.

    ##

    ######################################################



    def do_text(self, text, position, color, font ):

        """Draw some text to the screen using a bitmapped font"""

        #print "Drawing:", text

        if len(text) < 1:

            return



        if not font:

            font = pyui.desktop.getTheme().defaultFont



        (name, size, flags) = self.fonts[font]

        #print "do_text:", font, self.fontId, name, size, text, position, color

        

        glColor4ub( color[0], color[1], color[2], color[3] )

        glRasterPos2i(position[0], position[1] + size*1.2)

        glListBase(font)

        glCallLists(text)



    def getTextSize(self, text, font = None):

        """gets the width and height of a piece of text."""

        if not font:

            font = pyui.desktop.getTheme().defaultFont

        (name, size, flags) = self.fonts[font]

        return (size*len(text), (int)(size*1.4) )



    def createFont(self, fontName, fontSize, flags):

        """Create a font. returns a handle. NOTE: This wont work on LINUX!!!!

        """

        handle = self.fontId

        self.fontId += 256



        props = {"name":fontName, "height":(int)(fontSize*1.2), "charset":0, "weight":1, "pitch and family":18}

        if flags & pyui.locals.ITALIC:

            props["italic"] = 1

        if flags & pyui.locals.UNDERLINE:

            props["underline"] = 1

        if flags & pyui.locals.BOLD:

            props["weight"] = 128

            

        pf = win32ui.CreateFont( props )

        hdc = wglGetCurrentDC()

        pdc = win32ui.CreateDCFromHandle(hdc)



        

        old = pdc.SelectObject(pf)

        result = wglUseFontBitmaps(hdc , 0, 255, handle)

        if not result:

            print "ERROR!"

        pdc.SelectObject(old)



        self.fonts[handle] = (fontName, fontSize, flags)

        del pf

        del pdc



        return handle





    def createFont_OLD(self, fontName, fontSize, flags):

        pass

    

    def getTextSize_OLD(self, text, font = None):

        """This text method uses the old GLUT rendering instead of True Type fonts.

        """

        if font == 'fixed':

            return ( 8 * len( text ), 13 )        

        w = 0

        for c in text:

            w += glutBitmapWidth(GLUT_BITMAP_HELVETICA_12, ord(c))

        return (w, pyui.locals.TEXT_HEIGHT)







    def do_text_OLD(self, text, position, color, font ):

        """This text method uses the old GLUT rendering instead of True Type fonts.

        """

        glColor4ub( color[0], color[1], color[2], color[3] )

        glRasterPos2f(position[0], position[1]+13)

        if font == 'fixed':

            font = GLUT_BITMAP_8_BY_13

        else:

            font = GLUT_BITMAP_HELVETICA_12

        for char in text:

            glutBitmapCharacter(font, ord(char))



Now the source code will run, but it crashes my python editor when it does. How can I tweek it so it will run correctly ? Any ideas ?

kudu

---

### Post by cwaldbieser on 2005-10-23
[QUOTE=kudu]Well, I added a "." to it thus "WGL.__init__.py" but it still doesn't work. Same error message as before. Did I do that right ?[/QUOTE]
I looked at it again, and it really is looking for a module called "WGL__init__" to import.  It appears as though the module is not installed on the system, though.  I would think it ought ought to be included in the package, but it doesn't look like it is.

The "__init__.py" file in the WGL folder is a required initializer in a python package.  In this case, the WGL package is really a (mostly) empty folder, but the initializer is trying to import names from the WGL__init__ module into it.  Presumably the WGL__init__ module does all the real work.

---

### Post by kudu on 2005-10-23
[QUOTE=cwaldbieser]I looked at it again, and it really is looking for a module called "WGL__init__" to import.  It appears as though the module is not installed on the system, though.  I would think it ought ought to be included in the package, but it doesn't look like it is.

The "__init__.py" file in the WGL folder is a required initializer in a python package.  In this case, the WGL package is really a (mostly) empty folder, but the initializer is trying to import names from the WGL__init__ module into it.  Presumably the WGL__init__ module does all the real work.[/QUOTE]

I believe the WGL stuff is specific to the Windows OS, in this case has to do with using Windows fonts if running in windows OS. Since commenting out the call to import the WGL__init__ module, the code works defaulting to Glut fonts. So I guess that did the trick. Crashing my python editor is another unrelated issue. I'm using Stani's Python Editor and/or Gedit (my favorite). :)

Thanks to all for the help, I really appreciate it a lot!

kudu

---

### Post by jrbj on 2005-10-23
If I remember correctly, PyUI was last working with Python 2.1 and Pygame 1.1.

It's a real old module, and hasn't been worked on in a long time. I'm not surprised that it doesn't work.

Edit:


Have you seen this thread about WGL in the PyUI's sourceforge site:
[http://sourceforge.net/forum/forum.php?thread_id=1072557&forum_id=86574](http://sourceforge.net/forum/forum.php?thread_id=1072557&forum_id=86574)

---

### Post by kudu on 2005-10-23
[QUOTE=jrbj]If I remember correctly, PyUI was last working with Python 2.1 and Pygame 1.1.

It's a real old module, and hasn't been worked on in a long time. I'm not surprised that it doesn't work.

Edit:


Have you seen this thread about WGL in the PyUI's sourceforge site:
[http://sourceforge.net/forum/forum.php?thread_id=1072557&forum_id=86574](http://sourceforge.net/forum/forum.php?thread_id=1072557&forum_id=86574)[/QUOTE]

Seems to be working OK now. I'll check out the thread. Thanks.

---

