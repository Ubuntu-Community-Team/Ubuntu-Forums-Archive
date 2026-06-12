---
title: "Webview on 9.04 problem"
date: 2010-05-25
forum: Programming Talk
---

### Post by bcz on 2010-05-25
I used Synaptic to install webkit on my 9.04 system

The header files were installed under /usr/include/webkit-1.0/webkit which was fixed by ln -s webkit-1.0/webkit webkit

Now the link fails with "webkit_web_view_new" undefined

How do I sortout my library links?

test source:

//xi  .. clipboard graphics test

#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <gtk/gtk.h>
#include <webkit/webkit.h>

#include <gio/gio.h>
GtkWidget *screen,*baseBx,*sWndw,*webView;
static GIOChannel *stgFl;
static GIOStatus stat;
static GError **eFl;

static void WandE(GtkWidget *w,GtkWidget *window ){
        printf("WE\n");
        gtk_widget_destroy(w);
        return;}

static void PandE(GtkWidget *widget,GtkWidget *window ){
        printf("PE\n");
        gtk_exit(0);}

int main(int argc, char *argv[]){
        gtk_init(&argc,&argv);

        screen=gtk_window_new(GTK_WINDOW_TOPLEVEL);
        gtk_signal_connect(GTK_OBJECT(screen),"destroy",GTK_SIGNAL_FUNC(PandE),NULL);
        gtk_window_set_title(GTK_WINDOW(screen),"Screen");
        gtk_window_set_default_size(GTK_WINDOW(screen),800,400);
        baseBx=gtk_vbox_new(FALSE,2);
        gtk_container_add(GTK_CONTAINER(screen),baseBx);

        sWndw=gtk_scrolled_window_new(NULL,NULL);
        gtk_container_add(GTK_CONTAINER(baseBx),sWndw);

        webView=webkit_web_view_new();
        gtk_container_add(GTK_CONTAINER(sWndw),webView);
        gtk_widget_show_all(screen);

        gtk_main();
        return 0;
        }

Any help appreciated

Rgds Bill C

---

### Post by bcz on 2010-05-25
Problem fixed by adding "pkg-config --libs webkit-1.0" to cc command

Many Thanks

Bill C

---

