---
title: "Firefox testing problem"
date: 2014-07-21
forum: Programming Talk
---

### Post by fugu2 on 2014-07-21
I'm having trouble developing a browser fuzzer for Firefox, in that frequently when the browser incounters an error, it will break all of the functionality in that page, including the redirect that is used to continue the fuzzing process.
```

<html>
<head>
<META HTTP-EQUIV="Refresh" content="0; URL=fuzzy.php">
</head>
<hr><abbr style="" onmousedown="" draggable="" title="" accesskey="" lang="" onmouseup="" onmouseover="" onmouseout="" dir="" class="" id="" onkeydown="" contextmenu="" onkeypress="" contenteditable="" onmousemove="" onkeyup="" onclick="" ondblclick="" > </abbr><br />

```
This is a sample page of what its hangging on.
Anyone have an idea of how to fix this?

---

### Post by tgalati4 on 2014-07-21
I'm pretty sure that is by design.  What version of Firefox?  There are several consoles and windows in the Developer tab.  Perhaps open a few and see what they say when you are running your script.

What exactly are you trying to test?  Are you testing Mozilla's browser to handle [fuzzy]("https://www.mwrinfosecurity.com/knowledge-centre/15-minute-guide-to-fuzzing/") inputs or are you testing a website that you are hosting and you want to see how it handles fuzzed inputs while in  Firefox?  Is this a smart fuzzer, or a dumb fuzzer, or something in-between?

Without knowing what is in fuzzy.php it's hard to give any advice.

---

### Post by fugu2 on 2014-07-21
Ok, This is going to be somewhere inbetween smart and dumb fuzzing, and hopfully allow you to choose what attributes will get what kinda of a tailored random output, and what percent of the time. 
fuzzy.php is part of a much larger framework, but Ive isolated the problem that can be demonstrated in pure html 
This HTML file will loop over and over just fine. (I had to change one setting in firefox to prevent having to click on the accept button, i.e. Preferences >> Advance >> General >> Warn me when websites try to redirect or reload the page)
```

 <html>
<head>
<META HTTP-EQUIV="Refresh" content="0; URL=fuzzy.html">
</head>
<hr><--<abbr style="" onmousedown="" draggable="" title="" accesskey="" lang="" onmouseup="" onmouseover="" onmouseout="" dir="" class="" id="" onkeydown="" contextmenu="" onkeypress="" contenteditable="" onmousemove="" onkeyup="" onclick="" ondblclick="" > </abbr><br />-->

```
but if you uncomment the abbr tag inside fuzzy.html while its looping, it will stop looping. I think that the refresh is not working because firefox found errors on the page. My question is can this be bypassed to force firefox to refresh?

---

### Post by tgalati4 on 2014-07-21
The console windows that I mentioned earlier will highlight those errors.  I have no idea how to refresh a broken page without some timer to try to refresh after a certain time--sort of a watchdog.  When a page does not refresh, restart the page (and modify the fuzzy data slightly) after a certain period of time, say 15 seconds.  There may be plug-ins that do this.  I know there are several plug-ins to refresh data in pages automatically--so you don't have to constantly click on the page to update.  Of course the plug-in may interfere with your testing.

You can also invoke firefox in terminal with different modes:

```
firefox -h
```

---

### Post by fugu2 on 2014-07-21
Both the web and browser consoles are not showing any errors, so idk what is wrong.
i did find this really awful solution, and I'm sure theres gotta be a better way to fix this, but until then I think this might work.
```

//Linux
//sudo apt-get install libxtst-dev
//gcc -o test simulate_key_event.c -lX11 -lXtst
//Windows
//PATH=$PATH:/opt/mingw32/bin i686-w64-mingw32-gcc -o test.exe simulate_key_event.c
#include <stdio.h>
#ifdef _WIN32
 #include <windows.h>
#else
 #include <X11/Xlib.h>
 #include <X11/keysym.h>
 #include <X11/extensions/XTest.h>
#endif

int main(){
#ifndef _WIN32
	Display *display;
	display = XOpenDisplay(NULL);
#endif

	while(1) {
		printf("simulating F5 keypress (Refresh Browser)\n");
#ifdef _WIN32
		keybd_event(VK_F5, MapVirtualKey(VK_F5, 0), 0, 0);
		keybd_event(VK_F5, MapVirtualKey(VK_F5, 0), KEYEVENTF_KEYUP, 0);
		Sleep(1000);
#else
		XTestFakeKeyEvent(display, XKeysymToKeycode(display, XK_F5), True, 0);
		XTestFakeKeyEvent(display, XKeysymToKeycode(display, XK_F5), False, 0);
		XFlush(display);
		sleep(1);
#endif
	}
}


```

---

