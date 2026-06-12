---
title: "Program hanging"
date: 2014-03-24
forum: Programming Talk
---

### Post by wingnut2626 on 2014-03-24
I must be missing something here.  

```

void Database_create(struct Connection *conn)
{
    int i = 0;
      int total_addresses_used;
  
     printf("How many to store in this database?\n");
    *** scanf("%d", &total_addresses_used)***;
    

     for(i = 0; i < total_addresses_used; i++) {
             printf("%d", i);
       struct Address addr = {.id = i, .set = 0};
       printf("119 debug.");
            conn->db->rows[i] = addr;
    }
     printf("DEbug");
     conn->db = realloc(conn->db, sizeof(struct Address) * total_addresses_used);

}
```

After running this function, after the value total_addresses_used is inputted, there is nothing.  No debug output.  Why is this hanging?

---

### Post by mevun on 2014-03-25
Add a fflush(stdout) or possibly a newline character **\n** in the last printf.

---

