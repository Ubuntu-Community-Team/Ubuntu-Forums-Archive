---
title: "SQLite3 not showing proper errors !"
date: 2012-05-30
forum: Programming Talk
---

### Post by etdsbastar on 2012-05-30
Hello there,

Please look at the code below:
```

void
make_connection ()
{
    Database.data_file = g_build_path (G_DIR_SEPARATOR_S, get_current_directory (),
        "data", "default.khm", NULL);
    
    Database.error = sqlite3_open (Database.data_file, &Database.connection);
    if (Database.error)
    {
        g_error ("%s", "Unable to open default database.");
        sqlite3_close (Database.connection);
        exit (1);
    }
}
```

This code is creating a new database file in the data_file directory, But I want that sqlite3 should display the error message as specified.

Please help.

---

