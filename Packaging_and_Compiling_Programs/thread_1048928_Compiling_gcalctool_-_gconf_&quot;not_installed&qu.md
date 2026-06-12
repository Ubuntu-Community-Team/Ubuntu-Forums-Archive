---
title: "Compiling gcalctool - gconf &quot;not installed&quot;"
date: 2009-01-24
forum: Packaging and Compiling Programs
---

### Post by HyperHacker on 2009-01-24
I wanted to tweak the interface of gcalctool, but I can't compile it. ./configure says:```
checking for GCONF... configure: error: Package requirements (gconf-2.0 >= 1.1.9) were not met:

No package 'gconf-2.0' found
```But...```
$ sudo apt-get install gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gconf

$ sudo apt-get install gconf-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gconf-2.0

$ sudo apt-get install gconf2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gconf2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```:?

Is there not a tool that will give you a list of all packages a program needs to compile?

---

### Post by KIAaze on 2009-01-24
> **HyperHacker said:**
> 
Is there not a tool that will give you a list of all packages a program needs to compile?

Yes, there is:
```
sudo apt-get build-dep PACKAGE
```
Actually, this installs the dependencies.
To just get a list:
```
dpkg -I PACKAGE
apt-cache depends PACKAGE

```
[http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html](http://www.cyberciti.biz/tips/linux-debian-package-management-cheat-sheet.html)

While I'm at it, there's also:
```
apt-get source PACKAGE
```
(no root required here)

apt-get does more than just install/remove packages. 8)

edit: Easy package rebuilding:
[https://wiki.ubuntu.com/PbuilderHowto#Rebuilding%20a%20package](https://wiki.ubuntu.com/PbuilderHowto#Rebuilding%20a%20package) (best)
[http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/)
[http://cotton5415.wordpress.com/2007/04/26/how-to-rebuild-packages-with-source-files-in-debianubuntu/](http://cotton5415.wordpress.com/2007/04/26/how-to-rebuild-packages-with-source-files-in-debianubuntu/)

---

### Post by HyperHacker on 2009-01-24
Thanks. I forgot build-dep was a parameter for apt-get.

---

### Post by HyperHacker on 2009-01-24
So...```
static void
create_kframe()
{
    int i;
    char name[MAXLINE];
    GtkWidget *widget;
    PangoFontDescription *font_desc;
    GtkSizeGroup *size_group;
    GtkAccelGroup *accel_group;
    GtkWidget *treeview;
   
    X->ui = glade_xml_new(UI_FILE, NULL, NULL);
    if (X->ui == NULL) {
        GtkWidget *dialog;
        
        dialog = gtk_message_dialog_new(NULL, 0,
                                        GTK_MESSAGE_ERROR,
                                        GTK_BUTTONS_NONE,
                                        N_("Error loading user interface"));
        gtk_message_dialog_format_secondary_text(GTK_MESSAGE_DIALOG(dialog),
                                                 N_("The user interface file %s is missing or unable to be loaded. Please check your installation."), UI_FILE);
        gtk_dialog_add_buttons(GTK_DIALOG(dialog), GTK_STOCK_QUIT, GTK_RESPONSE_ACCEPT, NULL);
        
        gtk_dialog_run(GTK_DIALOG(dialog));
        exit(0);
    }
    
    /* When connecting up signals, would ideally use autoconnect but not 
     * sure how to get the build process working. 
     * See http://library.gnome.org/devel/libglade/unstable and
     * http://www.jamesh.id.au/software/libglade/ 
     * for some information on how to get this to work
     * glade_xml_signal_autoconnect(X->ui);
     */
    CONNECT_SIGNAL(kframe_key_press_cb);
    CONNECT_SIGNAL(button_cb);
    CONNECT_SIGNAL(menu_item_select_cb);
    CONNECT_SIGNAL(menu_item_deselect_cb);
    CONNECT_SIGNAL(mode_radio_cb);
    CONNECT_SIGNAL(inv_cb);
    CONNECT_SIGNAL(hyp_cb);
    CONNECT_SIGNAL(base_cb);
    CONNECT_SIGNAL(disp_cb);
    CONNECT_SIGNAL(quit_cb);
    CONNECT_SIGNAL(edit_cb);
    CONNECT_SIGNAL(copy_cb);
    CONNECT_SIGNAL(paste_cb);
    CONNECT_SIGNAL(insert_ascii_cb);
    CONNECT_SIGNAL(undo_cb);
    CONNECT_SIGNAL(redo_cb);
    CONNECT_SIGNAL(help_cb);
    CONNECT_SIGNAL(about_cb);
    CONNECT_SIGNAL(show_trailing_zeroes_cb);
    CONNECT_SIGNAL(show_thousands_separator_cb);
    CONNECT_SIGNAL(show_bitcalculating_cb);
    CONNECT_SIGNAL(show_registers_cb);
    CONNECT_SIGNAL(accuracy_radio_cb);
    CONNECT_SIGNAL(accuracy_other_cb);
    CONNECT_SIGNAL(accuracy_default_cb);    
    CONNECT_SIGNAL(constant_menu_cb);
    CONNECT_SIGNAL(function_menu_cb);
    CONNECT_SIGNAL(store_menu_cb);
    CONNECT_SIGNAL(recall_menu_cb);
    CONNECT_SIGNAL(exchange_menu_cb);
    CONNECT_SIGNAL(mouse_button_cb);
    /* Detect when populating the right-click menu to enable pasting */
    CONNECT_SIGNAL(buffer_populate_popup_cb);
    CONNECT_SIGNAL(shift_cb);
    CONNECT_SIGNAL(bit_toggle_cb);
    CONNECT_SIGNAL(aframe_delete_cb);
    CONNECT_SIGNAL(aframe_activate_cb);
    CONNECT_SIGNAL(aframe_response_cb);
    CONNECT_SIGNAL(spframe_delete_cb);
    CONNECT_SIGNAL(spframe_activate_cb);
    CONNECT_SIGNAL(spframe_response_cb);
    CONNECT_SIGNAL(rframe_delete_cb);
    CONNECT_SIGNAL(rframe_response_cb);
    CONNECT_SIGNAL(edit_constants_cb);
    CONNECT_SIGNAL(edit_functions_cb);
    CONNECT_SIGNAL(edit_constants_delete_cb);    
    CONNECT_SIGNAL(edit_constants_response_cb);
    CONNECT_SIGNAL(edit_constants_delete_cb);    
    CONNECT_SIGNAL(edit_functions_response_cb);
    CONNECT_SIGNAL(edit_functions_delete_cb);

    X->clipboard_atom = gdk_atom_intern("CLIPBOARD", FALSE);
    X->primary_atom = gdk_atom_intern("PRIMARY", FALSE);
    X->kframe       = GET_WIDGET("calc_window");
    X->aframe       = GET_WIDGET("ascii_dialog");
    X->aframe_ch    = GET_WIDGET("ascii_entry");
    X->spframe      = GET_WIDGET("precision_dialog");
    X->precision_spin  = GET_WIDGET("spframe_spin");
    X->rframe       = GET_WIDGET("register_dialog");
    X->con_dialog   = GET_WIDGET("edit_constants_dialog");
    X->fun_dialog   = GET_WIDGET("edit_functions_dialog");
    X->menubar      = GET_WIDGET("menubar");
    X->scrolledwindow = GET_WIDGET("display_scroll"),
    X->display_item = GET_WIDGET("displayitem"),
    X->bas_panel    = GET_WIDGET("basic_panel");
    X->sci_panel    = GET_WIDGET("scientific_panel");
    X->adv_panel    = GET_WIDGET("advanced_panel");
    X->fin_panel    = GET_WIDGET("financial_panel");
    X->bit_panel    = GET_WIDGET("bit_panel");
    X->clear_buttons[0] = GET_WIDGET("calc_clear_simple_button");
    X->clear_buttons[1] = GET_WIDGET("calc_clear_advanced_button");   
    X->mode_panel   = GET_WIDGET("mode_panel");
    X->trig[0]      = GET_WIDGET("degrees_radio");
    X->trig[1]      = GET_WIDGET("gradians_radio");
    X->trig[2]      = GET_WIDGET("radians_radio");
    X->base[0]      = GET_WIDGET("binary_radio");
    X->base[1]      = GET_WIDGET("octal_radio");
    X->base[2]      = GET_WIDGET("decimal_radio");
    X->base[3]      = GET_WIDGET("hexadecimal_radio");
    X->disp[0]      = GET_WIDGET("engineering_radio");
    X->disp[1]      = GET_WIDGET("fixed_point_radio");
    X->disp[2]      = GET_WIDGET("scientific_radio");
    X->inverse_toggle    = GET_WIDGET("inverse_check");
    X->hyperbolic_toggle = GET_WIDGET("hyperbolic_check");
    X->statusbar    = GET_WIDGET("statusbar");
    
    //HH: Change font size
	font_desc = pango_font_description_copy(X->clear_buttons[0]->style->font_desc);
	pango_font_description_set_size(font_desc, 24 * PANGO_SCALE);
	gtk_widget_modify_font(X->clear_buttons[0], font_desc);
	pango_font_description_free(font_desc);
	
	font_desc = pango_font_description_copy(X->clear_buttons[1]->style->font_desc);
	pango_font_description_set_size(font_desc, 24 * PANGO_SCALE);
	gtk_widget_modify_font(X->clear_buttons[1], font_desc);
	pango_font_description_free(font_desc);
    
    
    for (i = 0; i < 16; i++) {
        SNPRINTF(name, MAXLINE, "calc_%x_button", i);
        X->digit_buttons[i] = GET_WIDGET(name);
        
        //HH: Change font size
        font_desc = pango_font_description_copy(X->digit_buttons[i]->style->font_desc);
    	pango_font_description_set_size(font_desc, 24 * PANGO_SCALE);
        gtk_widget_modify_font(X->digit_buttons[i], font_desc);
        pango_font_description_free(font_desc);
    }
    
    for (i = 0; i < MAX_REGISTERS; i++) {
        SNPRINTF(name, MAXLINE, "register_entry_%d", i);
        X->regs[i] = GET_WIDGET(name);
    }
    
    /* Load buttons and set them all to be the same size */
    size_group = gtk_size_group_new(GTK_SIZE_GROUP_BOTH);
    for (i = 0; i < NBUTTONS; i++) {
        SNPRINTF(name, MAXLINE, "calc_%s_button", 
                 button_widgets[i].widget_name);
        X->buttons[i] = GET_WIDGET(name);            
        assert(X->buttons[i] != NULL);
        
        //HH: Change font size
        font_desc = pango_font_description_copy(X->buttons[i]->style->font_desc);
    	pango_font_description_set_size(font_desc, 24 * PANGO_SCALE);
        gtk_widget_modify_font(X->buttons[i], font_desc);
        pango_font_description_free(font_desc);
        
        gtk_size_group_add_widget(size_group, X->buttons[i]);
        
        g_object_set_data(G_OBJECT(X->buttons[i]), "calc_function", 
                          GINT_TO_POINTER(button_widgets[i].key));
    }

    /* Make popup buttons */
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_accuracy_button")),
                      "calc_menu", GET_WIDGET("accuracy_popup"));
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_shift_left_button")),
                      "calc_menu", GET_WIDGET("left_shift_popup"));
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_shift_right_button")),
                      "calc_menu", GET_WIDGET("right_shift_popup"));
    
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_constants_button")),
                      "calc_menu", GET_WIDGET("constants_popup"));
    for (i = 0; i < MAX_CONSTANTS; i++) {
        SNPRINTF(name, MAXLINE, "constant_menu_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "constant_id", GINT_TO_POINTER(i));
        X->constant_menu_labels[i] = gtk_bin_get_child(GTK_BIN(widget));
    }

    g_object_set_data(G_OBJECT(GET_WIDGET("calc_functions_button")),
                      "calc_menu", GET_WIDGET("functions_popup"));
    for (i = 0; i < MAX_FUNCTIONS; i++) {
        SNPRINTF(name, MAXLINE, "function_menu_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "function_id", GINT_TO_POINTER(i));
        X->function_menu_labels[i] = gtk_bin_get_child(GTK_BIN(widget));
    }

    g_object_set_data(G_OBJECT(GET_WIDGET("calc_store_button")),
                      "calc_menu", GET_WIDGET("memory_store_popup"));
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_recall_button")),
                      "calc_menu", GET_WIDGET("memory_recall_popup"));
    g_object_set_data(G_OBJECT(GET_WIDGET("calc_exchange_button")),
                      "calc_menu", GET_WIDGET("memory_exchange_popup"));
    for (i = 0; i < MAX_REGISTERS; i++) {
        SNPRINTF(name, MAXLINE, "store_menu_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "register_id", GINT_TO_POINTER(i));
        X->memory_store_labels[i] = gtk_bin_get_child(GTK_BIN(widget));
        
        SNPRINTF(name, MAXLINE, "recall_menu_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "register_id", GINT_TO_POINTER(i));
        X->memory_recall_labels[i] = gtk_bin_get_child(GTK_BIN(widget));
        
        SNPRINTF(name, MAXLINE, "exchange_menu_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "register_id", GINT_TO_POINTER(i));
        X->memory_exchange_labels[i] = gtk_bin_get_child(GTK_BIN(widget));
    }

    /* Load bit panel */
    for (i = 0; i < MAXBITS; i++)
    {
        SNPRINTF(name, MAXLINE, "bit_label_%d", i);
        X->bits[i] = GET_WIDGET(name);
        SNPRINTF(name, MAXLINE, "bit_eventbox_%d", i);
        g_object_set_data(G_OBJECT(GET_WIDGET(name)),
                          "bit_index", GINT_TO_POINTER(i));
    }
    
    /* Make menu tooltips displayed in the status bar */
    set_menubar_tooltip("quit_menu");
    set_menubar_tooltip("copy_menu");
    set_menubar_tooltip("paste_menu");
    set_menubar_tooltip("insert_ascii_menu");
    set_menubar_tooltip("undo_menu");
    set_menubar_tooltip("redo_menu");
    set_menubar_tooltip("view_basic_menu");
    set_menubar_tooltip("view_advanced_menu");
    set_menubar_tooltip("view_financial_menu");
    set_menubar_tooltip("view_scientific_menu");
    set_menubar_tooltip("show_trailing_zeroes_menu");
    set_menubar_tooltip("show_thousands_separator_menu");
    set_menubar_tooltip("show_bitcalculating_menu");
    set_menubar_tooltip("show_registers_menu");
    set_menubar_tooltip("help_menu");
    set_menubar_tooltip("about_menu");

    // ???
    widget = GET_WIDGET("kvbox");
    gtk_widget_set_direction(widget, GTK_TEXT_DIR_LTR);
    gtk_widget_set_direction(X->fin_panel, GTK_TEXT_DIR_LTR);
    
    /* Make dialogs transient of the main window */
    gtk_window_set_transient_for(GTK_WINDOW(X->aframe), GTK_WINDOW(X->kframe));    
    gtk_window_set_transient_for(GTK_WINDOW(X->spframe), GTK_WINDOW(X->kframe));
    gtk_window_set_transient_for(GTK_WINDOW(X->rframe), GTK_WINDOW(X->kframe));
    gtk_window_set_transient_for(GTK_WINDOW(X->con_dialog),
                                 GTK_WINDOW(X->kframe));

    /* Can't set max length for spin buttons in Glade 2 */
    gtk_entry_set_max_length(GTK_ENTRY(X->precision_spin), 2);

    gtk_dialog_set_default_response(GTK_DIALOG(X->con_dialog), 
                                    GTK_RESPONSE_ACCEPT);

    /* Make constant tree model */
    X->constants_model = create_constants_model();
    treeview = GET_WIDGET("edit_constants_treeview");
    gtk_tree_view_set_model(GTK_TREE_VIEW(treeview), X->constants_model);
    gtk_tree_selection_set_mode(
                                gtk_tree_view_get_selection(GTK_TREE_VIEW(treeview)),
                                GTK_SELECTION_SINGLE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("No."),
                  COLUMN_NUMBER, FALSE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("Value"),
                  COLUMN_VALUE, TRUE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("Description"),
                  COLUMN_DESCRIPTION, TRUE);

    /* Make function tree model */
    X->functions_model = create_functions_model();
    treeview = GET_WIDGET("edit_functions_treeview");
    gtk_dialog_set_default_response(GTK_DIALOG(X->fun_dialog), 
                                    GTK_RESPONSE_ACCEPT);
    gtk_window_set_transient_for(GTK_WINDOW(X->fun_dialog), 
                                 GTK_WINDOW(X->kframe));
    gtk_tree_view_set_model(GTK_TREE_VIEW(treeview), X->functions_model);
    gtk_tree_selection_set_mode(
                                gtk_tree_view_get_selection(GTK_TREE_VIEW(treeview)),
                                GTK_SELECTION_SINGLE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("No."),
                  COLUMN_NUMBER, FALSE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("Value"),
                  COLUMN_VALUE, TRUE);
    add_cf_column(GTK_TREE_VIEW(treeview), _("Description"),
                  COLUMN_DESCRIPTION, TRUE);

    X->display_buffer = gtk_text_view_get_buffer(GTK_TEXT_VIEW(X->display_item));
    gtk_widget_ensure_style(X->display_item);
    font_desc = pango_font_description_copy(X->display_item->style->font_desc);
    pango_font_description_set_size(font_desc, 8 * PANGO_SCALE);
    gtk_widget_modify_font(X->display_item, font_desc);
    pango_font_description_free(font_desc);
    gtk_widget_set_name(X->display_item, "displayitem");
    atk_object_set_role(gtk_widget_get_accessible(X->display_item), 
                                                  ATK_ROLE_EDITBAR);

    gtk_widget_realize(X->kframe);
    set_win_position();

    for (i = 0; i < 3; i++)
        g_object_set_data(G_OBJECT(X->trig[i]),
                          "trig_mode", GINT_TO_POINTER(i));
    for (i = 0; i < 4; i++)
        g_object_set_data(G_OBJECT(X->base[i]),
                          "base_mode", GINT_TO_POINTER(i));
    for (i = 0; i < 3; i++)        
        g_object_set_data(G_OBJECT(X->disp[i]),
                          "numeric_mode", GINT_TO_POINTER(i));

    /* Put status image into statusbar (glade doesn't support child widgets
     * in statusbars) */
    X->status_image = gtk_image_new_from_stock("", GTK_ICON_SIZE_BUTTON);
    gtk_widget_show(X->status_image);
    gtk_box_pack_start(GTK_BOX(X->statusbar), X->status_image, FALSE, TRUE, 0);

    /* Set modes for menu items */
    for (i = 1; i < 32; i++) {
        SNPRINTF(name, MAXLINE, "shift_left%d_menu", i);
        g_object_set_data(G_OBJECT(GET_WIDGET(name)),
                          "shiftcount", GINT_TO_POINTER(i));
        SNPRINTF(name, MAXLINE, "shift_right%d_menu", i);
        g_object_set_data(G_OBJECT(GET_WIDGET(name)),
                          "shiftcount", GINT_TO_POINTER(-i));
    }
    g_object_set_data(G_OBJECT(GET_WIDGET("view_basic_menu")),
                      "calcmode", GINT_TO_POINTER(BASIC));
    g_object_set_data(G_OBJECT(GET_WIDGET("view_advanced_menu")),
                      "calcmode", GINT_TO_POINTER(ADVANCED));
    g_object_set_data(G_OBJECT(GET_WIDGET("view_financial_menu")),
                      "calcmode", GINT_TO_POINTER(FINANCIAL));
    g_object_set_data(G_OBJECT(GET_WIDGET("view_scientific_menu")),
                      "calcmode", GINT_TO_POINTER(SCIENTIFIC));

    /* Make shortcuts for accuracy menus */
    accel_group = gtk_accel_group_new();
    gtk_window_add_accel_group(GTK_WINDOW(X->kframe), accel_group);
    for (i = 0; i < 10; i++) {
        SNPRINTF(name, MAXLINE, "acc_item%d", i);
        widget = GET_WIDGET(name);
        g_object_set_data(G_OBJECT(widget), "accuracy", GINT_TO_POINTER(i));
    }
}
```Any idea why the font size of the buttons just refuses to change? .gcalctoolrc and .gtkrc-2.0 don't do it either. Only globally changing the font size in Xfce Settings Manager works.

---

