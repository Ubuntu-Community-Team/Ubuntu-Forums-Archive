---
title: "Motif - bug with Ubuntu 10.4 - pointer locked when creatin a popup menu"
date: 2010-05-11
forum: Programming Talk
---

### Post by ylaprie on 2010-05-11
Hello,

I just changed to Ubuntu 10.4 and the pointer is frozzen when a popup menu should appear.

To replicate this new problem I just used the program simple_popup.c from [http://www.ist.co.uk/motif/books/vol6A/ch-19.fm.html](http://www.ist.co.uk/motif/books/vol6A/ch-19.fm.html).
After clicking the button 3 (the right one) the pointer is locked in the window without any popup menu. 

I've tried with OpenMotif and Lesstif and the result is the same...
Is there some solution? 

Yves

/* simple_popup.c -- demonstrate how to use a simple popup menu.
** Create a main window that contains a DrawingArea widget, which
** displays a popup menu when the user presses the third mouse button.
*/

#include <Xm/RowColumn.h>
#include <Xm/MainW.h>
#include <Xm/DrawingA.h>

main (int argc, char *argv[])
{
    XmString       line, square, circle, exit_b, exit_acc;
    Widget         toplevel, main_w, drawing_a, popup_menu;
    void           popup_cb(Widget, XtPointer, XtPointer);
    XtAppContext   app;
    Arg            args[4];
    int            n;

    XtSetLanguageProc (NULL, NULL, NULL);
    toplevel = XtVaOpenApplication (&app, "Demos", NULL, 0, &argc, argv, NULL, 
                                    sessionShellWidgetClass, NULL);

    /* Create a MainWindow widget that contains a DrawingArea in
    ** its work window.
    */
    n = 0;
    XtSetArg (args[n], XmNscrollingPolicy, XmAUTOMATIC); n++;
    main_w = XmCreateMainWindow (toplevel, "main_w", args, n);

    /* Create a DrawingArea -- no actual drawing will be done. */
    n = 0;
    XtSetArg (args[n], XmNwidth, 500);  n++;
    XtSetArg (args[n], XmNheight, 500); n++;
    drawing_a = XmCreateDrawingArea (main_w, "drawing_a", args, n);
    XtManageChild (drawing_a);

    line = XmStringCreateLocalized ("Line");
    square = XmStringCreateLocalized ("Square");
    circle = XmStringCreateLocalized ("Circle");
    exit_b = XmStringCreateLocalized ("Exit");
    exit_acc = XmStringCreateLocalized ("Ctrl+C");
    popup_menu = XmVaCreateSimplePopupMenu (drawing_a, "popup", popup_cb,
                        XmNpopupEnabled, XmPOPUP_AUTOMATIC,
                        XmVaPUSHBUTTON, line, 'L', NULL, NULL,
                        XmVaPUSHBUTTON, square, 'S', NULL, NULL,
                        XmVaPUSHBUTTON, circle, 'C', NULL, NULL,
                        XmVaSEPARATOR,
                        XmVaPUSHBUTTON, exit_b, 'x', "Ctrl<Key>c", exit_acc,
                        NULL);
    XmStringFree (line);
    XmStringFree (square);
    XmStringFree (circle);
    XmStringFree (exit_b);
    XmStringFree (exit_acc);

    XtManageChild (main_w);
    XtRealizeWidget (toplevel);
    XtAppMainLoop (app);
}

/* popup_cb() -- invoked when the user selects an item in the popup menu */
void popup_cb (Widget menu_item, XtPointer client_data, XtPointer call_data)
{
    int item_no = (int) client_data;

    if (item_no == 3) /* Exit was selected -- exit */
        exit (0);

    /* Otherwise, just print the selection */
    puts (XtName (menu_item));
}

---

### Post by tgalati4 on 2010-05-11
Motif is an old window widget toolkit from the 1980s.

[http://en.wikipedia.org/wiki/Motif_(widget_toolkit](http://en.wikipedia.org/wiki/Motif_(widget_toolkit))

It's possible that when you upgraded that you didn't get all of the motif packages installed.

apt-cache search motif

If you do have all of the packages installed, then you should file a bug with the motif folks so they can tell you that it's not their problem and send you back here.

---

### Post by ylaprie on 2010-05-12
I checked that everything necessary for running Motif has been installed. 
The problem is a new problem (the program attached in the mail works fin with Ubuntu 9.10) and it appears with OpenMotif and Lesstif as well. 
It thus could arise from a bug somewhere else in X11 or Xt.

---

### Post by n8_sl8er on 2010-11-10
I'm having the same problem except the Motif apps I'm running are on another computer running RHEL. I set DISPLAY so the apps show on my Ubuntu box. So it seems like the bug is in Xorg.

---

