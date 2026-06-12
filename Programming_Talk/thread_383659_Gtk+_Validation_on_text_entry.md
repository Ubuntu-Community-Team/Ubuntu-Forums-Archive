---
title: "Gtk+ Validation on text entry"
date: 2007-03-13
forum: Programming Talk
---

### Post by lucks on 2007-03-13
hi...am having a problem for a validation...:( 

 i want to display a dialog (when a button is clicked) if a number has been entered in a text entry which accepts only alphabets..that is a validation...

i`ve used the following code..there is no error and nothing is displayed...i dont know what it is...:confused: 

[B]void
on_bt_validate_clicked                 (GtkButton       *button,
                                       gpointer         user_data) 
{

         
         GtkWidget *entry;
   
       gboolean hasdigit = FALSE;
      
       const gchar * string = gtk_entry_get_text (entry);
      
       gint length = strlen (string);
      
       gint i = 0;

       while ((i < length) && (!hasdigit))
       {
               hasdigit = g_ascii_isdigit (string [i]);
               i++;
       }

       if (hasdigit)

       {
           /* Show dialog */
           GtkWidget *dialog1;
           dialog1 = create_dialog1 ();
           gtk_widget_show (dialog1);
              
       }     
     
       else
       {
          
           /* Do something else */
      
       } 


}[/B]

is this the proper way to do it?  please help me out...

any help will be appreciated

thanks

---

### Post by duff on 2007-03-13
you want  [http://www.gtk.org/api/2.6/gtk/GtkDialog.html#gtk-dialog-run](http://www.gtk.org/api/2.6/gtk/GtkDialog.html#gtk-dialog-run)

---

