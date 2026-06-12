---
title: "Made a C alarm program, wanting some feedback on it"
date: 2009-01-19
forum: Programming Talk
---

### Post by PmDematagoda on 2009-01-19
I just finished making a C program that works as a rudimentary(emphasis on "rudimentary";)) alarm clock, you start the alarm process by specifying the amount of time that should be elapsed before sounding the alarm, it also has a GTK UI that allows the user to easily end the process without having to do a kill. The code is given below:-
```
#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
#include<string.h>
#include<time.h>
#include<gtk/gtk.h>
#include<sys/types.h>
#include<signal.h>

/* We need this global variable to hold the child's PID 
 * so that it can be accessed by the stop_app() procedure.
 */
[COLOR="Red"]pid_t child;[/COLOR]

void alarm_daemon(){
  int hour, minute;
  long int curr_time,end_time;

  printf("Enter the amount of time to be elapsed to start the alarm in HH:MM:- ");
  scanf("%d:%d",&hour,&minute);

  end_time = hour * 60 * 60;
  end_time += minute * 60;
  end_time += (long int) time(NULL);

  for(;;){
    curr_time = (long int) time(NULL);

    if(curr_time >= end_time)  break;
    
    sleep(900);
  }
}

void alarm_bell(){
  for(;;){
    if(system("echo \"Yo\"")){
      printf("Fix your system dawg!");
      break;
    }
    sleep(1);
  }
}

void stop_app(){
  kill(child,SIGKILL);
  gtk_main_quit();
}

gboolean delete_event_handler(GtkWidget *widget, GdkEvent *event,
			      gpointer user_data)
{
  return (FALSE);
}


void gtk_front(int argc, char *argv[]){
 GtkWidget *gtk_test, *vbox, *sleepy_label, *stop_button, *separator;
  gtk_init(&argc,&argv);
  gtk_test = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  vbox = gtk_vbox_new(TRUE,10);
  sleepy_label = gtk_label_new("Got up yet?");
  stop_button = gtk_button_new_with_label("Yes");
  separator = gtk_hseparator_new();

  gtk_window_set_title(GTK_WINDOW(gtk_test),"Alaaarm!");

  gtk_container_set_border_width(GTK_CONTAINER(gtk_test),50);

  gtk_window_set_policy(GTK_WINDOW(gtk_test),FALSE,FALSE,FALSE);

  gtk_signal_connect(GTK_OBJECT(stop_button),"clicked",stop_app,NULL);
  gtk_signal_connect(GTK_OBJECT(gtk_test),"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  gtk_signal_connect(GTK_OBJECT(gtk_test),"destroy",GTK_SIGNAL_FUNC(stop_app),NULL);

  gtk_container_add(GTK_CONTAINER(gtk_test),vbox);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),sleepy_label);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),separator);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),stop_button);

  gtk_widget_show_all(gtk_test);
  gtk_main();
  return;
}

int main(int argc,char *argv[]){
  alarm_daemon();

  /* We fork the process so that such a situation occurs:-
   * One process is the inifinite loop process that keeps doing a certain action
   * again and again, sort of like a real world alarm clock(Child).
   * 
   * The other process is the GUI to the alarm clock and allows the user to
   * terminate the entire alarm by pressing the "OK" button(Parent).
   */
[COLOR="Red"]  child = fork();[/COLOR]

  // The child process is delegated the alarm_bell().
[COLOR="Red"]  if (!child) alarm_bell();[/COLOR]
  // The parent process is given the GUI task.
[COLOR="Red"]  else if (child) gtk_front(argc,argv);[/COLOR]

  // Once the user presses the "OK" button, we start a sequence of events, each spaced by a 1 second interval and then end the process.
  sleep(1);
  system("echo \"what\"");
  sleep(1);
  system("echo \"Yo\"");
  sleep(1);
  system("echo \"Hello\"");
  sleep(1);

  return 0;
}
```

My own concerns are marked in red. Any feedback, criticism or suggestions to the code are more than welcome(which is why I posted it in the first place):).

---

### Post by loganwm on 2009-01-19
That's pretty neat.

How well does GTK work with C, I rarely find any source code that uses C with GTK as opposed to C++?

---

### Post by PmDematagoda on 2009-01-19
> **loganwm said:**
> That's pretty neat.

How well does GTK work with C, I rarely find any source code that uses C with GTK as opposed to C++?

Well, considering that GTK+ was originally derived from C, I would imagine that people do use GTK+ with C, although I can agree with you when you say that most people prefer to use C++ and Python, I would think that people on the GNOME project would most usually prefer to use C with GTK+ than C++ with GTK+:).

Edit:- To answer your question a bit more directly, GTK+ should work very well with C, probably more so than with any other languages.

---

