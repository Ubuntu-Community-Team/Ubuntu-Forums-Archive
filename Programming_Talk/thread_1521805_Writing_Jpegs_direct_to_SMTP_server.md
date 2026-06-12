---
title: "Writing Jpegs direct to SMTP server"
date: 2010-07-01
forum: Programming Talk
---

### Post by bcz on 2010-07-01
Hi All

Just wondering how best to send an image with inline text as an email, direct from a C program.  Tried sending HTML as text and that is what arrived at the other end.. not surprising really.  Cant find a GTK API to do this.  Any ideas.  Sample code follows:

//xf1

#include <stdio.h>
#include <gtk/gtk.h>

GtkWidget *screen,*bttn;

static void WandE(GtkWidget *w,GtkWidget *window ){
        printf("WE\n");
        gtk_widget_destroy(w);
        return;}

static void PandE(GtkWidget *widget,GtkWidget *window ){
        printf("PE\n");
        gtk_exit(0);}
        
extern char openInp(char *);            // open html file
extern char *readInpLn();               // read a line
                
static void Email(GtkWidget *w, gpointer data){
        char *inp; int i;
        FILE *email=popen("esmtp -f senderEmail -- destEmail","w");
if(email){
        fprintf(email,"From: senderEmail\r\n");
        fprintf(email,"To: destEmail\r\n");
        fprintf(email,"Subject: URGENT\r\n");
        fprintf(email,"\r\n");
        //fprintf(email,"Ring office urgently\r\n");
        i=1; while(i){
                inp=readInpLn();
                i=strcmp(inp,"?*?*?*?*");
                if(i){fprintf(email,"%s",inp); fprintf(email,"\r\n");}
                }
        pclose(email);
}else printf("popen failure");
        }

int main(int argc, char *argv[]){
        gtk_init(&argc,&argv);

        openInp("x.html");

        screen=gtk_window_new(GTK_WINDOW_TOPLEVEL);
        gtk_signal_connect(GTK_OBJECT(screen),"destroy",GTK_SIGNAL_FUNC(PandE),NULL);
        gtk_window_set_title(GTK_WINDOW(screen),"Screen");
                                                              
 gtk_window_set_title(GTK_WINDOW(screen),"Screen");
        bttn=gtk_button_new_with_label("Email");
        gtk_signal_connect(GTK_OBJECT(bttn),"clicked",GTK_SIGNAL_FUNC(Email),NULL);
        gtk_container_add(GTK_CONTAINER(screen),bttn);
        gtk_widget_show_all(screen);

        gtk_main();
        return 0;
        }

---

### Post by Some Penguin on 2010-07-01
Look for a library that handles sending multipart MIME messages.

---

### Post by bcz on 2010-07-02
Thanks for idea penguin

Have tried makemime to format data and send it using my little testbed. All worked, but mail clients unable to handle it.  Have simplified to send alternative plain text and html data

Message is recieved OK over the web, but both thunderbird and Sylpheed mail clients display the makemime message "Email software does not support MIME-formatted messages" .  Cant check with outlook as I dont run windows

xf.txt contains "plain text"

xf.html

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtm11-transitional.dtd">
<html>
<head>
<title>Test Email</title>
</head>
<body>
HTML test
</body>
</html>

jcl

makemime -c "text/plain; charset=iso-8859-1" -o t1.txt xf.txt
makemime -c "text/html; charset=iso-8859-1" -o t1.html xf.html

makemime -m "multipart/alternative" -a "Content-Disposition: inline" -o t1.ma1 t1.txt
makemime -j t1.ma1 -o t1.ma2 t1.html

makemime -m "multipart/mixed" -a "Mime-Version: 1.0" -o logo.mm  t1.ma2

It look like this is going off topic, so I will open another thread, and post any final resolution back here

---

