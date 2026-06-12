---
title: "Too many arguments to function"
date: 2012-04-23
forum: Programming Talk
---

### Post by xtjacob on 2012-04-23
I am attempting to compile a multi-file program, and I keep getting these errors when attempting to compile it:```
main.c: In function &#8216;button_clicked&#8217;:
main.c:10:3: error: too many arguments to function &#8216;conditions&#8217;
main.c:3:5: note: declared here
main.c: In function &#8216;main&#8217;:
main.c:62:1: error: expected &#8216;;&#8217; before &#8216;}&#8217; token

```
Here is what I am compiling with:
```
gcc -Wall -lcurl -l json parser.c fileread.c sparser.c conditions.c `pkg-config --cflags gtk+-3.0` main.c `pkg-config --libs gtk+-3.0`

```


I'm not sure why I'm getting this error since I have this at the top: ```
void conditions(char *location);
```

Main.c:
```
#include <gtk/gtk.h>

void conditions(char *location);

void button_clicked(GtkButton *button, gpointer *entry1)
{
  const gchar *location;
  location = gtk_entry_get_text(GTK_ENTRY(entry1));
  conditions(location);

}


int main(int argc, char *argv[]) {

  GtkWidget *window;
  GtkWidget *table;
  GtkWidget *label1;
  GtkWidget *entry1;
  GtkWidget *button;
  
 
  gtk_init(&argc, &argv);

  window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
  gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);
  gtk_window_set_title(GTK_WINDOW(window), "GtkEntry");
  gtk_container_set_border_width(GTK_CONTAINER(window), 10);

  table = gtk_table_new(2, 1, FALSE);
  gtk_container_add(GTK_CONTAINER(window), table);

  label1 = gtk_label_new("Zipcode:");
  
  gtk_table_attach(GTK_TABLE(table), label1, 0, 1, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);
  
  entry1 = gtk_entry_new();

  gtk_table_attach(GTK_TABLE(table), entry1, 1, 2, 0, 1, GTK_FILL | GTK_SHRINK, GTK_FILL | GTK_SHRINK, 5, 5);

  button = gtk_button_new_with_label("Enter");
  gtk_table_attach_defaults(GTK_TABLE(table), button, 2, 3, 0, 1 );
 
  gtk_widget_show(table);

  gtk_widget_show(label1);
  
  gtk_widget_show(entry1);
  
  gtk_widget_show(button);
  
  gtk_widget_show(window);

  g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

  g_signal_connect(GTK_BUTTON(button), "clicked", G_CALLBACK(button_clicked), entry1);
  
  gtk_main();

  return 0;
}
```