### Post by loganwm on 2009-01-19
> **PmDematagoda said:**
> Well, considering that GTK+ was originally derived from C, I would imagine that people do use GTK+ with C, although I can agree with you when you say that most people prefer to use C++ and Python, I would think that people on the GNOME project would most usually prefer to use C with GTK+ than C++ with GTK+:).

Edit:- To answer your question a bit more directly, GTK+ should work very well with C, probably more so than with any other languages.

Once I get some more work done on my Music Player I might write up a small optional interface with GTK.  Check out the latest Code courtesy of 2AM programming. :)

---

### Post by PmDematagoda on 2009-01-19
> **loganwm said:**
> Once I get some more work done on my Music Player I might write up a small optional interface with GTK.  Check out the latest Code courtesy of 2AM programming. :)

I just saw it, it's pretty cool the way you use the ncurses interface to get the keyboard hits. Looks like a very nice program:).

---

### Post by PmDematagoda on 2009-01-19
Come on, anyone? I wouldn't mind even if the criticism or problem was with a way I used a variable, just any feedback on this would be nice:).

Even questions I don't mind.

---

### Post by slavik on 2009-01-19
the way you use a global var makes sense. what doesn't make sense is what happens if you can't fork ;)

as for general program design ... I have to say that it's crap. there is something called alarm() which would tell the system to send an interupt to your program once the timer expires. :)

---

### Post by SeanHodges on 2009-01-20
> **slavik said:**
> the way you use a global var makes sense. what doesn't make sense is what happens if you can't fork ;)

Makes sense to me, if the program can't fork, alarm bells should be ringing :)

> **slavik said:**
> as for general program design ... I have to say that it's crap. there is something called alarm() which would tell the system to send an interupt to your program once the timer expires. :)

I wouldn't go as far as to say the design was crap. Perhaps the OP was deliberately avoiding alarm() for learning purposes? But your point is correct, using alarm() to pass an interrupt would be neater than using fork().

---

### Post by PmDematagoda on 2009-01-20
> **SeanHodges said:**
> Makes sense to me, if the program can't fork, alarm bells should be ringing :)



I wouldn't go as far as to say the design was crap. Perhaps the OP was deliberately avoiding alarm() for learning purposes? But your point is correct, using alarm() to pass an interrupt would be neater than using fork().

Lol, to be honest, I am learning, however the main reason I didn't use alarm() in the first place was because I had no idea that it existed, hence the fork() and an attempt at reinventing the wheel.

Thanks for the point out slavik, I'll take a look at alarm() now:).

---

### Post by PmDematagoda on 2009-01-20
> **slavik said:**
> the way you use a global var makes sense. what doesn't make sense is what happens if you can't fork ;)

as for general program design ... I have to say that it's crap. there is something called alarm() which would tell the system to send an interupt to your program once the timer expires. :)

About the fork, according to my design, there are 2 parts, the CLI which keeps cycling infinitely to wake the user, and the GUI which allows the user to control the program without having to resort to a kill. So since I cannot(don't know is more like it:)) keep a command cycling once we initialise the GTK UI, I had to fork the process and the child one thing and the parent the other.

And about alarm(), am I to understand that I can use sigaction() to do something(like start the alarm) once we receive the SIGALRM signal? If so, should I use a while do loop until alarm() reaches 0? Or should I use something else?

---

### Post by Paul Miller on 2009-01-20
Well, I have no actual comments on the code itself, just a question: why did you choose to write such an app in C?  I mean, by design, all it does 99.9% of the time is sit and wait.  

What I'm trying to say is it's not exactly a performance-critical bit of code.  Unless you were doing this to learn something about C and/or using GTK from C, I'd suggest redoing it in Python.   (Or, even if you were doing it to learn C, do it again in Python ... or Ruby ... or Scheme ... or Perl, etc.)

---

### Post by SeanHodges on 2009-01-20
> **Paul Miller said:**
> why did you choose to write such an app in C?  I mean, by design, all it does 99.9% of the time is sit and wait.  

What I'm trying to say is it's not exactly a performance-critical bit of code.  Unless you were doing this to learn something about C and/or using GTK from C, I'd suggest redoing it in Python.   (Or, even if you were doing it to learn C, do it again in Python ... or Ruby ... or Scheme ... or Perl, etc.)

Careful, thar lie dragons! :)

You aren't limited to performance-critical programming in C, it's perfectly capable of producing an alarm-style program (one example is the popular "cron" service). 

Whilst Python/Ruby/Scheme/[insert language here] are all great; but you have to be careful not to take your eye off the ball, and focus on writing a single working solution before attempting it in a multitude of other languages.

---

### Post by slavik on 2009-01-20
the way that alarm works, is: you setup a signal handler for SIGALARM, you call alarm() and that's it ... inside alarm() (this is a system call, btw):

