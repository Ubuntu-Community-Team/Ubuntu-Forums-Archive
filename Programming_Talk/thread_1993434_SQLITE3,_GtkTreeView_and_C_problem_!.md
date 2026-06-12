---
title: "SQLITE3, GtkTreeView and C problem !"
date: 2012-06-02
forum: Programming Talk
---

### Post by etdsbastar on 2012-06-02
Hello friends,

The below given code is not displaying the list from sqlite3 database. please help.

```
void
populate_list()
{
    GtkTreeIter iter;
    
    ledger_store = gtk_list_store_new (9, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING,
        G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING, G_TYPE_STRING);
    
    exec_sql ("select * from ledgers", 10000);
    
    while (sqlite3_step (Database.result) == SQLITE_ROW)
    {
        gtk_list_store_append (ledger_store, &iter);
        gtk_list_store_set (ledger_store, &iter,
            COL_DEMANDNO, sqlite3_column_text (Database.result, 0),
            COL_CENSUSNO, sqlite3_column_text (Database.result, 1),
            COL_YEAR, sqlite3_column_text (Database.result, 2),
            COL_NAME, sqlite3_column_text (Database.result, 3),
            COL_CASTE, sqlite3_column_text (Database.result, 4),
            COL_ADDRESS, sqlite3_column_text (Database.result, 5),
            COL_MOBILENO, sqlite3_column_text (Database.result, 6),
            COL_STREET, sqlite3_column_text (Database.result, 7),
            COL_WARDNO, sqlite3_column_text (Database.result, 8),
            -1);
    
    }

    sqlite3_finalize (Database.result);
}

```

---

### Post by etdsbastar on 2012-06-02
is there anyone who can help me please?

---

### Post by etdsbastar on 2012-06-03
bump

---

### Post by etdsbastar on 2012-06-04
Please help me friends !

---

### Post by etdsbastar on 2012-06-04
Strange guys,

For the first time I haven't got any replies from the past two days.

Really strange.....

---

