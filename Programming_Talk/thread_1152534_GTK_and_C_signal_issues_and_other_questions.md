---
title: "GTK and C signal issues and other questions"
date: 2009-05-07
forum: Programming Talk
---

### Post by savagetwinky on 2009-05-07
My problem is I created a c program, its basicly a simple chat program. I'd like to write a gui and the only programming language I'm really familar with is C. I found gtk and since its all written in c I decided to make an attempt with that. So after some serious grinding last night I've managed to make a small chat window, that does absolutly nothing.

So I'm looking for some ideas on the best way to just create a gui around my c program that will capture the stdin and stdout of it.

A couple of my thoughts were to maybe to open my chat program as a child process and just pipe the inputs back to the parent using dup2. I have had a hard time finding good examples of using pipes in gtk, i've seen some examples but for the most part i couldn't find anything on polling the pipes. Another thought I had was just just have the window read and write to the terminal, then write a small script or another small c program to load the two and pipe everything back and forth, this way it might be easier that if the gui doesn't start or isn't available it could just boot into the terminal any way.

My other thoughts were are there any better languages to do this in, the other two I considered were C# since if i can get the sockets in my c program to work in windows too I'd be able to boot it up in either linux or windows. The other was perl, because I actually have a book on that.

Any help would be great, this was a small project for school, but we already passed in what we had, these additions are more or less because I'd like to learn how to integrate c programs i use later on with guis.

---

### Post by PmDematagoda on 2009-05-08
Why are you trying to integrate the core application and the GUI using IPC? You can do that more easily and reliably by adding calls from the GUI to the core application and compiling the stuff together. GTK+ is actually C, and it is something that can be used in any program, you do not have to have a GUI-only program in order to use it, you can use it whenever you want, except that you probably use a few more resources in doing so.

Also, the posting of the source code is useful. :)

---

### Post by savagetwinky on 2009-05-08
oh just the application is already build, and works in terminal, so i don't want to change that, so for now I'd like to just build a gui for it thats pretty basic. To make it interface with my program I'd have to figure out how it works with a pipe anyway since it actually uses select statement polls a socket and stdin, so i have no idea how i would build it on to of that any way without pipes, and i could put it at the end of my program and just open a pipe instead but i feel like for now its easier to just wrap it around the actual program. The first time i've even seen gtk code was wednesday night so I know i'm going to have to go through it a bit more. The only other languages i kinda know right now are assembly and vhdl and c. And i've never had any experience writing a gui, so this is more or less practice with gui, and signal handling.

---

### Post by PmDematagoda on 2009-05-09
> **savagetwinky said:**
> oh just the application is already build, and works in terminal, so i don't want to change that, so for now I'd like to just build a gui for it thats pretty basic. To make it interface with my program I'd have to figure out how it works with a pipe anyway since it actually uses select statement polls a socket and stdin, so i have no idea how i would build it on to of that any way without pipes, and i could put it at the end of my program and just open a pipe instead but i feel like for now its easier to just wrap it around the actual program. The first time i've even seen gtk code was wednesday night so I know i'm going to have to go through it a bit more. The only other languages i kinda know right now are assembly and vhdl and c. And i've never had any experience writing a gui, so this is more or less practice with gui, and signal handling.

Could you please post the source? At least of the GUI you're trying to create? Explanations and descriptions are all good, but without the source to take a look at, it's just too difficult to really help you.

---

### Post by savagetwinky on 2009-05-09
//*chatwin.c*//

#include "socketProj.h"
#include <gtk/gtk.h>


static void enter_callback (GtkWidget *widget,
                GtkWidget *entry)
{
    const gchar *entry_text;
    entry_text = gtk_entry_get_text (GTK_ENTRY (entry));
    //write to socket
}
    

int main(int argc, char *argv[])

