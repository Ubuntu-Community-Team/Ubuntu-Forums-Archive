---
title: "dynamic arrays in structs c"
date: 2014-01-09
forum: Programming Talk
---

### Post by wingnut2626 on 2014-01-09
This is the starting code (from "Learn C the hard way").  The goal is supposed to be to knock out the MAX_DATA and MAX_LENGTH values, and have the corresponding items dynamically alloted.


```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

#define MAX_DATA 512
#define MAX_ROWS 100

struct Address {
    int id;
    int set;
    char name[MAX_DATA];
    char email[MAX_DATA];
};

struct Database {
    struct Address rows[MAX_ROWS];
};

struct Connection {
    FILE *file;
    struct Database *db;
};

void die(const char *message)
{
    if(errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

void Address_print(struct Address *addr)
{
    printf("%d %s %s\n",
            addr->id, addr->name, addr->email);
}

void Database_load(struct Connection *conn)
{
    int rc = fread(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to load database.");
}

struct Connection *Database_open(const char *filename, char mode)
{
    struct Connection *conn = malloc(sizeof(struct Connection));
    if(!conn) die("Memory error");

    conn->db = malloc(sizeof(struct Database));
    if(!conn->db) die("Memory error");

    if(mode == 'c') {
        conn->file = fopen(filename, "w");
    } else {
        conn->file = fopen(filename, "r+");

        if(conn->file) {
            Database_load(conn);
        }
    }

    if(!conn->file) die("Failed to open the file");

    return conn;
}

void Database_close(struct Connection *conn)
{
    if(conn) {
        if(conn->file) fclose(conn->file);
        if(conn->db) free(conn->db);
        free(conn);
    }
}

void Database_write(struct Connection *conn)
{
    rewind(conn->file);

    int rc = fwrite(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to write database.");

    rc = fflush(conn->file);
    if(rc == -1) die("Cannot flush database.");
}

void Database_create(struct Connection *conn)
{
    int i = 0;

    for(i = 0; i < MAX_ROWS; i++) {
        // make a prototype to initialize it
        struct Address addr = {.id = i, .set = 0};
        // then just assign it
        conn->db->rows[i] = addr;
    }
}

void Database_set(struct Connection *conn, int id, const char *name, const char *email)
{
    struct Address *addr = &conn->db->rows[id];
    if(addr->set) die("Already set, delete it first");

    addr->set = 1;
    // WARNING: bug, read the "How To Break It" and fix this
    char *res = strncpy(addr->name, name, MAX_DATA);
    // demonstrate the strncpy bug
    if(!res) die("Name copy failed");

    res = strncpy(addr->email, email, MAX_DATA);
    if(!res) die("Email copy failed");
}

void Database_get(struct Connection *conn, int id)
{
    struct Address *addr = &conn->db->rows[id];

    if(addr->set) {
        Address_print(addr);
    } else {
        die("ID is not set");
    }
}

void Database_delete(struct Connection *conn, int id)
{
    struct Address addr = {.id = id, .set = 0};
    conn->db->rows[id] = addr;
}

void Database_list(struct Connection *conn)
{
    int i = 0;
    struct Database *db = conn->db;

    for(i = 0; i < MAX_ROWS; i++) {
        struct Address *cur = &db->rows[i];

        if(cur->set) {
            Address_print(cur);
        }
    }
}

int main(int argc, char *argv[])
{
    if(argc < 3) die("USAGE: ex17 <dbfile> <action> [action params]");

    char *filename = argv[1];
    char action = argv[2][0];
    struct Connection *conn = Database_open(filename, action);
    int id = 0;

    if(argc > 3) id = atoi(argv[3]);
    if(id >= MAX_ROWS) die("There's not that many records.");

    switch(action) {
        case 'c':
            Database_create(conn);
            Database_write(conn);
            break;

        case 'g':
            if(argc != 4) die("Need an id to get");

            Database_get(conn, id);
            break;

        case 's':
            if(argc != 6) die("Need id, name, email to set");

            Database_set(conn, id, argv[4], argv[5]);
            Database_write(conn);
            break;

        case 'd':
            if(argc != 4) die("Need id to delete");

            Database_delete(conn, id);
            Database_write(conn);
            break;

        case 'l':
            Database_list(conn);
            break;
        default:
            die("Invalid action, only: c=create, g=get, s=set, d=del, l=list");
    }

    Database_close(conn);

    return 0;
}

```