1. a timer is set up
2. the process is put to sleep
3. process is sent a SIGALARM once the timer expires
4. the signal handler that you registered for SIGALARM is called.
5. at the end of your handler, you return to just after the alarm() call. :)

also, can you re-iterate what the GUI does? I am sure that GTK has some similar action to alarm, where you can tell it to call some function after certain time (I remember doing this with GTK# when I was trying out monodevelop).

---

### Post by LinuxGuy1234 on 2009-01-20
> **PmDematagoda said:**
> I just finished making a C program that works as a rudimentary(emphasis on "rudimentary";)) alarm clock, you start the alarm process by specifying the amount of time that should be elapsed before sounding the alarm, it also has a GTK UI that allows the user to easily end the process without having to do a kill. The code is given below:-
```
#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
#include<string.h>
#include<time.h>
#include<gtk/gtk.h>
#include<sys/types.h>
#include<signal.h>

/* We need this global variable to hold the child's PID 
 * so that it can be accessed by the stop_app() procedure.
 */
[COLOR="Red"]pid_t child;[/COLOR]

void alarm_daemon(){
  int hour, minute;
  long int curr_time,end_time;

  printf("Enter the amount of time to be elapsed to start the alarm in HH:MM:- ");
  scanf("%d:%d",&hour,&minute);

  end_time = hour * 60 * 60;
  end_time += minute * 60;
  end_time += (long int) time(NULL);

  for(;;){
    curr_time = (long int) time(NULL);

    if(curr_time >= end_time)  break;
    
    sleep(900);
  }
}

void alarm_bell(){
  for(;;){
    if(system("echo \"Yo\"")){
      printf("Fix your system dawg!");
      break;
    }
    sleep(1);
  }
}

void stop_app(){
  kill(child,SIGKILL);
  gtk_main_quit();
}

gboolean delete_event_handler(GtkWidget *widget, GdkEvent *event,
			      gpointer user_data)
{
  return (FALSE);
}


void gtk_front(int argc, char *argv[]){
 GtkWidget *gtk_test, *vbox, *sleepy_label, *stop_button, *separator;
  gtk_init(&argc,&argv);
  gtk_test = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  vbox = gtk_vbox_new(TRUE,10);
  sleepy_label = gtk_label_new("Got up yet?");
  stop_button = gtk_button_new_with_label("Yes");
  separator = gtk_hseparator_new();

  gtk_window_set_title(GTK_WINDOW(gtk_test),"Alaaarm!");

  gtk_container_set_border_width(GTK_CONTAINER(gtk_test),50);

  gtk_window_set_policy(GTK_WINDOW(gtk_test),FALSE,FALSE,FALSE);

  gtk_signal_connect(GTK_OBJECT(stop_button),"clicked",stop_app,NULL);
  gtk_signal_connect(GTK_OBJECT(gtk_test),"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  gtk_signal_connect(GTK_OBJECT(gtk_test),"destroy",GTK_SIGNAL_FUNC(stop_app),NULL);

  gtk_container_add(GTK_CONTAINER(gtk_test),vbox);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),sleepy_label);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),separator);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),stop_button);

  gtk_widget_show_all(gtk_test);
  gtk_main();
  return;
}

int main(int argc,char *argv[]){
  alarm_daemon();

  /* We fork the process so that such a situation occurs:-
   * One process is the inifinite loop process that keeps doing a certain action
   * again and again, sort of like a real world alarm clock(Child).
   * 
   * The other process is the GUI to the alarm clock and allows the user to
   * terminate the entire alarm by pressing the "OK" button(Parent).
   */
[COLOR="Red"]  child = fork();[/COLOR]

  // The child process is delegated the alarm_bell().
[COLOR="Red"]  if (!child) alarm_bell();[/COLOR]
  // The parent process is given the GUI task.
[COLOR="Red"]  else if (child) gtk_front(argc,argv);[/COLOR]

  // Once the user presses the "OK" button, we start a sequence of events, each spaced by a 1 second interval and then end the process.
  sleep(1);
  system("echo \"what\"");
  sleep(1);
  system("echo \"Yo\"");
  sleep(1);
  system("echo \"Hello\"");
  sleep(1);

  return 0;
}
```

My own concerns are marked in red. Any feedback, criticism or suggestions to the code are more than welcome(which is why I posted it in the first place):).

Good. But I would recommend the inputting and interactive stuff to be driven by GTK. This removes the dependency on having a terminal open.

---

### Post by PmDematagoda on 2009-01-21
> **slavik said:**
> the way that alarm works, is: you setup a signal handler for SIGALARM, you call alarm() and that's it ... inside alarm() (this is a system call, btw):

1. a timer is set up
2. the process is put to sleep
3. process is sent a SIGALARM once the timer expires
4. the signal handler that you registered for SIGALARM is called.
5. at the end of your handler, you return to just after the alarm() call. :)