conditions.c:
```
/*************************************************************
 *                      Copyright 2012                       *
 *                       Jacob Boline                        *
 *************************************************************/

#include <stdio.h>
#include <curl/curl.h>
#include <string.h>
#include <stdlib.h>
#include <json/json.h>
#include <math.h>

void curlf(const char* url);
const char* fname = "conditions.json";
const char* sfname = "settings.json";
char* json_parse(json_object * jobj, char const *stemp);
char* json_sparse(json_object * jobj, char const *stemp);
char* file_read (const char* filename);
void conditions(char *location);

void conditions(char *location)
{
  char *temp;
  char *dpnt;
  char *rhum;
  char *wind;
  char *pressure;
  char *trend;
  char *metric;
  char *windir;
  //char location[5];
  char url[150] = "http://api.wunderground.com/api/59eb6f72cabe560e/conditions/q/"; /*Declares inital URL*/
  char const *srhum = "relative_humidity";
  char const *swind = "wind_mph";
  char const *spressure = "pressure_in";
  char const *strend = "pressure_trend";
  char const *smetric = "use_metric";
  char const *swindir = "wind_dir";
  char stemp[10] = "temp_";
  char sdpnt[10] = "dewpoint_";

  strcat(url, location);                                      /* Appends location to URL. */
  strcat(url, ".json");
  curlf(url);                                                 /* Calls cURL function. */
  //printf("File downloaded.\n");


  char* sfile = file_read(sfname);                    //Opens settings file
  if (sfile)
  {
    json_object* jobj = json_tokener_parse(sfile);    /* Sets parsing paramaters. */
    metric = json_sparse(jobj, smetric);              /* Parses for settings */
 
    free(sfile);                                      /* release allocated memory */
  }

  if (strcmp(metric, "0") == 0)
  {
    strcat(stemp, "f");
    strcat(sdpnt, "f");                                     
  } 	
  if (strcmp(metric, "1") == 0)
  {
    strcat(stemp, "c"); 
    strcat(sdpnt, "c");
  }
  
  char* file = file_read(fname);
  if (file)
  {
    json_object* jobj = json_tokener_parse(file);   /* Sets parsing paramaters. */
    temp = json_parse(jobj, stemp);                 /* Parses for temperature (f) */
    dpnt = json_parse(jobj, sdpnt);                 /* Parses for Dewpoint (f) */
    rhum = json_parse(jobj, srhum);                 /* Parses for relative humidity */
    wind = json_parse(jobj, swind);                 /* Parses for wind info */
    pressure = json_parse(jobj, spressure);         /* Parses for pressure (in) */
    trend = json_parse(jobj, strend);               /* Parses for pressure trend */
    windir = json_parse(jobj, swindir);

    free(file);                                     /* release allocated memory */
  }

  if (strcmp(metric, "1") == 0)
  {
    printf("The temperature is %s degrees celcius.\n", temp);
    printf("The dewpoint is %s degrees celcius.\n", dpnt);
  }
  if (strcmp(metric, "0") == 0)
  {
    printf("The temperature is %s degrees fahrenheit.\n", temp);
    printf("The dewpoint is %s degrees fahrenheit.\n", dpnt);
  }

  printf("Relative Humidity is %s.\n", rhum); 
  printf("Wind is %s mph %s.\n", wind, windir);
  
  if (strcmp(trend, "+") == 0)
  {
    printf("Pressure is %s in and increasing.\n", pressure);
  }
  
  if (strcmp(trend, "0") == 0)
  {
    printf("Pressure is %s in and constant.\n", pressure);
  }

  if (strcmp(trend, "-") == 0)
  {
    printf("Pressure is %s in and decreasing.\n", pressure);
  }


}

void curlf(const char* url)
{
  CURL *json;
  FILE *wdata;
  json = curl_easy_init();                           /* Start downloading process. */
  curl_easy_setopt(json, CURLOPT_URL, url);          /* Tells cURL what the URL is. */
  wdata = fopen(fname, "w");                         /* Create file to save data. */
  curl_easy_setopt(json, CURLOPT_WRITEDATA, wdata);  /* Tells cURL to save sata to wdata. */
  curl_easy_perform(json);                           /* Performs download. */
  curl_easy_cleanup(json);                           /* Cleans up. */
  fclose(wdata);                                     /* Close file. */
}
```

Any help would much appreciated!

---

### Post by Bachstelze on 2012-04-23
Please post the entire output.

Also, in general it is a bad idea to compile several .c files at the same time. Compile them separately to .o files and then link.

*EDIT:* That said, the file compiles fine here, with just some warnings due to mismatched types.

---

### Post by xtjacob on 2012-04-23
Well I discovered my error was me... I was editing the wrong file. How do I compile them into object files, and then link them?

---

### Post by Bachstelze on 2012-04-23
In general you rarely do multi-step compilation manually, and instead you write a Makefile. Something like

```

CC=gcc
CFLAGS=$(shell pkg-config --cflags gtk+-3.0)
LIBS=$(shell pkg-config --libs gtk+-3.0)
OBJFILES= parser.o \
          fileread.o \
          sparser.o \
          conditions.o \
          main.o
OUTPUT=program

$(OUTPUT): $(OBJFILES)
        $(CC) -o $@ $+ $(LIBS)

clean:
        rm -f $(OUTPUT) $(OBJFILES)

```

---

### Post by xtjacob on 2012-04-23
> **Bachstelze said:**
> In general you rarely do multi-step compilation manually, and instead you write a Makefile. Something like

```

CC=gcc
CFLAGS=$(shell pkg-config --cflags gtk+-3.0)
LIBS=$(shell pkg-config --libs gtk+-3.0)
OBJFILES= parser.o \
          fileread.o \
          sparser.o \
          conditions.o \
          main.o
OUTPUT=program

$(OUTPUT): $(OBJFILES)
        $(CC) -o $@ $+ $(LIBS)

clean:
        rm -f $(OUTPUT) $(OBJFILES)

```

