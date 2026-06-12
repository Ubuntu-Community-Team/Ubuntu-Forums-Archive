---
title: "C language, problem with accesing to structure"
date: 2006-03-14
forum: Programming Talk
---

### Post by tomcio on 2006-03-14
Hi!

I have very strange problem with my program. 
Firstly I'll say a few words about problem. I have function ***GSList *execute_sql_query_and_return_data (gchar *sql_query, gint mode)***. I pass to it string with SQL query, which I want execute, and integer variable *mode*, which specify type of structures, which will be created in this function. 
Now in this part of those function:
[INDENT][SIZE="1"]while (1)	{
					[INDENT]code = sqlite3_step (db_row);
					if (code == 21 || code == 101)
						break;
					
					StructEditDbList	*data;
					data = g_new (StructEditDbList, 1);
					data->id = sqlite3_column_int (db_row, 0);
					g_stpcpy (data->name, sql_query_revert ((gchar *)sqlite3_column_text (db_row, 1)));
					printf (">> %s\n", data->name);
					struct_pointers = g_slist_append (struct_pointers, GINT_TO_POINTER (&data));
[/INDENT]				}[/SIZE][/INDENT]
In this loop we get returned rows from database (there are two rows), then we create new structure *StructEditDbList*, and insert adress of those structure in lists (GSList). After it we return GSList with adresses to structures with data.

In other function we have this code:
[SIZE="1"][INDENT]
GSList *data_list = execute_sql_query_and_return_data (sql_query, STRUCT_EDIT_DB_LIST);
	
	items_number = g_slist_length (data_list);
        printf ("|| %d", items_number);
	while (i < items_number)	{
		[INDENT]StructEditDbList	*data;
		data = (StructEditDbList*) GPOINTER_TO_INT (g_slist_nth_data (data_list, i));
		printf (">>> %s\n", data->name);
		i++;[/INDENT]
	}[/INDENT][/SIZE]

I execute functions *execute_sql_query_and_return_data* and I want to get adresses to structures with data form returned list and then I wanto to acces to data in structures.

Like you see there are some *printf* functions in my code, which should print string stored in structures. I function ***execute_sql_query_and_return_data*** they work fine:
[INDENT][SIZE="1"]>> Jan Nowak
>> Jan Kowalski[/SIZE][/INDENT]
but in second function, which is trying to acces to tthe same structures by adresses in returned GList I see this:
[SIZE="1"][INDENT]>>> V
>>>        i| VVV[/INDENT][/SIZE]

Can someone tell my where is a bug?!

If you want whole code just write and i send it.

---