also, can you re-iterate what the GUI does? I am sure that GTK has some similar action to alarm, where you can tell it to call some function after certain time (I remember doing this with GTK# when I was trying out monodevelop).

Slavik, this more than just a simple alarm to inform a user once the time is up, the alarm is also supposed to keep happening for an(technically) infinite amount of time, and I realise that I need to return once SIGALRM is sent since the program terminates anyway, that isn't how I planned it, this is a case where:-

1) An alarm keep occurring second by second, an alarm bell, this happens in the background.

2) A GUI is present to give the user an easy way of stopping the alarm. This is because the alarm bell is kept in an infinite for() loop.

Perhaps I should try playing with sigaction()?

---

### Post by PmDematagoda on 2009-01-21
> **LinuxGuy1234 said:**
> Good. But I would recommend the inputting and interactive stuff to be driven by GTK. This removes the dependency on having a terminal open.

That is what I would like to do as well, but my skill in GTK+ is only so much:). Perhaps you have some good documentation I can look at?

---

### Post by bruce89 on 2009-01-21
I can only comment on the GTK+ bit.

**stop_button = gtk_button_new_with_label("Yes");**

Perhaps *stop_button = gtk_button_new_from_stock(GTK_STOCK_YES);*

**gtk_window_set_policy(GTK_WINDOW(gtk_test),FALSE,FALSE,FALSE);**

Use *gtk_window_set_resizable(GTK_WINDOW(gtk_test), TRUE);*

**gtk_signal_connect(GTK_OBJECT(stop_button),"clicked",stop_app,NULL);**

Use *g_signal_connect* (same arguments but don't cast the first argument, as it is supposed to be a pointer).
  
**gtk_box_pack_start_defaults(GTK_BOX(vbox),sleepy_label);**

Use *gtk_box_pack_start*.

---

### Post by slavik on 2009-01-21
so, once the alarm starts ringing, it keeps on ringing until the user stops it?

---

### Post by PmDematagoda on 2009-01-21
> **slavik said:**
> so, once the alarm starts ringing, it keeps on ringing until the user stops it?

Yep, with the GTK+ UI allowing the user to easily stop the alarm.

---

### Post by PmDematagoda on 2009-01-21
On bruce89's suggestions, the GTK+ part has been changed, this is how the new code checks out:-
[PHP]#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
#include<time.h>
#include<gtk/gtk.h>
#include<sys/types.h>
#include<signal.h>

#define ALARM
/* We need this global variable to hold the child's PID 
 * so that it can be accessed by the stop_app() procedure.
 */
pid_t child;

void alarm_daemon(){
  int hour, minute;
  long int curr_time,end_time;
  //int end_time;

  printf("Enter the amount of time to be elapsed to start the alarm in HH:MM:- ");
  scanf("%d:%d",&hour,&minute);

  end_time = hour * 60 * 60;
  end_time += minute * 60;
#ifdef ALARM
  end_time += (long int) time(NULL);

  for(;;){
    curr_time = (long int) time(NULL);

    if(curr_time >= end_time)  break;
    
    sleep(15);
  }
  
#else
  alarm(end_time);
  //Incomplete sigaction(), need to get more experience here.
  sigaction(&return; NULL; SIGALRM;SA_NODEFER);
  pause();
#endif

}

void alarm_bell(){
  for(;;){
    if(system("echo \"Yo\"")){
      printf("Fix your system dawg!");
      break;
    }
    sleep(1);
  }
}

void stop_app(){
  kill(child,SIGKILL);
  gtk_main_quit();
}

gboolean delete_event_handler(GtkWidget *widget, GdkEvent *event,
			      gpointer user_data)
{
  return (FALSE);
}


void gtk_front(int argc, char *argv[]){
 GtkWidget *gtk_test, *vbox, *sleepy_label, *stop_button, *separator;
  gtk_init(&argc,&argv);
  gtk_test = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  vbox = gtk_vbox_new(TRUE,10);
  sleepy_label = gtk_label_new("Got up yet?");
  //stop_button = gtk_button_new_with_label("Yes");
  stop_button = gtk_button_new_from_stock(GTK_STOCK_YES);
  separator = gtk_hseparator_new();

  gtk_window_set_title(GTK_WINDOW(gtk_test),"Alaaarm!");

  gtk_container_set_border_width(GTK_CONTAINER(gtk_test),50);

  gtk_window_set_resizable(GTK_WINDOW(gtk_test),TRUE);

  //gtk_signal_connect(GTK_OBJECT(stop_button),"clicked",stop_app,NULL);
  g_signal_connect(stop_button,"clicked",stop_app,NULL);

  gtk_signal_connect(GTK_OBJECT(gtk_test),"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  gtk_signal_connect(GTK_OBJECT(gtk_test),"destroy",GTK_SIGNAL_FUNC(stop_app),NULL);

  gtk_container_add(GTK_CONTAINER(gtk_test),vbox);
  
  gtk_box_pack_start_defaults(GTK_BOX(vbox),sleepy_label);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),separator);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),stop_button);
  /* gtk_box_pack_start(GTK_BOX(vbox),sleepy_label); */