{
    GtkWidget *window, *scrolled_win, *textview,  *hbox, *vbox,*entryl
    GtkTextBuffer *buffer;
    

    GIOChannel *g_signal_in;

    gtk_init (&argc,&argv);

    

    window= gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_window_set_title (GTK_WINDOW(window), "Chat");

    g_signal_connect (G_OBJECT (window), "destroy",
                      G_CALLBACK (gtk_main_quit), NULL);

        g_signal_connect (G_OBJECT (window), "delete_event",
                   G_CALLBACK (gtk_main_quit), NULL);

    gtk_container_set_border_width (GTK_CONTAINER(window), 1);
    gtk_widget_set_size_request (window,400,300);
    g_signal_connect (G_OBJECT (window), "destroy",
              G_CALLBACK (gtk_widget_destroy),
              G_OBJECT (window));


/** code for text view **/
    textview = gtk_text_view_new();

    gtk_text_view_set_wrap_mode (GTK_TEXT_VIEW (textview), GTK_WRAP_WORD);
    gtk_text_view_set_justification (GTK_TEXT_VIEW (textview), GTK_JUSTIFY_LEFT);

    gtk_text_view_set_editable (GTK_TEXT_VIEW (textview), FALSE);
    gtk_text_view_set_cursor_visible (GTK_TEXT_VIEW (textview), FALSE);

    gtk_text_view_set_left_margin (GTK_TEXT_VIEW (textview),10);
    gtk_text_view_set_right_margin (GTK_TEXT_VIEW (textview),10);

    buffer= gtk_text_view_get_buffer (GTK_TEXT_VIEW (textview));

    scrolled_win = gtk_scrolled_window_new (NULL,NULL);
    gtk_scrolled_window_set_policy (GTK_SCROLLED_WINDOW (scrolled_win), GTK_POLICY_AUTOMATIC, GTK_POLICY_ALWAYS);
    gtk_container_add (GTK_CONTAINER (scrolled_win), textview);

/** Code for text viewer buffer **/
    g_signal_in = g_io_channel_unix_new(socket);
    // read from socket  and out put in text buffer

    

/****Entry text code ****/
    entry = gtk_entry_new ();
    gtk_entry_set_max_length (GTK_ENTRY (entry), 200);
    g_signal_connect(G_OBJECT (entry),"activate",
             G_CALLBACK (enter_callback),
             (gpointer) entry);
/****End text entry******/    


    
/****End button ****/
    
    hbox = gtk_hbox_new (FALSE, 5);
    gtk_box_pack_start_defaults (GTK_BOX (hbox), entry);

    vbox=gtk_vbox_new (FALSE, 5);
    gtk_box_pack_start (GTK_BOX (vbox), scrolled_win,TRUE, TRUE,0);
    gtk_box_pack_start (GTK_BOX (vbox), hbox, FALSE, TRUE,0);

    gtk_container_add(GTK_CONTAINER (window),vbox);
    gtk_widget_show_all (window);
    
    gtk_main();
}

i Decided to add the socket in this one instead of trying to tie their stdin and stdout after, but still have an issue with i don't know how to handle inputs, but I'd like to just be able to take the ip as an argument, and open up a socket, I'm going to assume that its the same way you normally would in c. Then turn the socket into a signal so on a signal event i can read from it? but i have no idea how i would read from it in a callback fucntion, or how to specify this call back function. I havn't added the socket code but I'll probably just copy and past it in, if you'd like to see that code i can show you too.  But if i open the socket in this program then i don't have to poll stdin since its on a textentry event, and all i need to do is out how to read from a socket when there is something to be read.

---

### Post by PmDematagoda on 2009-05-10
Before trying to find a way to read from the socket periodically, did you check if whatever you put into the socket is actually displayed in the text view widget? If that works out, then you could use something like g_timeout_add to periodically check the socket for data and then write them into the text view widget.

---

### Post by savagetwinky on 2009-05-10
Nope i just started working with this the other day, and was having a hard time finding out about how to even read from a pipe or socket. Since they are both handled as file descriptors I'm just assuming they work the same way with gtk. I just could'nt find anything on how to poll a socket/pipe. I did find some stuff where they added a printf in the call back so it seems to me, if i opened up a socket like i did with my terminal program i could just write to on a text entry, and poll the socket for incoming data, and write it to the text buffer.

I'm compeletly new to gtk, and its my first experience writing a gui, so i'm finding it quite a bit difficult to get my head around. Like even if i did open a socket and a buffer, how do i pass those into one of the call back funtions?

---

### Post by PmDematagoda on 2009-05-10
> **savagetwinky said:**
> Nope i just started working with this the other day, and was having a hard time finding out about how to even read from a pipe or socket. Since they are both handled as file descriptors I'm just assuming they work the same way with gtk. I just could'nt find anything on how to poll a socket/pipe. I did find some stuff where they added a printf in the call back so it seems to me, if i opened up a socket like i did with my terminal program i could just write to on a text entry, and poll the socket for incoming data, and write it to the text buffer.

I'm compeletly new to gtk, and its my first experience writing a gui, so i'm finding it quite a bit difficult to get my head around. Like even if i did open a socket and a buffer, how do i pass those into one of the call back funtions?

About reading from the pipe/socket, why not try the simple thing and just use the normal functions, a non-blocking pipe/socket as well, and a g_timeout_add?

