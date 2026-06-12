---
title: "Compile errors"
date: 2013-12-23
forum: Packaging and Compiling Programs
---

### Post by vadim_omeltchenko on 2013-12-23
I am not C developer and just need to compile this program for a project I'm working on, but getting the following errors:

```

$ gcc `pkg-config --cflags --libs gnome-keyring-1 glib-2.0` -o gnome-keyring-query gnome-keyring-query.c
/tmp/ccm7KQBg.o: In function `main':
gnome-keyring-query.c:(.text+0x2d): undefined reference to `g_set_application_name'
gnome-keyring-query.c:(.text+0x55): undefined reference to `g_ascii_strcasecmp'
gnome-keyring-query.c:(.text+0x7a): undefined reference to `g_ascii_strcasecmp'
gnome-keyring-query.c:(.text+0x12e): undefined reference to `g_free'
gnome-keyring-query.c:(.text+0x13a): undefined reference to `g_malloc'
gnome-keyring-query.c:(.text+0x1ad): undefined reference to `g_free'
/tmp/ccm7KQBg.o: In function `get_password':
gnome-keyring-query.c:(.text+0x1d5): undefined reference to `g_array_new'
gnome-keyring-query.c:(.text+0x1ee): undefined reference to `gnome_keyring_attribute_list_append_string'
gnome-keyring-query.c:(.text+0x204): undefined reference to `gnome_keyring_attribute_list_append_string'
gnome-keyring-query.c:(.text+0x219): undefined reference to `gnome_keyring_find_items_sync'
gnome-keyring-query.c:(.text+0x228): undefined reference to `gnome_keyring_attribute_list_free'
gnome-keyring-query.c:(.text+0x25f): undefined reference to `g_strdup'
gnome-keyring-query.c:(.text+0x270): undefined reference to `gnome_keyring_found_list_free'
/tmp/ccm7KQBg.o: In function `set_password':
gnome-keyring-query.c:(.text+0x29a): undefined reference to `g_array_new'
gnome-keyring-query.c:(.text+0x2b3): undefined reference to `gnome_keyring_attribute_list_append_string'
gnome-keyring-query.c:(.text+0x2c9): undefined reference to `gnome_keyring_attribute_list_append_string'
gnome-keyring-query.c:(.text+0x2fb): undefined reference to `gnome_keyring_item_create_sync'
gnome-keyring-query.c:(.text+0x30a): undefined reference to `gnome_keyring_attribute_list_free'
collect2: ld returned 1 exit status



```




All the libraries seem to be there.. h files too... Please help!

---

### Post by vadim_omeltchenko on 2013-12-23
never mind, solved by placing -l for each library at the end of the command line...

---

