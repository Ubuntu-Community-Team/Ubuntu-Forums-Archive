---
title: "Calling .pl script in .thml file problem"
date: 2007-05-12
forum: Programming Talk
---

### Post by leo246 on 2007-05-12
Hi all

I have a quick question about html and perl/cgi.  Please bear in mid that I have not programming or scripting experience:

I have a perl script, whihc works fine from within the command prompt.  However, I need to incorporate this script in a html file.  All is set up and the html file views fine, however, when clicking on the 'Submit' button, it prompts to have the script downloaded.

my html code looks as follows:

<h3>Query</h3><table><form method="post" action="/path/to/scriptl" enctype="multipart/form-data">
 <tr>

any advise or tips would be appreciated.

Leo

---

### Post by Wybiral on 2007-05-12
Sounds like you don't have CGI enabled (or it doesn't recognize perl as being executable)

---

