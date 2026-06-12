---
title: "swapping image of gtk button"
date: 2012-11-19
forum: Programming Talk
---

### Post by 681ankit on 2012-11-19
I am creating a program in which ,there are two buttons ,when these two buttons are clicked one after other ,it will swap the image assign to these buttons..Can't find way ..
** But I'm getting error :

GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed


code is:-

<code>
#include<gtk/gtk.h>
#include<stdio.h>


static GtkWidget *prev_b; // previous button click stored here
static GtkWidget *prev_i;    // previuos button's image
static int count=0;  //distinguish between two button's click

static void on_click(GtkWidget * button, GtkWidget *b);
int main(int argc , char *argv[])
    { 

    GtkWidget * window;
    GtkWidget *button1,*button2;
    GtkWidget *img1,*img2,*temp;
    GtkWidget * hbox;
    
    gtk_init(&argc,&argv);
    
    
    
    window=gtk_window_new(GTK_WINDOW_TOPLEVEL);
    hbox=gtk_hbox_new(TRUE,5);
    
    button1=gtk_button_new_with_label("");
    button2=gtk_button_new_with_label("");
    
    img1=gtk_image_new_from_file("img/other/h6.png");
    img2=gtk_image_new_from_file("img/other/h7.png");
    temp=gtk_image_new_from_file("img/other/temp.png");
    
    
    gtk_button_set_image(GTK_BUTTON(button1),img1);
    gtk_button_set_image(GTK_BUTTON(button2),img2);
    gtk_box_pack_start_defaults(GTK_BOX(hbox),button1);
    gtk_box_pack_start_defaults(GTK_BOX(hbox),button2);
    
    
    
    gtk_container_add(GTK_CONTAINER(window),hbox);
    gtk_widget_show_all(window);
    gtk_widget_show(img1);
    gtk_widget_show(img2);
    gtk_widget_show(temp);
    
    
    
    
    
    g_signal_connect(G_OBJECT(button1),"clicked",G_CALLBACK(on_click),img1);
    g_signal_connect(G_OBJECT(button2),"clicked",G_CALLBACK(on_click),img2);
    g_signal_connect(G_OBJECT(window), "destroy",G_CALLBACK(gtk_main_quit), NULL);
    
    
    gtk_main();
    
    return 0;
    }
    
    
    
    
static void on_click(GtkWidget * button, GtkWidget *img)
    {
        
    
        if(count==1)
            {
                count=count-1;
                if(prev_i==img)return;
                else
                {    
                gtk_button_set_image(GTK_BUTTON(button),prev_i);//setting image to current button
                gtk_button_set_image(GTK_BUTTON(prev_b),img); //setting image to prev button
                }
                return ;
            }
        if(count==0)
            {
                count=count+1;
                prev_b=button;
                prev_i=img;
                return ;
            }
            
        
            
        
    }

</code>

---

### Post by mali2297 on 2012-11-19
I believe the problem is that the button takes *ownership* of the image when you call *gtk_button_set_image*. Then, when you replace the image with a new call to the same function, the old image is destroyed.

As a solution, increase the reference count of the image objects after their creation:
```

img1=gtk_image_new_from_file("img/other/h6.png");
img2=gtk_image_new_from_file("img/other/h7.png");

g_object_ref (img1);
g_object_ref (img2);

gtk_button_set_image(GTK_BUTTON(button1),img1);
gtk_button_set_image(GTK_BUTTON(button2),img2);

```
Ideally, you should also unref them when you are finished using them.

---

