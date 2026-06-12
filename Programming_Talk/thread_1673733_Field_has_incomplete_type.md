---
title: "Field has incomplete type"
date: 2011-01-22
forum: Programming Talk
---

### Post by cguy on 2011-01-22
This is the code:
```
struct directory;
typedef struct directory directory_t;

typedef struct file
{
  char           name[256];
  unsigned long  size;
  date_t         created;
  date_t         modified;
  directory_t    parent;     <---------- This line is troublesome
}file_t;


struct directory
{
  char              name;
  struct directory  *parent;
  date_t            created;
  date_t            modified;
};
```

and this is the compilation error:
```
error: field 'parent' has incomplete type
```

But I declared the second structure's prototype and then declared a type definition.

Why do I still get an error?

---

### Post by worksofcraft on 2011-01-22
> **cguy said:**
> This is the code:
```
struct directory;
typedef struct directory directory_t;

typedef struct file
{
  char           name[256];
  unsigned long  size;
  date_t         created;
  date_t         modified;
  directory_t    parent;     <---------- This line is troublesome
}file_t;


struct directory
{
  char              name;
  struct directory  *parent;
  date_t            created;
  date_t            modified;
};
```

and this is the compilation error:
```
error: field 'parent' has incomplete type
```

But I declared the second structure's prototype and then declared a type definition.

Why do I still get an error?

That is correct.
The declaration of struct directory is AFTER the definition of "parent"... so when the compiler is trying to work out the size of your struct file... it doesn't yet know how big the directory structure is.

You can either make it so the declaration of directory comes BEFORE file or you can declare a parent as a POINTER which has the same size no matter what it points to :)

p.s. If I understand what you are trying to do... then you simply have to put a * in front of parent on that line!

---

