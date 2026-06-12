---
title: "ache2 mod-myvhost"
date: 2010-04-23
forum: Programming Talk
---

### Post by Spikerok on 2010-04-23
Did some one manage to get apache2 2.2 module "mod-myvhost" to work on Ubuntu 9.10?
When I tried to install it, I get error with 'adsx' or some thing like that, about it not installed on my system.
If not, are their some substitutes for this module.
Other path is to make 'mod_shapvh' to work with apache2.2

when i tried to install mod-myvhost i get next problem:

[PHP]
# make
apxs2 -c -Wc,-W -Wc,-Wall `mysql_config --include` -DWITH_PHP -DWITH_CACHE -DDEBUG -W,l`mysql_config --libs` mod_myvhost.c mod_myvhost_cache.c escape_sql.c
apxs:Error: Unknown option: r.
apxs:Error: Unknown option: d.
apxs:Error: Unknown option: y.
Usage: apxs -g [-S <var>=<val>] -n <modname>
       apxs -q [-S <var>=<val>] <query> ...
       apxs -c [-S <var>=<val>] [-o <dsofile>] [-D <name>[=<value>]]
               [-I <incdir>] [-L <libdir>] [-l <libname>] [-Wc,<flags>]
               [-Wl,<flags>] [-p] <files> ...
       apxs -i [-S <var>=<val>] [-a] [-A] [-n <modname>] <dsofile> ...
       apxs -e [-S <var>=<val>] [-a] [-A] [-n <modname>] <dsofile> ...
make: *** [mod_myvhost.so] Error 1
[/PHP]

---

### Post by Spikerok on 2010-05-08
bump

---

