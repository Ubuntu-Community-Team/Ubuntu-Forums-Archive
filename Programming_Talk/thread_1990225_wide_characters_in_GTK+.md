---
title: "wide characters in GTK+"
date: 2012-05-29
forum: Programming Talk
---

### Post by chuchi on 2012-05-29
Hi everyone!! I am developing  GTK application that has to treat with wide characters. But when I pass a wide character to a label, it does not work properly.
 

 This is a sample code that does not work:
 

 ```

 

 

 int main(int   argc, char *argv[] ){
 	
 	gtk_init (&argc, &argv);
 	
     setlocale(LC_CTYPE, "UTF-8");
     GtkWidget *window=gtk_window_new (GTK_WINDOW_TOPLEVEL);
     GtkWidget *hbox=gtk_hbox_new (FALSE, 1);
 	wchar_t wide[]=L"this is wide";
     GtkWidget *label=gtk_label_new(wide);
 	gtk_container_add (GTK_CONTAINER (window), hbox);
 	gtk_box_pack_start (GTK_BOX (hbox), label, FALSE, FALSE, 0);
 	
 	gtk_widget_show(label);
 	gtk_widget_show_all (window);
 

 	gtk_main ();
      
      
     return 0;
 }
 

 
```


The label is not shown properly, why??


Thank you very much!

---

