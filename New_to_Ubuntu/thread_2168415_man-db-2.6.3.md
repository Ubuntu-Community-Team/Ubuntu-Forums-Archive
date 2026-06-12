---
title: "man-db-2.6.3"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by pavan_kumar2 on 2013-08-17
Hi Trying to install man-db-2.6.3 giving the following errors while configuration can anyone help?

checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);
checking for po4a... no
checking for an ANSI C-conforming const... yes
checking for inline... (cached) inline
checking for pid_t... (cached) yes
checking for uid_t in sys/types.h... (cached) yes
checking for size_t... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libpipeline... yes
checking gdbm.h usability... no
checking gdbm.h presence... no
checking for gdbm.h... no
checking db5/db_185.h usability... no
checking db5/db_185.h presence... no
checking for db5/db_185.h... no
checking db_185.h usability... no
checking db_185.h presence... no
checking for db_185.h... no
checking db4/db_185.h usability... no
checking db4/db_185.h presence... no
checking for db4/db_185.h... no
checking for db_185.h... (cached) no
checking db3/db_185.h usability... no
checking db3/db_185.h presence... no
checking for db3/db_185.h... no
checking for db_185.h... (cached) no
checking for db_185.h... (cached) no
checking db2/db_185.h usability... no
checking db2/db_185.h presence... no
checking for db2/db_185.h... no
checking db2_185.h usability... no
checking db2_185.h presence... no
checking for db2_185.h... no
checking db/db.h usability... no
checking db/db.h presence... no
checking for db/db.h... no
checking db.h usability... no
checking db.h presence... no
checking for db.h... no
checking db1/db.h usability... no
checking db1/db.h presence... no
checking for db1/db.h... no
checking ndbm.h usability... no
checking ndbm.h presence... no
checking for ndbm.h... no
configure: error: Fatal: no supported database library/header found

---

### Post by pavan_kumar2 on 2013-08-17
so it was meant to be ./configure

---

