---
title: "gtk+"
date: 2007-03-11
forum: Programming Talk
---

### Post by lucks on 2007-03-11
hi....am having some problems with coding in Gtk+ which is in C.....

i want to display 2 images on 2 different image widgets when only one item is selected from a combobox...that is i have assigned an item with 2 different images...

in fact i dont want to use the packing boxes  because its a bit difficult for me since am new to Gtk+...i know that its possible to do what am trying to say but i need a little help ....


please help me..

here is the code that am using to display an image when an item is selected from the combobox...please tell me what code must be added without using boxes....
[COLOR="DarkRed"]void
on_cbo_pickobject_changed              (GtkComboBox     *combobox,
                                         gpointer         user_data)
{

gchar *mystr;   
   
mystr = gtk_combo_box_get_active_text (combobox);   

if (strcmp (mystr, "Chair 1") == 0)

           GtkWidget *myimage_object = lookup_widget(GTK_WIDGET(combobox), "img_objectpreview");               
       
           gtk_image_set_from_file (GTK_IMAGE(myimage_object), "Pictures/Chair 1.jpg");

[COLOR="Blue"]i want to add the code here for the same item (Chair 1) and display another image Chair1.gif in an image widget which i`ve named as "img_patternpreview" just like for the first one (img_objectpreview): the code below is what i was trying but cant get it????[/COLOR]


       GtkWidget *myimage_pattern = lookup_widget(GTK_WIDGET(combobox), "img_patternpreview");           
       
       gtk_image_set_from_file (GTK_IMAGE(myimage_pattern), "Pictures/Chair 1.gif");
   
    }
    else
    {
      ...................

    }

g_free (mystr);

}[/COLOR]


i would be much grateful if somebody could help me...please

thanks

---

