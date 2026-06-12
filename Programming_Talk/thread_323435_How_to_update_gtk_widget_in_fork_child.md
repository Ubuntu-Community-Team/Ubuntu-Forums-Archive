---
title: "How to update gtk widget in fork child?"
date: 2006-12-22
forum: Programming Talk
---

### Post by ckh on 2006-12-22
Anybody knows how to update UI (gtk widget) in a fork child?

here is my code,
but it does not work.
The child will not update the lable of button.
```

#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <gtk/gtk.h>

GtkWidget *button;

void destroy(GtkWidget *widget, gpointer data)
{
    gtk_main_quit();
}

void fork_me(GtkWidget *widget, gpointer data)
{
	pid_t pid;

    pid = fork();

    if(pid == -1)
    {
        /* ouch, fork() failed */
        perror("fork");
        exit(-1);
    }
    else if(pid == 0)
    {
        /* child */
        gchar str[10];
        int i=0;
        fprintf(stderr, "Child: pid = %d\n", (int)getpid());

        strcpy(str,  gtk_button_get_label(button));
        printf("%s\n",str);
        sscanf(str,"%d", &i);
        i++;
        printf("%d\n",i);
        sprintf(str,"%d",i);
        gtk_button_set_label(button, str);   //does not work!!!
      
        _exit(-1);
    }
    else
    {
        /* parent */
        fprintf(stderr, "Parent: forked a child with pid = %d\n", (int)pid);
    }
}

int main(int argc, char *argv[])
{
    GtkWidget *window;

    gtk_init(&argc, &argv);
   
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_signal_connect(GTK_OBJECT (window), "destroy",
                       GTK_SIGNAL_FUNC(destroy), NULL);

  gtk_container_set_border_width(GTK_CONTAINER (window), 10);

  /* add a button to do something usefull */
  button = gtk_button_new_with_label("0");
          
  gtk_signal_connect(GTK_OBJECT (button), "clicked",
                     GTK_SIGNAL_FUNC(fork_me), NULL);

  gtk_container_add(GTK_CONTAINER(window), button);
          
  /* show everything */
  gtk_widget_show (button);
  gtk_widget_show (window);

  
  /* main loop */
  gtk_main ();
  exit(0);           

}


```

---