Here is what I have.  I am just happy that I had something to compile, but of course it doesnt work!


```
/*
 * ex17.c
 * 
 * Copyright 2014 Ronald C. Reid <ronald@laptop1>
 * 
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 * MA 02110-1301, USA.
 * 
 * 
 */


#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>





struct Address {
    int id;
    int set;
    char *name;
    char *email;
};

struct Database {
    struct Address *rows;
};

struct Connection {
    FILE *file;
    struct Database *db;
};

int getTotal(const char *ptr)
{
    int i;
    int total = 0;
    for(i = 0; *ptr++ != '\0'; i++){
        total++;
    }
    
    return total;
}

int getTotalRows(struct Address *addr)
{
    int i;
    int total = 0;
    for(i = 0; !addr++; i++){
        total++;
    }
    return total;
}

void die(const char *message)
{
    if(errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

void Address_print(struct Address *addr)
{
    printf("%d %s %s\n",
            addr->id, addr->name, addr->email);
}

void Database_load(struct Connection *conn)
{
    int rc = fread(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to load database.");
}

struct Connection *Database_open(const char *filename, char mode)
{
    struct Connection *conn = malloc(sizeof(struct Connection));
    if(!conn) die("Memory error");

    conn->db = malloc(sizeof(struct Database));
    if(!conn->db) die("Memory error");

    if(mode == 'c') {
        conn->file = fopen(filename, "w");
    } else {
        conn->file = fopen(filename, "r+");

        if(conn->file) {
            Database_load(conn);
        }
    }

    if(!conn->file) die("Failed to open the file");

    return conn;
}

void Database_close(struct Connection *conn)
{
    if(conn) {
        if(conn->file) fclose(conn->file);
        if(conn->db) free(conn->db);
        free(conn);
    }
}

void Database_write(struct Connection *conn)
{
    rewind(conn->file);

    int rc = fwrite(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to write database.");

    rc = fflush(conn->file);
    if(rc == -1) die("Cannot flush database.");
}

[B]void Database_create(struct Connection *conn)
{
    int i = 0;
    int x;
    printf("How many items do you want in the database?\n");
    scanf("%d", &x);
    for(i = 0; i < x; i++) {
        printf("Run number %d\n", i);
        getchar();
        // make a prototype to initialize it
        struct Address addr = {.id = i, .set = 0};
        // then just assign it
        conn->db->rows[i] = addr;
    }
    printf("DEBUG.  Line 150.  I is now %d\n", i);
    getchar(); 
}[/B]

void Database_set(struct Connection *conn, int id, const char *name, const char *email)
{
    struct Address *addr = &conn->db->rows[id];
    if(addr->set) die("Already set, delete it first");

    addr->set = 1;
    // WARNING: bug, read the "How To Break It" and fix this
    char *res = strncpy(addr->name, name, getTotal(name));
    // demonstrate the strncpy bug
    if(!res) die("Name copy failed");

    res = strncpy(addr->email, email, getTotal(email));// need total function here to get size of email!
    if(!res) die("Email copy failed");
}

void Database_get(struct Connection *conn, int id)
{
    struct Address *addr = &conn->db->rows[id];

    if(addr->set) {
        Address_print(addr);
    } else {
        die("ID is not set");
    }
}

void Database_delete(struct Connection *conn, int id)
{
    struct Address addr = {.id = id, .set = 0};
    conn->db->rows[id] = addr;
}

void Database_list(struct Connection *conn)
{
    int i = 0;
    struct Database *db = conn->db;

    
    for(i = 0; i < getTotalRows(conn->db->rows); i++) {
        struct Address *cur = &db->rows[i];

        if(cur->set) {
            Address_print(cur);
        }
    }
}

int main(int argc, char *argv[])
{
    if(argc < 3) die("USAGE: ex17 <dbfile> <action> [action params]");

    char *filename = argv[1];
    char action = argv[2][0];
    struct Connection *conn = Database_open(filename, action);
    int id = 0;

    if(argc > 3) id = atoi(argv[3]);
    if(id >= getTotalRows(conn->db->rows)) die("There's not that many records.");//need that function to compute total number of rows here!

    switch(action) {
        case 'c':
            Database_create(conn);
            Database_write(conn);
            break;

        case 'g':
            if(argc != 4) die("Need an id to get");

            Database_get(conn, id);
            break;

        case 's':
            if(argc != 6) die("Need id, name, email to set");

            Database_set(conn, id, argv[4], argv[5]);
            Database_write(conn);
            break;

        case 'd':
            if(argc != 4) die("Need id to delete");

            Database_delete(conn, id);
            Database_write(conn);
            break;

        case 'l':
            Database_list(conn);
            break;
        default:
            die("Invalid action, only: c=create, g=get, s=set, d=del, l=list");
    }

    Database_close(conn);

    return 0;
}

```

