---
title: "[SOLVED] Export to PICASA in F-Spot fail"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by wariskampar on 2008-09-26
When I click on this button, F-Spot will be terminated. I try running F-Spot in Terminal and I got some error message:

Reloading
item changed

(f-spot:8198): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.

What does it means? Can anyone tell me how to solve this problem?

---

### Post by wariskampar on 2008-09-26
I just remember I changed my Gmail (PICASA is effected too) yesterday. So maybe, F-spot fail to connect to my PICASA online and terminate itself subsequently. Now I try to change PICASA password in F-Spot but nowhere I find the option. Does anyone knows?

---

### Post by vikramaditya on 2008-09-26
there might be some help in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/238212").

---

### Post by wariskampar on 2008-09-26
Thanks vikram. On the 2 post (referring to bug report), somebody tell about changing key ring. How do I do it?

This is my f-spot --debug outcome:

```
Reloading
item changed

(f-spot:11938): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
GoogleAccount.Connect()
Can not connect to Picasa. Bad username ? password ? network connection ?
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpotGoogleExport.GoogleExport.HandleAlbumOptionMenuChanged (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.gtk_option_menu_set_menu(IntPtr , IntPtr )
   at Gtk.OptionMenu.set_Menu(Gtk.Widget value)
   at FSpotGoogleExport.GoogleExport.PopulateAlbumOptionMenu(Mono.Google.Picasa.PicasaWeb picasa)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected, System.String token, System.String text)
   at FSpotGoogleExport.GoogleExport.Connect(FSpotGoogleExport.GoogleAccount selected)
   at FSpotGoogleExport.GoogleExport.Connect()
   at FSpotGoogleExport.GoogleExport.Run(IBrowsableCollection selection)
   at FSpot.Extensions.ExportMenuItemNode.OnActivated(System.Object o, System.EventArgs e)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

```

---

### Post by wariskampar on 2008-09-26
Problem solved! Just change the password in Applications>Accessories>Password and Application and once done, F-Spot and PICASA work along well again!

---

