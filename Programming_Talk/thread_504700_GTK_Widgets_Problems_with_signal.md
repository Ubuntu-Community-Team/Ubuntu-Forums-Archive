---
title: "GTK Widgets: Problems with signal"
date: 2007-07-19
forum: Programming Talk
---

### Post by ADT on 2007-07-19
I am having a problem with closing a gtk widget window when I press a button i.e. when the clicked signal is emitted.

I want the window to close when a button is pressed but only if a function triggered by the button returns a '1'.



The following is the button **NEXT**:

It is packed into the box **sub_box** which is packed into the **window widget**.

**set_ifaces_check** is a function that checks if two IP addresses are in the correct format. 
If they are correct **set_ifaces_check** will return a **0**, if they are not it will return a **1**.

**wle** is a pointer to a structure which contains two char strings which contain the two IP addresses.

```

button = gtk_button_new_with_label ( "NEXT" );
                 gtk_box_pack_start ( GTK_BOX ( sub_box ), 
                                                     button, TRUE, TRUE, 0 );
                 gtk_widget_show ( button );
                 g_signal_connect ( G_OBJECT ( button), "clicked",
                                                  G_CALLBACK ( set_ifaces_check ), 
                                                  wle );

/* Psuedo Code to close window if set_ifaces_check returns 1 */

if ( returned_value = 1 )
{
      gtk_widget_destroy ( window );
}


```




I want the window I am in now i.e. The **SET Interfaces window**
to close if when the NEXT button is pressed the IP addresses are in the correct format.

How can I do this?

How do I close a window when the button's signal doesn't directly call gtk_widget_destroy ( window ) and how do I get it to work when only a certain condition is met i.e. the IP addresses being correct.

---

### Post by smartbei on 2007-07-19
See if this helps you out:
Inside the hello function you can put any code you want, to compare whatever.
```

import pygtk
pygtk.require('2.0')
import gtk


class GTKCL:
    def hello(self, widget, data=None):
    	if data=="whatever":
    		self.destroy(widget)
    	else:
    		print data

    def delete_event(self, widget, event, data=None):
        print "delete event occurred"
        return False

    def destroy(self, widget, data=None):
        print "destroy signal occurred"
        gtk.main_quit()

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)
        self.window.set_border_width(10)
        self.button = gtk.Button("Hello World")
        self.button.connect("clicked", self.hello, "whatever")
        self.window.add(self.button)
        self.button.show()
        self.window.show()

    def main(self):
        gtk.main()

g = GTKCL()
g.main()

```

---

### Post by leibowitz on 2007-07-19
Here's a brief example. First, create another function that will receive our struct, and will call set_ifaces_check.

This is the prototype you need to respect for the callback function[1].
```
void user_function(GtkButton *button, gpointer   user_data)
```

The user_data field is what you sent to the g_signal_connect. It's the pointer to your struct wle. But we need more infos than that. We need the GtkWindow pointer. You can do what you want to receive that. I choose to build another struct and embed yours into that one.


```

struct _withwindow
{
  GtkWidget *window;
  struct _yourdata *wle;
} my_data_struct;

...

g_signal_connect ( G_OBJECT ( button), "clicked",
                                                  G_CALLBACK ( my_callback_function ), 
                                                  &my_data_struct );

...

void my_callback_function(GtkButton *button, gpointer data)
{
   struct _withwindow *my_data_struct = (struct _withwindow*) data;

   if( set_ifaces_check(my_data_struct->wle) == 1 )
     gtk_widget_destroy(my_data_struct->window);
   
}

```

I suppose that your set_ifaces_check function has a prototype like this one below. Please adapt if needed.

```
int set_ifaces_check(struct _yourdata *);
```