Here is the error output when i try to run the program invoking the 'c' option:

```
ronald@laptop1 ~/c/exercise 17 $ ./ex17 db.db c
How many items do you want in the database?

4
Run number 0
Segmentation fault

```

I looked into the highlighted segment of code, but I dont see why it wont work....can someone point me in the right direction?

---

### Post by trent.josephsen on 2014-01-09
What do you think conn->db points to when you call Database_create(conn)?

BTW, it's probably better to use the alternate version of sizeof in malloc():
```
struct Connection *conn = malloc(sizeof *conn);
```
Less prone to maintenance-induced bugs.

---

### Post by wingnut2626 on 2014-01-09
I'm going to take a look at that.

---

### Post by wingnut2626 on 2014-01-11
Sorry it took me so long to reply.  Been busy over here.  It looks like conn->db is pointing to the first address in 
 conn->db = **malloc(sizeof(struct Database))**....am i right?

---

### Post by trent.josephsen on 2014-01-11
Yes, but that's not exactly what I was getting at. Perhaps I started wrong.

More to the point, conn->db is a proper pointer to memory legally obtained through malloc(), but you forget to initialize the contents of that memory. Take another look at the definition of "struct Database" in each case:

```
/* old version */
struct Database {
    struct Address rows[MAX_ROWS];
};
/* new version */
struct Database {
    struct Address *rows;
};
struct Database *db;
db = malloc(sizeof *db);
```

In the old version, db->rows is an array [MAX_ROWS] of struct Address, and the memory required to hold that many "struct Address"es is part of the "struct Database" object (*db). It doesn't matter that the memory is not initialized by malloc() because the first thing you do is initialize it.

In the new version, db->rows is no longer an entire array, but just a pointer. And the pointer is uninitialized because it sits in memory obtained by malloc(). (If you used calloc() instead, it would be NULL.) The first thing you do with that pointer,
```
    db->rows[0] = addr; /* slightly paraphrased */
```
dereferences it and tries to store the value "addr" at the memory location it "points" to. And fails, because db->rows probably doesn't point anywhere useful.

You might have noticed this bug because you don't call malloc() at any point after prompting the user for the size of the database, so your program can't tell if the user wants to create a database larger than available memory. However, and this is just a side note, checking the return value of malloc() is much less useful than checking whether scanf() succeeded -- on Linux at least, malloc() basically never fails, and programs that try to grab too much memory get killed when they try to use it, not when they call malloc(). (This is debatably a design flaw.) Checking malloc() is more or less optional; user input validation is mandatory. I would use fgets() and strtoul() instead of scanf(), which can't tell you what went wrong but only whether it succeeded or not (and also has that annoying habit of leaving spare newlines in the stream). But enough editorializing, I'll leave it to you to fix it and/or ask more questions as necessary.

---

### Post by ofnuts on 2014-01-12
> **trent.josephsen said:**
> on Linux, malloc() basically never fails, and programs that try to grab too much memory get killed when they try to use it, not when they call malloc(). (This is debatably a design flaw.)

IIRC this is true of other OSes (OS/2 and Windows) and would be due to lazy allocation (the OS finds it cannot fullfill its promises).

---

### Post by trent.josephsen on 2014-01-12
Thanks ofnuts, I was thinking that but I don't know enough about other OSes to verify.

