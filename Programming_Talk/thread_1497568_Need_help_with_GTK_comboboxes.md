---
title: "Need help with GTK comboboxes"
date: 2010-05-30
forum: Programming Talk
---

### Post by sandyd on 2010-05-30
I was wondering if you guys could figure out why the attached program keeps on segfaulting whenever the "go" button is clicked. :)

Thanks!

its compiled using
```

gcc      -o test test.c -W -Wall -ansi -pedantic -g `pkg-config --cflags --libs gtk+-2.0`

``````

#include <gtk/gtk.h>
#include <stdio.h>
#include <stdlib.h>
 

/* This function gets called when currently selected item changes */
static void
cb_changed( GtkComboBox *combo,
            gpointer     data )
{
    /* Obtain currently selected string from combo box */
    gchar *string = gtk_combo_box_get_active_text( combo );
    /* Print it to the console - if nothing is selected, print NULL */
    g_print( "Selected (simple): >> %s <<\n", ( string ? string : "NULL" ) );
 
    /* Free string */
    g_free( string );
}
 
/* This function deletes currently selected item from combo box */
static void

 
int
main( int    argc,
      char **argv )
{
    /*Common variables */
    GtkWidget *window;
    GtkWidget *vbox;
    GtkWidget *frame;
    GtkWidget *combo;
    GtkWidget *button;
    GtkWidget *app;
 
    /* Initialization */
    gtk_init( &argc, &argv );
 
    /* Create main window */
    window = gtk_window_new( GTK_WINDOW_TOPLEVEL );
    g_signal_connect( G_OBJECT( window ), "destroy",
                      G_CALLBACK( gtk_main_quit ), NULL );
    gtk_container_set_border_width( GTK_CONTAINER( window ), 10 );
 
    /* Create vbox */
    vbox = gtk_vbox_new( FALSE, 6 );
    gtk_container_add( GTK_CONTAINER( window ), vbox );
 
    /* Create frame */
    frame = gtk_frame_new( "Text API" );
    gtk_box_pack_start( GTK_BOX( vbox ), frame, FALSE, FALSE, 0 );
 
    /* Create combo box using text API and add some data to it */
    combo = gtk_combo_box_new_text();
    gtk_container_add( GTK_CONTAINER( frame ), combo );
    gtk_combo_box_append_text( GTK_COMBO_BOX( combo ), "Adobe_Flash_32bit" );
    gtk_combo_box_prepend_text( GTK_COMBO_BOX( combo ), "Adobe_Flash_64bit" );
    gtk_combo_box_insert_text( GTK_COMBO_BOX( combo ), 1, "Adobe_Flash_Remover" );
 
    /* Connect signal to tour handler function */
    g_signal_connect( G_OBJECT( combo ), "changed",
                      G_CALLBACK( cb_changed ), NULL );
  
    /* Add button that, when clicked, deletes currently selected entry */
    button = gtk_button_new_with_mnemonic( "_Go!" );
    gtk_box_pack_start( GTK_BOX( vbox ), button, FALSE, FALSE, 0 );
    gint index;
    index = gtk_combo_box_get_active( combo );
    g_signal_connect( G_OBJECT( button ), "clicked",
                      G_CALLBACK(index), app);

void Adobe_Flash_32bit(GtkWidget *widget, gpointer adobe)
{
  system("kdesudo 'apt-get -y install flashplugin-installer'"); 
  system("zenity --info --text 'Flash Plugin Installed Successfully'");
}
void install_beta(GtkWidget *widget, gpointer app)
{
  system("wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz");
  system("tar xvfz flashplayer10_1_rc4_linux_050510.tar.gz");
  system("kdesudo 'mv libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so'");
  system("rm flashplayer10_1_rc4_linux_050510.tar.gz");
  system("zenity --info --text 'Flash Player 10.1 Installed Successfully'");
}
void install_air(GtkWidget *widget, gpointer app)
{
  system("wget --progress=bar:force 'http://airdownload.adobe.com/air/lin/download/latest/AdobeAIRInstaller.bin' -O/dev/null 2>&1 | zenity --title='Downloading...' --progress --auto-close --auto-kill");
  system("chmod 667 AdobeAIRInstaller.bin");
  system("sh ./AdobeAIRInstaller.bin");
  system("rm AdobeAirInstaller.bin");
}
void Adobe_Flash_Remover(GtkWidget *widget, gpointer app)
{
  system("kdesudo 'rm /var/lib/dpkg/info/flashplugin* '");
  system("kdesudo 'rm /var/lib/dpkg/info/adobe-flashplugin* '");
  system("kdesudo 'dpkg --remove --force-remove-reinstreq adobe-flashplugin '");
  system("kdesudo 'apt-get -y  purge flashplugin-installer gnash mozilla-swfdec'"); 
  system("kdesudo 'rm /usr/lib/mozilla/plugins/libflashplayer.so'"); 
  system("kdesudo 'rm ~/.mozilla/plugins/libflash*'"); 
  system("kdesudo 'rm /usr/lib/firefox-3*/plugins/libflash*'"); 
  system("kdesudo 'apt-get -y remove --purge flashplugin-installer'"); 
  system("kdesudo 'apt-get -y remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash '");
  system("kdesudo 'apt-get -y remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin '");
  system("kdesudo 'apt-get -y remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin'");
  system("kdesudo 'apt-get -y remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin'");
  system("kdesudo 'rm -f ~/.mozilla/plugins/libflash* '");
  system("kdesudo 'rm -f ~/.mozilla/plugins/ns*flash* '");
  system("kdesudo 'rm -f /usr/lib/firefox-addons/plugins/libflash*'");
  system("kdesudo 'rm -f /usr/lib/firefox/plugins/libflash*'");
  system("kdesudo 'rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so' ");
  system("kdesudo 'rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so' ");
  system("kdesudo 'rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so' ");
  system("kdesudo 'rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so' ");
  system("kdesudo 'rm -f /usr/lib/mozilla/plugins/libflash*'");
  system("kdesudo 'rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so' ");
  system("kdesudo 'rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so' ");
  system("kdesudo 'rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' ");
  system("zenity --info --text 'Flash Plugin Removed'");
}
 
    /* Show our application and start main loop */
    gtk_widget_show_all( window );
    gtk_main();
 
    return( 0 );
}


```

