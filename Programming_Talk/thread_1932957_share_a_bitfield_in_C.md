---
title: "share a bitfield in C"
date: 2012-02-28
forum: Programming Talk
---

### Post by cybo on 2012-02-28
hello everyone. i recently encountered an interesting problem and don't know how to solve it.

i need to be able to share (union) a bit field and i'm not sure it is even possible in C, but if it is then it will make my code work a lot better. here is what i'm trying to do:

```
typedef struct {
  uint16 field1 : 1,
         field2 : 2,
         union {
           field3 : 1,
           field4 : 1,
           field5 : 2
         }
         field6 : 9;
} MyStruct;
```

idea is to share fields 3, 4 and 5. and i need those to be specifically bit fields.

any help is appreciated

---

### Post by cybo on 2012-02-28
folks,

right after i posted a question i managed to figure out an answer. sorry for taking your time.

here is the answer:

```
typedef struct {
  union {
    uint16 : 3,
           field3 : 1,
           field4 : 1,
           : 9;

    uint16 field1 : 1,
           field2 : 2,
           field5 : 2
           field6 : 9;
  };
} MyStruct;
```

---

