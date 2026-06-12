---
title: "issue with nginx server"
date: 2019-06-22
forum: New to Ubuntu
---

### Post by anacondaonline on 2019-06-22
I have build angular application
ng build --output-path=dist/myapp --base-href=/myapp/


in NGINX , I have this settings
nginx :


location /myapp/ {
alias /usr/share/nginx/html/myapp/;
try_files $uri$args $uri$args/ /myapp/index.html;
}


when I open the url xx.xx.xx.xxx/myapp I see 404 for asset folder contents in browser console.


How to fix this ?


screenshot attached.[ATTACH=CONFIG]283469[/ATTACH]

---

### Post by TheFu on 2019-06-22
Might want to lead with  "Angular on nginx" in the title.  
I'm pretty good at nginx, but haven't any clue about angular. Never deployed one of those apps and have absolutely know idea what those screen shots are for.

---

