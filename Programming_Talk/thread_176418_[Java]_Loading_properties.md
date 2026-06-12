---
title: "[Java] Loading properties"
date: 2006-05-14
forum: Programming Talk
---

### Post by mlind on 2006-05-14
Is there a way to load contents of .properties file so, that order of the entries which
they appear in the file could be preserved? Properties is a instance of Hashtable and
Maps doen't preserve order like Lists do..

I'd like to accomplish this without
* modifying existing .properties file
* extending Properties and overriding put() or other logic methods

Are there any corresponding Apache module that would load properties into List instead?

Thanks.

---

### Post by yaaarrrgg on 2006-05-14
I think this will do what you are describing:

[http://jakarta.apache.org/tapestry/tapestry/apidocs/org/apache/tapestry/util/text/LocalizedProperties.html](http://jakarta.apache.org/tapestry/tapestry/apidocs/org/apache/tapestry/util/text/LocalizedProperties.html)

---

### Post by mlind on 2006-05-15
Yes, thanks. Althought I decided to evetually drop the idea, it was too error prone
for changes.

---

