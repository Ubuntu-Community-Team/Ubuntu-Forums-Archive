---
title: "unary operator expected"
date: 2017-11-22
forum: Programming Talk
---

### Post by kikosanjuan on 2017-11-22
#!/bin/bash


for WFILE in $(sudo ls -lR / | grep .sh);
  do
    if [ -l "$WFILE" ];
     then
       echo '$WFILE' Is a Directory
     else 
       if [ -d "$WFILE" ];
        then
        echo "$WFILE" is a link
       fi
    fi
  done

error: line 5: unary operator expected

what diud I wrong?

greetings 
kikosanjuan

---

### Post by howefield on 2017-11-22
Thread moved to the "*Programming Talk*" forum.

---

### Post by spjackson on 2017-11-23
Welcome to the forums.

There is no operator -l that tests whether a file is a plain file, which is why you get the syntax error. You probably want to use -f instead.

I am assuming that this is a learning exercise, so I won't go into detail about several other issues with this script.

---

