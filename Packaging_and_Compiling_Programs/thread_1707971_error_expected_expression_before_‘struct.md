---
title: "error: expected expression before ‘struct"
date: 2011-03-16
forum: Packaging and Compiling Programs
---

### Post by dasgenie on 2011-03-16
root@ubuntu:/usr/src/linux-2.6.38-rc1/fs/btrfs# gcc dedup.c
dedup.c: In function ‘hash_tree_insert’:
dedup.c:89: error: expected expression before ‘struct’
dedup.c: In function ‘file_tree_insert’:
dedup.c:150: error: expected expression before ‘struct’
dedup.c: In function ‘file_tree_search’:
dedup.c:172: error: expected expression before ‘struct’
dedup.c: In function ‘hash_file’:
dedup.c:258: error: expected expression before ‘struct’
dedup.c: In function ‘print_stats’:
dedup.c:286: error: expected expression before ‘struct’
dedup.c: In function ‘free_hash_tree’:
dedup.c:304: error: expected expression before ‘struct’
dedup.c: In function ‘free_file_tree’:


any idea why this error is occurring .

---

