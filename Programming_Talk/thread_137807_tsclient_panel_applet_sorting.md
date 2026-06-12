---
title: "tsclient panel applet sorting"
date: 2006-02-28
forum: Programming Talk
---

### Post by Bil-E-daKid on 2006-02-28
Hey there guys,

I'm wanting to add a sort routine into the tsclient panel applet.  I think I've found the function where the rdp files are read into an array but I have no knowledge of GTK+ and wether there is some kind of built in sort function available.

Here's the code:

> /***************************************
*                                      *
*   rdp_files_to_hash                  *
*                                      *
***************************************/

GHashTable* rdp_files_to_hash(void){
  gchar *path_name;
  GHashTable *hash;
	
  hash = g_hash_table_new (g_str_hash, g_str_equal);
	
  #ifdef TSCLIENT_DEBUG
  printf ("rdp_files_to_list\n");
  #endif

  path_name = g_build_path ("/", g_get_home_dir (), ".tsclient", NULL);
  read_dir (path_name, hash, "-1");

/*
  g_sort (hash);
*/

  g_free (path_name);
  return hash;
};

(The g_sort (hash); part is what I've put in there as I believe that's where I need to add sorting code).

I should preface this all by saying that, though I trained as a C programmer some 12 years ago, it's been a while since I did anything with it.  Please forgive my lack of knowledge and rusty skills - any help would be most appreciated.

Many thanks

---

### Post by harp2812 on 2007-09-07
Glad to know I'm not the only one looking to do this (albeit a year later)... did you have any luck with the sort function?

If not, I'm thinking about trying my hand at making a patch... Although I'm only a SysAdmin and it's been a few years since my programming back in college, so I doubt it'll be pretty. :)

---

### Post by Bil-E-daKid on 2007-09-07
Hey there harp2812 - unfortunately, I got no further than the above (best intentions and all) and just learned to live with it.

Go for it - I'd be interested to see what the code looks like - and I don't think the original author has done anything else with that either.

have fun!

---

