---
title: "xcb_io.c"
date: 2010-08-16
forum: Programming Talk
---

### Post by utkarshrawat on 2010-08-16
what does xcb_io.c file does ? because iam getting this type of error 

```
xcb_io.c:242: process_responses: Assertion `(((long) (dpy->last_request_read) - (long) (dpy->request)) <= 0)' failed. 
```

---

### Post by tbastian on 2010-08-16
my guess is you're passing some bad/illegal argument to some function in the xcb_io library. I'm not sure what that library is nor what it does, but my advise is to run a debugger, isolate whatever call prints that message, then check the input.

---

### Post by utkarshrawat on 2010-10-15
In GTK I am creating sub menu  for a menu .Whne i run the application if I click  the menu with mouse or keyboard it coming perfectly alright . 
I am using a GPIO keypad (a external device just like keyboard)
when iam clicking on to menu with submenu ,iam getting the error ,which i have mentioned above

**CODE MENTIONED BELOW**
 ```
 gdk_color_parse ("dark grey", &colorPink);

  Hwindow1 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_widget_set_size_request (Hwindow1, 800, 600);
  gtk_window_set_title (GTK_WINDOW (Hwindow1), ("window1"));
  gtk_window_set_resizable (GTK_WINDOW (Hwindow1), TRUE);
  gtk_window_set_type_hint (GTK_WINDOW (Hwindow1), GDK_WINDOW_TYPE_HINT_DIALOG);
  gtk_window_set_gravity (GTK_WINDOW (Hwindow1), GDK_GRAVITY_CENTER);
  gtk_window_set_urgency_hint (GTK_WINDOW (Hwindow1), TRUE);
  gtk_widget_modify_bg(Hwindow1,GTK_STATE_NORMAL,&colorPink);
  gtk_widget_show(Hwindow1);

  fixed1 = gtk_fixed_new ();
  gtk_widget_show (fixed1);
  gtk_container_add (GTK_CONTAINER (Hwindow1), fixed1);
  gtk_widget_set_size_request (fixed1, 800, 500);
  gtk_container_set_border_width (GTK_CONTAINER (fixed1), 15);

  menubar1 = gtk_menu_bar_new ();

  gtk_widget_show (menubar1);
  gtk_fixed_put (GTK_FIXED (fixed1), menubar1, 24, 0);
  gtk_widget_set_size_request (menubar1, 500, 32);


 Wm_View = gtk_menu_item_new_with_label("View");//gtk_menu_new();
 gtk_menu_bar_append (GTK_MENU_BAR(menubar1), Wm_View);
 gtk_widget_show(Wm_View);

  Wm_View_menu = gtk_menu_new();
  gtk_menu_item_set_submenu(Wm_View, Wm_View_menu);

  for(i=0;i<3;i++)
  {
     switch(i)
     {
         case 0:
         WVView[i] = gtk_menu_item_new_with_label (VSetting);
               gtk_menu_append(GTK_MENU(Wm_View_menu), VView[i]);
                      gtk_widget_show (WVView[i]);
                        break;
             case 1:
            WVView[i] = gtk_menu_item_new_with_label (VStatus);
            gtk_menu_append(GTK_MENU(Wm_View_menu), WVView[i]);
            gtk_widget_show (WVView[i]);
              break;
             case 2:
               WVView[i] = gtk_menu_item_new_with_label ErrorLog);
                    gtk_menu_append(GTK_MENU(Wm_View_menu), WVView[i]);
                    gtk_widget_show (WVView[i]);
                        break;
                    }
         }



   Wm_Set = gtk_menu_item_new_with_mnemonic (SSet);
   gtk_widget_show(Wm_Set);
   gtk_container_add (GTK_CONTAINER (menubar1), Wm_Set);

 
```

---

### Post by saulgoode on 2010-10-15
```
 WVView[i] = gtk_menu_item_new_with_label ErrorLog);
```

Is this just a posting typo or is there also missing the lpar in the original source?

---