(It's worth observing that C runs on many more platforms than just the three major "modern" OS families, and a defensive programming style would always check the return value of malloc() regardless.)

---

### Post by wingnut2626 on 2014-01-13
```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>





struct Address {
    int id;
    int set;
    char *name;
    char *email;
};

struct Database {
    struct Address *rows;
};

struct Connection {
    FILE *file;
    struct Database *db;
};

int getTotal(const char *ptr)
{
    int i;
    int total = 0;
    for(i = 0; *ptr++ != '\0'; i++){
        total++;
    }
    
    return total;
}

int getTotalRows(struct Address *addr)
{
    int i;
    int total = 0;
    for(i = 0; !addr++; i++){
        total++;
    }
    return total;
}

void die(const char *message)
{
    if(errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

void Address_print(struct Address *addr)
{
    printf("%d %s %s\n",
            addr->id, addr->name, addr->email);
}

void Database_load(struct Connection *conn)
{
    int rc = fread(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to load database.");
}

[B]struct Address getRows(int x)
{
    rows = malloc(sizeof(Address *x));
    return rows;
}[/B]

struct Connection *Database_open(const char *filename, char mode)
{
    struct Connection *conn = malloc(sizeof(struct Connection));
    if(!conn) die("Memory error");

    conn->db = malloc(sizeof(struct Database));
    if(!conn->db) die("Memory error");

    if(mode == 'c') {
        conn->file = fopen(filename, "w");
    } else {
        conn->file = fopen(filename, "r+");

        if(conn->file) {
            Database_load(conn);
        }
    }

    if(!conn->file) die("Failed to open the file");

    return conn;
}

void Database_close(struct Connection *conn)
{
    if(conn) {
        if(conn->file) fclose(conn->file);
        if(conn->db) free(conn->db);
        free(conn);
    }
}

void Database_write(struct Connection *conn)
{
    rewind(conn->file);

    int rc = fwrite(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to write database.");

    rc = fflush(conn->file);
    if(rc == -1) die("Cannot flush database.");
}

[B]void Database_create(struct Connection *conn)
{
    int i = 0;
    int x;
    printf("How many items do you want in the database?\n");
    scanf("%d", &x);
    _conn->db->rows = getRows(x);_
    for(i = 0; i < x; i++) {
        printf("Run number %d\n", i);
        getchar();
        // make a prototype to initialize it
        struct Address addr = {.id = i, .set = 0};
        // then just assign it
        conn->db->rows[i] = addr;
    }[/B]
    printf("DEBUG.  Line 150.  I is now %d\n", i);
    getchar(); 
}

void Database_set(struct Connection *conn, int id, const char *name, const char *email)
{
    struct Address *addr = &conn->db->rows[id];
    if(addr->set) die("Already set, delete it first");

    addr->set = 1;
    // WARNING: bug, read the "How To Break It" and fix this
    char *res = strncpy(addr->name, name, getTotal(name));
    // demonstrate the strncpy bug
    if(!res) die("Name copy failed");

    res = strncpy(addr->email, email, getTotal(email));// need total function here to get size of email!
    if(!res) die("Email copy failed");
}

void Database_get(struct Connection *conn, int id)
{
    struct Address *addr = &conn->db->rows[id];

    if(addr->set) {
        Address_print(addr);
    } else {
        die("ID is not set");
    }
}

void Database_delete(struct Connection *conn, int id)
{
    struct Address addr = {.id = id, .set = 0};
    conn->db->rows[id] = addr;
}

void Database_list(struct Connection *conn)
{
    int i = 0;
    struct Database *db = conn->db;

    
    for(i = 0; i < getTotalRows(conn->db->rows); i++) {
        struct Address *cur = &db->rows[i];

        if(cur->set) {
            Address_print(cur);
        }
    }
}

int main(int argc, char *argv[])
{
    if(argc < 3) die("USAGE: ex17 <dbfile> <action> [action params]");

    char *filename = argv[1];
    char action = argv[2][0];
    struct Connection *conn = Database_open(filename, action);
    int id = 0;

    if(argc > 3) id = atoi(argv[3]);
    if(id >= getTotalRows(conn->db->rows)) die("There's not that many records.");//need that function to compute total number of rows here!

    switch(action) {
        case 'c':
            Database_create(conn);
            Database_write(conn);
            break;

        case 'g':
            if(argc != 4) die("Need an id to get");

            Database_get(conn, id);
            break;

        case 's':
            if(argc != 6) die("Need id, name, email to set");

            Database_set(conn, id, argv[4], argv[5]);
            Database_write(conn);
            break;

        case 'd':
            if(argc != 4) die("Need id to delete");

            Database_delete(conn, id);
            Database_write(conn);
            break;

        case 'l':
            Database_list(conn);
            break;
        default:
            die("Invalid action, only: c=create, g=get, s=set, d=del, l=list");
    }

    Database_close(conn);

    return 0;
}
```

Am I getting warmer?

---

### Post by wingnut2626 on 2014-01-13
```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>





struct Address {
    int id;
    int set;
    char *name;
    char *email;
};

struct Database {
    struct Address *rows;
};

struct Connection {
    FILE *file;
    struct Database *db;
};

int getTotal(const char *ptr)
{
    int i;
    int total = 0;
    for(i = 0; *ptr++ != '\0'; i++){
        total++;
    }
    
    return total;
}

int getTotalRows(struct Address *addr)
{
    int i;
    int total = 0;
    for(i = 0; !addr++; i++){
        total++;
    }
    return total;
}

void die(const char *message)
{
    if(errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

void Address_print(struct Address *addr)
{
    printf("%d %s %s\n",
            addr->id, addr->name, addr->email);
}

void Database_load(struct Connection *conn)
{
    int rc = fread(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to load database.");
}

[B]struct Address getRows(int x)
{
    struct Address *rows;
    
    rows = malloc(sizeof(struct Address) *x);
    
    return rows[x];
}[/B]

struct Connection *Database_open(const char *filename, char mode)
{
    struct Connection *conn = malloc(sizeof(struct Connection));
    if(!conn) die("Memory error");

    conn->db = malloc(sizeof(struct Database));
    if(!conn->db) die("Memory error");

    if(mode == 'c') {
        conn->file = fopen(filename, "w");
    } else {
        conn->file = fopen(filename, "r+");

        if(conn->file) {
            Database_load(conn);
        }
    }

    if(!conn->file) die("Failed to open the file");

    return conn;
}

void Database_close(struct Connection *conn)
{
    if(conn) {
        if(conn->file) fclose(conn->file);
        if(conn->db) free(conn->db);
        free(conn);
    }
}

void Database_write(struct Connection *conn)
{
    rewind(conn->file);

    int rc = fwrite(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to write database.");

    rc = fflush(conn->file);
    if(rc == -1) die("Cannot flush database.");
}

[B]void Database_create(struct Connection *conn)
{
    int i = 0;
    int x;
    printf("How many items do you want in the database?\n");
    scanf("%d", &x);
    *conn->db->rows = getRows(x);
    for(i = 0; i < x; i++) {
        printf("Run number %d\n", i);
        getchar();
        // make a prototype to initialize it
        struct Address addr = {.id = i, .set = 0};
        // then just assign it
        conn->db->rows[i] = addr;
    }[/B]
    printf("DEBUG.  Line 150.  I is now %d\n", i);
    getchar(); 
}

void Database_set(struct Connection *conn, int id, const char *name, const char *email)
{
    struct Address *addr = &conn->db->rows[id];
    if(addr->set) die("Already set, delete it first");

    addr->set = 1;
    // WARNING: bug, read the "How To Break It" and fix this
    char *res = strncpy(addr->name, name, getTotal(name));
    // demonstrate the strncpy bug
    if(!res) die("Name copy failed");

    res = strncpy(addr->email, email, getTotal(email));// need total function here to get size of email!
    if(!res) die("Email copy failed");
}

void Database_get(struct Connection *conn, int id)
{
    struct Address *addr = &conn->db->rows[id];

    if(addr->set) {
        Address_print(addr);
    } else {
        die("ID is not set");
    }
}

void Database_delete(struct Connection *conn, int id)
{
    struct Address addr = {.id = id, .set = 0};
    conn->db->rows[id] = addr;
}

void Database_list(struct Connection *conn)
{
    int i = 0;
    struct Database *db = conn->db;

    
    for(i = 0; i < getTotalRows(conn->db->rows); i++) {
        struct Address *cur = &db->rows[i];

        if(cur->set) {
            Address_print(cur);
        }
    }
}

int main(int argc, char *argv[])
{
    if(argc < 3) die("USAGE: ex17 <dbfile> <action> [action params]");

    char *filename = argv[1];
    char action = argv[2][0];
    struct Connection *conn = Database_open(filename, action);
    int id = 0;

    if(argc > 3) id = atoi(argv[3]);
    if(id >= getTotalRows(conn->db->rows)) die("There's not that many records.");//need that function to compute total number of rows here!

    switch(action) {
        case 'c':
            Database_create(conn);
            Database_write(conn);
            break;

        case 'g':
            if(argc != 4) die("Need an id to get");

            Database_get(conn, id);
            break;

        case 's':
            if(argc != 6) die("Need id, name, email to set");

            Database_set(conn, id, argv[4], argv[5]);
            Database_write(conn);
            break;

        case 'd':
            if(argc != 4) die("Need id to delete");

            Database_delete(conn, id);
            Database_write(conn);
            break;

        case 'l':
            Database_list(conn);
            break;
        default:
            die("Invalid action, only: c=create, g=get, s=set, d=del, l=list");
    }

    Database_close(conn);

    return 0;
}
```

Heres what i have now.  Here is the output:
```

ronald@laptop1 ~/c/exercise 17 $ ./ex17 db.db c
How many items do you want in the database?
3
Segmentation fault

```

its faulting out before the debug statement now.  Please do not give me the direct answer, please just work with me and help me figure out how to do this.

---

### Post by ofnuts on 2014-01-13
Your code is getting cleaner :)

