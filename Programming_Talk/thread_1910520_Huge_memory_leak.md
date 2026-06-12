---
title: "Huge memory leak"
date: 2012-01-17
forum: Programming Talk
---

### Post by Petrolea on 2012-01-17
Hi everyone!

I was making a simple highlighting program in GTK when I encountered a huge memory leak in my code. If I open a FileChooserDialog the memory usage of a program gets from 1.6MB to 3.8MB. But that's just once, later it remains there. I've read about this dialog leaking memory, but 100kB not 2.2MB. Leak occurs when I open the dialog and don't do anything yet, which means that the code inside the "if" doesn't really matter.

This is the code that causes memory leak:

[PHP]
void load_file(GtkButton *button, Objects *data)
{
	GtkWidget *dialog;
	dialog = gtk_file_chooser_dialog_new ("Open File", GTK_WINDOW(data -> window1), GTK_FILE_CHOOSER_ACTION_OPEN, GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT, NULL);
	if (gtk_dialog_run (GTK_DIALOG (dialog)) == GTK_RESPONSE_ACCEPT)
	{
		filename = gtk_file_chooser_get_filename (GTK_FILE_CHOOSER (dialog));
		FILE *file = fopen(filename, "r");
		
		gtk_text_buffer_set_text(GTK_TEXT_BUFFER(data -> textbuffer1), "", -1);
		gtk_text_buffer_get_iter_at_offset(data -> textbuffer1, &data -> start, -1);
		
		char line[50];
		while(fgets(line, sizeof(line), file) != NULL)
		{
			gtk_text_buffer_get_iter_at_offset(data -> textbuffer1, &data -> start, -1);
			gtk_text_buffer_insert(data -> textbuffer1, &data -> start, line, -1);
		}
				
		fclose(file);
		changed = false;
	}
	gtk_widget_destroy (dialog);
}

[/PHP]

Hope anyone can help me.
Thanks in advance!

---

### Post by trent.josephsen on 2012-01-17
How are you measuring memory usage?

Can you use a debugger, or printf() and getchar(), to step through and see whether gtk_file_chooser_dialog_new or gtk_dialog_run is causing the sudden inflation of memory usage?

Finally, just a thought -- if you run your program twice simultaneously, does it inflate memory usage by twice as much?  And, since I'm thinking about it, are you linking this stuff statically or dynamically?

---

### Post by Petrolea on 2012-01-17
It's gtk_file_chooser_dialog_new() that causes such high memory usage. So the dialog takes up 2.2MB of memory? It shouldn't to that, right?

I don't know much about linking but this is the command I use to compile & run the app:

```

c99 -Wall -g editor.c -o editor `pkg-config --cflags --libs gtk+-2.0` -export-dynamic && ./editor

```

If I run 2 apps at time, they both have same memory usage.

I thought a check with valgrind might help, this is a part I cut out of million other similiar messages:

