---
title: "Problem with multithread and xwindow[C]"
date: 2012-03-17
forum: Programming Talk
---

### Post by CynicRus on 2012-03-17
There was a poser, which consists of the following: pthread create in a separate window, it displays some dynamic data. From the main thread - calling methods:
[PHP]int blockDisplay (Display **dsp,Window *wnd1)
{
    XSetWindowAttributes attr,attr1,attr2;
	Pixmap shape,pic,lock,shp, bg_pic, bg_shp;
    unsigned long white;
	int snumber = 0;
	long win_mask = CWBackPixel|CWBorderPixel|CWOverrideRedirect;
if(running == 1)
    return 0;
	running = 1;
	x=5;
	y=35;
	XInitThreads();
	(*dsp) = XOpenDisplay(0);
	if((*dsp) == NULL)
		return(-1);
	//dsp = XOpenDisplay(getenv("DISPLAY"));
	dW = XDisplayWidth(*dsp,snumber);
	dH = XDisplayHeight(*dsp,snumber);
	root = XRootWindow(*dsp,snumber);

	if(background != NULL)
	  {
	    if(XpmReadFileToPixmap(*dsp,root,background,&bg_pic,&bg_shp,NULL) != XpmOpenFailed)
	      win_mask = CWBackPixmap|CWBorderPixel|CWOverrideRedirect;
	  }
    white = XWhitePixel(*dsp,0);
	attr.background_pixel =white ;
	attr.background_pixmap = bg_pic;
	attr.border_pixel = 100;
	attr.override_redirect = True;
	(*wnd1) = XCreateWindow(*dsp, root, 0, 0, dW, dH,0,
		 CopyFromParent, CopyFromParent,CopyFromParent,
		 win_mask
		,&attr);
	XMapRaised(*dsp,*wnd1);

	XpmCreatePixmapFromData(*dsp,*wnd1,ccafe_xpm,&pic,&shape,NULL);
    attr1.background_pixel =white ;
	attr1.background_pixmap = pic;
	logo = XCreateWindow(*dsp,*wnd1,dW-150,0,150,30,0,CopyFromParent,CopyFromParent,CopyFromParent,CWBackPixmap,&attr1);
	XMapWindow(*dsp,logo);
	//logo2 = XCreateSimpleWindow(*dsp, *wnd1, 0, 0, dW-150, 30, 0, 0,300);
	//XMapWindow(*dsp,logo2);

	XpmCreatePixmapFromData(*dsp,*wnd1,Locked_xpm,&lock,&shp,NULL);
	attr2.background_pixmap = lock;
	wnd = XCreateWindow(*dsp,*wnd1,dW/4+20,dH/4,600,600,0,CopyFromParent,CopyFromParent,CopyFromParent,CWBackPixmap,&attr2);
	//wnd = XCreateSimpleWindow(*dsp, *wnd1, x, y, 200, 200, 1, 0, 400);
	XMapWindow(*dsp,wnd);

	XGrabPointer(*dsp,*wnd1,False,ButtonPressMask|ButtonReleaseMask|PointerMotionMask,GrabModeAsync,GrabModeAsync,None,None,CurrentTime);
	XGrabKeyboard(*dsp,*wnd1,False,GrabModeAsync,GrabModeAsync,CurrentTime);
	XSelectInput(*dsp,*wnd1,KeyPressMask|KeyReleaseMask|ButtonPressMask|ButtonReleaseMask|PointerMotionMask|ShiftMask|LockMask|ControlMask|Mod1Mask|Mod2Mask|Mod3Mask|Mod4Mask|Mod5Mask);
  
	return(0);
}


int unlockDisplay(Display **dsp,Window *wnd1){
	if(running == 1){
		XDestroyWindow(*dsp,*wnd1);
		XCloseDisplay(*dsp);
		running = 0;
	}
	return(0);
}[/PHP]
blockDisplay - work fine, when i call unblockDisplay - get a Segmentation Fault. What could be wrong? Thanks in advance for your help, code routines to create a window - quote:
[PHP]#include "stdlib.h"
#include "stdio.h"
#include "string.h"
#include "timer.h"
#include "window.h"
#include "X11/Xlib.h"
#include <X11/Xutil.h>
#include <X11/Xatom.h>
#include <X11/xpm.h>
#include "ccafe.xpm"
#include "Locked.xpm"
#include "pthread.h"
//&#1086;&#1073;&#1098;&#1103;&#1074;&#1083;&#1103;&#1077;&#1084; &#1087;&#1077;&#1088;&#1077;&#1084;&#1077;&#1085;&#1085;&#1099;&#1077;-&#1089; &#1076;&#1083;&#1103; &#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1086;&#1074;&#1097;&#1080;&#1082;&#1072;
Window root,wnd,logo,logo2;
int x,y,dW,dH;
int running = 0;
char *background = NULL;

