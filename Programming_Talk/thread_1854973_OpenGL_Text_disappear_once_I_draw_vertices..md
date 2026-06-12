---
title: "OpenGL: Text disappear once I draw vertices."
date: 2011-10-05
forum: Programming Talk
---

### Post by DarkAmbient on 2011-10-05
Hiya!

Kinda new to OpenGL. But catching up quite fast atleast, with the help from various tutorials. Got this one problem i can't figure out though.

Got this CFont class which holds on to 256 ascii-characters once the font is built. Later on i can print text with:

```

CFont* m_font = new CFont();

m_font->print(position_x, position_y, "some text");

```

And it works. But whenever I draw some vertices on-screen, the text disappear. I've tried both glLoadIdentity() and glPushMatrix() before and glPopMatrix after drawing shapes, nothing helps.

The only other shape I've tested this with was my polygon-mousecursor. Once I draw the mousecursor, the text hide. I made a DisplayList of my mousecursor  after a while, then the text got visible again.

Anyways... first here's where I build the font. Should be sufficient.
```

GLvoid CFont::build_font(void) {

    Display *dpy;          /* Our current X display */
    XFontStruct *fontInfo; /* Our font info */

    /* Storage for 256 characters */
    m_base = glGenLists(256);

    /* Get our current display long enough to get the fonts */
    dpy = XOpenDisplay(NULL);

    /* Get the font information */
    fontInfo = XLoadQueryFont(dpy, "-adobe-helvetica-medium-r-normal--18-*-*-*-p-*-iso8859-1");

    /* If the above font didn't exist try one that should */
    if (!fontInfo) {
	    fontInfo = XLoadQueryFont(dpy, "fixed");
	    /* If that font doesn't exist, something is wrong */
	    if (fontInfo == NULL) {
		    fprintf(stderr, "no X font available?\n");
		}
	}

    /* generate list */
    glXUseXFont(fontInfo->fid, 32, 256, m_base);

    /* Free some memory */
    XFreeFont(dpy, fontInfo);

    /* Close display */
    XCloseDisplay(dpy);

    return;
}
``` 

And here we print out text. Note that I got the **glRasterPos2f(x, y);** that positions the text, inside the print-function.
```

GLvoid CFont::print(GLint x, GLint y, const char *fmt, ...) {

    glRasterPos2f(x, y); // set writing position

    char text[256];
    va_list ap;

    /* If there's no text, do nothing */
    if (fmt == NULL)
	return;

    /* Parses The String For Variables */
    va_start(ap, fmt);
    /* Converts Symbols To Actual Numbers */
    vsprintf(text, fmt, ap);
    va_end(ap);

    /* Pushes the Display List Bits */
    glPushAttrib(GL_LIST_BIT);

    /* Sets base character to 32 */
    glListBase(m_base-32);

    /* Draws the text */
    glCallLists(strlen(text), GL_UNSIGNED_BYTE, text);

    /* Pops the Display List Bits */
    glPopAttrib();

}
```

So if I do this, text disappear.

```

    m_font->print(4, m_render->get_height()-4 , "Down left corner");

//    glPushMatrix(); // <-- should I be here? See no difference.

    glTranslatef(mouse_x, mouse_y, 0);

    glBegin(GL_TRIANGLES);
        glVertex3f(0, 0, 0);;
        glVertex3f(35.f, 20.f, 0);
        glVertex3f(20.f, 35.f, 0);
    glEnd();

//     glPopMatrix(); // if push

```

Anyone has an idea? Been stuck on this all day long now.
PS. Could add that the app. is 2D only. No depth/z.

Grateful for any hints on what could be wrong. ~ Rikard

---