```

18,336 bytes in 382 blocks are possibly lost in loss record 6,249 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41482AE: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41483E6: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4754C4B: g_object_newv (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== 19,265 bytes in 1,779 blocks are possibly lost in loss record 6,250 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F3D68: g_strdup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B156F: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4753B05: ??? (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333==    by 0x4754C4B: g_object_newv (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== 23,560 bytes in 95 blocks are possibly lost in loss record 6,253 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D02D5: g_list_prepend (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0636: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1A88: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 24,448 bytes in 382 blocks are possibly lost in loss record 6,254 of 6,274
==4333==    at 0x4025016: realloc (vg_replace_malloc.c:525)
==4333==    by 0x47DB00E: g_realloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F623E: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F6DB7: g_string_insert_len (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F7157: g_string_append_len (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C19BC: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C1BD3: g_build_filename (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x4148285: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41483E6: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 24,576 bytes in 1 blocks are possibly lost in loss record 6,256 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3A31: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3CB2: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41485A9: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 24,576 bytes in 1 blocks are possibly lost in loss record 6,257 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3A31: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3CB2: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B064E: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1A88: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 25,792 bytes in 104 blocks are possibly lost in loss record 6,258 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D02D5: g_list_prepend (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AF99F: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D99AE: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4753B05: ??? (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== 30,008 bytes in 121 blocks are possibly lost in loss record 6,259 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D02D5: g_list_prepend (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1B73: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 33,232 bytes in 134 blocks are possibly lost in loss record 6,260 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AEA7B: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1B54: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 38,443 bytes in 1,779 blocks are possibly lost in loss record 6,261 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F3D68: g_strdup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AEA85: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1B54: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4753B05: ??? (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== 43,440 bytes in 2 blocks are possibly lost in loss record 6,262 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x46A307C: ??? (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46A714A: ft_mem_qalloc (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46A8E52: ft_mem_alloc (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46A8FA0: ft_mem_qrealloc (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46A97AE: ft_mem_realloc (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46DD0CF: ??? (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46E1396: ??? (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46B7DF4: ??? (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46A948C: ??? (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46ABB78: FT_Open_Face (in /usr/lib/libfreetype.so.6.3.22)
==4333==    by 0x46ACCBE: FT_New_Face (in /usr/lib/libfreetype.so.6.3.22)
==4333== 
==4333== 48,384 bytes in 96 blocks are possibly lost in loss record 6,263 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AE9BB: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B19FA: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 48,888 bytes in 97 blocks are possibly lost in loss record 6,264 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AEB12: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1321: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 74,088 bytes in 147 blocks are possibly lost in loss record 6,266 of 6,274
==4333==    at 0x4024106: memalign (vg_replace_malloc.c:581)
==4333==    by 0x4024163: posix_memalign (vg_replace_malloc.c:709)
==4333==    by 0x47F09C1: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F1222: g_slice_alloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3FC8: g_hash_table_new_full (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AEB50: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1321: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 82,199 bytes in 4,578 blocks are possibly lost in loss record 6,267 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F58D3: g_strndup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41478BA: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4148569: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149678: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 90,240 bytes in 36 blocks are possibly lost in loss record 6,268 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3A31: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3CB2: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41485CE: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149678: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 103,984 bytes in 5,831 blocks are possibly lost in loss record 6,269 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F58D3: g_strndup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41478BA: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4148569: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 104,261 bytes in 5,829 blocks are possibly lost in loss record 6,270 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F58D3: g_strndup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41478BA: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4148569: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41483E6: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 112,512 bytes in 52 blocks are possibly lost in loss record 6,271 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3A31: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3CB2: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41485CE: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4128022: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 112,512 bytes in 52 blocks are possibly lost in loss record 6,272 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3A31: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C3CB2: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41485CE: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41483E6: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149666: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4149DFB: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B701: gtk_icon_theme_lookup_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x414B827: gtk_icon_theme_load_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41456E6: gtk_icon_set_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x42B57B4: gtk_widget_render_icon (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333== 
==4333== 115,550 bytes in 1,559 blocks are possibly lost in loss record 6,273 of 6,274
==4333==    at 0x4024F20: malloc (vg_replace_malloc.c:236)
==4333==    by 0x47DB243: g_malloc (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47F3D68: g_strdup (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AE9C5: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B19FA: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4753B05: ??? (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== 149,664 bytes in 1,559 blocks are possibly lost in loss record 6,274 of 6,274
==4333==    at 0x402425F: calloc (vg_replace_malloc.c:467)
==4333==    by 0x47DB13B: g_malloc0 (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47C401F: g_hash_table_new_full (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47AEB50: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B1321: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47D8AEE: ??? (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47DA496: g_markup_parse_context_parse (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0217: g_bookmark_file_load_from_data (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x47B0380: g_bookmark_file_load_from_file (in /lib/libglib-2.0.so.0.2400.1)
==4333==    by 0x41DC86D: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x41DF92A: ??? (in /usr/lib/libgtk-x11-2.0.so.0.2000.1)
==4333==    by 0x4753B05: ??? (in /usr/lib/libgobject-2.0.so.0.2400.1)
==4333== 
==4333== LEAK SUMMARY:
==4333==    definitely lost: 2,976 bytes in 11 blocks
==4333==    indirectly lost: 11,540 bytes in 576 blocks
==4333==      possibly lost: 2,011,749 bytes in 33,808 blocks
==4333==    still reachable: 483,654 bytes in 6,221 blocks
==4333==         suppressed: 0 bytes in 0 blocks
==4333== Reachable blocks (those to which a pointer was found) are not shown.
==4333== To see them, rerun with: --leak-check=full --show-reachable=yes

```

