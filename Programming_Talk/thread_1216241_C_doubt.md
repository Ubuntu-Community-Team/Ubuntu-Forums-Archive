---
title: "C doubt"
date: 2009-07-18
forum: Programming Talk
---

### Post by nipunreddevil on 2009-07-18
i made the following program in c
somehow i have not beeen able to get it work 100% correctly.

#include<stdio.h>

int main()
	{
	FILE *fp;
	char ch[2000];
	int i=0;
	char filename[100];
	printf("enter the name of the file to be opened with .c extension\n");
	scanf("%s",filename);
	fp=fopen(filename,"r");
	while (1)
		{
		ch[i]=fgetc(fp);
		if (ch[i]==EOF)	
		break;
		if(ch[i]=='i')
		printf("\t%c%c%c%c",ch[i-1],ch[i],ch[i+1],ch[i+2]);
		i++;
		}
	fclose(fp);
	printf("Total characters are:%d\t",i);
	return 0;
	}		



i get strange output for it
however if i print all characters i get correct result.

---

### Post by c0mput3r_n3rD on 2009-07-18
#include "file.h"
?

---

### Post by lisati on 2009-07-18
One observation: in C, strings are usually zero-terminated. It might be a good idea to have something like
```
ch[i]=0;
```
just before your printf(). Hope this helps.

---

### Post by nipunreddevil on 2009-07-18
why is file.h needed
i am able to run the program properly.
maybe some error if i try to print a portion of the read file.

---

### Post by lisati on 2009-07-18
> **nipunreddevil said:**
> why is file.h needed
i am able to run the program properly.
maybe some error if i try to print a portion of the read file.

I'm curious too......what's file.h and where does it come from?

---

### Post by c0mput3r_n3rD on 2009-07-18
If you're working with files you have to include the file header file. 

And you would initialize ch[0] to "" as so:
```

ch[0] = "";

```

---

### Post by nipunreddevil on 2009-07-18
This is the sought of output i get:
nipun@ubuntu:~$ gcc file_read.c -o file_read1
nipun@ubuntu:~$ ./file_read1
enter the name of the file to be opened with .c extension
nipun.c
	#i	di&	
i	ai	ri&#65533;&#65533;	ui	ui	ui	uiTotal characters are:55	nnipun@ubuntu:~$ 

but if change one line ie printf(ch[i]) without any condition output is fine

---

### Post by lisati on 2009-07-18
Please stand by......putting my "thinking cap" on (I have a hunch)

Edit: I'm not sure if this is quite what you want, but check this out:
```

#include<stdio.h>

int main()
{
	FILE *fp;
	char ch[2000];
	int i=0;
	char filename[100];

// Lisati's kludge
	for (i=0; i<2000; i++) // initialise ch[]
		ch[i]=0;
	i=0;			// put i back how we want it
// end of kludge

	printf("enter the name of the file to be opened with .c extension\n");
	scanf("%s",filename);
	fp=fopen(filename,"r");
	while (1)
	{
		ch[i]=fgetc(fp);
		if (ch[i]==EOF)
			break;
		if(ch[i]=='i')
			printf("\t%c%c%c%c",ch[i-1],ch[i],ch[i+1],ch[i+2]);
		i++;
	}
fclose(fp);
printf("Total characters are:%d\t",i);
return 0;
}

```

---

### Post by lisati on 2009-07-18
OK - I've had a look, you might want to initialise the ch[] array to zeros. Others more skilled in C programming might have better suggestions than what I've illustrated.

---

### Post by nipunreddevil on 2009-07-18
i was basically searching for a string in the file.
Try 1:
tried to search ch[i],ch[i+1] and ch[i+2] for i n and t respectively
program gave errors
Try 2:
tried with ch[i-2],ch[i-1] and ch[i]
worked perfectly.
can anyone explain the error
Thanks to all those who replied
but there is no need to initialise the array to 0
works without it too

---

