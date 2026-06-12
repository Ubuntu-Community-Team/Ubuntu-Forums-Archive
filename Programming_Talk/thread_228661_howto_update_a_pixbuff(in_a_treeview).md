---
title: "howto update a pixbuff(in a treeview)"
date: 2006-08-03
forum: Programming Talk
---

### Post by rupert on 2006-08-03
Hi, 
im looking for a way to frequently update a pixbuf in my treeview.
here the function gets called and the pixbuf is passed to it.

g_timeout_add(1000, crypto_mount_set_pixbuf, pixbuf_mount);

```

crypto_mount_set_pixbuf(gpointer data){
	
   FILE *fp = popen("grep DATEN /etc/mtab", "r");
   gchar buf[512];
    GtkImage *pic_mount;
    GdkPixbuf *neues_bild;
    
    pic_mount = gtk_image_new_from_pixbuf(data);
    
    if (fp) 
    {
	size_t got = fread(buf, 1, sizeof(buf), fp);
        
        if(got != 0)
        {
	g_print("mounted");
        
        gtk_image_set_from_pixbuf(pic_mount, data);
        // data =  gdk_pixbuf_new_from_file("pics/mount.png", NULL);
        //g_object_set(pic_mount, "pixbuf", neues_bild, NULL);
        g_object_unref(data);
            
        }else{
            
	g_print("not mounted");
            
        data=  gdk_pixbuf_new_from_file("pics/unmount.png", NULL);
        //g_object_set(pic_mount, "pixbuf", neues_bild, NULL);
        g_object_unref(data);
        }
   }
//return data;
}

```

im goggleing for hours now, but I cant find any solution, alreday tried many function without success.

thx

---

