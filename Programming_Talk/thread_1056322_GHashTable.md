---
title: "GHashTable"
date: 2009-01-31
forum: Programming Talk
---

### Post by nitro_n2o on 2009-01-31
Hi.. i was wondering does anybody know of a place that i can get code samples of how to use the GHashTable from glib? 

thx a lot

---

### Post by nitro_n2o on 2009-01-31
here i go [http://www.ibm.com/developerworks/edu/l-dw-linux-glib-i.html](http://www.ibm.com/developerworks/edu/l-dw-linux-glib-i.html)

---

### Post by bruce89 on 2009-01-31
Sort of ported from my Vala test.

```

#include <stdio.h>

#include <glib.h>

static GHashTable *table;

static void
add_data (void)
{
	gchar *key;
	gchar *value;

	key = g_new (gchar, 1);
	value = g_new (gchar, 1);

	printf ("Input the key ");
	scanf ("%s", key);
	printf ("Input the value ");
	scanf ("%s", value);

	g_hash_table_insert (table, g_strdup (key), g_strdup (value));
}

static void
print_data (gchar *key, gchar *value)
{
	printf ("%s:%s\n", key, value);
}

int
main (void)
{
	table = g_hash_table_new_full (g_str_hash, g_str_equal, g_free, g_free);

	while (1)
	{
		add_data ();
		g_hash_table_foreach (table, (GHFunc) print_data, NULL);
	}

	return 0;
}

```

---

### Post by nitro_n2o on 2009-02-06
interesting :) 

does anybody know how to use the table for custom datatypes? 

thanks alot

---

### Post by bruce89 on 2009-02-06
> **nitro_n2o said:**
> does anybody know how to use the table for custom datatypes?

Change the third and forth arguments to *g_hash_table_new ()* to whatever free functions the key and values need. Everything else is the same, but be aware that the hash table doesn't store a copy of its contents, all it stores are pointers to things.

---