One of the things I do(though I am not sure if this is accepted by GTK+ devs), is put all the necessary, related stuff into one single struct, and then pass the whole struct to the callbacks being used. An example:-
```
#include <gtk/gtk.h>

/* The struct we are going to use to hold all the required data to pass along.*/
typedef struct _Stuff_struct { 
  GtkWidget *text_view;
  GtkTextBuffer *text_view_buffer;
  GtkTextIter text_iter;
} Stuff_struct;


void add_text(GtkWidget *calling_widget, Stuff_struct *stuff){
/*   GtkTextBuffer *text_view_buffer; */
/*   GtkTextIter text_iter; */



  gtk_text_buffer_insert( stuff->text_view_buffer, &(stuff->text_iter),gtk_entry_get_text(GTK_ENTRY(calling_widget)),-1);


}

int main(int argc, char *argv[]){

  GtkWidget *window, *text_entry, *text_view, *vbox;
  Stuff_struct stuff;

  gtk_init(&argc,&argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  vbox = gtk_vbox_new(FALSE,0);
  text_entry = gtk_entry_new();

  stuff.text_view = gtk_text_view_new();

  stuff.text_view_buffer = gtk_text_view_get_buffer( GTK_TEXT_VIEW(stuff.text_view) );
  gtk_text_buffer_get_end_iter( (stuff.text_view_buffer), &(stuff.text_iter));

  gtk_box_pack_start(GTK_BOX(vbox), stuff.text_view,FALSE,FALSE,0);
  gtk_box_pack_start(GTK_BOX(vbox),text_entry,FALSE,FALSE,0);

  gtk_container_add(GTK_CONTAINER(window),vbox);

  g_signal_connect(window,"delete-event",gtk_main_quit,NULL);

  g_signal_connect(text_entry,"activate",G_CALLBACK(add_text),&stuff);

  gtk_widget_show_all(window);

  gtk_main();

  return 0;

}
```

---

### Post by savagetwinky on 2009-05-10
I've actually seen people do that thing with the structure but wasn't sure why exactly. 
But anyway, how to make a non blocking socket? I used select() to get around that in my original code, all it did for the client was poll stdin and my socket.

and with g_time_add()

I think i probably would need a structure because part of my problem was i didn't really under stand how data would be passed to my.

so would it be all right to g_time_add(g_priority_default,50,read,stuff,NULL) 
where read is a function to read from my socket and enter it in to the text view buffer, and stuff is the structure containing  textbuf and socket.

---

### Post by PmDematagoda on 2009-05-10
> **savagetwinky said:**
> I've actually seen people do that thing with the structure but wasn't sure why exactly. 
But anyway, how to make a non blocking socket? I used select() to get around that in my original code, all it did for the client was poll stdin and my socket.

and with g_time_add()

I think i probably would need a structure because part of my problem was i didn't really under stand how data would be passed to my.

so would it be all right to g_time_add(g_priority_default,50,read,stuff,NULL) 
where read is a function to read from my socket and enter it in to the text view buffer, and stuff is the structure containing  textbuf and socket.

About the socket, I am not really sure as I have not done a lot of network programming, but how about giving fcntl() a try on that?

And the g_timeout_add seems to be ok, but you left out the text entry pointer and the iteration variable in the struct to be used.:)

---

### Post by dwhitney67 on 2009-05-10
> **savagetwinky said:**
> ... 
But anyway, how to make a non blocking socket? I used select() to get around that in my original code, all it did for the client was poll stdin and my socket.
...

Since you have to poll stdin and a socket, the correct procedure is to use the select().  If you are required to perform other tasks, then you can specify a timeout period for the select(), so that it does not block indefinitely.

If you need to make a socket non-blocking, the only way I am familiar with it to tweak its options using fcntl().  So assuming you have a socket descriptor, sd, that is returned from a call to socket(), then the fcntl() call would be:
```

int sd = socket(...);

if (fcntl(sd, F_SETFL, O_NONBLOCK) != 0)
{
  /* error */
}

```

---

### Post by savagetwinky on 2009-05-10
@dwhitney67
Thanks but i'm pretty sure with gtk i know longer nead to use select since with gtk, i'm not using stdin anymore, but an event with the text entry.
 
@PmDematagoda
Yah i'll give it a try with opening one socket in the structure then, the normal way i did it in c, then try to let all the gtk calls manage it.
 
typedef struct _Stuff_struct { 
  GtkWidget *text_view;
  GtkTextBuffer *text_view_buffer;
  GtkTextIter text_iter;
  int sockFd;
} Stuff_struct;
 
since stdin and pipes, and a socket are all treated as a file descriptor i'm going to assume i can treat them the same way in this. The only thing now is it possible to a nonblock recieve? select seems to be more involved then what i need since i just need to check one signal but if thats what has to happend then w/e.

---

