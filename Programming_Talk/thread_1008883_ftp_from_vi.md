---
title: "ftp from vi"
date: 2008-12-12
forum: Programming Talk
---

### Post by Mars8082686 on 2008-12-12
I wrote a little bash script to upload pages in my site to the server without leaving vi then I mapped q to upload it but it only works when I explicitly name the file to upload. Is there any variable in vim that displays the current file?

right now it's

:map q :!put index.php[esc]

But I'd like to replace it with a variable so I can put the map in the sites .vimrc and upload any file I'm editing with q without having to explicitly name it. Maybe I'm going about this wrong. I normally use Dreamweaver for php web development.

---

### Post by geirha on 2008-12-12
Replace index.php with %. % will be expanded to the filename currently being edited.

---