Hmm, I tried it, but it outputs ```
main.c:1:21: fatal error: gtk/gtk.h: No such file or directory

```

---

### Post by Bachstelze on 2012-04-23
That was just an example, though it shouldn't have given that error... Once again, please paste the *entire* output.

---

### Post by xtjacob on 2012-04-23
Sorry, I had 2 makefiles in my directory. The one you gave me has this error: ```
[jacob@Jacob-PC backend]$ make
Makefile:12: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```

---

### Post by Bachstelze on 2012-04-24
Yes sorry, I had spaces instead of tabs because I wrote it directly in the forum. Open it in a text editor and insert one tab instead of all the spaces in all the indented lines.

---

### Post by xtjacob on 2012-04-24
Alright it runs now, but I get a whole bunch of compiling errors.
```
[jacob@Jacob-PC backend]$ make
gcc -DGSEAL_ENABLE -pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o parser.o parser.c
parser.c: In function ‘json_parse’:
parser.c:14:16: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
gcc -DGSEAL_ENABLE -pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o fileread.o fileread.c
gcc -DGSEAL_ENABLE -pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o sparser.o sparser.c
sparser.c: In function ‘json_sparse’:
sparser.c:14:16: warning: initialization discards ‘const’ qualifier from pointer target type [enabled by default]
gcc -DGSEAL_ENABLE -pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o conditions.o conditions.c
gcc -DGSEAL_ENABLE -pthread -I/usr/include/gtk-3.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12     -c -o main.o main.c
main.c: In function ‘button_clicked’:
main.c:33:3: warning: passing argument 1 of ‘conditions’ discards ‘const’ qualifier from pointer target type [enabled by default]
main.c:4:18: note: expected ‘char *’ but argument is of type ‘const gchar *’
g++  -o program parser.o fileread.o sparser.o conditions.o main.o
parser.o: In function `json_parse':
parser.c:(.text+0x1d): undefined reference to `json_object_object_get'
parser.c:(.text+0x34): undefined reference to `json_object_object_get'
parser.c:(.text+0x44): undefined reference to `json_object_get_string'
sparser.o: In function `json_sparse':
sparser.c:(.text+0x1d): undefined reference to `json_object_object_get'
sparser.c:(.text+0x34): undefined reference to `json_object_object_get'
sparser.c:(.text+0x44): undefined reference to `json_object_get_string'
conditions.o: In function `conditions':
conditions.c:(.text+0x260): undefined reference to `json_tokener_parse'
conditions.c:(.text+0x42e): undefined reference to `json_tokener_parse'
conditions.o: In function `curlf':
conditions.c:(.text+0x572): undefined reference to `curl_easy_init'
conditions.c:(.text+0x597): undefined reference to `curl_easy_setopt'
conditions.c:(.text+0x5d3): undefined reference to `curl_easy_setopt'
conditions.c:(.text+0x5df): undefined reference to `curl_easy_perform'
conditions.c:(.text+0x5eb): undefined reference to `curl_easy_cleanup'
main.o: In function `button_clicked':
main.c:(.text+0x1a): undefined reference to `gtk_entry_get_type'
main.c:(.text+0x2f): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x37): undefined reference to `gtk_entry_get_text'
main.c:(.text+0x64): undefined reference to `gtk_label_get_type'
main.c:(.text+0x76): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x83): undefined reference to `gtk_label_set_text'
main.o: In function `main':
main.c:(.text+0xaa): undefined reference to `gtk_init'
main.c:(.text+0xb4): undefined reference to `gtk_window_new'
main.c:(.text+0xbd): undefined reference to `gtk_window_get_type'
main.c:(.text+0xcf): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0xdc): undefined reference to `gtk_window_set_position'
main.c:(.text+0xe1): undefined reference to `gtk_window_get_type'
main.c:(.text+0xf3): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x100): undefined reference to `gtk_window_set_title'
main.c:(.text+0x105): undefined reference to `gtk_container_get_type'
main.c:(.text+0x117): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x124): undefined reference to `gtk_container_set_border_width'
main.c:(.text+0x138): undefined reference to `gtk_table_new'
main.c:(.text+0x141): undefined reference to `gtk_container_get_type'
main.c:(.text+0x153): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x162): undefined reference to `gtk_container_add'
main.c:(.text+0x16c): undefined reference to `gtk_label_new'
main.c:(.text+0x175): undefined reference to `gtk_entry_new'
main.c:(.text+0x183): undefined reference to `gtk_button_new_with_label'
main.c:(.text+0x191): undefined reference to `gtk_label_new'
main.c:(.text+0x19a): undefined reference to `gtk_table_get_type'
main.c:(.text+0x1ac): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x1ed): undefined reference to `gtk_table_attach'
main.c:(.text+0x1f6): undefined reference to `gtk_table_get_type'
main.c:(.text+0x208): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x248): undefined reference to `gtk_table_attach'
main.c:(.text+0x24d): undefined reference to `gtk_table_get_type'
main.c:(.text+0x25f): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x281): undefined reference to `gtk_table_attach_defaults'
main.c:(.text+0x28a): undefined reference to `gtk_table_get_type'
main.c:(.text+0x29c): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x2bd): undefined reference to `gtk_table_attach_defaults'
main.c:(.text+0x2c9): undefined reference to `gtk_widget_show'
main.c:(.text+0x2d5): undefined reference to `gtk_widget_show'
main.c:(.text+0x2e1): undefined reference to `gtk_widget_show'
main.c:(.text+0x2ed): undefined reference to `gtk_widget_show'
main.c:(.text+0x2f9): undefined reference to `gtk_widget_show'
main.o:main.c:(.text+0x305): more undefined references to `gtk_widget_show' follow
main.o: In function `main':
main.c:(.text+0x31f): undefined reference to `gtk_main_quit'
main.c:(.text+0x32c): undefined reference to `g_signal_connect_data'
main.c:(.text+0x33a): undefined reference to `gtk_button_get_type'
main.c:(.text+0x34c): undefined reference to `g_type_check_instance_cast'
main.c:(.text+0x36b): undefined reference to `g_signal_connect_data'
main.c:(.text+0x370): undefined reference to `gtk_main'
collect2: ld returned 1 exit status
make: *** [program] Error 1
[jacob@Jacob-PC backend]$ 

