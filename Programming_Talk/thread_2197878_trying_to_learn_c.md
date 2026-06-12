---
title: "trying to learn c"
date: 2014-01-05
forum: Programming Talk
---

### Post by wingnut2626 on 2014-01-05
Im working on the tutorial from 'Learn C the hard way' and currently im on the exercise for malloc and pointers to structures.  I have a few questions for someone that is willing to help a newbie out.  Here is the code:

```
#include <stdio.h>
#include <assert.h>
#include <stdlib.h>
#include <errno.h>
#include <string.h>

[COLOR=#008000]#define MAX_DATA 512
#define MAX_ROWS 100

struct Address {
    int id;
    int set;
    char name[MAX_DATA];
    char email[MAX_DATA];
};

struct Database {
    struct Address rows[MAX_ROWS];
};[/COLOR]   
```How can I set MAX_DATA and MAX_ROWS to parameters, vs as constants?```
 

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

[COLOR=#4b0082]struct Connection *Database_open(const char *filename, char mode)[/COLOR]  
```Im confused.  Database open is a pointer to what exactly?```

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
    [COLOR=#4b0082]struct Connection *conn = Database_open(filename, action);[/COLOR]
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

This is very confusing to me.  I have been trying to get this for almost 2 weeks and now am at the point of (almost) giving up.  Please help me.

---

### Post by ofnuts on 2014-01-06
It returns a  pointer to a Connection, which is an aggregate (a "struct", in C) that keeps together the FILE on the disk (to load/save the data) and the data in memory (as a Database aggregate). That Database aggregate itself contains just an array of rows (but this is likely to change by adding more fields later).

---

### Post by StephenF on 2014-01-06
Database_open is not a pointer. It's a function that returns a pointer.

char *f()
From the identifier, f, Look right then left, then right then left and so on so: f is a function () whose return type is char *

You are going to love this link:
[http://www.cdecl.org]("http://www.cdecl.org")
Be sure to strip out the function call parameter variable names e.g:
struct Connection *Database_open(const char *, char)

Edit: regarding your first question regarding doing away with arbitrary size restrictions it shows you have good programming instincts. The flaws in the program design are there as examples of the wrong/lazy approach to C programming that I believe are addressed in later parts of the tutorial. Google 'C programmers disease'.

---

### Post by wingnut2626 on 2014-01-06
Thanks!

---