[1] syntax of the callback function in respect to the "clicked" signal of a GtkButton
[http://developer.gnome.org/doc/API/2.0/gtk/GtkButton.html#GtkButton-clicked](http://developer.gnome.org/doc/API/2.0/gtk/GtkButton.html#GtkButton-clicked)

---

### Post by ADT on 2007-07-20
Thank you smartbei and leibowitz for the replies.

smartbei:
I forgot to say that I was using C. I don't know the python language. But I can kind of understand what its doing. Cheers.

leibowitz:
Thank you you for the example good. I tried it out but I got a segmentation fault.

I pass the **&my_data_struct** structure to the **my_callback_function** function and then cast the **gpointer data** back to the **struct _withwindow** structure.

I then didn't bother with the if statement but just wrote the following:
**gtk_widget_destroy(my_data_struct->window);**

This line causes a seg fault. 
Does trying to shut down a **GtkWidget *window** from outside of its original callback cause a seg fault.

This is the debugging data:
**sudo gdb ./a**

```
(gdb) run
Starting program: /home/adam/work/wle/code/july/week3/a 
[Thread debugging using libthread_db enabled]
[New Thread -1218095424 (LWP 4355)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1218095424 (LWP 4355)]
0xb7e84123 in gtk_widget_destroy () from /usr/lib/libgtk-x11-2.0.so.0
(gdb) 
```

This happens when I press the NEXT button which calls the **my_callback_function** which has the **gtk_widget_destroy(my_data_struct->window);** line of code.

I left out the wle structure and if statement.



**Temporary Solution Found**
I tried a different way of doing things but it's not the way I want it to work.
When I press the **NEXT** button I have two g_signals triggered by the same button (NEXT).
One g_signal calls the **set_ifaces_check** function the other g_signal destroys the **window widget** that contains everything in the **SET interfaces screen**.

Inside the **set_ifaces_check** I check if the IP addresses are correct and if they are I create the next screen.
If the IP addresses are wrong I create a Popup that shows the error. When the user presses the Ok button on the Popup the **SET interfaces screen** is created again.

---

### Post by leibowitz on 2007-07-20
I probably did something wrong. I did not tried my code by the way. My bad.

I will look into this later on to make it work properly. I'm sure it's possible.

---

### Post by ADT on 2007-07-20
No problem. 

It was a good solution but I don't understand why it was giving a seg fault.

I found another way to do it. As in to destroy the **Set interfaces Screen** when clicking NEXT and if the IP addresses are wrong to create a Popup. Then when I click the Popup it  creates the **Set interfaces screen** again, and the Popup destroys itself.

I don't think thats the normal behaviour of applications. Usually when an error message pops, up the screen that led to the message remains.

---

### Post by ADT on 2007-07-22
leibowitz any luck with getting it to work?

---

### Post by leibowitz on 2007-07-22
See attached example.

---

### Post by ADT on 2007-07-22
Thank you very much for the code. 
It is a great help.

---

### Post by ADT on 2007-07-26
I have another problem that I can't seem to figure out.

**In**
**main ( int argc, char *argv[] )**

I create a struct called wle

```
struct data_list wle;
```

and I pass the address of it (pass by reference) to a function call set_ifaces, when I press the start button.

```
/* Setup the start button */
    button = gtk_button_new_with_label ( "START" );
    g_signal_connect ( G_OBJECT ( button ), "clicked",
                       G_CALLBACK ( set_ifaces ), &wle );
    gtk_box_pack_start ( GTK_BOX ( box ), button, FALSE, FALSE, 0 );
    gtk_widget_show ( button );
```

**In**
**set_ifaces ( GtkWidget *widget, gpointer data )**

I cast the data variable to a data_list struct.

```
struct data_list *wle = ( struct data_list* ) data;
```

I then allow the user to fill in the elements of the wle struct by calling gtk_entry functions. All the time passing by reference i.e 
```
&wle->ifaces.client.ip
```

Then there is a button called NEXT when it is pressed I call a function that creates two threads which are both passed the **wle data** again by reference. Then I destroy the set_ifaces window.

In the threads I try to display the data in the wle struct but they only display rubbish.

The problem is, is when I destroy the set_ifaces window all the data in the wle struct becomes deallocated.

**My question is how do I keep that data? **

And still be able to destroy a window. In order to stop the dealloction the only way I know how is to keep every window that changes something in the struct open. That is a lot of windows!

---

### Post by leibowitz on 2007-07-26
You need to post your code right here, otherwise it's impossible to help you.

---

### Post by ADT on 2007-07-26
I put in some comments trying to explain what I am trying to do.

The main problems I'm having are in the gtk_screens.c file.

**set_ifaces**
Lines 190 to 218

**set_capture**
Lines 394 to 420


```
/* &&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&& */
    /*                AREA CAUSING ME THE GREATEST DIFFICULTY                   */
    /* &&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&& */
    
    /* Setup Next Button */
    button = gtk_button_new_with_label ( "NEXT" );
    gtk_box_pack_start ( GTK_BOX ( sub_box ), 
                         button, TRUE, TRUE, 0 );
    gtk_widget_show ( button );
    
    /* Signal 1 */
    /* comment out this signal to test threads */
    g_signal_connect ( G_OBJECT ( button ), "clicked",
                       G_CALLBACK ( set_ifaces_check ), 
                       wle );
    
    /* uncomment this signal to test threads */
    /*g_signal_connect ( G_OBJECT ( button ), "clicked",
                       G_CALLBACK ( start_capture ), 
                       wle );
                       */
    
    /* Closes the set_ifaces window using this signal call causes the struct data to be deallocated */
    /*  Comment out this signal call to allow the struct data to remain. */
    /*g_signal_connect_swapped ( G_OBJECT ( button ), "clicked",
                               G_CALLBACK ( gtk_widget_destroy ), 
                               G_OBJECT ( window ) );*/
           
    /* &&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&&& */
```


```
* f set_capture */
void set_capture ( void *data )
{
    GtkWidget* window;
    GtkWidget* button;
    
    struct data_list *wle = ( struct data_list* ) data;
                
    window = gtk_window_new ( GTK_WINDOW_TOPLEVEL );
    gtk_container_set_border_width ( GTK_CONTAINER ( window ), 50 );
        
    button = gtk_button_new_with_label ( "CAPTURE" );
    gtk_container_add ( GTK_CONTAINER ( window ), button );
    g_signal_connect ( G_OBJECT ( button ), "clicked",
                       G_CALLBACK ( start_capture ),
                       wle );
    
    /* If I leave this window here then the wle structure is not deallocated */
    
    /* comment signal */
    /*g_signal_connect_swapped ( G_OBJECT ( button ), "clicked",
                               G_CALLBACK ( gtk_widget_destroy ),
                               G_OBJECT ( window ) );*/
    
        
    gtk_widget_show ( button );
    gtk_widget_show ( window );    
}
```

Edit: The compiled program needs to be run in root because of a call that finds all network interface devices.

---

### Post by ADT on 2007-07-30
The problem is solved. 

I studied your code more thoroughly and the answer was right there. The problem was with using declarations like these in my structures:

```

struct iface_settings {
	char *ip;
	char *client_dev;
        char *server_dev;
	char *filter;
        bpf_u_int32 net_mask;
	int is_iface_client;
};

```

And in entry box callbacks I was putting the data into the address of the structures like this:

```

    struct iface_settings *iface = ( struct iface_settings* ) data;
    const gchar *entry_text;
        
    entry_text = gtk_entry_get_text ( GTK_ENTRY ( widget ) );
        
    iface->ip = ( char* ) entry_text;

```

For some reason the way these are declared and assigned cause the data to be lost when the window that was used to input the data is exited.

The code that works for the structure is:

```

struct iface_settings {
	char ip [15];
	char client_dev [15];
        char server_dev [15];
	char filter [100];
        bpf_u_int32 net_mask;
	int is_iface_client;
};

```

And for the entry box callbacks:

```

    struct iface_settings *iface = ( struct iface_settings* ) data;
    const gchar *entry_text;
    char *text;
    
    entry_text = gtk_entry_get_text ( GTK_ENTRY ( widget ) );
    text = ( char* ) entry_text;
    
    g_strlcpy ( iface->ip, text, 15 );

```

Now I can quit windows at any stage and any changes they caused to the data remains.

Thanks

---

