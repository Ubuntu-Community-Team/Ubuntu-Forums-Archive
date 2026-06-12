---
title: "GTK Pthread Problem"
date: 2008-10-30
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-10-30
This is my program, I can't understand :
        When the pthread_kill is called, the program exits and sleep(10) doesn't works !!!
Any one can help me ?
Thanks a lot

#include <gtk/gtk.h>
#include <string>
#include <pthread.h>
#include <signal.h>

using namespace std;

class IUTClient {
private:
	string msg;
	GtkWidget *window,*label,*eventbox;
	GdkColor color;
	void *close_f;

public :
	IUTClient(){
		gdk_color_parse("#3081ff",&color);
		window=gtk_window_new(GTK_WINDOW_POPUP);
		eventbox = gtk_event_box_new(); 
		label=gtk_label_new("");
		gtk_event_box_set_above_child(GTK_EVENT_BOX(eventbox), FALSE); 
		g_signal_connect_swapped(G_OBJECT (eventbox), "button_press_event",G_CALLBACK(gtk_widget_hide_all),(gpointer)window);  
		gtk_container_add(GTK_CONTAINER(eventbox),label);
		gtk_widget_modify_bg(eventbox,GTK_STATE_NORMAL,&color);
		gtk_container_add(GTK_CONTAINER(window),eventbox);
	}
	void setText(string msg){
		IUTClient::msg="<span color=\"white\">";
		IUTClient::msg+=msg.c_str();
		IUTClient::msg+="</span>";
		gtk_label_set_markup(GTK_LABEL(label),IUTClient::msg.c_str());
	}
	void close(GtkWidget *window=0,GdkEvent *e=NULL,gpointer data=NULL){
		gtk_widget_destroy(window);
		gtk_main_quit();
	}
	void show(){
		gtk_widget_set_size_request(window,800,-1);
		gtk_widget_show_all(window);
		int default_width,width_screen=gdk_screen_get_width(gdk_screen_get_default());
		default_width=window->allocation.width;
		gtk_window_move(GTK_WINDOW(window),(width_screen/2)-(default_width/2),0);
		gtk_main();
	}
};

void* ThreadFunc(void* str)
{
	IUTClient A;	
	char *s=(char*)str;
	A.setText(s);
	A.show();
}

int main(int argc,char * argv[]){
	gtk_init(&argc,&argv);
	pthread_t thread1;
	char* s="Hi";
	int retval=pthread_create(&thread1,NULL,ThreadFunc,(void*)s);
	sleep(1);
	//pthread_cancel(thread1);
	//pthread_exit((void*)thread1);
	pthread_kill(thread1,SIGKILL);
	sleep(10);
	return 0;
}

---

### Post by uljanow on 2008-10-30
Signal actions are performed for the current process as a whole. Use pthread_cancel() instead.

---