```

---

### Post by Bachstelze on 2012-04-24
You need to add your other [font=monospace]-l[/font] flags to the LIBS variable, change that line to

```
LIBS=$(shell pkg-config --libs gtk+-3.0) -ljson -lcurl
```

However, it seems to ignore it when it does the linking (hence why you also get the errors about GTK even though the flags are there). Did you change something in it?

---

### Post by xtjacob on 2012-04-24
No, I copied it exactly. Here's what I have:
```
CC=gcc
CFLAGS=$(shell pkg-config --cflags gtk+-3.0)
LIBS=$(shell pkg-config --libs gtk+-3.0) -ljson -lcurl
OBJFILES= parser.o \
	fileread.o \
	sparser.o \
	conditions.o \
	main.o
OUTPUT=program

$(OUTPUT): $(OBJFILES)
	$(CXX) $(LDFLAGS) -o $@ $+

clean:
	rm -f $(OUTPUT) $(OBJFILES)
```

---

### Post by Bachstelze on 2012-04-24
That's the Makefile I based it on. Maybe I posted it yesterday and then edited it later... Go back to my first message, it is different now (but it doesn't say I edited it, weird). You should have

```
$(OUTPUT): $(OBJFILES)
	$(CC) -o $@ $+ $(LIBS)
```

---

### Post by xtjacob on 2012-04-24
Alright, that fixed it! Thanks for the help! What's the advantages of doing it this way over the other way?

---

### Post by Bachstelze on 2012-04-24
For one, make is shorter to type than your long command. Of course there is the up-arrow, but if you do other things and then go back to your project, you will have to hit the up-arrow a lot of times.

Also, when you have a big project with a lot of .c files, you don't want to recompile everything when you change only one .c file. With make, only that file will be recompiled. For all the others, it will just reuse the .o file.

---

### Post by xtjacob on 2012-04-24
Ooh, I see. Thanks!

---

