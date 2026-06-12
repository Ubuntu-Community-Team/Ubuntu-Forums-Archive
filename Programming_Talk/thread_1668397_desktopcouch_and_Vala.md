---
title: "desktopcouch and Vala"
date: 2011-01-16
forum: Programming Talk
---

### Post by pavolzetor on 2011-01-16
Hi, I work on my RSS reader, but I have problems with desktopcouch

I can browse databases here
[http://localhost:59693/_utils/](http://localhost:59693/_utils/)

but, my program reports this

$ ./xml_parser rss.xml
Cannot connect to destination (127.0.0.1)

but couchdb is running

connecting part of program
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

---

