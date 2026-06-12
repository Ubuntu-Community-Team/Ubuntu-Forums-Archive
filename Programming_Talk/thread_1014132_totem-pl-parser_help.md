---
title: "totem-pl-parser help"
date: 2008-12-17
forum: Programming Talk
---

### Post by wolterh on 2008-12-17
Hi. I'm working on an internet radio project (visit: [google-code site]("http://code.google.com/p/bambox/")) and one of the last things missing is the playlist parser, which is essential, for almost every internet radio station points to a playlist file.

I was mixing around some code based on what they sampled [here]("http://library.gnome.org/devel/totem-pl-parser/stable/totem-pl-parser-totem-pl-parser.html").

This is my current source. It may seem to you like it is a whole mess, but its my proof that I gave it a shot to code something out and am not just asking for somebody to write the code for me. Now, I did not attempt to build the package because it is not ready yet. I want somebody to check it out first to tell me what am I doing wrong and how to correct it.
```

/* parser.h */

/*
 *      bambox parser header
 *      --------------------
 *      Copyright 2008, Wolter Hellmund <whellmundv@gmail.com>
 *      
 */

#ifndef BAMBOX_PARSER
#define BAMBOX_PARSER

#include <totem-pl-parser.h>

TotemPlParser *parser_data;
GtkTreeModel *parser_model;
GtkTreeIter *parser_model_iter;
GHashTable *parser_hash;

/* Song data */
struct
{
	char *uri;
	char *artist;
	char *title;
	unsigned short int duration;
} bambox_metadata;

void parser_init(); /* Will prepare everything for parsing stations*/
void parser_parse();/* Will parse the url and store the information in the bambox_metadata struct under the correct sections. */

#endif

/* -------------------------------------------------------------- */
/*parser.c */

/*
 *      bambox parser source
 *      --------------------
 *      Copyright 2008, Wolter Hellmund <whellmundv@gmail.com>
 *      
 */

#include "parser.h"

void parser_init()
{
	g_object_set(parser_data, "recurse", FALSE, "disable-unsafe", TRUE, NULL);
	g_signal_connect( G_OBJECT(parser_data), "playlist-started", G_CALLBACK(playlist_started), NULL);
	g_signal_connect( G_OBJECT(parser_data), "entry-parsed", G_CALLBACK(entry_parsed), NULL);

	parser_data = totem_pl_parser_new();
	parser_model = gtk_list_store_new(4, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_INT);
	populate_model(parser_model);
}

void parser_parse()
{
	if ( totem_parser_parse(parser_data, playlist, FALSE) != TOTEM_PL_PARSER_RESULT_SUCCESS)
	{
		action_reportError("failed to parse playlist");
	}
	
	bambox_metadata.uri = g_hash_table_lookup(parser_hash, TOTEM_PL_PARSER_FIELD_URL);
	bambox_metadata.artist = g_hash_table_lookup(parser_hash, TOTEM_PL_PARSER_FIELD_ARTIST);
	bambox_metadata.title = g_hash_table_lookup(parser_hash, TOTEM_PL_PARSER_FIELD_TITLE);
	bambox_metadata.duration = g_hash_table_lookup(parser_hash, TOTEM_PL_PARSER_FIELD_DURATION);
	
	gtk_tree_model_get (parser_model, parser_model_iter,
		0, bambox_metadata.uri,
		1, bambox_metadata.artist,		
		2, bambox_metadata.title,
		3, bambox_metadata.duration,
		-1);
}

```

---

