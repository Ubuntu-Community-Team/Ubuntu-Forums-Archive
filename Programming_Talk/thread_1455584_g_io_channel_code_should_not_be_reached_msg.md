---
title: "g_io_channel code should not be reached msg"
date: 2010-04-16
forum: Programming Talk
---

### Post by bcz on 2010-04-16
Am calling g_io_channel_write_chars from a gtk callback function and get the message "...glib2.0-2.20.1/glib/giochannel.c:2202:IA__g_io_channel_write_chars: code should not be reached

Have simplified source to reproduce problem:
```

//xh  .. pango test

#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <gtk/gtk.h>

#include <gio/gio.h>
GtkWidget *screen,*bttn;
static GIOChannel *stgFl;
static GIOStatus stat;
static GError **eFl;
static gint tCnt;

static void WandE(GtkWidget *w,GtkWidget *window ){
        printf("WE\n");
        gtk_widget_destroy(w);
        return;}

static void PandE(GtkWidget *widget,GtkWidget *window ){
        printf("PE\n");
        gtk_exit(0);}

void migFont(gchar *font){ //stage data for later processing
        int i=strlen(font)+1;
g_print("mgFnt\n");
        stat=g_io_channel_write_chars(stgFl,(gchar *)font,i,&tCnt,eFl);
        if(!tCnt==i){
                g_print("migPr Bad staged font write 0 %d %d\n",i,tCnt);
                exit(200);}
g_print("mgFnt1\n");
        }

static void migLnkPr(){
        stgFl=g_io_channel_new_file("printfile","w+",eFl);
        g_print("mgLnkPr stgFl:%p\n",(char *)stgFl);
        }

static void doApp(){
        migLnkPr();
        migFont("Nimbus Roman No9 L Bold 18");
        }

int main(int argc, char *argv[]){
        gtk_init(&argc,&argv);

        screen=gtk_window_new(GTK_WINDOW_TOPLEVEL);
        gtk_signal_connect(GTK_OBJECT(screen),"destroy",GTK_SIGNAL_FUNC(PandE),NULL);
        gtk_window_set_title(GTK_WINDOW(screen),"Screen");
        gtk_window_set_default_size(GTK_WINDOW(screen),250,100);
        bttn=gtk_button_new_with_label("_AppCode");
        gtk_signal_connect(GTK_OBJECT(bttn),"clicked",GTK_SIGNAL_FUNC(doApp),NULL);
        gtk_container_add(GTK_CONTAINER(screen),bttn);
        gtk_widget_show_all(screen);

        gtk_main();
        return 0;
        }

```
Can g_io_channel_io routines be used from a gtk callback ?

Any help appreciated

Rgds Bill

---

### Post by bcz on 2010-04-16
Dont know what happened to source code in above.  Have attached c source as a txt file

---

### Post by bcz on 2010-04-16
Thanks Slavik for editing original post which was unreadable.  Looked OK before posting.  As you say..  Check things carefully.  After 40 years system programming, I should do so automatically.  Unfortunately I'm not as accurate as I was before I got grey hair..  The "Cut and paste" concept is very useful, except when it includes unwanted whitespace for no discernable reason

Anyway many thanks

Rgds Bill C

---

### Post by MadCow108 on 2010-04-16
the encoding of the channel is set to non-binary data
so the write_chars ends on the terminating null byte of the string but your buffer count is greater than that.

either decrease the buffer count by one
or set the buffer count to -1 (it then assumes buffer is null terminated)
or set the encoding to binary

---

### Post by bcz on 2010-04-17
Thanks MC108.  I needed the line

stat=g_io_channel_set_encoding(stgFl,NULL,eFL);

after creating the file.

This sets binary mode on the file, which is what I need.  Simplified code posted as an example needed only a text file as you say

Problem resolved over weekend within 24 hrs.  MS howl in anguish

glib code might say something like "binary mode write on text mode io channel" prior to the "aborted" message

---

