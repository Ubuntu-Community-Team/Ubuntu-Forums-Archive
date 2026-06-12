---
title: "[C] Weird crash on PQgetResult"
date: 2010-06-18
forum: Programming Talk
---

### Post by martijntje on 2010-06-18
I get some weird crashes when trying to run some database queries through libpq. The strange thing is that sometimes it doesn't crash  at all and when it crashes it always crashes at a different place.

The code:

```
long	load_group(struct nntp_group *group)
{
	char		db_query[1024];
	PGresult	*db_result;
	int		col_group_id;
	long		col_highest, article_count;

	sprintf(db_query, "SELECT * FROM load_group('%s', %ld, %ld);", group->group_name, group->lowest, group->highest);

	db_result	=	PQexec(db_conn, db_query);

	if (PQresultStatus(db_result) == PGRES_TUPLES_OK) {
		// retrieve column numbers
		col_group_id	=	PQfnumber(db_result, "group_id");
		col_highest	=	PQfnumber(db_result, "highest");

		group->db_id	=	atoi(PQgetvalue(db_result, 0, col_group_id));
		group->lowest	=	atol(PQgetvalue(db_result, 0, col_highest));

		article_count	=	group->highest - group->lowest + 1;

		PQclear(db_result);
		return article_count;
	} else {
		return -1;
	}
}
```

I have checked which queries are being ran, and the queries are fine, even the ones it crashes on. A backtrace of the problem gose like this:

```
Program received signal SIGSEGV, Segmentation fault.
0x001bc83e in ?? () from /lib/tls/i686/cmov/libc.so.6
(gdb) backtrace 
#0  0x001bc83e in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0x001beafd in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0x001c0f9c in malloc () from /lib/tls/i686/cmov/libc.so.6
#3  0x00139617 in ?? () from /usr/lib/libpq.so.5
#4  0x0014531f in ?? () from /usr/lib/libpq.so.5
#5  0x0013a868 in ?? () from /usr/lib/libpq.so.5
#6  0x0013c541 in PQgetResult () from /usr/lib/libpq.so.5
#7  0x0013c800 in ?? () from /usr/lib/libpq.so.5
#8  0x08048cdf in load_group (group=0x8066468) at db.c:29
#9  0x08049293 in nntp_process_group (groups=0x804c038, group_line=0x80558dd "msn.forums.outdoors.recreation.general") at nntp.c:138
#10 0x0804913a in nntp_list (connection=0x8055890, groups=0x804c038) at nntp.c:105
#11 0x080495bb in main () at main.c:48
```

For your information, db_conn is a PGconn pointer declared elsewhere. The program always runs a number of queries correctly before crashing.

---

### Post by gmargo on 2010-06-18
(Un)Educated guess: PQresultStatus() will return PGRES_TUPLES_OK if the PQexec() SQL query was successful, even if the number of rows returned is zero.  You don't account for the zero rows case.

---

### Post by martijntje on 2010-06-18
> **gmargo said:**
> (Un)Educated guess: PQresultStatus() will return PGRES_TUPLES_OK if the PQexec() SQL query was successful, even if the number of rows returned is zero.  You don't account for the zero rows case.

Ehm, I get a SIGSEGV on the line before, so it doesn't actually get to PQresultStatus... ;)

---

### Post by Some Penguin on 2010-06-18
It's dying inside malloc(), so that tells you that you've got some memory corruption going on.  Somewhere, you're probably writing bytes where you shouldn't be or the like -- consider using something like Purify or Electric Fence to help you find out where.

Other notes -
- You're not validating whether or not the string will fit within the string buffer.
- You're not checking for and escaping fun characters like ; and ' in the string.
These may or may not be issues in practice; if the object can be constructed by a user then it's a problem.

---

