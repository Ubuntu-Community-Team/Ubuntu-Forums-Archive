---
title: "script java app"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by redpower1989 on 2011-11-18
Hello.
I make a jar file and l run it with java -jar name.jar
After that i make a deb package to install my java application.
I write a script with this code > #!/bin/bash
                     mv /usr/lib/name app/nameapp.jar /usr/bin/

                    java -jar /usr/bin/name.jar $@and after i install my deb and when i run the package the program didn't run and it give me this message> Unable to access jarfile /usr/bin/name.jarDo you know how fix that and make my app run ?
Or do you know a another script to run my java app?

---