/*   gtk_box_pack_start(GTK_BOX(vbox),separator); */
/*   gtk_box_pack_start(GTK_BOX(vbox),stop_button); */

  gtk_widget_show_all(gtk_test);
  gtk_main();
}

int main(int argc,char *argv[]){
  alarm_daemon();

  /* We fork the process so that such a situation occurs:-
   * One process is the inifinite loop process that keeps doing a certain action
   * again and again, sort of like a real world alarm clock(Child).
   * 
   * The other process is the GUI to the alarm clock and allows the user to
   * terminate the entire alarm by pressing the "OK" button(Parent).
   */
  child = fork();

  // The child process is delegated the alarm_bell().
  if (!child) alarm_bell();
  // The parent process is given the GUI task.
  else if (child) gtk_front(argc,argv);

  // Once the user presses the "OK" button, we start a sequence of events, each spaced by a 1 second interval and then end the process.
  sleep(1);
  system("echo \"what\"");
  sleep(1);
  system("echo \"Yo\"");
  sleep(1);
  system("echo \"Hello\"");
  sleep(1);

  return 0;
}[/PHP]

As seen, I still have the old alarm_daemon() code as it seems that alarm() and pause() don't seem to work out to my requirements. Although alarm() and pause() are much better, if they can be used, than the current code.

---

### Post by PmDematagoda on 2009-02-01
I made a few updates:-

1) alarm() and pause() are now in use in order to pass the task of the alarm clock to the OS.

2) sigaction() is used to ensure that the application is not closed down on the receiving of SIGARLM.

3) Pipes are used to allow for IPC between the parent and child, so kill() is no longer needed and the child variable is now local to main(). However, the variable for the pipes must be global, and it creates some weird stuff I need to check out by reading the book I have on process IPC.

The new code:-
```
#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
#include<time.h>
#include<gtk/gtk.h>
#include<sys/types.h>
#include<signal.h>
#include<string.h>
#include<sys/wait.h>
#include<fcntl.h>
#include<errno.h>

/* The pipe is declared globally so as to be accessible by the stop_app() procedure.
 */
int main_pipe[2];

void alarm_bell(){
  char buffer[strlen("Stop")];
  int error_var;

  fcntl(main_pipe[0],F_SETFL, O_NONBLOCK);
  while(1){
    error_var = read(main_pipe[0],buffer,strlen("Stop"));
    if (error_var < 0){
      if(system("echo \"Yo\"")){
	printf("Fix your system!");
	break;
      }
      sleep(1);
    }
    else{
      break;
    }
  }
  exit(0); 
}

void stop_app(){
  write(main_pipe[1],"Stop",strlen("Stop"));
  wait(0);
  gtk_main_quit();
}

gboolean delete_event_handler(GtkWidget *widget, GdkEvent *event,
			      gpointer user_data)
{
  return (FALSE);
}


void gtk_front(int argc, char *argv[]){
  GtkWidget *gtk_test, *vbox, *sleepy_label, *stop_button, *separator;
  gtk_init(&argc,&argv);
  gtk_test = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  vbox = gtk_vbox_new(TRUE,10);
  sleepy_label = gtk_label_new("Got up yet?");
  stop_button = gtk_button_new_from_stock(GTK_STOCK_YES);
  separator = gtk_hseparator_new();

  gtk_window_set_title(GTK_WINDOW(gtk_test),"Alaaarm!");

  gtk_container_set_border_width(GTK_CONTAINER(gtk_test),50);

  gtk_window_set_resizable(GTK_WINDOW(gtk_test),TRUE);

  g_signal_connect(stop_button,"clicked",stop_app,NULL);

  g_signal_connect(gtk_test,"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  g_signal_connect(gtk_test,"destroy",GTK_SIGNAL_FUNC(stop_app),NULL);

  gtk_container_add(GTK_CONTAINER(gtk_test),vbox);
  
  gtk_box_pack_start_defaults(GTK_BOX(vbox),sleepy_label);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),separator);
  gtk_box_pack_start_defaults(GTK_BOX(vbox),stop_button);

  gtk_widget_show_all(gtk_test);
  gtk_main();
}


//This is present to just act as a dummy outlet.
void null_code(){
}

void alarm_daemon(){
  int hour, minute;
  long int end_time;
  struct sigaction alarm_handler;

  alarm_handler.sa_handler = null_code;
  sigemptyset(&alarm_handler.sa_mask);
  alarm_handler.sa_flags = 0;


  printf("Enter the amount of time to be elapsed to start the alarm in HH:MM:- ");
  scanf("%d:%d",&hour,&minute);

  end_time = hour * 60 * 60;
  end_time += minute * 60;

  alarm(end_time);
  sigaction(SIGALRM, &alarm_handler, NULL);

  if(end_time)
  pause();

}

int main(int argc,char *argv[]){
  pid_t child;

  alarm_daemon();

  pipe(main_pipe);

  /* We fork the process so that such a situation occurs:-
   * One process is the inifinite loop process that keeps doing a certain action
   * again and again, sort of like a real world alarm clock(Child).
   * 
   * The other process is the GUI to the alarm clock and allows the user to
   * terminate the entire alarm by pressing the "OK" button(Parent).
   */
  child = fork();

  // The child process is delegated the alarm_bell().
  if (!child){
    close(main_pipe[1]);
    alarm_bell();
    exit(0);
  }
  // The parent process is given the GUI task.
  else if (child){
    close(main_pipe[0]);
    gtk_front(argc,argv);
  }
  // Once the user presses the "OK" button, we start a sequence of events, each spaced by a 1 second interval and then end the process.
  sleep(1);
  system("echo \"what\"");
  sleep(1);
  system("echo \"Yo\"");
  sleep(1);
  system("echo \"Hello\"");
  sleep(1);

  return 0;
}
```