If I run the app but never run that function, the leak summary looks like this:

```

LEAK SUMMARY:
==4342==    definitely lost: 1,952 bytes in 8 blocks
==4342==    indirectly lost: 7,500 bytes in 376 blocks
==4342==      possibly lost: 336,282 bytes in 2,591 blocks
==4342==    still reachable: 318,828 bytes in 4,651 blocks
==4342==         suppressed: 0 bytes in 0 blocks

```

The funny thing is also, that if I use that function more than just 1 times (the function that creates dialog), the memory usage remains the same and there are no additional leaks. Most of the time when a function causes a leak, the leak also occurs any other time when you call that function, but this time it's different.
Usually I could trace down the leaks with valgrind, but this time I'm kinda lost.

---

### Post by hakermania on 2012-01-17
Well, I have the feeling that OpenFileDialogs in general are not so well designed, my case is very similar to yours.

---

### Post by Petrolea on 2012-01-17
> **hakermania said:**
> Well, I have the feeling that OpenFileDialogs in general are not so well designed, my case is very similar to yours.

I'm glad I'm not the only one. Hope anyone can find a solution for this.

---

### Post by pbrane on 2012-01-17
Why not create the file chooser once and reuse it?

Have a look at this. Question 1.5 in particular.
[http://www.gtk.org/api/2.6/gtk/gtk-question-index.html]("http://www.gtk.org/api/2.6/gtk/gtk-question-index.html")

---

### Post by Petrolea on 2012-01-17
> **pbrane said:**
> Why not create the file chooser once and reuse it?

Have a look at this. Question 1.5 in particular.
[http://www.gtk.org/api/2.6/gtk/gtk-question-index.html]("http://www.gtk.org/api/2.6/gtk/gtk-question-index.html")

I tried to reuse it, still no luck. I also tried to use the technique described in that link, this is the code and it still causes a massive memory usage jump:

```

void load_file(GtkButton *button, Objects *data)
{
	GtkWidget *dialog;
	dialog = gtk_file_chooser_dialog_new ("Open File", GTK_WINDOW(data -> window1), GTK_FILE_CHOOSER_ACTION_OPEN, GTK_STOCK_CANCEL, GTK_RESPONSE_CANCEL, GTK_STOCK_OPEN, GTK_RESPONSE_ACCEPT, NULL);
	
	g_object_ref (dialog); 
	gtk_object_sink (GTK_OBJECT(dialog));
	
	if (gtk_dialog_run (GTK_DIALOG (dialog)) == 1)
	{
		filename = gtk_file_chooser_get_filename (GTK_FILE_CHOOSER (dialog));
		FILE *file = fopen(filename, "r");
		
		gtk_text_buffer_set_text(GTK_TEXT_BUFFER(data -> textbuffer1), "", -1);
		gtk_text_buffer_get_iter_at_offset(data -> textbuffer1, &data -> start, -1);
		
		char line[50];
		while(fgets(line, sizeof(line), file) != NULL)
		{
			gtk_text_buffer_get_iter_at_offset(data -> textbuffer1, &data -> start, -1);
			gtk_text_buffer_insert(data -> textbuffer1, &data -> start, line, -1);
		}
				
		fclose(file);
		changed = false;
	}
	
	gtk_widget_destroy (dialog); 
	g_object_unref (dialog);
}

```

And the last thing I tried was to create FileChooserDialog with GLADE and then use it inside my program, but that caused the usage to be this high when I simply started a program.

**My conclusion is that FileChooserDialog simply uses that much memory.**

---