Your getTotal() function looks a lot like the garden-variety strlen() (by the way, did you notice that you never use the value of "I" in your loop? Maybe you should thing about rewriting the same without that variable).

For your segfault, move your debug segment (or add a few more) until you have cornered the failing statement. Brian Kernighan, one of the authors of C, wrote in one of his books:  "*The most effective debugging tool is still careful thought, coupled with judiciously placed print statements.*"

---

### Post by trent.josephsen on 2014-01-13
You're very close. Here's a question for you that might help you find the solution: where and how are you going to call free() on the pointer returned by the malloc() in getRows()?

It might help, if you're stuck, to draw pictures to represent your data structures. E.g., `conn' is an arrow (a pointer) that points to a box (a struct) that contains `file' and a pointer `db', which is an arrow pointing to another box that contains `rows', etc.

---

### Post by wingnut2626 on 2014-01-15
is *conn->db->rows a pointer to rows?  or is it an array of conn->db->rows

---

### Post by wingnut2626 on 2014-01-15
just found out about calloc.....going to mess around with this....

---

### Post by wingnut2626 on 2014-01-15
```
/*
 * ex17.c
 * 
 * Copyright 2014 Ronald C. Reid <ronald@laptop1>
 * 
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or
 * (at your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
 * MA 02110-1301, USA.
 * 
 * 
 */


#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>





struct Address {
    int id;
    int set;
    char *name;
    char *email;
};

struct Database {
    struct Address *rows;
};

struct Connection {
    FILE *file;
    struct Database *db;
};

int getTotal(const char *ptr)
{
    int i;
    int total = 0;
    for(i = 0; *ptr++ != '\0'; i++){
        total++;
    }
    
    return total;
}

int getTotalRows(struct Address *addr)
{
    int i;
    int total = 0;
    for(i = 0; !addr++; i++){
        total++;
    }
    return total;
}

void die(const char *message)
{
    if(errno) {
        perror(message);
    } else {
        printf("ERROR: %s\n", message);
    }

    exit(1);
}

void Address_print(struct Address *addr)
{
    printf("%d %s %s\n",
            addr->id, addr->name, addr->email);
}

void Database_load(struct Connection *conn)
{
    int rc = fread(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to load database.");
}

struct Connection *Database_open(const char *filename, char mode)
{
    struct Connection *conn = malloc(sizeof(struct Connection));
    if(!conn) die("Memory error");

    conn->db = malloc(sizeof(struct Database));
    if(!conn->db) die("Memory error");

    if(mode == 'c') {
        conn->file = fopen(filename, "w");
    } else {
        conn->file = fopen(filename, "r+");

        if(conn->file) {
            Database_load(conn);
        }
    }

    if(!conn->file) die("Failed to open the file");

    return conn;
}

void Database_close(struct Connection *conn)
{
    if(conn) {
        if(conn->file) fclose(conn->file);
        if(conn->db) free(conn->db);
        free(conn);
    }
}

void Database_write(struct Connection *conn)
{
    rewind(conn->file);

    int rc = fwrite(conn->db, sizeof(struct Database), 1, conn->file);
    if(rc != 1) die("Failed to write database.");

    rc = fflush(conn->file);
    if(rc == -1) die("Cannot flush database.");
}

void Database_create(struct Connection *conn)
{
    int i = 0;
    int x;
    printf("How many items do you want in the database?\n");
    scanf("%d", &x);
    **conn->db->rows = calloc(x, sizeof(struct Address));**
    for(i = 0; i < x; i++) {
        printf("Run number %d\n", i);
        getchar();
        // make a prototype to initialize it
        struct Address addr = {.id = i, .set = 0};
        printf("Debug statement. line 149 after the prototype of Address is set.");
        getchar();
        // then just assign it
        conn->db->rows[i] = addr;
    }
    printf("DEBUG.  Line 150.  I is now %d\n", i);
    getchar(); 
}

void Database_set(struct Connection *conn, int id, const char *name, const char *email)
{
    struct Address *addr = &conn->db->rows[id];
    if(addr->set) die("Already set, delete it first");

    addr->set = 1;
    // WARNING: bug, read the "How To Break It" and fix this
    char *res = strncpy(addr->name, name, getTotal(name));
    // demonstrate the strncpy bug
    if(!res) die("Name copy failed");

    res = strncpy(addr->email, email, getTotal(email));// need total function here to get size of email!
    if(!res) die("Email copy failed");
}

void Database_get(struct Connection *conn, int id)
{
    struct Address *addr = &conn->db->rows[id];

    if(addr->set) {
        Address_print(addr);
    } else {
        die("ID is not set");
    }
}

void Database_delete(struct Connection *conn, int id)
{
    struct Address addr = {.id = id, .set = 0};
    conn->db->rows[id] = addr;
}

void Database_list(struct Connection *conn)
{
    int i = 0;
    struct Database *db = conn->db;

    
    for(i = 0; i < getTotalRows(conn->db->rows); i++) {
        struct Address *cur = &db->rows[i];

        if(cur->set) {
            Address_print(cur);
        }
    }
}

int main(int argc, char *argv[])
{
    if(argc < 3) die("USAGE: ex17 <dbfile> <action> [action params]");

    char *filename = argv[1];
    char action = argv[2][0];
    struct Connection *conn = Database_open(filename, action);
    int id = 0;

    if(argc > 3) id = atoi(argv[3]);
    if(id >= getTotalRows(conn->db->rows)) die("There's not that many records.");//need that function to compute total number of rows here!

    switch(action) {
        case 'c':
            Database_create(conn);
            Database_write(conn);
            break;

        case 'g':
            if(argc != 4) die("Need an id to get");

            Database_get(conn, id);
            break;

        case 's':
            if(argc != 6) die("Need id, name, email to set");

            Database_set(conn, id, argv[4], argv[5]);
            Database_write(conn);
            break;

        case 'd':
            if(argc != 4) die("Need id to delete");

            Database_delete(conn, id);
            Database_write(conn);
            break;

        case 'l':
            Database_list(conn);
            break;
        default:
            die("Invalid action, only: c=create, g=get, s=set, d=del, l=list");
    }

    Database_close(conn);

    return 0;
}
```


GETTING BETTER!!!!!

---

### Post by trent.josephsen on 2014-01-15
Congrats!

(Don't forget to free() it...)

Strictly speaking, calloc() isn't necessary here; since you don't need it zeroed, malloc(x * sizeof(struct Address)) would work as well (marginally faster, probably). But the most important part is figuring out how to declare and initialize the pointer and it looks like you figured that out already.

---