Thanks for the guys in this [thread]("http://ubuntuforums.org/showthread.php?t=1055542") for helping me out with the pipes.

As previously mentioned, any feedback is welcome:).

Edit:- There was a slight bug with the alarm, it has now been(hopefully) fixed.

---

### Post by shindz on 2009-02-02
Hi all, I've nothing to say about the program. I just want to know what can we do with an alarm??? I could have an idea to work with.
thank you

---

### Post by PmDematagoda on 2009-02-03
> **shindz said:**
> Hi all, I've nothing to say about the program. I just want to know what can we do with an alarm??? I could have an idea to work with.
thank you

Incidentally, there are some people who use their computers as alarm clocks, I made this program to see if I could achieve this with my skills in programming and to ask other people if what I did was correct. This program is in no way an official project of any sort, I did this because I wanted to learn certain parts of C and since IMO, practical experience tends to be better than just reading only theory.

You are more then welcome to give the alarm a try and see if it works ok, but please keep in mind that this program is being done by me purely for educational purposes. If you have any improvements(a program like what I made most definitely would have to have some;)), then I would be happy to see if I could try and implement them.

---

### Post by nvteighen on 2009-02-03
It's a bit weird, but I think it's a good job.

Maybe it'd be great to try to make it trigger a custom application.

---

### Post by PmDematagoda on 2009-02-05
> **nvteighen said:**
> It's a bit weird, but I think it's a good job.

Maybe it'd be great to try to make it trigger a custom application.

Lol, it is quite weird:D, but thanks:).

About the custom application, are you talking about prompting the user for what to run as the alarm?

---

### Post by PmDematagoda on 2009-02-12
Some updates:-

1) You now specify the hour and minute of the time in which the alarm is rung, but it still needs work.

2) You now have a GUI to enter the required alarm time into, still needs some thought as to the design.

Code:-
[PHP]#include<stdio.h>
#include<unistd.h>
#include<stdlib.h>
#include<time.h>
#include<gtk/gtk.h>
#include<sys/types.h>
#include<signal.h>
#include<string.h>
#include<sys/wait.h>
#include<fcntl.h>
#include<errno.h>
#include<ctype.h>

/* Compile with:-
 * gcc name-of-source.c -o name-of-executable `pkg-config --libs --cflags gtk+-2.0`
 */

/* The pipe is declared globally so as to be accessible by the stop_app() procedure.
 */
int main_pipe[2];

/* The variables below hold the amount of time in hours and minutes.*/
unsigned int total_elapse;
/* This structure now holds all the pointers to the widgets for both the windows:-
 * 1) The time entry window.
 * 2) The alarm notice window.
 */

/* Basically, I only need the input_box pointer to be global, so I do not really need this, but for easier to understand code, it is made this way.*/
struct properties{
  GtkWidget *input_box;
  GtkWidget *window;
  GtkWidget *label;
  GtkWidget *vbox;
  GtkWidget *stop_button;
  GtkWidget *separator;
  GtkWidget *h_box;
};
struct properties window;


