---
title: "Please Help!!"
date: 2006-05-18
forum: Programming Talk
---

### Post by moberry on 2006-05-18
Ok. I have been scratching my head on this one for a couple days now. First here is the code:

```

GList* read_dir(const gchar* path )

{

	g_print("running: read_dir()\n");

	GList* song_list=NULL;

	gchar* name;

	GDir* current=g_dir_open(path,0,NULL);

	gchar* full_file_name;

	name=(gchar*)g_dir_read_name(current);

	while(name!=NULL)

	{

	    full_file_name=g_build_filename(path,name,NULL);

	    if(g_file_test(full_file_name,G_FILE_TEST_IS_DIR))

			song_list=g_list_concat(song_list,read_dir(full_file_name));

	    else

		if(check_extension(name))

		{

		    //g_print("Found song: %s\n",name);

		    number_of_songs++;

		    song_list=g_list_prepend(song_list,g_strdup(full_file_name));

		}

	    name=(gchar*)g_dir_read_name(current);

	}

	g_dir_close(current);

	g_free(full_file_name);

	g_print("returned: read_dir()\n");

	return song_list;

	

	



}

```

The problem is this. That function works fine, the first time it is run. But the second time it is called the program segfaults. I have narrowed the segfault down to the function above (hence the prints at the beginning, and the end). Because it works once I am led to believe it is a memory allocation issue, but I cannot find anything I have done wrong. Any help would be appreciated. Below is the contents of the entire file (its a little messy, as i try to figure out what is wrong).

```

#include <glib.h>

#include <gtk/gtk.h>

#include "config.h"

#include "hang.h"

#include "database.h"

#include "tag_c.h"



GList* read_dir(const gchar* path );



static int number_of_songs;



void do_load(GtkWidget* widget, gpointer data)

{

	g_print("running: do_load()\n");

	number_of_songs=0;

	GList* song_list=NULL;

	HangTrack* info;

    int i=0;

	//keep track of the linked list

    GList* temp;

    g_print("%s\n",LIBRARY_LOCATION);

    song_list=read_dir(LIBRARY_LOCATION);

    temp=song_list;

    g_print("Number of songs from list: %d\n",g_list_length(temp));

	g_print("Number of songs from var: %d\n",number_of_songs);

    for(i;i<number_of_songs;i++)

    {

		g_print("Trying to load: %s\n",temp->data);

		//info=read_file(temp->data);

		

		//gtk_progress_bar_set_fraction(GTK_PROGRESS_BAR(data),(gdouble)i/number_of_songs);

		//call main_iter to redraw progress bar

		//gtk_main_iteration();

		//g_print("Loaded: %s - %s\n",info->artist,info->title);

		temp=temp->next;

    }

	g_free(info);

	temp=song_list;

	/*while(temp->next)

	{

		g_free(temp->data);

		temp=temp->next;

	}

	temp=song_list;*/

	g_list_free(temp);

	g_list_free(song_list);

	song_list=NULL;

	temp=NULL;

	g_print("returned: do_load()\n");

	

	

}

GList* read_dir(const gchar* path )

{

	g_print("running: read_dir()\n");

	GList* song_list=NULL;

	gchar* name;

	GDir* current=g_dir_open(path,0,NULL);

	gchar* full_file_name;

	name=(gchar*)g_dir_read_name(current);

	while(name!=NULL)

	{

	    full_file_name=g_build_filename(path,name,NULL);

	    if(g_file_test(full_file_name,G_FILE_TEST_IS_DIR))

			song_list=g_list_concat(song_list,read_dir(full_file_name));

	    else

		if(check_extension(name))

		{

		    //g_print("Found song: %s\n",name);

		    number_of_songs++;

		    song_list=g_list_prepend(song_list,g_strdup(full_file_name));

		}

	    name=(gchar*)g_dir_read_name(current);

	}

	g_dir_close(current);

	g_free(full_file_name);

	g_print("returned: read_dir()\n");

	return song_list;

	

	



}

gboolean check_extension(char* name)

{

	char** split_str=g_strsplit(name,".",-1);

	char* extension=split_str[g_strv_length(split_str)-1];

	int i=0;

	for(i;i<number_ext;i++)

		if(g_str_equal(extension,extensions[i]))

			return TRUE;

	return FALSE;

}

HangTrack* read_file(char* str)

{

	HangTrack* ret=g_malloc(sizeof(HangTrack));

  	taglib_set_strings_unicode(FALSE);

	TagLib_File *file;

	TagLib_Tag *tag;

	file=taglib_file_new(str);

	tag=taglib_file_tag(file);

	ret->artist=taglib_tag_artist(tag);

	ret->title=taglib_tag_title(tag);

	taglib_file_free(file);

	file=NULL;

	tag=NULL;

	return ret;	

}


```

---

### Post by moberry on 2006-05-19
A great way to solve a problem is to post a long well thought out thread to a forum, wait an hour. At which point the solution becomes blatantly obvious.

---

### Post by mostwanted on 2006-05-19
[QUOTE=moberry]A great way to solve a problem is to post a long well thought out thread to a forum, wait an hour. At which point the solution becomes blatantly obvious.[/QUOTE]

I make those all the time ;)

---

