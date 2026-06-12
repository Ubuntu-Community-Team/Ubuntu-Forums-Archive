---
title: "Netbeans web application file streamer"
date: 2011-07-09
forum: Programming Talk
---

### Post by RobikShrestha on 2011-07-09
I am coding a web application in netbeans. I opened a file stream, wrote some objects. Then I read from that file. Everything works fine except that the file is not saved anywhere i.e. I cannot find the file which the program creates in the project's folder. Why so?

---

### Post by PaulM1985 on 2011-07-09
Have you got any sample code?

Have you searched your entire file system looking for the name of the file you created?

Have you given your file an absolute path or a relative path?

Paul

---

### Post by RobikShrestha on 2011-07-10
I found the file in 
/usr/local/glassfish-3.1/glassfish/domains/domain1.
So a netbeans web application saves the file inside the server folder not the project folder.

---

