---
title: "GLFW 3.0 example fails to compile"
date: 2013-06-16
forum: Programming Talk
---

### Post by bird1500 on 2013-06-16
EDIT: the solution is to add "--static":
 g++ test.cpp -o test `pkg-config glfw3 --static --cflags --libs`

Hi,
I installed from source GLFW 3.0, no errors reported.
But when I try to test it by compiling the example (saved as test.cpp) at the end of [this page]("http://www.glfw.org/docs/3.0/quick.html"), the compilation fails, any ideas what's wrong?

compiler output:
```

g++ test.cpp -o test `pkg-config glfw3 --cflags --libs`
/tmp/ccdp2BKH.o: In function `main':
test.cpp:(.text+0x12a): undefined reference to `glViewport'
test.cpp:(.text+0x134): undefined reference to `glClear'
test.cpp:(.text+0x13e): undefined reference to `glMatrixMode'
test.cpp:(.text+0x143): undefined reference to `glLoadIdentity'
test.cpp:(.text+0x186): undefined reference to `glOrtho'
test.cpp:(.text+0x190): undefined reference to `glMatrixMode'
test.cpp:(.text+0x195): undefined reference to `glLoadIdentity'
test.cpp:(.text+0x1d3): undefined reference to `glRotatef'
test.cpp:(.text+0x1dd): undefined reference to `glBegin'
test.cpp:(.text+0x1f0): undefined reference to `glColor3f'
test.cpp:(.text+0x208): undefined reference to `glVertex3f'
test.cpp:(.text+0x21b): undefined reference to `glColor3f'
test.cpp:(.text+0x233): undefined reference to `glVertex3f'
test.cpp:(.text+0x246): undefined reference to `glColor3f'
test.cpp:(.text+0x259): undefined reference to `glVertex3f'
test.cpp:(.text+0x25e): undefined reference to `glEnd'
/usr/local/lib/libglfw3.a(context.c.o): In function `parseGLVersion':
context.c:(.text+0x53): undefined reference to `glGetString'
/usr/local/lib/libglfw3.a(context.c.o): In function `_glfwRefreshContextAttribs':
context.c:(.text+0x8ef): undefined reference to `glGetIntegerv'
context.c:(.text+0x972): undefined reference to `glGetIntegerv'
context.c:(.text+0x9c7): undefined reference to `glGetIntegerv'
context.c:(.text+0xa1a): undefined reference to `glGetIntegerv'
/usr/local/lib/libglfw3.a(context.c.o): In function `glfwExtensionSupported':
context.c:(.text+0xd26): undefined reference to `glGetString'
context.c:(.text+0xd60): undefined reference to `glGetIntegerv'
/usr/local/lib/libglfw3.a(window.c.o): In function `glfwCreateWindow':
window.c:(.text+0x725): undefined reference to `glClear'
/usr/local/lib/libglfw3.a(x11_gamma.c.o): In function `_glfwInitGammaRamp':
x11_gamma.c:(.text+0x49): undefined reference to `XRRGetScreenResources'
x11_gamma.c:(.text+0x6a): undefined reference to `XRRGetCrtcGammaSize'
x11_gamma.c:(.text+0x81): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_gamma.c.o): In function `_glfwPlatformGetGammaRamp':
x11_gamma.c:(.text+0xce): undefined reference to `XRRGetCrtcGammaSize'
x11_gamma.c:(.text+0xf1): undefined reference to `XRRGetCrtcGamma'
x11_gamma.c:(.text+0x17d): undefined reference to `XRRFreeGamma'
x11_gamma.c:(.text+0x1a5): undefined reference to `XF86VidModeGetGammaRampSize'
x11_gamma.c:(.text+0x1f3): undefined reference to `XF86VidModeGetGammaRamp'
/usr/local/lib/libglfw3.a(x11_gamma.c.o): In function `_glfwPlatformSetGammaRamp':
x11_gamma.c:(.text+0x231): undefined reference to `XRRAllocGamma'
x11_gamma.c:(.text+0x2cd): undefined reference to `XRRSetCrtcGamma'
x11_gamma.c:(.text+0x2d9): undefined reference to `XRRFreeGamma'
x11_gamma.c:(.text+0x321): undefined reference to `XF86VidModeSetGammaRamp'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `translateKey':
x11_init.c:(.text+0x3f): undefined reference to `XkbKeycodeToKeysym'
x11_init.c:(.text+0x101): undefined reference to `XkbKeycodeToKeysym'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `updateKeyCodeLUT':
x11_init.c:(.text+0xb72): undefined reference to `XkbGetKeyboard'
x11_init.c:(.text+0x1246): undefined reference to `XkbFreeKeyboard'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `getSupportedAtom':
x11_init.c:(.text+0x12d0): undefined reference to `XInternAtom'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `detectEWMH':
x11_init.c:(.text+0x134e): undefined reference to `XInternAtom'
x11_init.c:(.text+0x136b): undefined reference to `XInternAtom'
x11_init.c:(.text+0x13b6): undefined reference to `XFree'
x11_init.c:(.text+0x13ec): undefined reference to `XFree'
x11_init.c:(.text+0x13f8): undefined reference to `XFree'
x11_init.c:(.text+0x141c): undefined reference to `XFree'
x11_init.c:(.text+0x1428): undefined reference to `XFree'
/usr/local/lib/libglfw3.a(x11_init.c.o):x11_init.c:(.text+0x1439): more undefined references to `XFree' follow
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `initDisplay':
x11_init.c:(.text+0x1568): undefined reference to `XOpenDisplay'
x11_init.c:(.text+0x15da): undefined reference to `XrmUniqueQuark'
x11_init.c:(.text+0x15f9): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1619): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1639): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1659): undefined reference to `XF86VidModeQueryExtension'
x11_init.c:(.text+0x1678): undefined reference to `XRRQueryExtension'
x11_init.c:(.text+0x16a2): undefined reference to `XRRQueryVersion'
x11_init.c:(.text+0x1705): undefined reference to `XQueryExtension'
x11_init.c:(.text+0x1736): undefined reference to `XIQueryVersion'
x11_init.c:(.text+0x1780): undefined reference to `XkbQueryExtension'
x11_init.c:(.text+0x17ba): undefined reference to `XkbSetDetectableAutoRepeat'
x11_init.c:(.text+0x1824): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1844): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1864): undefined reference to `XInternAtom'
x11_init.c:(.text+0x1884): undefined reference to `XInternAtom'
x11_init.c:(.text+0x18a4): undefined reference to `XInternAtom'
/usr/local/lib/libglfw3.a(x11_init.c.o):x11_init.c:(.text+0x18c4): more undefined references to `XInternAtom' follow
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `createNULLCursor':
x11_init.c:(.text+0x1963): undefined reference to `XCreatePixmap'
x11_init.c:(.text+0x1993): undefined reference to `XCreateGC'
x11_init.c:(.text+0x19cf): undefined reference to `XFillRectangle'
x11_init.c:(.text+0x1a25): undefined reference to `XCreatePixmapCursor'
x11_init.c:(.text+0x1a45): undefined reference to `XFreePixmap'
x11_init.c:(.text+0x1a5e): undefined reference to `XFreeGC'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `terminateDisplay':
x11_init.c:(.text+0x1a86): undefined reference to `XCloseDisplay'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `_glfwPlatformInit':
x11_init.c:(.text+0x1a9c): undefined reference to `XInitThreads'
/usr/local/lib/libglfw3.a(x11_init.c.o): In function `_glfwPlatformTerminate':
x11_init.c:(.text+0x1b12): undefined reference to `XFreeCursor'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwSetVideoMode':
x11_monitor.c:(.text+0x177): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x19c): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x1be): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0x3ae): undefined reference to `XRRSetCrtcConfig'
x11_monitor.c:(.text+0x3ba): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0x3c6): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x3d2): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwRestoreVideoMode':
x11_monitor.c:(.text+0x40d): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x432): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x4a7): undefined reference to `XRRSetCrtcConfig'
x11_monitor.c:(.text+0x4b3): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x4bf): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetMonitors':
x11_monitor.c:(.text+0x50f): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x52c): undefined reference to `XRRGetOutputPrimary'
x11_monitor.c:(.text+0x584): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x59f): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x60e): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0x62b): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0x637): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x6cb): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0x6d7): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x6fb): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetMonitorPos':
x11_monitor.c:(.text+0x87f): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x8a4): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0x8dc): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0x8e8): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetVideoModes':
x11_monitor.c:(.text+0x98a): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0x9ac): undefined reference to `XRRGetOutputInfo'
x11_monitor.c:(.text+0xb43): undefined reference to `XRRFreeOutputInfo'
x11_monitor.c:(.text+0xb4f): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_monitor.c.o): In function `_glfwPlatformGetVideoMode':
x11_monitor.c:(.text+0xc22): undefined reference to `XRRGetScreenResources'
x11_monitor.c:(.text+0xc47): undefined reference to `XRRGetCrtcInfo'
x11_monitor.c:(.text+0xc9c): undefined reference to `XRRFreeCrtcInfo'
x11_monitor.c:(.text+0xca8): undefined reference to `XRRFreeScreenResources'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `translateChar':
x11_window.c:(.text+0xa5): undefined reference to `XLookupString'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `createWindow':
x11_window.c:(.text+0x106): undefined reference to `XCreateColormap'
x11_window.c:(.text+0x205): undefined reference to `XCreateWindow'
x11_window.c:(.text+0x2aa): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x2d4): undefined reference to `XSaveContext'
x11_window.c:(.text+0x31f): undefined reference to `XChangeWindowAttributes'
x11_window.c:(.text+0x3b5): undefined reference to `XSetWMProtocols'
x11_window.c:(.text+0x414): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x419): undefined reference to `XAllocWMHints'
x11_window.c:(.text+0x48b): undefined reference to `XSetWMHints'
x11_window.c:(.text+0x49a): undefined reference to `XFree'
x11_window.c:(.text+0x49f): undefined reference to `XAllocSizeHints'
x11_window.c:(.text+0x5ab): undefined reference to `XSetWMNormalHints'
x11_window.c:(.text+0x5ba): undefined reference to `XFree'
x11_window.c:(.text+0x61b): undefined reference to `XISelectEvents'
x11_window.c:(.text+0x65d): undefined reference to `XRRSelectInput'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `hideCursor':
x11_window.c:(.text+0x6a0): undefined reference to `XUngrabPointer'
x11_window.c:(.text+0x6de): undefined reference to `XDefineCursor'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `captureCursor':
x11_window.c:(.text+0x763): undefined reference to `XGrabPointer'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `showCursor':
x11_window.c:(.text+0x7b0): undefined reference to `XUngrabPointer'
x11_window.c:(.text+0x7e7): undefined reference to `XUndefineCursor'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `enterFullscreenMode':
x11_window.c:(.text+0x844): undefined reference to `XGetScreenSaver'
x11_window.c:(.text+0x868): undefined reference to `XSetScreenSaver'
x11_window.c:(.text+0x9a0): undefined reference to `XSendEvent'
x11_window.c:(.text+0xa46): undefined reference to `XSendEvent'
x11_window.c:(.text+0xa9e): undefined reference to `XRaiseWindow'
x11_window.c:(.text+0xac5): undefined reference to `XSetInputFocus'
x11_window.c:(.text+0xaec): undefined reference to `XMoveWindow'
x11_window.c:(.text+0xb19): undefined reference to `XResizeWindow'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `leaveFullscreenMode':
x11_window.c:(.text+0xb98): undefined reference to `XSetScreenSaver'
x11_window.c:(.text+0xc74): undefined reference to `XSendEvent'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `processEvent':
x11_window.c:(.text+0x11b8): undefined reference to `XSendEvent'
x11_window.c:(.text+0x1302): undefined reference to `XFree'
x11_window.c:(.text+0x1354): undefined reference to `XGetEventData'
x11_window.c:(.text+0x14b8): undefined reference to `XFreeEventData'
x11_window.c:(.text+0x14dc): undefined reference to `XRRUpdateConfiguration'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwFindWindowByHandle':
x11_window.c:(.text+0x152a): undefined reference to `XFindContext'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwGetWindowProperty':
x11_window.c:(.text+0x15b4): undefined reference to `XGetWindowProperty'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformDestroyWindow':
x11_window.c:(.text+0x16b5): undefined reference to `XGetSelectionOwner'
x11_window.c:(.text+0x16e9): undefined reference to `XDeleteContext'
x11_window.c:(.text+0x1706): undefined reference to `XUnmapWindow'
x11_window.c:(.text+0x1723): undefined reference to `XDestroyWindow'
x11_window.c:(.text+0x175f): undefined reference to `XFreeColormap'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowTitle':
x11_window.c:(.text+0x17cd): undefined reference to `Xutf8SetWMProperties'
x11_window.c:(.text+0x1827): undefined reference to `XChangeProperty'
x11_window.c:(.text+0x1881): undefined reference to `XChangeProperty'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetWindowPos':
x11_window.c:(.text+0x18db): undefined reference to `XTranslateCoordinates'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowPos':
x11_window.c:(.text+0x192f): undefined reference to `XMoveWindow'
x11_window.c:(.text+0x193e): undefined reference to `XFlush'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformGetWindowSize':
x11_window.c:(.text+0x1987): undefined reference to `XGetWindowAttributes'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetWindowSize':
x11_window.c:(.text+0x19de): undefined reference to `XAllocSizeHints'
x11_window.c:(.text+0x1a48): undefined reference to `XSetWMNormalHints'
x11_window.c:(.text+0x1a54): undefined reference to `XFree'
x11_window.c:(.text+0x1ab3): undefined reference to `XResizeWindow'
x11_window.c:(.text+0x1af0): undefined reference to `XResizeWindow'
x11_window.c:(.text+0x1aff): undefined reference to `XFlush'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformIconifyWindow':
x11_window.c:(.text+0x1b6c): undefined reference to `XIconifyWindow'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformRestoreWindow':
x11_window.c:(.text+0x1ba9): undefined reference to `XMapWindow'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformShowWindow':
x11_window.c:(.text+0x1bd7): undefined reference to `XMapRaised'
x11_window.c:(.text+0x1be6): undefined reference to `XFlush'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformHideWindow':
x11_window.c:(.text+0x1c11): undefined reference to `XUnmapWindow'
x11_window.c:(.text+0x1c20): undefined reference to `XFlush'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformPollEvents':
x11_window.c:(.text+0x1c4b): undefined reference to `XPending'
x11_window.c:(.text+0x1c6c): undefined reference to `XNextEvent'
x11_window.c:(.text+0x1d1d): undefined reference to `XFlush'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformWaitEvents':
x11_window.c:(.text+0x1d50): undefined reference to `XPending'
/usr/local/lib/libglfw3.a(x11_window.c.o): In function `_glfwPlatformSetCursorPos':
x11_window.c:(.text+0x1ead): undefined reference to `XWarpPointer'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `getFBConfigAttrib':
glx_context.c:(.text+0x71): undefined reference to `glXGetFBConfigAttrib'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `chooseFBConfig':
glx_context.c:(.text+0x9e): undefined reference to `glXGetClientString'
glx_context.c:(.text+0x109): undefined reference to `glXGetFBConfigs'
glx_context.c:(.text+0x3cb): undefined reference to `XFree'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `createLegacyContext':
glx_context.c:(.text+0x44d): undefined reference to `glXCreateNewContext'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwInitContextAPI':
glx_context.c:(.text+0x462): undefined reference to `pthread_key_create'
glx_context.c:(.text+0x49d): undefined reference to `glXQueryExtension'
glx_context.c:(.text+0x4d8): undefined reference to `glXQueryVersion'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwTerminateContextAPI':
glx_context.c:(.text+0x6cc): undefined reference to `pthread_key_delete'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwCreateContext':
glx_context.c:(.text+0x7bd): undefined reference to `glXGetVisualFromFBConfig'
glx_context.c:(.text+0x8da): undefined reference to `XSetErrorHandler'
glx_context.c:(.text+0xd4c): undefined reference to `XSetErrorHandler'
glx_context.c:(.text+0xd80): undefined reference to `XGetErrorText'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwDestroyContext':
glx_context.c:(.text+0xdef): undefined reference to `XFree'
glx_context.c:(.text+0xe2b): undefined reference to `glXDestroyContext'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwPlatformMakeContextCurrent':
glx_context.c:(.text+0xe77): undefined reference to `glXMakeCurrent'
glx_context.c:(.text+0xe92): undefined reference to `glXMakeCurrent'
glx_context.c:(.text+0xea6): undefined reference to `pthread_setspecific'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwPlatformGetCurrentContext':
glx_context.c:(.text+0xeb9): undefined reference to `pthread_getspecific'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwPlatformSwapBuffers':
glx_context.c:(.text+0xee4): undefined reference to `glXSwapBuffers'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwPlatformExtensionSupported':
glx_context.c:(.text+0xf87): undefined reference to `glXQueryExtensionsString'
/usr/local/lib/libglfw3.a(glx_context.c.o): In function `_glfwPlatformGetProcAddress':
glx_context.c:(.text+0xfcf): undefined reference to `glXGetProcAddress'
/usr/local/lib/libglfw3.a(x11_clipboard.c.o): In function `writeTargetToProperty':
x11_clipboard.c:(.text+0x121): undefined reference to `XChangeProperty'
x11_clipboard.c:(.text+0x237): undefined reference to `XChangeProperty'
x11_clipboard.c:(.text+0x2b2): undefined reference to `XChangeProperty'
x11_clipboard.c:(.text+0x2be): undefined reference to `XFree'
x11_clipboard.c:(.text+0x2fe): undefined reference to `XInternAtom'
x11_clipboard.c:(.text+0x342): undefined reference to `XChangeProperty'
x11_clipboard.c:(.text+0x3d6): undefined reference to `XChangeProperty'
/usr/local/lib/libglfw3.a(x11_clipboard.c.o): In function `_glfwHandleSelectionRequest':
x11_clipboard.c:(.text+0x512): undefined reference to `XSendEvent'
/usr/local/lib/libglfw3.a(x11_clipboard.c.o): In function `_glfwPushSelectionToManager':
x11_clipboard.c:(.text+0x582): undefined reference to `XConvertSelection'
x11_clipboard.c:(.text+0x5a5): undefined reference to `XCheckIfEvent'
/usr/local/lib/libglfw3.a(x11_clipboard.c.o): In function `_glfwPlatformSetClipboardString':
x11_clipboard.c:(.text+0x666): undefined reference to `XSetSelectionOwner'
x11_clipboard.c:(.text+0x67f): undefined reference to `XGetSelectionOwner'
/usr/local/lib/libglfw3.a(x11_clipboard.c.o): In function `_glfwPlatformGetClipboardString':
x11_clipboard.c:(.text+0x710): undefined reference to `XGetSelectionOwner'
x11_clipboard.c:(.text+0x796): undefined reference to `XConvertSelection'
x11_clipboard.c:(.text+0x7b2): undefined reference to `XCheckTypedEvent'
x11_clipboard.c:(.text+0x810): undefined reference to `XFree'
x11_clipboard.c:(.text+0x830): undefined reference to `XDeleteProperty'
collect2: error: ld returned 1 exit status

```

I have glfw2 installed with sudo apt-get install libglfw2-dev and it works fine.
OpenGL version string: 4.3.0 NVIDIA 319.23
Ubuntu amd64 13.04

---

### Post by Halsafar on 2013-07-11
And how was this solved...  GLFW3 is compiling for me aside from this call XF86VidModeQueryExtension being an undefined reference all the sudden.  Was working 12.04, not working 13.04.

---

### Post by Halsafar on 2013-07-11
Added lib -lXxf86vm to linker flags.  Works now.

---

