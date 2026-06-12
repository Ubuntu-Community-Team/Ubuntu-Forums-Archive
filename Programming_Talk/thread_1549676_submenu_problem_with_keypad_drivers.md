---
title: "submenu problem with keypad drivers"
date: 2010-08-10
forum: Programming Talk
---

### Post by utkarshrawat on 2010-08-10
Hi All 
I am getting a strange error in GTK .I have GPIO keypad(physical device) I have its shared library  which i have sucessfully integrated with my GTK application .
In my GTK application i have created a window which is having list of menu's & submenu's. This program is executing well i.e. I meant i  can see all my menu's & submenu's perfectly all right (**with mouse**)

But when i run this program with my GPIO keypad .I can move along with menus( **SUB MENU not created**) easily  .

But when I am creating submenu for suppose only for one menu & iam pressing  keypad to go to that menu which is having submenus ,my keypad control goes to mouse & give me error 

** fatal IO error 11 (Resource temporarily unavailable) **
 or sometimes 

[B]/../src/xcb_io.c:240 process_responses Assertion: (((long)
(dpy->last_request_read)-(long)(dpy->req)<=0) failed[/B] 

Below is the code for the window ,menu & submenus
```
gdk_color_parse ("dark grey", &colorPink);

CREATING WINDOW
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
  //gtk_widget_set_size_request (menubar1, 240, 32);
  gtk_widget_set_size_request (menubar1, 500, 32);
///////////CREATING MENUS//////////////

   Wm_View = gtk_menu_item_new_with_label("View");//gtk_menu_new();
  gtk_menu_bar_append (GTK_MENU_BAR(menubar1), Wm_View);
  gtk_widget_show(Wm_View);

Wm_Set = gtk_menu_item_new_with_mnemonic (SSet);
   gtk_widget_show(Wm_Set);
   gtk_container_add (GTK_CONTAINER (menubar1), Wm_Set);

 Wm_AdvSet = gtk_menu_item_new_with_mnemonic (AdvSet);
      gtk_widget_show(Wm_AdvSet);
      gtk_container_add (GTK_CONTAINER (menubar1), Wm_AdvSet);


///////////////CREATING MENU & SUBMENU ///////////////
        GtkWidget *WVTest;
         Wm_Test = gtk_menu_item_new_with_mnemonic (("Test"));
         gtk_widget_show (Wm_Test);
         gtk_container_add (GTK_CONTAINER (menubar1), Wm_Test);

         Wm_Test_menu = gtk_menu_new ();
         gtk_menu_item_set_submenu (GTK_MENU_ITEM (Wm_Test), Wm_Test_menu);
         WVTest = gtk_menu_item_new_with_label (VSetting);
         gtk_menu_append(Wm_Test_menu, WVTest);
         gtk_widget_show (WVTest);

```

Looking forward for reply

---

