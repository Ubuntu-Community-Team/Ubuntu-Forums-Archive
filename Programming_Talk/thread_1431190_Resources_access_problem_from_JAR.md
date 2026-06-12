---
title: "Resources access problem from JAR"
date: 2010-03-16
forum: Programming Talk
---

### Post by cdiem on 2010-03-16
I have the following directory structure of a project:

> 
Folder "project" in Eclipse:
-- src
-- resources
  ---- trayicon.png
-- db 
  ---- test.db
-- bin

I'm accessing the image with:

```
Image image = Toolkit.getDefaultToolkit().getImage("resources/trayicon2.png");
```

and from Eclipse that is not a problem. Then I generate an executable jar file, and add the dirs, with a directory structure of:
> 
Folder "project"
-- folder "db"
  ---- test.db
-- folder "resources"
  ---- trayicon2.png
-- project.jar

And now the image is no more accessible. Also, the database is no more accessible; while in Eclipse I used to access it with:

```
Connection conn = DriverManager.getConnection("jdbc:sqlite:db/test.db");
```

How can I access the resources (images and db) after generating the jar file "project.jar"?

---

### Post by cdiem on 2010-03-16
Solved the image part by using:

```

URL imageURL = getClass().getResource("/resources/trayicon2.png"); 
Image image = Toolkit.getDefaultToolkit().getImage(imageURL);

```

Now the only thing left for me to understand is why when starting the program with "java -jar project.jar" it starts with all the test entries in "test.db" and when starting it with "right click/open with Sun Java 6 runtime environment" it starts with no entries in the database.

---

