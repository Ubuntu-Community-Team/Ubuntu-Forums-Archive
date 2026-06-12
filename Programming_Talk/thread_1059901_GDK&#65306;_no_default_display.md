---
title: "GDK&#65306; no default display?"
date: 2009-02-04
forum: Programming Talk
---

### Post by SouthernRyan on 2009-02-04
I'm writing a very simple program trying to read the resolution of the screen, as follows
```

#include <gdk/gdk.h>
#include <glib.h>

int main()
{	
	GdkScreen *theScreen;
	gint iHeight, iWidth;
	theScreen = gdk_screen_get_default();
	if(theScreen != NULL)
	{
		iHeight = gdk_screen_get_height(theScreen);
		iWidth = gdk_screen_get_width(theScreen);
	}
	
	return 0;
}
```

However, the return of gdk_screen_get_default() is always null. I don't understand why. And is there any other way to get GdkScreen object? Or more directly, whatever method it is, to get screen resolution in a C++ program?

Thanks in advance.

---

### Post by SouthernRyan on 2009-02-05
still struggling.....

---

