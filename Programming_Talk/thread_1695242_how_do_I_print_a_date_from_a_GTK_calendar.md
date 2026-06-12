---
title: "how do I print a date from a GTK calendar?"
date: 2011-02-25
forum: Programming Talk
---

### Post by LarryJor on 2011-02-25
Hi.  Can anyone tell me how to print the date a user double-clicks on from a GTK calendar?  I just want to print the date back to STDOUT (default).

---

### Post by nvteighen on 2011-02-26
> **LarryJor said:**
> Hi.  Can anyone tell me how to print the date a user double-clicks on from a GTK calendar?  I just want to print the date back to STDOUT (default).

Look at this: [http://library.gnome.org/devel/gtk/stable/GtkCalendar.html#gtk-calendar-get-date](http://library.gnome.org/devel/gtk/stable/GtkCalendar.html#gtk-calendar-get-date)

---

### Post by LarryJor on 2011-02-26
Yeah, I keep looking at that, but can't get it to work.  I'm using this:

/*
 *File name: calendar.c
 */

#include <stdio.h>
#include <string.h>
#include <gtk/gtk.h>
#include <glib.h>

typedef struct _CalendarData {
  GtkWidget *flag_checkboxes[5];
  gboolean  settings[5];
  GtkWidget *font_dialog;
  GtkWidget *window;
  GtkWidget *prev2_sig;
  GtkWidget *prev_sig;
  GtkWidget *last_sig;
  GtkWidget *month;
} CalendarData;


/*-- This function allows the program to exit properly when the window is closed --*/
gint destroyapp (GtkWidget *widget, gpointer gdata)
{
  g_print ("Quitting...\n");
  gtk_main_quit();
  return (FALSE);
}

static void calendar_date_to_string( CalendarData *data,
                                     char         *buffer,
                                     gint          buff_len )
{
  GDate date;
  guint year, month, day;

  gtk_cPlease click one of the Quick Reply icons in the posts above to activate Quick Reply.alendar_get_date (GTK_CALENDAR (data->window),
             &year, &month, &day);
  g_date_set_dmy (&date, day, month + 1, year);
  g_date_strftime (buffer, buff_len - 1, "%x", &date);

}

static void calendar_day_selected_double_click ( GtkWidget    *widget,
                                                 CalendarData *data )
{
  char buffer[256] = "";
  guint year;
  guint month;
  guint day;Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

  calendar_date_to_string (data, buffer, 256);

  gtk_calendar_get_date (GTK_CALENDAR (data->window),
             &year, &month, &day);
  printf ( "%d/%d/%d\n", month + 1, day, year );

  if (GTK_CALENDAR (data->window)->marked_date[day-1] == 0) {
    gtk_calendar_mark_day (GTK_CALENDAR (data->window), day);
  } else { 
    gtk_calendar_unmark_day (GTK_CALENDAR (data->window), day);
  }
}


int main (int argc, char *argv[])
{
  /*-- Declare the GTK Widgets used in the program --*/
  GtkWidget *window;
  GtkWidget *calendar;

  /*--  Initialize GTK --*/
  gtk_init (&argc, &argv);

  /*-- Create the new window --*/
  calendar = gtk_calendar_new();

  /*-- Create the new window --*/
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  /*-- Connect the window to the destroyapp function  --*/
  gtk_signal_connect(GTK_OBJECT(window), "delete_event", GTK_SIGNAL_FUNC(destroyapp), NULL);

  /*-- Add the calendar to the window --*/
  gtk_container_add(GTK_CONTAINER(window), calendar);

  /*-- Display the widgets --*/
  gtk_widget_show(calendar);
  gtk_widget_show(window);

  /*-- Start the GTK event loop --*/
  gtk_main();

  /*-- Return 0 if exit is successful --*/
  return 0;
}

     This is a cut down version of an example, and a lot of it is unnecessary (font info, etc), but seems to me it still should print the date selected.  What I want to do is to be able to check it by calling it from a terminal, but use it as an app in larger programs.  So can you tell me what I am doing wrong?:confused:

---

### Post by jeffathehutt on 2011-02-28
I'm not sure if you posted your entire code or not, but in the code you posted you never connected your callback to the "day-selected-double-click" signal from the calendar, so your function will never be called. :)

---

### Post by LarryJor on 2011-12-30
Took me a long time to get what I wanted from this, but finally got it to work.  I am building a set of tools, at a beginner level, that vaguely resemble zenity.  The advantage is that I can develop them further as I learn more about GTK.  What I ended up with for this is as follows:

#include <stdio.h>
#include <string.h>
#include <gtk/gtk.h>
#include <glib.h>

typedef struct _CalendarData {
  GtkWidget *flag_checkboxes[5];
  gboolean  settings[5];
  GtkWidget *font_dialog;
  GtkWidget *window;
  GtkWidget *prev2_sig;
  GtkWidget *prev_sig;
  GtkWidget *last_sig;
  GtkWidget *month;
} CalendarData;

static CalendarData calendar_data;
  /*-- Declare the GTK Widgets used in the program --*/
  GtkWidget *window;
  GtkWidget *calendar;

/*-- This function allows the program to exit properly when the window is closed --*/
gint destroyapp(GtkWidget *widget, gpointer gdata)
{
  gtk_main_quit();
  return (FALSE);
}


static void calendar_day_selected_double_click ( GtkWidget    *widget,
                                                 CalendarData *data,
                                             gint          buff_len )
{
  guint day, month, year;

  gtk_calendar_get_date (GTK_CALENDAR (calendar),
             &day, &month, &year);
/* --WHY do I have to switch the year and the day??-- */

  printf("%d/%d/%d\n", month + 1, year, day);

  gtk_main_quit();
}



int main (int argc, char *argv[])
{

  /*--  Initialize GTK --*/
  gtk_init (&argc, &argv);

  /*-- Create the new window --*/
  calendar = gtk_calendar_new();

  /*-- Create the new window --*/
  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

  /* --------------------- Attempt to use double-click --------------------*/
  gtk_signal_connect(GTK_OBJECT(calendar), "day-selected-double-click",
                G_CALLBACK(calendar_day_selected_double_click), &calendar_data);

  /*-- Connect the window to the destroyapp function  --*/
  gtk_signal_connect(GTK_OBJECT(window), "delete_event", GTK_SIGNAL_FUNC(destroyapp), NULL);

  /*-- Add the calendar to the window --*/
  gtk_container_add(GTK_CONTAINER(window), calendar);

  /*-- Display the widgets --*/
  gtk_widget_show(calendar);
  gtk_widget_show(window);

  /*-- Start the GTK event loop --*/
  gtk_main();

  /*-- Return 0 if exit is successful --*/
  return 0;
}

---

