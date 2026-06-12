---
title: "How do you bring a program window to the foreground?"
date: 2015-10-23
forum: Programming Talk
---

### Post by sysrpl2 on 2015-10-23
Under Linux Ubuntu with Unity, how is it possible to programatically bring a window belonging to my application to the front and give it keyboard/input focus?


I am unsure if this is the appropriate forum for this type of questions. If not would you be so kind as to direct me to the pertinent community forum.


With that out of the way, here are a few more details related to my question. 


I am writing a few similar programs...


Application A
--------------


One is a screen color picker application which upon a globally hotkey being pressed will copy the entire screen to a bitmap and then replace the screen with a fullscreen window with the bitmap painted to it. The user can then mouse over and magnify portions of the bitmap copy of the screen to pick a color. I was unable to find a way to do this easily with Unity and had to resort to trickery.


[http://cache.getlazarus.org/video/colormix.mp4](http://cache.getlazarus.org/video/colormix.mp4)


Application B
--------------


The other is a screen recording which again upon a globally hotkey being pressed will start recording you screen. Upon pressing the same globally hotkey the screen recording is ended and a window is presented to the user where he may choose a filename, a cloud storage upload, or to discard the recording altogether. Again I am unable to find a way to do this with Unity and am to resorting to trickery. The difference in this case is that the final popup window does not have keyboard focus requiring the user to click on the window to begin typing.


So the question is, how can I programatically bring a window belonging to my application to the front and give it keyboard/input focus?


Ubuntu 14.04 64bit
Unity desktop


gtk_window_present <- doesn't work to solve this problem in my tests

Final Note: When showing a window or hiding, how is it possible to do so without window animations? The animations are screwing with my color picker an screen capture windows, where I my window then immediately capture. With window animations on my window I'm left to guess when the animation ends before I start the capture. I'd rather show or hide certain windows without the animations in some cases.

Thanks!

---