### Post by zgornel on 2006-12-22
Hey ... solved the thingie...
The problem was that child and parent processes are independent unelss pipes are used (modifications in the child are not reflected in the parent). I created a pipe through which the child modifies *str* and sends it to the parent (the gtk app) which updates the button label. 
Another solution to the problem is to use threads (more ellegant I'd immagine). 

Good luck.

PS. I dunno what compilation parameters you used, i used, ```
gcc -Wall ./testgtk.c `pkg-config --cflags --libs gtk+-2.0`
```

---

### Post by lnostdal on 2006-12-22
> **ckh said:**
> Anybody knows how to update UI (gtk widget) in a fork child?

Do not use fork; you get copy-on-write when you really want shared memory between the threads.

Use pthreads instead: man 3 pthread_create. Remember to link with pthread: -lpthread .. or you'll get random SIGSEGV's!

---

### Post by ckh on 2006-12-26
Helllo zgornel,

Thank you very much,
your code do update gtk widget correctly.

however I need to update UI several times,
actually I need to update a progress bar while child process do something.
maybe update the bar from 0% to 100%.

but in the code I was only able to update UI once,
How should I do?

I added a prograss bar in the code
here is the code:
```

#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <gtk/gtk.h>

GtkWidget *button;
GtkWidget *progressbar;
double fraction=0.0;

void destroy(GtkWidget *widget, gpointer data)
{
    gtk_main_quit();
}

void fork_me(GtkWidget *widget, gpointer data)
{
	/*Pipe Section */
	int pipe1[2]; 				//pointer to filedescriptor for pipe
	int pipe_stat;
	pipe_stat = pipe(pipe1);		//creation of pipe
	/* The pipe1[0] is used for reading - parent from child AND child from parent
	   pipe1[1] is used for writing */ 	

	
	pid_t pid;
	pid = fork();

    if(pid == -1)
    {
        /* ouch, fork() failed */
        perror("fork");
        exit(-1);
    }
    else if(pid == 0)
    {
        /* child */
        double fr=0.0;
        int i=0;
        fprintf(stderr, "Child: pid = %d\n", (int)getpid());

        fr = gtk_progress_bar_get_fraction(progressbar);
        printf("%.02f\n",fr);
        for(i=0;i<5;i++)  //use for loop try to update UI  for several times
        {
        sleep(0.5);
        fr +=0.01;
        printf("%.02f\n",fr);
        write(pipe1[1], &fr, sizeof(fr)); //child sends data to parent
        }
	close(pipe1[0]); //child does not read
	
        //gtk_button_set_label(button, str);   //does not work!!!
	printf("Exiting child ...\n");
        _exit(-1);
    }
    else
    {
        /* parent */
        double fr = 0.0;
        char  str[10];
	close(pipe1[1]); //parent does not write;
	read(pipe1[0], &fr, sizeof(fr)); //parent reads data from child (str)
        sprintf(str,"%.0f%%", fr*100.0);
        printf("percent= %s\n", str);
	
        gtk_progress_bar_set_fraction(progressbar, fr);
        gtk_progress_bar_set_text(progressbar, str);
        fprintf(stderr, "Parent: forked a child with pid = %d\n", (int)pid);		
		
    }
}

int main(int argc, char *argv[])
{   

    GtkWidget *window;
    GtkWidget *vbox1;

    gtk_init(&argc, &argv);
   
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_signal_connect(GTK_OBJECT (window), "destroy",
                       GTK_SIGNAL_FUNC(destroy), NULL);

  gtk_container_set_border_width(GTK_CONTAINER (window), 10);

  /* add a button to do something usefull */
  vbox1 = gtk_vbox_new( 0, 2);
  button = gtk_button_new_with_label("0");
  progressbar = gtk_progress_bar_new();
          
  gtk_signal_connect(GTK_OBJECT (button), "clicked",
                     GTK_SIGNAL_FUNC(fork_me), NULL);

  gtk_container_add(GTK_CONTAINER(window), vbox1); 
  gtk_container_add(GTK_CONTAINER(vbox1), progressbar); 
  gtk_container_add(GTK_CONTAINER(vbox1), button);
          
  /* show everything */
  gtk_widget_show_all(window);
  /* main loop */
  gtk_main ();
  exit(0);           

}


```

---

### Post by ckh on 2006-12-26
Hello lnostdal,
thanks for your comment,
I just did a gthread version,
but in UI seems still update once in my code,
could you or anybody please kindly give me some help?

I build the source code with:
```

gcc gtk_thread_progressbar.c -o gtk_thread_progressbar `pkg-config --cflags --libs gtk+-2.0 gthread-2.0`

```

---

### Post by lnostdal on 2006-12-26
> **ckh said:**
> Hello lnostdal,
thanks for your comment,
I just did a gthread version,
but in UI seems still update once in my code,
could you or anybody please kindly give me some help?

I build the source code with:
```

gcc gtk_thread_progressbar.c -o gtk_thread_progressbar `pkg-config --cflags --libs gtk+-2.0 gthread-2.0`

```


always compile with -Wall and -g .. this gives you more info and the possibility to use GDB to debug your software..

i've done some changes:

```

lars@ibmr52:~/programming/c$ cat gtk_thread_progressbar.c
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <gtk/gtk.h>

GtkWidget *button;
GtkWidget *progressbar;
double fraction=0.0;
pthread_t a_thread;


void destroy(GtkWidget *widget, gpointer data)
{
    gtk_main_quit();
}

void* threadfunc(void* arg)
{
    double fr=0.0;
    int i=0;
    char str[10];
    fr = gtk_progress_bar_get_fraction((GtkProgressBar*) progressbar);
    for(i=0;i<5;i++)
    {
        fr +=0.01;
        if(fr >1.0)
            fr = 1.0;
        gtk_progress_bar_set_fraction((GtkProgressBar*) progressbar, fr);
        sprintf(str,"%.0f%%",fr*100.0);
        gtk_progress_bar_set_text ((GtkProgressBar*) progressbar, str);
        sleep(0.3);
    }
    pthread_exit("threadfunc exit..");
}

void buttonclicked(GtkWidget *widget, gpointer data)
{
    int res;
    void *thread_result;
    res = pthread_create(&a_thread, NULL, threadfunc, NULL);
    if (res != 0)
    {
        perror("thread creation failed");
        exit(-1);
    }
    res = pthread_join(a_thread, &thread_result);
    if (res != 0)
    {
        perror("thread join failed");
        exit(-1);        
    }
    printf("thread joined and returned with %s\n", (char*)thread_result);
    return;
}

int main(int argc, char *argv[])
{   

    GtkWidget *window;
    GtkWidget *vbox1;

    g_thread_init(NULL);
    gtk_init(&argc, &argv);
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_signal_connect(GTK_OBJECT (window), "destroy",
                       GTK_SIGNAL_FUNC(destroy), NULL);

  gtk_container_set_border_width(GTK_CONTAINER (window), 10);

  /* add a button to do something usefull */
  vbox1 = gtk_vbox_new( 0, 2);
  button = gtk_button_new_with_label("0");
  progressbar = gtk_progress_bar_new();
          
  gtk_signal_connect(GTK_OBJECT (button), "clicked",
                     GTK_SIGNAL_FUNC(buttonclicked), NULL);

  gtk_container_add(GTK_CONTAINER(window), vbox1); 
  gtk_container_add(GTK_CONTAINER(vbox1), progressbar); 
  gtk_container_add(GTK_CONTAINER(vbox1), button);
          
  /* show everything */
  gtk_widget_show_all(window);
  /* main loop */
  gdk_threads_enter();
  gtk_main ();
  gdk_threads_leave();  
  exit(0);           

}
lars@ibmr52:~/programming/c$ gcc -Wall -g gtk_thread_progressbar.c -o gtk_thread_progressbar `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lpthread && ./gtk_thread_progressbar 

```

..now; when i click the button the progressbar increases by 5% each time .. is this what you want to see?

---

### Post by ckh on 2006-12-26
Hello lnostdal,

Thanks you for quickly responding.
No, this is not what I want,
I want the progressbar increase step by step everytime I do gtk_progress_bar_set_fraction() in the thread,
so it should be 1,2,3,4,5%, but it shows 0% - 5%.
Do you known what I mean?

thanks in advanced!
-ckh

---

### Post by lnostdal on 2006-12-26
> **ckh said:**
> 
Do you known what I mean?

maybe .. like this?

```

lars@ibmr52:~/programming/c$ cat gtk_thread_progressbar.c
#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
#include <gtk/gtk.h>

GtkWidget* button;
GtkWidget* progressbar;
double fraction=0.0;
pthread_t a_thread;
pthread_mutex_t mutex;



void destroy(GtkWidget* widget, gpointer data){
  gtk_main_quit();
}



void* threadfunc(void* arg){
  pthread_mutex_lock(&mutex);
  printf("threadfunc: new thread got mutex and has started execution..\n");
  double fr=0.0;
  int i=0;
  char str[10];
  gdk_threads_enter(); fr = gtk_progress_bar_get_fraction((GtkProgressBar*) progressbar); gdk_threads_leave();
  for(i=0; i < 5; i++){
    fr +=0.01;
    if(fr > 1.0)
      fr = 1.0;
    gdk_threads_enter();
    gtk_progress_bar_set_fraction((GtkProgressBar*) progressbar, fr);
    sprintf(str, "%.0f%%", fr * 100.0);
    gtk_progress_bar_set_text ((GtkProgressBar*) progressbar, str);
    gdk_threads_leave();
    usleep(500000);
  }

  pthread_mutex_unlock(&mutex);
  return NULL;
}



void buttonclicked(GtkWidget* widget, gpointer data){
  int res;
  printf("buttonclicked: creating new thread ..\n");
  res = pthread_create(&a_thread, NULL, threadfunc, NULL);
  if(res != 0){
    perror("thread creation failed");
    exit(-1);
  }
}



int main(int argc, char* argv[]){   
  g_thread_init(NULL);
  gdk_threads_init();
  gtk_init(&argc, &argv);
  
  pthread_mutex_init(&mutex, NULL);
  
  GtkWidget* window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_signal_connect(GTK_OBJECT (window), "destroy",
                     GTK_SIGNAL_FUNC(destroy), NULL);
  
  gtk_container_set_border_width(GTK_CONTAINER (window), 10);

  /* add a button to do something usefull */
  GtkWidget* vbox1 = gtk_vbox_new( 0, 2);
  button = gtk_button_new_with_label("0");
  progressbar = gtk_progress_bar_new();
          
  gtk_signal_connect(GTK_OBJECT (button), "clicked",
                     GTK_SIGNAL_FUNC(buttonclicked), NULL);

  gtk_container_add(GTK_CONTAINER(window), vbox1); 
  gtk_container_add(GTK_CONTAINER(vbox1), progressbar); 
  gtk_container_add(GTK_CONTAINER(vbox1), button);
          
  /* show everything */
  gtk_widget_show_all(window);
  
  /* main loop */
  gdk_threads_enter();
  gtk_main ();
  gdk_threads_leave();
  return 0;
}
lars@ibmr52:~/programming/c$ gcc -Wall -g gtk_thread_progressbar.c -o gtk_thread_progressbar `pkg-config --cflags --libs gtk+-2.0 gthread-2.0` -lpthread && ./gtk_thread_progressbar 


```

---

### Post by ckh on 2006-12-27
Hi lnostdal,

Yes!  this is exactly what I want.:D 
thank you very much.

the other question is,
you did not join the thread,
if I click the button several times and then close program immediately,
would it cause memory problem?

Thanks again!

-ckh

---

### Post by lnostdal on 2006-12-27
> **ckh said:**
> 
the other question is,
you did not join the thread,


The reason for this is because the main thread must not wait (block) for the created thread(s) because it needs to get back into its main loop (code "in" gtk_main (initial or main thread) is what's calling your handler-function for the "clicked"-event of the button) to handle redrawing of the interface etc as soon as possible. 

If you in some context need to be sure all threads are done you need to store them in a list upon creation then call join on each of them.

> **ckh said:**
> if I click the button several times and then close program immediately,
would it cause memory problem?

Not at all - your program is a process that is isolated from all other processes in the system; it cannot hurt the other ones in this context. ( [http://en.wikipedia.org/wiki/Protected_Mode](http://en.wikipedia.org/wiki/Protected_Mode) )

If you try clicking the button multiple times before the last previous "click/thread is done" you'll just queue up multiple threads waiting/blocking for exclusive access as governed by the variable `mutex' -- and they'll run one after each other in "serial". If you want you could have each thread working in parallel instead; but this will require some redesign of course. :)

---

### Post by ckh on 2006-12-27
thank you lnostdal,
you really did a big help to me. :D

-ckh

---