---

### Post by splicerr on 2010-05-30
> **carlee said:**
> I was wondering if you guys could figure out why the attached program keeps on segfaulting whenever the "go" button is clicked. :)

Thanks!

its compiled using

```

    gint index;
    index = gtk_combo_box_get_active( combo );
    g_signal_connect( G_OBJECT( button ), "clicked",
                      G_CALLBACK(index), app);

```


You're passing an integer where it expects a callback function, so of course it's going to segfault.

---

### Post by sandyd on 2010-06-12
> **splicerr said:**
> You're passing an integer where it expects a callback function, so of course it's going to segfault.
I have a question then, how do I convert the index to the actual entry (in the combobox?)

---

### Post by simeon87 on 2010-06-12
> **carlee said:**
> I have a question then, how do I convert the index to the actual entry (in the combobox?)

The actual entry? An integer can only be converted to similar types, like double. If you need to pass a callback function, then it really needs to be a callback function. I only know the syntax on how to do this in Python so you should lookup some examples of that. If you want, in that callback function, you can get the active index and do further calculations based on that.

---

### Post by SledgeHammer_999 on 2010-06-13
What exaclty are you trying to accomplish with that line? Maybe we can propose an alternative approach if you explain what you want to do.

On a sidenote. You use Gtk+ while you use KDE? You're a particular one. It's not bad what you do, but someone would expect to use Qt for consistency. (I noticed that you use "kdesudo")

---

### Post by sandyd on 2010-06-13
Im trying to create a GTK combobox.

When a entry in the combobox is selected, and I click the "Go!" button, it does a callback for the function associated with the comobox entry

---

### Post by SledgeHammer_999 on 2010-06-15
Sorry but I really cannot I understand what you want to do.

Do you want cb_delete() called, when the "Go!" button is clicked?

---

### Post by sandyd on 2010-06-16
> **SledgeHammer_999 said:**
> Sorry but I really cannot I understand what you want to do.

Do you want cb_delete() called, when the "Go!" button is clicked?
No, I want the function thats associated with the combobox entry to be called

---