// &#1057;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1077; &#1089; &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1086;&#1084;
Display *display;

// &#1054;&#1082;&#1085;&#1086;
Window window;

// &#1064;&#1080;&#1088;&#1080;&#1085;&#1072; &#1080; &#1074;&#1099;&#1089;&#1086;&#1090;&#1072; &#1086;&#1082;&#1085;&#1072;
int window_width	= 80;
int window_height	= 30;

void* initWindow(void* arg)
{
	//pthread_t lthread;
	int ret;
	//pthread_attr_t tattr;
	XInitThreads();
    window_init();
    printf("Window Thread\n");
    window_loop();
 //   ret = pthread_attr_init(&tattr); 
//	ret = pthread_attr_setdetachstate(&tattr,PTHREAD_CREATE_DETACHED);

//    if( ret = pthread_create(&lthread, &tattr,window_loop , NULL) != 0) {
  //  printf("TThread creation failed: %d\n", ret);
 // }
}

void window_init()
{
	display = XOpenDisplay(NULL);
	if (display == NULL)
	{
		exit(EXIT_FAILURE);
	}

	int screen_number = DefaultScreen(display);

	int display_width = DisplayWidth(display, screen_number);
	int display_height = DisplayHeight(display, screen_number);

	int window_pos_x = display_width - window_width;
	int window_pos_y = display_height - window_height;
    XLockDisplay(display);
	window = XCreateSimpleWindow(display, RootWindow(display, screen_number),
			window_pos_x, window_pos_y, window_width, window_height, 0,
			BlackPixel(display, screen_number),WhitePixel(display, screen_number));
	//window = XCreateWindow(display, RootWindow(display, screen_number),
        //                window_pos_x, window_pos_y, window_width, window_height, 0,
         //               CopyFromParent,CopyFromParent,CopyFromParent,0, 0);

	XSelectInput(display, window, ExposureMask/* | ResizeRedirectMask*/);
	//XRaiseWindow(display, window);

	SetNoBorder(display, window,RootWindow(display, screen_number));

	//&#1091;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084;&#1089;&#1103; &#1080;&#1079; &#1087;&#1072;&#1085;&#1077;&#1083;&#1080; &#1079;&#1072;&#1076;&#1072;&#1095; &#1080; pager
    Atom a = XInternAtom(display, "_NET_WM_STATE", True);
    if (a != None) {
	Atom prop = XInternAtom(display, "_NET_WM_STATE_SKIP_TASKBAR", True);
	XChangeProperty(display, window, a, XA_ATOM, 32, PropModeAppend, (unsigned char *) &prop, 1);
	Atom prop1 = XInternAtom(display, "_NET_WM_STATE_SKIP_PAGER", True);
	XChangeProperty(display, window, a, XA_ATOM, 32, PropModeAppend, (unsigned char *) &prop1, 1);
    Atom prop2 = XInternAtom(display, "_NET_WM_STATE_ABOVE", True);
    XChangeProperty(display, window, a, XA_ATOM, 32, PropModeAppend, (unsigned char *) &prop2, 1);
    }
    XMapWindow(display, window);
	XStoreName(display, window, "CCafe");
	XMoveWindow(display, window, display_width, display_height);
	XUnlockDisplay(display);
	XFlush(display);
}
//&#1091;&#1073;&#1080;&#1088;&#1072;&#1077;&#1084; &#1082; &#1093;&#1091;&#1103;&#1084; &#1088;&#1072;&#1084;&#1086;&#1095;&#1082;&#1080; &#1074;&#1086;&#1082;&#1088;&#1091;&#1075; &#1086;&#1082;&#1085;&#1072;.