void get_details(){
  const gchar *pointer = gtk_entry_get_text(GTK_ENTRY(window.input_box));
  int hour, minute;
  
  time_t time_sec,time_new_sec;
  struct tm *time_old,*time_new;

  time_sec = time(NULL);
  time_old = localtime(&time_sec);
  time_new = localtime(&time_sec);

  // TODO:- Improve the parsing of the time entered.


  hour = atoi(pointer);
  do{
  ++pointer;
  }while(isdigit(*pointer));
  ++pointer;
  minute = atoi(pointer);

  // TODO:- Be more smarter about what time the alarm must ring, perhaps a day field?
  if(hour < 24 && hour > 12)
  time_new->tm_mday++;
  time_new->tm_min = minute;
  time_new->tm_hour = hour;

  time_new_sec = mktime(time_new);

  total_elapse = -(unsigned int) difftime(time_sec,time_new_sec);
  printf("Total:-%d\n",total_elapse);

  // It may be a little more resource efficient to just destroy the window.
  gtk_widget_hide(window.window);
  gtk_main_quit();
}

void alarm_bell(){
  char buffer[strlen("Stop")];
  int error_var;

  fcntl(main_pipe[0],F_SETFL, O_NONBLOCK);
  while(1){
    error_var = read(main_pipe[0],buffer,strlen("Stop"));
    if (error_var < 0){
      if(system("echo \"Yo\"")){
	printf("Fix your system!");
	break;
      }
      sleep(1);
    }
    else{
      break;
    }
  }
  exit(0); 
}

void stop_app(){
  write(main_pipe[1],"Stop",strlen("Stop"));
  wait(0);
  gtk_main_quit();
  gtk_widget_hide(window.window);

}

void close_app(){
  exit(0);
}

gboolean delete_event_handler(GtkWidget *widget, GdkEvent *event,
			      gpointer user_data)
{
  return (FALSE);
}


void gtk_front(){

  window.window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  window.vbox = gtk_vbox_new(TRUE,10);
  window.label = gtk_label_new("Got up yet?");
  window.stop_button = gtk_button_new_from_stock(GTK_STOCK_YES);
  window.separator = gtk_hseparator_new();

  gtk_window_set_title(GTK_WINDOW(window.window),"Alaaarm!");

  gtk_container_set_border_width(GTK_CONTAINER(window.window),50);

  gtk_window_set_resizable(GTK_WINDOW(window.window),TRUE);

  gtk_window_set_position(GTK_WINDOW(window.window),GTK_WIN_POS_CENTER_ALWAYS);

  gtk_window_set_keep_above(GTK_WINDOW(window.window),TRUE);

  g_signal_connect(window.stop_button,"clicked",stop_app,NULL);

  g_signal_connect(window.window,"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  g_signal_connect(window.window,"destroy",GTK_SIGNAL_FUNC(stop_app),NULL);

  gtk_container_add(GTK_CONTAINER(window.window),window.vbox);
  
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.label);
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.separator);
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.stop_button);

  gtk_widget_show_all(window.window);
  gtk_main();
}


//This is present to just act as a dummy outlet.
void null_code(){
}

void alarm_daemon(){
  long int end_time;
  struct sigaction alarm_handler;

  alarm_handler.sa_handler = null_code;
  sigemptyset(&alarm_handler.sa_mask);
  alarm_handler.sa_flags = 0;

  alarm(total_elapse);
  sigaction(SIGALRM, &alarm_handler, NULL);

  if(end_time)
  pause();

}

void alarm_entry(){

  window.window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  window.stop_button = gtk_button_new_from_stock(GTK_STOCK_YES);
  window.input_box = gtk_entry_new();
  window.label = gtk_label_new("Enter the time at which the alarm should ring tomorrow(HH:MM)");
  window.vbox = gtk_vbox_new(TRUE,10);
  window.h_box = gtk_hbox_new(TRUE,10);

  gtk_window_set_title(GTK_WINDOW(window.window),"Alaarm!");
  g_signal_connect(window.stop_button,"clicked",GTK_SIGNAL_FUNC(get_details),NULL);

  g_signal_connect(window.window,"delete-event",GTK_SIGNAL_FUNC(delete_event_handler),NULL);
  g_signal_connect(window.window,"destroy",GTK_SIGNAL_FUNC(close_app),NULL);

  gtk_container_add(GTK_CONTAINER(window.window),window.vbox);
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.label);
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.input_box);
  gtk_box_pack_start_defaults(GTK_BOX(window.vbox),window.stop_button);

  gtk_widget_show_all(window.window);
  
  gtk_main();

}

int main(int argc,char *argv[]){
  pid_t child;

  /* The GTK environment is initialised first since there are two dialog boxes and since it is just faster. (Not much of an argument, 
   * I suppose I could start new GTK environments for both GUIs since they do not follow one another).*/
  gtk_init(&argc,&argv);

  alarm_entry();

  alarm_daemon();

  pipe(main_pipe);

  /* We fork the process so that such a situation occurs:-
   * One process is the inifinite loop process that keeps doing a certain action
   * again and again, sort of like a real world alarm clock(Child).
   * 
   * The other process is the GUI to the alarm clock and allows the user to
   * terminate the entire alarm by pressing the "OK" button(Parent).
   */
  child = fork();

  // The child process is delegated the alarm_bell().
  if (!child){
    close(main_pipe[1]);
    alarm_bell();
    exit(0);
  }
  // The parent process is given the GUI task.
  else if (child){
    close(main_pipe[0]);
    //gtk_init(&argc,&argv);
    gtk_front();
    sleep(1);
    system("echo \"what\"");
    sleep(1);
    system("echo \"Yo\"");
    sleep(1);
    system("echo \"Hello\"");
  }
  // Once the user presses the "OK" button, we start a sequence of events, each spaced by a 1 second interval and then end the process.


  return 0;
}[/PHP]

