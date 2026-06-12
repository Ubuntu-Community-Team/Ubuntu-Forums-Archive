---
title: "[S]QL [P]owered Awk (SPAWK)"
date: 2009-09-30
forum: Programming Talk
---

### Post by panos1962 on 2009-09-30
Hello everybody!

I'm new to Ubuntu forums, but I've been developing programs in UNIX or Linux operating systems for more than 20 years. I'm the system administrator of the main database in City Hall of Thessaloniki, Greece. The database contains about 100,000,000 rows over more than 1,000 tables and is based on Unify's DataServer RDBMS.

About 6 years ago I developed a library of **awk** functions in order to use **SQL** queries from within awk programs and that was proved to be a very successful project. However, Unify's DataServer is not a popular DBMS and is a proprietary licencensed product, so last year I've developed a GNU/awk (gawk), so called, "extension" library, named **libspawk**, which does the same job over MySQL databases. It's an elegant collection of awk functions in order to manipulate MySQL databases from within gawk programs. To give an example, the following gawk program prints all the tables and columns of any MySQL database:

```

BEGIN {
    extension("libspawk.so", "dlload")
    SPAWKINFO["database"] = "information_schema"
    SPAWKINFO["OFS"] = "."
    spawk_query("SELECT TABLE_SCHEMA, TABLE_NAME FROM TABLES")
    spawk_select()
    while (spawk_data(table)) {
        print table[0]
        spawk_query("SELECT COLUMN_NAME FROM COLUMNS " \
            "WHERE TABLE_SCHEMA = '" table[1] \
            "' AND TABLE_NAME = '" table[2] "'")
            spawk_select()
            while (spawk_data(column))
                print "\t" column[1]
    }

    exit(0)
}

```

I've managed to upload the whole project in GoogleCode (the codes are also included) under Mercurial VCS and you can visit [http://code.google.com/p/spawk/](http://code.google.com/p/spawk/) to have a detailed and comprehensive view of SPAWK. Anybody can download the sources and install the library to any Linux distro using MySQL databases. The installation process is straightforward but there are too many steps and the downloader must have some programming experience. I believe it's worth including the compiled version (just a small single object shared library) in a future Ubuntu (or other) distro. Please let me know if you find that idea interesting enough to proceed.

Thank you all,
Panos

---

### Post by lhowaf on 2009-09-30
Panos,
That looks like an interesting library. I'm not quite sure if I would use it since there are other MySQL manipulation tools available. However, I think this is one of those tools that would be very useful under the right conditions.
Your hard work and generosity are very much appreciated and I look forward to trying out your handiwork.
By the way, I admire anybody who is multi-lingual and, as a way of making up for my being mono-lingual, I've attached a corrected version of your post text.
Cheers.

---

