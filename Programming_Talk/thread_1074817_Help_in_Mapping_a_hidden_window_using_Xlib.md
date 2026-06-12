---
title: "Help in Mapping a hidden window using Xlib"
date: 2009-02-19
forum: Programming Talk
---

### Post by ycar on 2009-02-19
Hi guys,

I'm trying to write a clone of AutoHotkey ([http://www.autohotkey.com/](http://www.autohotkey.com/)) for Linux.

But I'm having problems in showing the hidden windows.
Let's consider the following scenario:

1. I have Pidgin opened (and displayed on the screen).
2. I run "wmctrl -l " and find out the window ID
3. I close Pidgin window (which doesn't really quit the application but just hides the window)
4. Using the following piece of code, I'm trying to show (map) the hidden window (based on its window ID found at step 2)

      Display * display = XOpenDisplay(NULL);
      int screen = DefaultScreen(display);
      ...
      XMapWindow(display, (Window) 0x0FFF);<- I get the value @ step 2
      XSync(display, False);
      ...
      XCloseDisplay(display);

As a result the window just flashes (it appears and immediately disappears).
It doesn't remain on the screen.
I have the same behavior if instead of Pidgin I use a small dummy window, created in GTK, which I hide using gtk_widget_hide().

Unfortunately, I have a "requirement" to use only Xlib in my code.

Please let me know in case you have any ideas.
Thanks a lot for your time.

---

### Post by kknd on 2009-02-20
Well, in my opinion, changing other programs in an unexpected way isn't a good thing. The user should write a macro that requests pidgin to open (by using the standard pidgin interface, ie, clicking on the tray icon) and not by manipulating the internals. Even if you could map the window, pidgin (or other app) wouldn't be aware of that and it will result in unexpected behavior.

---

### Post by ycar on 2009-02-20
Hi kknd, thanks for the answer.

But let's think from another point. What is the reason of having a common X library if at the end the user should deal with each application using its own interface?
The reason of Xlib is to have a common library for window functions (in my opinion).
Why then Xlib provides such functionality like "Iconify", "Close", "Send To Desktop N"?
It's absolutely the same for Mapping and Unmapping a window (I mean hiding it).
If an application it's not behaving normally at Xlib functions then it's a poor design of that app.
In my case, I still think that this is possible, but I'm missing something...

But, anyway, kknd - thanks a lot for the reply! :)
I'm continuing my "investigations". I will let u know in case I find something.
Thanks! :)

---

### Post by khc on 2009-02-25
I don't think this is covered in the X protocol, and instead is under the EWMH/NetWM spec. See wmctrl(1).

---

### Post by ycar on 2009-02-25
thanks khc,
Maybe you are right.
Thanks for the hint about 'wmctrl'. I'm checking its code now.. to see how it works... :)

Also I have spent a lot of time by investigating the source code of: gtk, alltray, stalonetray, tint.
But I don't know the answer yet: "how to show a hidden window using Xlib". I now that gtk is doing it (gtk_widget_show) but I cannot understand (yet) how.

---

### Post by kknd on 2009-02-26
> **ycar said:**
> Hi kknd, thanks for the answer.

But let's think from another point. What is the reason of having a common X library if at the end the user should deal with each application using its own interface?
The reason of Xlib is to have a common library for window functions (in my opinion).
Why then Xlib provides such functionality like "Iconify", "Close", "Send To Desktop N"?
It's absolutely the same for Mapping and Unmapping a window (I mean hiding it).
If an application it's not behaving normally at Xlib functions then it's a poor design of that app.
In my case, I still think that this is possible, but I'm missing something...

But, anyway, kknd - thanks a lot for the reply! :)
I'm continuing my "investigations". I will let u know in case I find something.
Thanks! :)

Hi,

I think that window management itself it's OK (de-iconifing an iconified window, move a window, etc), but showing a window that's totally hidden from the user (not appearing in the toolbar and etc) isn't good. The program can be doing anything with the window, like modifying it or even 'destroying' it) (well, I don't know how Xlib works, thus I can be totally wrong).

---