As always, comments and feedback of any kind are welcome. :)

P.S:- I realise the increasing size of the code, about 200+ lines, if anyone does not want to view the code in this way, I can tar it up. In any case, the next update(if any) will be tarred up.

---

### Post by PmDematagoda on 2009-02-13
Updates:- 

1) The GtkWidget pointer structure for the windows has been removed.

2) I have been messing with Glade, so I managed to create a better GUI.

3) The alarm notification window is now a popup window.

4) There are tons of mistakes(spelling, grammar, relevance, the lot;)), I need to fix them up.

Code is now attached.

And feedback or suggestions(as usual) is more than welcome. Even if your feedback is to comment on my useless design, I would really like to hear it:).

Also if someone could give me a nice guide to using Glade properly, I would really appreciate that:).

---

### Post by SeanHodges on 2009-02-16
> **PmDematagoda said:**
> And feedback or suggestions(as usual) is more than welcome. Even if your feedback is to comment on my useless design, I would really like to hear it:).

Looks good.

Regarding your time parser: The "at" program uses a collection of tokens to calculate the date and time, this concept might be completely overkill for your purposes, but there might be some ideas to take from it:

[http://www.google.com/codesearch/p?hl=en#kZ3AOq_GupA/src/usr.bin/at/parsetime.c](http://www.google.com/codesearch/p?hl=en#kZ3AOq_GupA/src/usr.bin/at/parsetime.c)

I believe part of that code was generated with YACC, hence it's complexity. I would suggest a simple enum approach would be sufficient for you :)

Also, as have been suggested by others, you could get your program to trigger another program/script when the alarm sounds. This would allow a user to customise the event as they see fit.

Something simple like exec() might do:

```
char *external_program = "mpg321 /home/user/alarm.mp3";
if (strlen(external_program) > 0) {
    exec(external_program);
}
```

> **PmDematagoda said:**
> Also if someone could give me a nice guide to using Glade properly, I would really appreciate that:).

Unfortunately, GTK/Glade documentation is fairly scarce in many areas, but a lot of the time you can find what you need through Google.

I would assume by Glade you are referring to the Glade-3 interface builder (apt://glade-3) and the libglade library. Glade uses an XML-based format that you can then pass into your code. Not everyone likes this approach, but I find it much more efficient for simple dialogs than typing out all the gtk_ commands for drawing the interface. Even if you choose not to use the output, this tool is useful as a sandbox for testing out what properties you can adjust, and how they affect the widgets.

A tutorial on it can be found here: [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html#Introduction_to_Glade3](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html#Introduction_to_Glade3)

In essence, you draw your interface using the interface designer tool, export the XML as a ".glade" file, and use libglade in your program to parse the XML and do all the work:

```
GtkBuilder *builder = gtk_builder_new();
gtk_builder_add_from_file(builder, "mywindow.glade", NULL);
GtkWidget *window = GTK_WIDGET(gtk_builder_get_object(builder, "window"));
```

---

### Post by bruce89 on 2009-02-16
> **SeanHodges said:**
> In essence, you draw your interface using the interface designer tool, export the XML as a ".glade" file, and use libglade in your program to parse the XML and do all the work:

```
GtkBuilder *builder = gtk_builder_new();
gtk_builder_add_from_file(builder, "mywindow.glade", NULL);
GtkWidget *window = GTK_WIDGET(gtk_builder_get_object(builder, "window"));
```

That's GtkBuilder, not libglade. I'd recommend using GtkBuilder. You can convert a glade file to a GtkBuilder one with *gtk-builder-convert*.

---

### Post by WitchCraft on 2009-07-02
> **bruce89 said:**
> That's GtkBuilder, not libglade. I'd recommend using GtkBuilder. You can convert a glade file to a GtkBuilder one with *gtk-builder-convert*.

I recommend using wxWidgets & wxFormBuilder instead of GTk.

---

### Post by jacensolo on 2009-07-02
> **WitchCraft said:**
> I recommend using wxWidgets & wxFormBuilder instead of GTk.

Did you check the dates?

---

### Post by WitchCraft on 2009-07-03
> **jacensolo said:**
> Did you check the dates?

Sir no sir. Ooops - Sorry.

---

