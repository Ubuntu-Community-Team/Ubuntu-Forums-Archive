---
title: "Find out how long an X session has been idle?"
date: 2009-08-29
forum: Programming Talk
---

### Post by unutbu on 2009-08-29
Is there a command or program which can return the number of seconds an X session has been idle?

Per this tutorial on dbus, 
[http://foss-boss.blogspot.com/2008/11/ride-d-bus-control-your-linux-desktop.html](http://foss-boss.blogspot.com/2008/11/ride-d-bus-control-your-linux-desktop.html)

I've tried
```

sleep 5; qdbus org.gnome.ScreenSaver / GetSessionIdleTime
```

but it always seems to return 0.

I've also tried
```

sleep 5; qdbus org.freedesktop.ScreenSaver / GetSessionIdleTime
```
Which returns```

Service 'org.freedesktop.ScreenSaver' does not exist.
```

---

### Post by stroyan on 2009-08-29
It seems that the gnome dbus method reports the time since gnome decided the screen was idle.
That varies with the gnome screensaver time setting.
This reports a 2 second idle time.  But it turns on the screensaver.
```

qdbus org.gnome.ScreenSaver / org.gnome.ScreenSaver.SetActive False;sleep 2;qdbus org.gnome.ScreenSaver / org.gnome.ScreenSaver.GetSessionIdleTime

```
You could use the X screensaver extension directly to read X server idle time.
See [http://linux.die.net/man/3/xscreensaverqueryinfo](http://linux.die.net/man/3/xscreensaverqueryinfo)
You may need to install the right development packages to build this.
I needed "sudo apt-get install libxss-dev" on my system.
```

#include <stdio.h>
#include <X11/Xlib.h>
#include <X11/extensions/scrnsaver.h>

/* Report amount of X server idle time. */
/* Build with- */
/* cc xidle.c -o xidle -lX11 -lXext -lXss */


int main(int argc, char *argv[])
{
    Display *display;
    int event_base, error_base;
    XScreenSaverInfo info;
    float seconds;

    display = XOpenDisplay("");

    if (XScreenSaverQueryExtension(display, &event_base, &error_base)) {
	XScreenSaverQueryInfo(display, DefaultRootWindow(display), &info);

	seconds = (float)info.idle/1000.0f;
	printf("%f\n",seconds);
	return(0);
    }
    else {
	fprintf(stderr,"Error: XScreenSaver Extension not present\n");
	return(1);
    }
}

```

---

### Post by unutbu on 2009-08-29
Thank you, stroyan. The C code works wonderfully.

---

### Post by naggappan on 2013-03-20
If i run this code into a while(1) loop and get the return value continuously i am getting the error  "Maximum number of clients reached " , but if i use sleep(1) then it is working fine . is there a way to over come it without sleep one . Hear is my altered code .      
     

#include <stdio.h>
#include <X11/Xlib.h>
#include <X11/extensions/scrnsaver.h>

/* Report amount of X server idle time. */
/* Build with- */
/* cc xidle.c -o xidle -lX11 -lXext -lXss */

unsigned int abc();
void main()
{
  unsigned int idletime123;
  
  while(1)
   {
     idletime123=abc();
     printf("idletime : %u \n",idletime123);
     //sleep(1);
   }
  
}

unsigned int abc()
//float time123(int argc, char *argv[])
{
    Display *display;
    int event_base, error_base;
    XScreenSaverInfo info;
    unsigned int seconds;

    display = XOpenDisplay("");

    if (XScreenSaverQueryExtension(display, &event_base, &error_base)) {
    XScreenSaverQueryInfo(display, DefaultRootWindow(display), &info);

    seconds = (unsigned int)info.idle/1000.0f;
    //printf("%f\n",seconds);
    return(seconds);
    }
    else {
    fprintf(stderr,"Error: XScreenSaver Extension not present\n");
    return(1);
    }
}

---

