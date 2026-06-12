---
title: "Extremely wierd JSON PARSE FAILED error"
date: 2010-05-25
forum: Programming Talk
---

### Post by megamonk on 2010-05-25
hi

Im having difficulty trying to solve a weird JSON parse error on my site [https://www.courio.com]("https://www.courio.com") when uploading. i dont know if its something with the server or the way the site was made (i took over it from a previous developer). here's the weird problem:

the uploads works flawlessly on small files but on large files it fails and throws "a server error has occurred: json parse failed". initially i thought maybe its the server settings or the php.ini settings but i checked it and configured it and nothings wrong. the weird part is that the error does not always occur. i used the same file (238mb) and tried to upload it several times and after 3 tries it succeeded so the server upload limit settings is correct since i was able to upload a huge file. heres the even weirder part, i downloaded chrome on my ubuntu box and the 238mb file got uploaded the first try and even got a max upload speed of 1.3mbps but when i tried it on firefox on the same ubuntu box i only got max upload speed of 35kbps and it failed (again) throwing a "a server error has occurred: json parse failed". i tried testing the upload on windows using IE, firefox and chrome but got no visible differences and they all failed. i want to remove that error of the site however i only have a vague idea how to since the symptoms isn't really clear.

so anyone got any ideas to what might be triggering that server error on my site?

thanks!

---

