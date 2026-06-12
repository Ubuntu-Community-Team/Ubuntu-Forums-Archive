---
title: "ircu compiling issues"
date: 2010-09-14
forum: Packaging and Compiling Programs
---

### Post by cyclobs on 2010-09-14
trying to compile ircu server and i keep getting this error. any ideas?

```
Building config...
make[1]: Entering directory `/home/cyclobs/irc-servers/ircu2.10.10/config'
make[1]: Nothing to be done for `build'.
make[1]: Leaving directory `/home/cyclobs/irc-servers/ircu2.10.10/config'
Building ircd...
make[1]: Entering directory `/home/cyclobs/irc-servers/ircu2.10.10/ircd'
/bin/sh version.c.SH
Extracting ircd/version.c ...
gcc  -I../include -c version.c
gcc  IPcheck.o bsd.o channel.o class.o common.o crule.o dbuf.o fileio.o ircd.o list.o map.o match.o numnicks.o opercmds.o packet.o parse.o querycmds.o random.o res.o runmalloc.o s_auth.o s_bsd.o s_conf.o s_debug.o s_err.o s_misc.o s_numeric.o s_ping.o s_serv.o s_user.o send.o sprintf_irc.o support.o userload.o whocmds.o whowas.o hash.o version.o   -o ircd
res.o: In function `query_name':
res.c:(.text+0xadd): undefined reference to `__res_mkquery'
res.o: In function `proc_answer':
res.c:(.text+0xe55): undefined reference to `__dn_skipname'
res.c:(.text+0xeb4): undefined reference to `__dn_expand'
res.c:(.text+0x112b): undefined reference to `__dn_expand'
collect2: ld returned 1 exit status
make[1]: *** [ircd] Error 1
make[1]: Leaving directory `/home/cyclobs/irc-servers/ircu2.10.10/ircd'
```

---

