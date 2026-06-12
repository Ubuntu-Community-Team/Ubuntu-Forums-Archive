---
title: "help with GTK!"
date: 2009-09-28
forum: Programming Talk
---

### Post by slurrrp on 2009-09-28
The goal of this game is to click the buttons in correct order from lowest to highest with a time limit. Two parameters will be entered, which are the number of buttons [max of 52] and the time limit. My approach is when the button is clicked, it copies its label to the button in the other window.

I don't get compile errors but when I click the buttons, erros start to come up such as:

(me4:10877): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkButton'

(me4:10877): Gtk-CRITICAL **: gtk_button_set_label: assertion `GTK_IS_BUTTON (button)' failed

Segmentation fault

This code worked totally fine in my windows vista OS, but now that I'm on ubuntu [and I have to make it work on ubuntu], it doesn't.

I hope someone can help me fix this. I know my code is kinda long, but I really need help.

Attached is my code.

> 
#define NUM_OF_COLUMNS 6
#define RAND_NUM_MIN 1
#define RAND_NUM_MAX 52
#ifdef HAVE_CONFIG_H

#  include <config.h>
#endif

#include <gtk/gtk.h>
#include <string.h>
#include <stdlib.h>
#include <time.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <ctype.h>

#include "interface.h"
#include "support.h"

GtkWidget *window1, *window2;
GtkWidget *button;
GtkWidget *label;
GtkWidget *table1;
GtkWidget *table2;
GtkWidget *timerLabel;
GtkWidget **buttonArray1;
GtkWidget **buttonArray2;
GTimer *timer;
gint tag;
time_t timeStart;
GtkWidget *vbox;
GtkWidget *hbox;

int list1Count;
int list2Count;
int timerValue;
int timeout;
int numOfButtons;

int getRandNum(min, max) //to get random numbers
{
int fd;
      unsigned int random;
  fd = open("/dev/urandom", O_RDONLY);
  read(fd, &random, sizeof(random));
  return random%(max-min+1);
}

int *makeRandList(int min, int max, int randListCount) // make a list of random numbers
{
      int i;
      int randNum;
      int tempNum;
      int tempListCount;
      int *randList;
      int *tempList;
    
       tempListCount = max-min+1;
       if(tempListCount < randListCount)[INDENT]     return NULL;
[/INDENT]tempList = (int*)malloc(tempListCount*sizeof(int));
       for(i=0; i<tempListCount;i++)[INDENT]              tempList[i] = min+i;
[/INDENT]for(i=0; i<randListCount; i++)
       {[INDENT]              randNum = i + getRandNum(i, tempListCount-1);
             tempNum = tempList[i];
             tempList[i] = tempList[randNum];
             tempList[randNum] = tempNum;
[/INDENT]}
    
      randList = (int*)malloc(randListCount*sizeof(int)+1);
      for (i = 0; i < randListCount; i++) randList[i] = tempList[i];[INDENT]             free(tempList);
[/INDENT]return randList;
  }

void getDateToday(char *timeString)
{
      time_t today;
      struct tm *timeinfo;
      const size_t size= 50;
      time(&today);
      timeinfo = localtime(&today);
       strftime(timeString, size, "%B %d, %Y", timeinfo);
}

char checkString(char *string) // checker
{
      while (isspace(*string) && *string != '\0')[INDENT]             string++;   
[/INDENT]if (*string == '-')[INDENT]             string++;
[/INDENT]else if (*string == '\0')[INDENT]         return 0;
[/INDENT]while (!isspace(*string) && *string != '\0')
      {    
          if (!isdigit(*string))[INDENT]                 return 0; 
[/INDENT]string++;
      }
  
      while (isspace(*string) && *string != '\0')[INDENT]              string++;     
[/INDENT]if (*string == '\0')[INDENT]             return 1;
[/INDENT]else[INDENT]             return 0;
[/INDENT]}

char getParam(int argc, char *argv[], int *numOfButtons, int *timeout, char *errorMsg) // checks parameters
{
      *errorMsg = '\0';
    
       if (argc != 3)
      {[INDENT]             strcpy(errorMsg, "Error: Invalid number of parameters.\n");
            return -1;
[/INDENT]}
  
      if (!checkString(argv[1]) )
      {[INDENT]              strcpy(errorMsg, "Error: The parameter for the number of buttons is not a number.\n");
            return -1;
[/INDENT]}
    
      *numOfButtons = atoi(argv[1] );
      
  if (!(*numOfButtons))
      {[INDENT]             strcpy(errorMsg, "Error: Zero cannot be a parameter for the number of buttons.\n");
            return -1;
[/INDENT]}
      else if (*numOfButtons < 0)
      {[INDENT]             strcpy(errorMsg, "Error: A negative number cannot be a parameter for the number of buttons.\n");
            return -1;
[/INDENT]}
  
      if (!checkString(argv[2]))
      {[INDENT]             strcpy(errorMsg, "Error: The parameter for timeout is not a number.\n");
            return -1;
[/INDENT]}    

      *timeout = atoi(argv[2] );
      if (!(*timeout) )
      {[INDENT]             strcpy(errorMsg, "Error: Zero cannot be a paramet er for timeout.\n");
            return -1;
[/INDENT]}
      else if (*timeout < 0)
      {[INDENT]             strcpy(errorMsg, "Error: A negative number cannot be a parameter for time out.\n");
            return -1;
[/INDENT]}  
  
      return 0;
}

#define OK 1
#define HINDI 2
#define DI_PA_TAPOS 3 

char okBa() // checks the buttons are in order
{
      int i;
      int num1, num2;
    
       for(i=0; i<=list2Count-2; i++)
       {[INDENT]             num1 = atoi(gtk_button_get_label(GTK_BUTTON(buttonArray2[i])));
            num2 = atoi(gtk_button_get_label(GTK_BUTTON(buttonArray2[i+1])));
            if(num1>num2)
                  return    HINDI;
[/INDENT]}
      if(list2Count<numOfButtons)[INDENT]             return    DI_PA_TAPOS;
[/INDENT]return OK;
}
    
void itsOver(GtkWidget *widget, gpointer window) //dialog box when game over
{
      GtkWidget *dialog;
      time_t timeEnd;
       char temp1[50], temp2[50];
      char okNgaBa;
    
       g_source_remove(tag);
      okNgaBa = okBa();
    
    if(okNgaBa == OK)
      {[INDENT]            strcpy(temp1, "You have arranged the buttons in ");
            sprintf (temp2, "%lf seconds.", (double)g_timer_elapsed(timer, NULL) );
          strcat(temp1, temp2);
[/INDENT]}
      else if(okNgaBa == DI_PA_TAPOS)[INDENT]            strcpy(temp1, "The buttons are in the right order but you haven't selected all of them.");
[/INDENT]else[INDENT]            strcpy(temp1, "The buttons are in the wrong order!");
[/INDENT]dialog = gtk_message_dialog_new(window, GTK_DIALOG_DESTROY_WITH_PARENT, GTK_MESSAGE_INFO, GTK_BUTTONS_OK, temp1, "title");
     gtk_window_set_title(GTK_WINDOW(dialog), "Mouse Speed Click Game");
     gtk_dialog_run(GTK_DIALOG(dialog));
     gtk_widget_destroy(dialog);
     g_timer_destroy(timer);
     gtk_main_quit();
}

gint updateTimer(gpointer window)
{
      GtkWidget *dialog;
      GtkWidget *label;

       char temp1[100], temp2[100];
    
      if(!timerValue)
      {[INDENT]             gtk_label_set_text(GTK_LABEL(timerLabel), "Time's up!");
            strcpy(temp1, "Time's up!");
            dialog = gtk_message_dialog_new(window, GTK_DIALOG_DESTROY_WITH_PARENT, GTK_MESSAGE_INFO, GTK_BUTTONS_OK, temp1, "title");
            gtk_window_set_title(GTK_WINDOW(dialog), "Mouse Speed Click Game");
            gtk_dialog_run(GTK_DIALOG(dialog));
            gtk_widget_destroy(dialog);
            g_timer_destroy(timer);
           gtk_main_quit();         
            return 0;
[/INDENT]}
    
      strcpy(temp1, "You have ");
      sprintf(temp2, "%d seconds left...", timerValue--);
     strcat(temp1, temp2);
     gtk_label_set_text(GTK_LABEL(timerLabel), temp1);
     return 1;
}

void buttonClickedOnWindow2(GtkWidget *widget, gpointer data) // callback for buttons in window2
{
      char tempString[100];
      int id;
    
       strcpy(tempString, gtk_button_get_label(GTK_BUTTON(widget)));
      gtk_button_set_label(GTK_BUTTON(buttonArray1
[list1Count]), tempString);
      gtk_widget_show(buttonArray1
[list1Count]);
       list1Count++;
    
      for(id=atoi(gtk_widget_get_name(widget)); id<=list2Count-2; id++)
      {[INDENT]             strcpy(tempString, gtk_button_get_label(GTK_BUTTON(buttonArray2[id+1])));
            gtk_button_set_label(GTK_BUTTON(buttonArray2[id]), tempString);
[/INDENT]}
  list2Count--;
      gtk_widget_hide(buttonArray2
[list2Count]);
}

void buttonClickedOnWindow1(GtkWidget *widget, gpointer data) //callback for buttons in window1
{
      char tempString[100];
      int id;
    
      strcpy(tempString, gtk_button_get_label(GTK_BUTTON(widget)));
       gtk_button_set_label(GTK_BUTTON(buttonArray2
[list2Count]), tempString);
      gtk_widget_show(buttonArray2
[list2Count]);
      list2Count++;
    
      for(id = atoi(gtk_widget_get_name(widget)); id<=list1Count-2; id++)
      {[INDENT]             strcpy(tempString, gtk_button_get_label(GTK_BUTTON(buttonArray1[id+1])));
            gtk_button_set_label(GTK_BUTTON(buttonArray1[id]), tempString);
[/INDENT]}
      list1Count--;
      gtk_widget_hide(buttonArray1
[list1Count]);
}

int main(int argc, char *argv[])
{
      gtk_set_locale();
      gtk_init(&argc, &argv);
    
       int *randList;
       int numOfRows;
       int i, x, y;
    
      char tempString[100];
       char tempString2[100];
       char errorMsg[100];
    
       if(getParam(argc, argv, &numOfButtons, &timeout, errorMsg))
       {[INDENT]              puts(errorMsg);
            return;
[/INDENT]}
    
      numOfRows = (NUM_OF_COLUMNS-1)/numOfButtons+1;
      randList = makeRandList(RAND_NUM_MIN, RAND_NUM_MAX, numOfButtons);
      buttonArray1 = (GtkWidget**)g_malloc(numOfButtons*sizeof(GtkButton**));
      list1Count = numOfButtons;
      buttonArray2 = (GtkWidget**)g_malloc(numOfButtons*sizeof(GtkButton**));
      list2Count = 0;
      timerValue = timeout;
      time(&timeStart);
      timer = g_timer_new();
      tag = g_timeout_add(1000, updateTimer, (gpointer)window2);
    
       window1 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
      gtk_window_set_title(GTK_WINDOW(window1), "ME 4 - Main Window");

      vbox = gtk_vbox_new(FALSE, 0);
    
       label  = gtk_label_new("Mouse Click Speed Game");
       gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(label), FALSE, FALSE, 0);
    
       strcpy(tempString, "Today is ");
       getDateToday(tempString2);
       strcat(tempString, tempString2);
       label = gtk_label_new(tempString);
       gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(label), FALSE, FALSE, 0);
    
      label = gtk_label_new("Arrange the buttons by clicking the button with the lowest value up to the highest value.");
      gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(label), FALSE, FALSE, 0);
    
      table1 = gtk_table_new(numOfRows, NUM_OF_COLUMNS, TRUE);
      gtk_table_set_row_spacings(GTK_TABLE(table1), 2);
      gtk_table_set_col_spacings(GTK_TABLE(table1), 2);
      x=y=0;
    
      for(i=0; i<numOfButtons;i++)
      {[INDENT]             sprintf(tempString, "%d", randList[i]);   
            buttonArray1[i] = gtk_button_new_with_label(tempString);
            gtk_table_attach_defaults(GTK_TABLE(table1), buttonArray1[i], x, x+1, y, y+1);
            sprintf(tempString, "%d", i);
            gtk_widget_set_name(buttonArray1[i], tempString);
            g_signal_connect(G_OBJECT(buttonArray1[i]), "clicked", G_CALLBACK(buttonClickedOnWindow1), NULL);
            x++;
            if(x==NUM_OF_COLUMNS)
            {[INDENT]                   x=0;
                  y++;
[/INDENT]}
[/INDENT]}
    
      gtk_box_pack_start(GTK_BOX(vbox), table1, FALSE, FALSE, 0);
    
       strcpy(tempString, "You have ");
      sprintf(tempString2, "%d seconds left..", timeout);
      strcat(tempString, tempString2);
      timerLabel = gtk_label_new(tempString);
      gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(timerLabel), FALSE, FALSE, 0);
      gtk_container_add(GTK_CONTAINER(window1), GTK_WIDGET(vbox));
      g_signal_connect((gpointer)window1, "destroy", G_CALLBACK(gtk_main_quit), NULL);
      gtk_widget_show_all(GTK_WIDGET(window1));
    
       window2 = gtk_window_new (GTK_WINDOW_TOPLEVEL);
       gtk_window_set_title(GTK_WINDOW(window2), "ME 4 - Window 2");

      gtk_window_move(GTK_WINDOW(window2), 300, 400);
  
      vbox = gtk_vbox_new(FALSE, 0);
  
      label = gtk_label_new("Selected Buttons");
       gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(label), FALSE, FALSE, 0);
    
      table2 = gtk_table_new(numOfRows, NUM_OF_COLUMNS, TRUE);
      gtk_table_set_row_spacings(GTK_TABLE(table2), 2);
      gtk_table_set_col_spacings(GTK_TABLE(table2), 2); 
      x = y = 0;
      for (i = 0; i < numOfButtons; i++)
      {[INDENT]             buttonArray2[i] = gtk_button_new_with_label("");
            gtk_table_attach_defaults(GTK_TABLE(table2), buttonArray2[i], x, x+1, y, y+1);
            sprintf(tempString, "%d", i);
            gtk_widget_set_name(buttonArray2[i], tempString);    
            g_signal_connect(G_OBJECT(buttonArray2[i]), "clicked", G_CALLBACK(buttonClickedOnWindow2), NULL);
            x++;
            if (x == NUM_OF_COLUMNS)
             {[INDENT]                   x = 0;
                  y++;
[/INDENT]}   
[/INDENT]}     
  
       gtk_box_pack_start(GTK_BOX(vbox), table2, FALSE, FALSE, 0);  
  
       button = gtk_button_new_with_label("DONE");
       gtk_box_pack_start(GTK_BOX(vbox), GTK_WIDGET(button), FALSE, FALSE, 0);
       g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(itsOver), (gpointer)window2);
    
      gtk_container_add(GTK_CONTAINER(window2), vbox);

      g_signal_connect ((gpointer) window2, "destroy", G_CALLBACK(gtk_main_quit), NULL);
      gtk_widget_show_all(GTK_WIDGET(window2));

      for (i = 0; i < numOfButtons; i++)[INDENT]             gtk_widget_hide(buttonArray2[i]);
[/INDENT]free(buttonArray1);
       free(buttonArray2);  
    
       gtk_set_locale ();
       gtk_init (&argc, &argv);
    
       gtk_main();
       return 0;
}

---

### Post by PmDematagoda on 2009-09-28
Can you please first indent and properly format the source and post the code here within code tags? It is just too difficult to read the source code you posted.

---

### Post by slurrrp on 2009-09-28
> **PmDematagoda said:**
> Can you please first indent and properly format the source and post the code here within code tags? It is just too difficult to read the source code you posted.

Sorry for that.. I tried my best to indent it, and I hope it's better now.

---

### Post by PmDematagoda on 2009-09-28
I'm sorry, but the code could still use a little more sprucing up, for example:-
```
buttonArray1 = (GtkWidget**)g_malloc(numOfButtons*sizeof(GtkButto n**));
```
would look a lot better as:-
```
buttonArray1 = (GtkWidget **) g_malloc (numOfButtons * sizeof (GtkButton **));
```
the usage of spaces is not a crime, in fact, you should use it if it makes things more clearer. :)

By the way, there is an error in the first, uncorrected line of code posted which was corrected in the second, I think it may have crept in when you were reorganising the code.

---

### Post by PmDematagoda on 2009-09-28
Another error, why are you giving the source file the "txt" extension? That is not correct, such files should(and you probably know it) have the extension of "c".

Also I am unable to compile the code myself as you have not provided the whole source, I would like to compile and run the program myself to see how exactly its failing.

---

### Post by slurrrp on 2009-09-28
> **PmDematagoda said:**
> Another error, why are you giving the source file the "txt" extension? That is not correct, such files should(and you probably know it) have the extension of "c".

Also I am unable to compile the code myself as you have not provided the whole source, I would like to compile and run the program myself to see how exactly its failing.

I couldn't upload a .c file here.. :(

[EDIT]
I uploaded a .zip file instead of the whole thing.. I used glade for the GUI since we were supposed to use that.

---

### Post by PmDematagoda on 2009-09-28
The issue concerning your problem is really simple, please look at the last few lines of your program, especially your free() functions. It is not possible to access a dynamically allocated array of pointers if it has been freed, the buttons and the general program are unaffected because you are only getting rid of the references to them, not freeing them totally.

Also, why are you initialising the GTK environment twice? Once is more than enough. Also, if it was to be done properly, the gtk_main() call should have been before everything was freed.

Edit:- Additionally, for good practice, please do not mix GLib and ISO C types together, if you are using GTK+, stick with the types provided by GLib.

---

### Post by slurrrp on 2009-09-28
> **PmDematagoda said:**
> The issue concerning your problem is really simple, please look at the last few lines of your program, especially your free() functions. It is not possible to access a dynamically allocated array of pointers if it has been freed, the buttons and the general program are unaffected because you are only getting rid of the references to them, not freeing them totally.

Also, why are you initialising the GTK environment twice? Once is more than enough. Also, if it was to be done properly, the gtk_main() call should have been before everything was freed.

Edit:- Additionally, for good practice, please do not mix GLib and ISO C types together, if you are using GTK+, stick with the types provided by GLib.

Wow I never thought that the wrong positioning of gtk_main() could affect this greatly.. thanks for the help! :)

---

### Post by PmDematagoda on 2009-09-28
> **slurrrp said:**
> Wow I never thought that the wrong positioning of gtk_main() could affect this greatly.. thanks for the help! :)

When you use UIs like with GTK+, you need to use a loop to ensure that the program does not exit right after you have just shown them, gtk_main() starts the required loop until a call to gtk_main_quit() is made. Any attempt to do cleanups such as freeing dynamically allocated memory should be done after, not before gtk_main() if the memory has something to do with the operation of the UI.:)

---