void SetNoBorder(Display *dpy, Window win, Window root)
{ int set = 0;
  Atom WM_HINTS;
  WM_HINTS = XInternAtom(dpy, "_MOTIF_WM_HINTS", True);
  if(WM_HINTS != None)
  {
    struct
    { unsigned long flags;
      unsigned long functions;
      unsigned long decorations;
      long input_mode;
      unsigned long status;
    } MWMHints = { (1L << 1), 0, 0, 0, 0 };

    XChangeProperty(dpy, win, WM_HINTS, WM_HINTS, 32,
                    PropModeReplace, (unsigned char *)&MWMHints,
                    sizeof(MWMHints)/sizeof(long));
    set = 1;
  }
  WM_HINTS = XInternAtom(dpy, "KWM_WIN_DECORATION", True);
  if(WM_HINTS != None)
  { long KWMHints = 0;

    XChangeProperty(dpy, win, WM_HINTS, WM_HINTS, 32,
                    PropModeReplace, (unsigned char *)&KWMHints,
                    sizeof(KWMHints)/sizeof(long));
    set = 1;
  }

  WM_HINTS = XInternAtom(dpy, "_WIN_HINTS", True);
  if(WM_HINTS != None)
  { long GNOMEHints = 0;

    XChangeProperty(dpy, win, WM_HINTS, WM_HINTS, 32,
                    PropModeReplace, (unsigned char *)&GNOMEHints,
                    sizeof(GNOMEHints)/sizeof(long));
    set = 1;
  }
  if(! set)
    XSetTransientForHint(dpy, win, root);
}
//&#1085;&#1091;-&#1089;...&#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1086;&#1074;&#1082;&#1072; &#1101;&#1082;&#1088;&#1072;&#1085;&#1072;
int blockDisplay (Display **dsp,Window *wnd1)
{
    XSetWindowAttributes attr,attr1,attr2;
	Pixmap shape,pic,lock,shp, bg_pic, bg_shp;
    unsigned long white;
	int snumber = 0;
	long win_mask = CWBackPixel|CWBorderPixel|CWOverrideRedirect;
if(running == 1)
    return 0;
	running = 1;
	x=5;
	y=35;
	XInitThreads();
	(*dsp) = XOpenDisplay(0);
	if((*dsp) == NULL)
		return(-1);
	//dsp = XOpenDisplay(getenv("DISPLAY"));
	dW = XDisplayWidth(*dsp,snumber);
	dH = XDisplayHeight(*dsp,snumber);
	root = XRootWindow(*dsp,snumber);

	if(background != NULL)
	  {
	    if(XpmReadFileToPixmap(*dsp,root,background,&bg_pic,&bg_shp,NULL) != XpmOpenFailed)
	      win_mask = CWBackPixmap|CWBorderPixel|CWOverrideRedirect;
	  }
    white = XWhitePixel(*dsp,0);
	attr.background_pixel =white ;
	attr.background_pixmap = bg_pic;
	attr.border_pixel = 100;
	attr.override_redirect = True;
	(*wnd1) = XCreateWindow(*dsp, root, 0, 0, dW, dH,0,
		 CopyFromParent, CopyFromParent,CopyFromParent,
		 win_mask
		,&attr);
	XMapRaised(*dsp,*wnd1);

	XpmCreatePixmapFromData(*dsp,*wnd1,ccafe_xpm,&pic,&shape,NULL);
    attr1.background_pixel =white ;
	attr1.background_pixmap = pic;
	logo = XCreateWindow(*dsp,*wnd1,dW-150,0,150,30,0,CopyFromParent,CopyFromParent,CopyFromParent,CWBackPixmap,&attr1);
	XMapWindow(*dsp,logo);
	//logo2 = XCreateSimpleWindow(*dsp, *wnd1, 0, 0, dW-150, 30, 0, 0,300);
	//XMapWindow(*dsp,logo2);

	XpmCreatePixmapFromData(*dsp,*wnd1,Locked_xpm,&lock,&shp,NULL);
	attr2.background_pixmap = lock;
	wnd = XCreateWindow(*dsp,*wnd1,dW/4+20,dH/4,600,600,0,CopyFromParent,CopyFromParent,CopyFromParent,CWBackPixmap,&attr2);
	//wnd = XCreateSimpleWindow(*dsp, *wnd1, x, y, 200, 200, 1, 0, 400);
	XMapWindow(*dsp,wnd);

	XGrabPointer(*dsp,*wnd1,False,ButtonPressMask|ButtonReleaseMask|PointerMotionMask,GrabModeAsync,GrabModeAsync,None,None,CurrentTime);
	XGrabKeyboard(*dsp,*wnd1,False,GrabModeAsync,GrabModeAsync,CurrentTime);
	XSelectInput(*dsp,*wnd1,KeyPressMask|KeyReleaseMask|ButtonPressMask|ButtonReleaseMask|PointerMotionMask|ShiftMask|LockMask|ControlMask|Mod1Mask|Mod2Mask|Mod3Mask|Mod4Mask|Mod5Mask);
  
	return(0);
}

//&#1088;&#1072;&#1079;&#1073;&#1083;&#1086;&#1082;&#1080;&#1088;&#1091;&#1077;&#1084; &#1076;&#1080;&#1089;&#1087;&#1083;&#1077;&#1081;
int unlockDisplay(Display **dsp,Window *wnd1){
	if(running == 1){
		XDestroyWindow(*dsp,*wnd1);
		//XCloseDisplay(*dsp);
		running = 0;
	}
	return(0);
}

void window_destroy()
{
	XDestroyWindow(display, window);
	XCloseDisplay(display);
}