### Post by lisati on 2009-07-18
> **nipunreddevil said:**
> i was basically searching for a string in the file.
Try 1:
tried to search ch[i],ch[i+1] and ch[i+2] for i n and t respectively
program gave errors
Try 2:
tried with ch[i-2],ch[i-1] and ch[i]
worked perfectly.
can anyone explain the error
Thanks to all those who replied
but there is no need to initialise the array to 0
works without it too

you're right: there's no need to initialise the whole array to zero - that was a [kludge]("http://en.wikipedia.org/wiki/Kludge") on my part to prevent printf printing out rubbish, putting a zero after the EOF would suffice.

Edit: Just one extra thought: if you're checking ch[i] for 'i' as you read the file, the next few entries in the array won't have been filled in yet.

---

### Post by nipunreddevil on 2009-07-18
ok that done how shall i proceed with searching for any string that the user inputs.
have an idea though seems in efficient:
input string
find stringlength
match each character from ch[i-stringlength+count] with string[count]
and then display if true
Any better algo

---

### Post by lisati on 2009-07-18
My C skills aren't so great but here a couple of thoughts:

One possibility would be to read the whole file at once and then use something like the strncmp() function to search for the sequence "int"

A program illustrating different ways of loading and scanning a file can be found at [http://www.mrx.net/c/source.html](http://www.mrx.net/c/source.html)

---

### Post by dwhitney67 on 2009-07-18
@ nipunreddevil

You indicated that you are searching for a particular string in the file.  Then why are you reading one character at a time from the file?  Why not consider reading one line at a time, and then using strstr() to search for your string?  It would be much more efficient.

You should also attempt to get into the habit of initializing your variables and checking the validity of pointers before attempting to access them.

The easiest way to initialize an array (to zero/null) is to assign it to {0}.  Alternatively, memset() can be used.

P.S.  Unless your application is meant to be compiled with an older compiler, I personally would recommend that you use the GNU 99 version of GCC.
```

gcc -std=gnu99 MyFile.c -o MyApp

```

Anyhow, to open a file and search for a particular string:
```

#include <stdio.h>
#include <string.h>

int main()
{
   char filename[256]  = {0};
   char searchFor[256] = {0};

   printf("Enter a filename with the .c extension   : ");
   fgets(filename, sizeof(filename), stdin);

   printf("Enter the word that you are searching for: ");
   fgets(searchFor, sizeof(searchFor), stdin);

   if (strchr(filename, '\n'))  filename[strlen(filename) - 1] = '\0';
   if (strchr(searchFor, '\n')) searchFor[strlen(searchFor) - 1] = '\0';

   FILE* fp = fopen(filename, "r");

   if (fp)
   {
      char         line[256] = {0};
      unsigned int linenum = 0;

      while (fgets(line, sizeof(line), fp))
      {
         ++linenum;

         if (strstr(line, searchFor))
         {
            printf("%d: %s", linenum, line);
         }
      }
   }
   else
   {
      printf("Failed to open %s\n", filename);
      return -1;
   }

   return 0;
}

```

---

### Post by nipunreddevil on 2009-07-18
@dwhitney
your solution is very nice,compact and elegant
some doubts:
1.i only need to print the exact word and not the line containing it.
2.whats the importance of initializing
3.how can i make this all in a gui
like qt or gtk
i have just started linux programming

---

### Post by PmDematagoda on 2009-07-18
> **nipunreddevil said:**
> @dwhitney
your solution is very nice,compact and elegant
some doubts:
1.i only need to print the exact word and not the line containing it.
2.whats the importance of initializing
3.how can i make this all in a gui
like qt or gtk
i have just started linux programming

Initialising variables are useful to reduce confusions when you get garbage values or segmentation faults from your programs, but it is not an absolute necessity.

For GUI stuff, you can use GTK+ in your C program as well, but Qt would be another story since it requires C++. Although both GTK+ and Qt have language bindings for Python, etc. but that probably won't be of much use to you.

---

### Post by dwhitney67 on 2009-07-18
> **nipunreddevil said:**
> @dwhitney
your solution is very nice,compact and elegant
some doubts:
1.i only need to print the exact word and not the line containing it.
2.whats the importance of initializing
3.how can i make this all in a gui
like qt or gtk
i have just started linux programming

1.  Then what is the point of the exercise?  Whatever... just change this line of code in the if-block...
```

...
   if (fp)
   {
      char line[256] = {0};

      while (fgets(line, sizeof(line), fp))
      {
         if (strstr(line, searchFor))
         {
            printf("%s\n", searchFor);
         }
      }
   }
...

```

2.  It is a personal opinion, and also an opinion shared by many organizations that develop software.  Some programmers don't see the importance, and that is fine.  Just keep them away from my software products.

3.  Design a dialog box, with a file selection widget, and a text-entry widget that allows the user to input their search string.  An Ok and Cancel button will also be helpful.  Display the file and highlight the text that is found (if any).  You can find the begin position of the search string within a line of text using the strstr().  Highlight the number of characters from that position plus the length of the search string.

If you require specific details for developing Qt or GTK apps, I'm not the most qualified person to give advice.

---

### Post by markux^Hs on 2009-07-18
You might also learn the difference between 'a doubt' and 'a question'.

Mark.

---

### Post by PmDematagoda on 2009-07-18
Here is an example GTK program you might use:-
```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#include <gtk/gtk.h>

typedef struct _FileTesterUI {
  GtkWidget *window;

  GtkWidget *vbox_main;

  GtkWidget *file_name_entry;
  GtkWidget *search_term_entry;

  GtkWidget *search_button;

  GtkWidget *results_text_view;
  GtkTextBuffer *results_view_buff;
  GtkWidget *scrolled_text_view;

} FileTesterUI;

gboolean delete_event_handler(){
  return FALSE;
}

void exit_gtk_app (GtkWidget *signaling_wid, int *exit_code){
  if (exit_code == NULL)
    exit (EXIT_SUCCESS);
  else
    exit (*exit_code);
}

void do_searching (GtkWidget *signaling_wid, FileTesterUI *main_ui){
  const gchar *file_name, *search_term;
  char file_line[256];
  unsigned int nbr_of_chars = 0, line_no = 0;
  FILE *fp;
  GtkTextIter buff_end_iter;

  file_name = gtk_entry_get_text (GTK_ENTRY(main_ui->file_name_entry));
  search_term = gtk_entry_get_text (GTK_ENTRY(main_ui->search_term_entry));

  if ( (fp = fopen (file_name, "r") ) == NULL ){
    g_print ("Incorrect file name entered!");
    exit (EXIT_FAILURE);
  }

  if ( (strlen (search_term)) == 0 ){
    g_print ("Invalid search term entered!");
    exit (EXIT_FAILURE);
  }

 while (fgets (file_line, sizeof(file_line), fp) ){
    line_no++;
    nbr_of_chars += strlen (file_line);

    if (strstr (file_line, search_term)){
      gtk_text_buffer_get_end_iter (main_ui->results_view_buff, &buff_end_iter);
      gtk_text_buffer_insert (main_ui->results_view_buff,
			      &buff_end_iter,
			      g_strdup_printf ("Found search term in line:- %s\n"\
					       "Line number:- %d\n",
					       file_line, line_no),
			      -1);
    }
  }
 gtk_text_buffer_get_end_iter (main_ui->results_view_buff, &buff_end_iter);

 gtk_text_buffer_insert (main_ui->results_view_buff,
			 &buff_end_iter,
			 g_strdup_printf ("There were %d characters in the given file.\n", nbr_of_chars),
			 -1);
 
}

void create_window (FileTesterUI *main_ui){

  main_ui->window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
  gtk_window_set_title (GTK_WINDOW(main_ui->window), "String Searcher");

  gtk_widget_set_size_request (main_ui->window, 500, 500);

  main_ui->vbox_main = gtk_vbox_new (FALSE, 6);

  main_ui->file_name_entry = gtk_entry_new ();
  main_ui->search_term_entry = gtk_entry_new ();

  main_ui->search_button = gtk_button_new_from_stock (GTK_STOCK_OK);

  main_ui->results_view_buff = gtk_text_buffer_new (NULL);
  main_ui->results_text_view = gtk_text_view_new_with_buffer (main_ui->results_view_buff);
  main_ui->scrolled_text_view = gtk_scrolled_window_new (NULL,NULL);

  gtk_scrolled_window_add_with_viewport (GTK_SCROLLED_WINDOW(main_ui->scrolled_text_view), main_ui->results_text_view);
  gtk_widget_set_size_request (main_ui->scrolled_text_view, 200, 200);

  gtk_box_pack_start (GTK_BOX(main_ui->vbox_main), main_ui->file_name_entry, FALSE, FALSE, 6);
  gtk_box_pack_start (GTK_BOX(main_ui->vbox_main), main_ui->search_term_entry, FALSE, FALSE, 6);
  gtk_box_pack_start (GTK_BOX(main_ui->vbox_main), main_ui->search_button, FALSE, FALSE, 6);
  gtk_box_pack_start (GTK_BOX(main_ui->vbox_main), main_ui->scrolled_text_view, FALSE, FALSE, 6);

  gtk_container_add (GTK_CONTAINER(main_ui->window), main_ui->vbox_main);

  g_signal_connect (main_ui->search_button, "clicked", G_CALLBACK(do_searching), main_ui);
  g_signal_connect (main_ui->window, "delete-event", G_CALLBACK(delete_event_handler), NULL);
  g_signal_connect (main_ui->window, "destroy", G_CALLBACK(exit_gtk_app), NULL);

  gtk_widget_show_all (main_ui->window);
}

int main (int argc, char *argv[]){
  char search_term[256], file_line[256], file_name[256];
  unsigned int line_no = 0, nbr_of_chars = 0;
  FILE *fp;
  FileTesterUI main_ui;

  gtk_init (&argc, &argv);

  create_window (&main_ui);
  gtk_main ();

  return 0;

}
```
mind you, this application was created in little time, and hence it is quite unpolished but it does do the job, though not to the point and you would still need to read the GTK+ programming tutorials and reference manuals before you can fully understand what is going on, but now you atleast have something to work on.

---

### Post by JordyD on 2009-07-18
> **c0mput3r_n3rD said:**
> If you're working with files you have to include the file header file. 

And you would initialize ch[0] to "" as so:
```

ch[0] = "";

```

You can also initialize it like this:
```
ch[0] = 0;
```
or (what I use):
```
ch[0] = '\0';
```

---

### Post by MindSz on 2009-07-20
> @dwhitney
your solution is very nice,compact and elegant
some doubts:
1.i only need to print the exact word and not the line containing it.
2.whats the importance of initializing
3.how can i make this all in a gui
like qt or gtk
i have just started linux programming

About initializing, I've run into many stupid problems just because I forgot to initialize my variables.

From integer valued operations (sum, mean, etc) to signed/unsigned char stuff (image processing and such) it is important that you are sure you are starting out with a 'clean' variable or you can run into headaches that could keep you busy for quite a while ("Why do I keep getting trash out of this? The computer must be broken...").

And as dwhitney said, if you only need to print the word you are searching for, then why search for it if you already know what to print?

---

### Post by nipunreddevil on 2009-07-20
> **MindSz said:**
> 

And as dwhitney said, if you only need to print the word you are searching for, then why search for it if you already know what to print?
What i wish to do is:Suppose you enter a string lets say alpha.
Now you specify a file say: file.txt
Next you search whether alpha exists in file.txt or not.
if it does then print it otherwise not.

---

