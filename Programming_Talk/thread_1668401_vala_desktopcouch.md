---
title: "vala desktopcouch"
date: 2011-01-16
forum: Programming Talk
---

### Post by pavolzetor on 2011-01-16
pk@pk-laptop:~/Programming/speedyrss/src$ ./xml_parser rss.xml ACannot connect to destination (127.0.0.1)

```

// constructor
	public Database() {
		 this.session = new CouchDB.Session();
		 this.db = new CouchDB.Database (session, "test");
		 
		 try {
		  var newdoc = new CouchDB.Document ();
        newdoc.set_boolean_field ("awesome", true);
        newdoc.set_string_field ("phone", "555-VALA");
        newdoc.set_double_field ("pi", 3.14159);
        newdoc.set_int_field ("meaning_of_life", 42);
        db.put_document (newdoc);    // store document
        } catch (Error e) {
        stderr.printf ("%s\n", e.message);
        }
	}

```
desktopcouch is running

---

