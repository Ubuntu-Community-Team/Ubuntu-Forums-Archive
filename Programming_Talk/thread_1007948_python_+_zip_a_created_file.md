---
title: "python + zip a created file"
date: 2008-12-10
forum: Programming Talk
---

### Post by somebodyhelpme on 2008-12-10
if form.accepts(request.vars,session): 
        for table in db.tables: 
            rows=db(db[table].id).select() 
            print rows 
            open(str(os.sep).join([os.getcwd(), 'applications', 
                request.application, 'databases', 
                table+'.csv']),'w').write(str(db(db[table].id).select())) 


can someone help me how to zip above file?? thanks

---

### Post by ghostdog74 on 2008-12-11
read the reference library for gzip or tarfile module.

---

### Post by Greyed on 2008-12-11
> **somebodyhelpme said:**
> 
[php]
if form.accepts(request.vars,session): 
    for table in db.tables: 
        rows=db(db[table].id).select() 
        print rows 
        open(str(os.sep).join([os.getcwd(), 'applications', request.application, 
                'databases', table+'.csv']),'w').write(str(db(db[table].id).select()))
[/php]

Ahhh, much better.  Code blocks are your friend, especially with Python.  ;)

---

