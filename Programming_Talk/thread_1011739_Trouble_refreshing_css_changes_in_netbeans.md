---
title: "Trouble refreshing css changes in netbeans"
date: 2008-12-15
forum: Programming Talk
---

### Post by Bucephalus01 on 2008-12-15
Hi
I am learning php and html in netbeans.
I set up a virtual host as per, 
[http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot](http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html#specifyDocumentRoot)

Anyway, I don't get immediate changes to my webpage format when I change the css. For instance, I changed the width in some of these css expressions and a  change occured but when I changed it back it doesn't. Then I might walk away for a few hours and try it again and it updates.

```
*.indent{position:relative; margin-left:120px;}
*.graphic-dropcap{position:absolute; width:120px; height:90px; left:-120px; top:0 }
*.graphic-dropcap span{position:absolute; width:120px; height:60px; margin:0; left:0; top:0;
                        background:url("heading.jpg") no-repeat}

```

Does anyone know why there is lag in my webpage updating?
I looked to see if the file was being copied to somewhere else where the webserver is accessing a file that hasn't been updated but I didn't find one. I'm sure it's some other problem that is causing this behaviour.

Any ideas?????
thanks

---

