---
title: "Compiling BSD Version of ar - Help with Error"
date: 2011-12-15
forum: Packaging and Compiling Programs
---

### Post by dodle on 2011-12-15
I'm trying to compile the BSD version of [color=blue]ar[/color] (the archiver). I've already had to modify the source a bit but I am still getting one error that I'm not sure how to deal with:

> In file included from util.c:38:0:
ar.h:100:2: error: expected specifier-qualifier-list before &#8216;uint32_t&#8217;

ar.h:100:
[php]uint32_t s_cnt;  /* current number of symbols. */[/php]

ar.h:97-107:
[php]/*
 * Fields for the archive symbol table.
 */
uint32_t s_cnt;  /* current number of symbols. */
uint32_t *s_so;  /* symbol offset table. */
size_t s_so_cap;  /* capacity of so table buffer. */
char *s_sn;  /* symbol name table */
size_t s_sn_cap;  /* capacity of sn table buffer. */
size_t s_sn_sz;  /* current size of sn table. */
/* Current member's offset (relative to the end of pseudo members.) */
off_t rela_off;[/php]

I don't know what this error means.

**----- EDIT -----**
Okay, I gess it means that [color=blue]uint32_t[/color] isn't defined. Is there a header that I need to include or can I just change this to [color=blue]int[/color] or something?

**----- EDIT -----**
I've changed [color=blue]uint32_t[/color] to [color=blue]u_int32_t[/color] and that seems to have worked. Is this okay? But I'm still getting a couple of errors that I can't figure out:

> write.c: In function &#8216;write_archive&#8217;:
write.c:371:58: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
write.c: In function &#8216;write_cleanup&#8217;:
write.c:446:57: error: expected &#8216;;&#8217; before &#8216;{&#8217; token
make: *** [ar] Error 1

write.c:369-380:
[php]av = &bsdar->argv[i];

TAILQ_FOREACH_SAFE(obj, &bsdar->v_obj, objs, obj_temp) { // Offending line
	if ((bname = basename(*av)) == NULL)
		bsdar_errc(bsdar, EX_SOFTWARE, errno,
		    "basename failed");
	if (bsdar->options & AR_TR) {
		if (strncmp(bname, obj->name, _TRUNCATE_LEN))
			continue;
	} else
		if (strcmp(bname, obj->name) != 0)
			continue;[/php]

write.c:444-456:
[php]struct ar_obj		*obj, *objs, *obj_temp;

TAILQ_FOREACH_SAFE(obj, &bsdar->v_obj, objs, obj_temp) { // Offending line
	if (obj->fd == -1)
		free(obj->maddr);
	else
		if (obj->maddr != NULL && munmap(obj->maddr, obj->size))
			bsdar_warnc(bsdar, errno,
			    "can't munmap file: %s", obj->name);
	TAILQ_REMOVE(&bsdar->v_obj, obj, objs);
	free(obj->name);
	free(obj);
}[/php]

I've tried adding a ";" to the end of these lines but then I get linker errors concerning these items:

[php]TAILQ_FOREACH_SAFE(obj, &bsdar->v_obj, objs, obj_temp); {[/php]

> gcc -s -O9 ar.c read.c util.c write.c -larchive -lbz2 -lz -lelf -o ar
/tmp/ccl6UMGw.o: In function `main':
ar.c:(.text+0x1b8): undefined reference to `getprogname'
ar.c:(.text+0x2cf): undefined reference to `strlcpy'
/tmp/cc4HUBXa.o: In function `read_archive':
read.c:(.text+0x3ff): undefined reference to `strmode'
/tmp/cccdBeOw.o: In function `write_archive':
write.c:(.text+0xc90): undefined reference to `TAILQ_FOREACH_SAFE'
write.c:(.text+0x12db): undefined reference to `TAILQ_FOREACH_SAFE'
collect2: ld returned 1 exit status
make: *** [ar] Error 1

**----- EDIT -----**

Okay, I've changed these lines:

[php]TAILQ_FOREACH_SAFE(obj, &bsdar->v_obj, objs, obj_temp)[/php]

to this:

[php]TAILQ_FOREACH(obj, &bsdar->v_obj, objs)[/php]

Now I'm just getting some linking errors:

> gcc -s -O9 ar.c read.c util.c write.c -larchive -lbz2 -lz -lelf -o ar
/tmp/ccbLjPWw.o: In function `main':
ar.c:(.text+0x1b8): undefined reference to `getprogname'
ar.c:(.text+0x2cf): undefined reference to `strlcpy'
/tmp/cctKXduC.o: In function `read_archive':
read.c:(.text+0x3ff): undefined reference to `strmode'
collect2: ld returned 1 exit status
make: *** [ar] Error 1

**----- EDIT -----**

I've figured another thing, these functions are part of the standard C library, but they have different names under BSD and GNU Linux. I've figured out that [color=blue]strlcpy[/color] and [color=blue]strmode[/color] are both from "string.h" and [color=blue]getprogname[/color] is from "stdlib.h". [color=blue]strlcpy[/color] under GNU Linux is called [color=blue]strncpy[/color] but I haven't figured out what the other two are called.


**----- SOLVED -----**

Figured out that I needed to install [color=blue]libbsd-dev[/color] then point my [color=blue]include[/color] statements to its directory:

[php]#if defined (__linux__)
    #include <bsd/sys/cdefs.h>
    #include <endian.h>
    #include <bsd/sys/queue.h>
    #include <bsd/stdio.h>
    #include <bsd/stdlib.h>
    #include <bsd/string.h>
#else
    #include <sys/cdefs.h>
    #include <sys/endian.h>
    #include <sys/queue.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <string.h>
#endif

#include <sys/mman.h>
#include <sys/stat.h>
#include <archive.h>
#include <archive_entry.h>
#include <errno.h>
#include <fcntl.h>
#include <gelf.h>
#include <libgen.h>
#include <sysexits.h>[/php]

Now I have a working BSD version of ar:
> :/media/Data/Developing/bsdar/bsdar$ ./ar --version
BSD ar 1.0.2 - libarchive 2.8.4

**----- EDIT -----**

If anybody wants a copy I put it up here:
[https://sourceforge.net/projects/delugebuilds/files/utilities/bsdar](https://sourceforge.net/projects/delugebuilds/files/utilities/bsdar)
[https://sourceforge.net/projects/delugebuilds/files/source/linux/bsdar](https://sourceforge.net/projects/delugebuilds/files/source/linux/bsdar)

---