void window_loop()
{
	int ret;
	XEvent event;
	for (;;)
	{
	//	printf("Loop Thread\n");
	//XLockDisplay(display);
		XNextEvent(display, &event);
	//XUnlockDisplay(display);	
		switch (event.type)
		{
		case Expose:
		{
			window_repaint();
		//	printf("Loop Thread_1\n");
			break;
		}
		case ResizeRequest:
		{
			XResizeRequestEvent *resize = (XResizeRequestEvent *) &event;

			window_width = resize->width;
			window_height = resize->height;
           // printf("Loop Thread_2\n");
			break;
		}
		default:
		{
			break;
		}
		}
	}
}

void window_repaint_send()
{
	XExposeEvent expose = { Expose, 0, 1, display, window, 0, 0, window_width, window_height, 0 };
	//XLockDisplay(display);
	XSendEvent(display, window, 0, ExposureMask, (XEvent *) &expose);
//	XUnlockDisplay(display);
	//printf("repaint_send\n");
	XFlush(display);
}

void window_repaint()
{
  //  printf("repaint\n");
  XLockDisplay(display);
    XClearArea(display, window, 0, 0, window_width, window_height, 0);


    XFontStruct *font = XLoadQueryFont(display, "10x20");
	if (!font)
	{
		exit(EXIT_FAILURE);
	}


	GC gc = XCreateGC(display, window, 0, NULL);



	XSetFont(display, gc, font->fid);

	char timer_message[100];

	timer_str(timer_message);

	int timer_message_pos_x = window_width / 2 - XTextWidth(font, timer_message, strlen(timer_message)) / 2;
    int timer_message_pos_y = window_height / 2 ;
	XDrawString(display, window, gc, timer_message_pos_x, timer_message_pos_y, timer_message, strlen(timer_message));

	char attention_message[100];
	if (timer_get_message(attention_message))
	{
		int attention_message_pos_x = window_width / 2 - XTextWidth(font, attention_message, strlen(attention_message)) / 2;
		int attention_message_pos_y = window_height / 2 + 30;

		XDrawString(display, window, gc, attention_message_pos_x, attention_message_pos_y, attention_message, strlen(attention_message));
	}
	XUnlockDisplay(display);

	XFreeGC(display, gc);
}
[/PHP]
Valgrind output:
[PHP]==27044== Command: ./cclient
==27044== 
Initializing parameters to default values...
Reading config file...
==27044== Source and destination overlap in strcpy(0x7fefffd20, 0x7fefffd20)
==27044==    at 0x4C2982A: strcpy (mc_replace_strmem.c:311)
==27044==    by 0x4037BA: trim (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x4038C6: parse_config (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x4021C2: main (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044== 
value: 9030
Final values:
port: 9030, MSG: 512
Timer Thread
Window Thread
Server: connect from host 127.0.0.1, port -28110.
block
start
==27044== Use of uninitialised value of size 8
==27044==    at 0x4E4C5DC: XDestroyWindow (in /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0)
==27044==    by 0x402F89: unlockDisplay (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401CD8: parseCommand (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401F9C: read_from_client (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x40254D: main (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044== 
==27044== Invalid read of size 8
==27044==    at 0x4E4C5DC: XDestroyWindow (in /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0)
==27044==    by 0x402F89: unlockDisplay (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401CD8: parseCommand (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401F9C: read_from_client (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x40254D: main (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==  Address 0x972 is not stack'd, malloc'd or (recently) free'd
==27044== 
==27044== 
==27044== Process terminating with default action of signal 11 (SIGSEGV)
==27044==  Access not within mapped region at address 0x972
==27044==    at 0x4E4C5DC: XDestroyWindow (in /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0)
==27044==    by 0x402F89: unlockDisplay (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401CD8: parseCommand (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x401F9C: read_from_client (in /home/cynic/Coding/CCafe/CClient/cclient)
==27044==    by 0x40254D: main (in /home/cynic/Coding/CCafe/CClient/cclient)[/PHP]

---

### Post by CynicRus on 2012-03-17
```
Program received signal SIGSEGV, Segmentation fault.
0x00007ffff7ad1049 in XLockDisplay ()
   from /usr/lib/x86_64-linux-gnu/libX11.so.6
(gdb) backtrace
#0  0x00007ffff7ad1049 in XLockDisplay ()
   from /usr/lib/x86_64-linux-gnu/libX11.so.6
#1  0x0000000000402f11 in unlockDisplay ()
#2  0x0000000000401c89 in parseCommand ()
#3  0x0000000000401f4d in read_from_client ()
#4  0x00000000004024fe in main ()
```output from GDB, and no have idea, how to fix it-(

---

### Post by CynicRus on 2012-03-17
Fixed, ublockDevice - has used undefined display. Tnx all.

---

