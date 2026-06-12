---
title: "Odd linking problem"
date: 2010-06-24
forum: Programming Talk
---

### Post by Vadi on 2010-06-24
Can anyone spot what is wrong with this?

```
$ gcc -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/json-glib-1.0  -pthread -ljson-glib-1.0 -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0 -I./deps/Linux/ -I. -L./deps/Linux/ -L. -ggdb -Wall -o bot main.c -lz -ldl
/tmp/ccjGwQ3I.o: In function `parse_new_json':
/home/vadi/Systems/vadi-2.1/main.c:3067: undefined reference to `json_parser_new'
/home/vadi/Systems/vadi-2.1/main.c:3069: undefined reference to `json_parser_load_from_data'
/home/vadi/Systems/vadi-2.1/main.c:3075: undefined reference to `json_parser_get_root'
/tmp/ccjGwQ3I.o: In function `get_name':
/home/vadi/Systems/vadi-2.1/main.c:3082: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3082: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3085: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3085: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3087: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3087: undefined reference to `json_object_get_string_member'
/tmp/ccjGwQ3I.o: In function `handle_gmcp':
/home/vadi/Systems/vadi-2.1/main.c:3112: undefined reference to `json_node_get_node_type'
/home/vadi/Systems/vadi-2.1/main.c:3117: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3117: undefined reference to `json_object_get_int_member'
/home/vadi/Systems/vadi-2.1/main.c:3118: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3118: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3120: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3120: undefined reference to `json_object_get_object_member'
/home/vadi/Systems/vadi-2.1/main.c:3120: undefined reference to `json_object_get_members'
/home/vadi/Systems/vadi-2.1/main.c:3144: undefined reference to `json_node_get_array'
/home/vadi/Systems/vadi-2.1/main.c:3145: undefined reference to `json_array_foreach_element'
collect2: ld returned 1 exit status

```

A bit out of ideas myself :/

---

### Post by ju2wheels on 2010-06-25
You have to add all your custom .c files after main.c in the compile command as well...

---

### Post by Zugzwang on 2010-06-25
When linking in Linux, the order of the libraries is important. I would suggest trying to put "main.c" before "-ljson-glib-1.0", but I'm not sure if that helps.

---

### Post by Vadi on 2010-06-25
Other .c's are build as libraries so it doesn't matter... changing the order didn't matter as well:

```
$ gcc main.c `pkg-config --cflags --libs glib-2.0 gthread-2.0 json-glib-1.0 gobject-2.0` -I./deps/Linux/ -I. -L./deps/Linux/ -L. -ggdb -Wall -o bot -lz -ldl
/tmp/ccjw9dFA.o: In function `parse_new_json':
/home/vadi/Systems/vadi-2.1/main.c:3065: undefined reference to `json_parser_new'
/home/vadi/Systems/vadi-2.1/main.c:3067: undefined reference to `json_parser_load_from_data'
/home/vadi/Systems/vadi-2.1/main.c:3073: undefined reference to `json_parser_get_root'
/tmp/ccjw9dFA.o: In function `get_name':
/home/vadi/Systems/vadi-2.1/main.c:3080: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3080: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3083: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3083: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3085: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3085: undefined reference to `json_object_get_string_member'
/tmp/ccjw9dFA.o: In function `handle_gmcp':
/home/vadi/Systems/vadi-2.1/main.c:3110: undefined reference to `json_node_get_node_type'
/home/vadi/Systems/vadi-2.1/main.c:3115: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3115: undefined reference to `json_object_get_int_member'
/home/vadi/Systems/vadi-2.1/main.c:3116: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3116: undefined reference to `json_object_get_string_member'
/home/vadi/Systems/vadi-2.1/main.c:3118: undefined reference to `json_node_get_object'
/home/vadi/Systems/vadi-2.1/main.c:3118: undefined reference to `json_object_get_object_member'
/home/vadi/Systems/vadi-2.1/main.c:3118: undefined reference to `json_object_get_members'
/home/vadi/Systems/vadi-2.1/main.c:3142: undefined reference to `json_node_get_array'
/home/vadi/Systems/vadi-2.1/main.c:3143: undefined reference to `json_array_foreach_element'
collect2: ld returned 1 exit status

```

---

### Post by Vadi on 2010-06-25
Turns out I had a bad copy of the library in the compile folder.

---

