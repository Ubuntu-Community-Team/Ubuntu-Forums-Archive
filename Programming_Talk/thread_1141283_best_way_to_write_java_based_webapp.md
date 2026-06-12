---
title: "best way to write java based webapp"
date: 2009-04-28
forum: Programming Talk
---

### Post by badperson on 2009-04-28
Hi,
I'm finishing up a class in web services, and after having gone through that and web server programming, I'd like to work on creating a web app of some complexity on my own. 

I was thinking it would be mysql/glassfish based...is that the best way to go? Will glassfish ultimately replace tomcat as the top opensource web server? 

bp

---

### Post by CptPicard on 2009-04-28
Glassfish is a J2EE application server actually. There is a web app container component too as a part of it,  but there are standalone web app servers such as Tomcat and Jetty as well.

I would recommend looking into a combination of Netbeans, Spring and Hibernate, of if you're looking for something that gets you up to speed faster, Groovy on Grails (Groovy is a dynamic language built out of Java).

---

### Post by slavik on 2009-04-28
Jboss is the top open-source application server ;)

---

### Post by Luke has no name on 2009-04-30
I'm looking into using Grails for a production web application to manage national product conferences. It might be awesome, might not. I'm new to Java web development.

I suggest checking out this link:
[http://www.google.com/bookmarks/url?url=http://www.ibm.com/developerworks/views/java/libraryview.jsp%3Fend_no%3D100%26lcl_sort_order%3Ddesc%26type_by%3DAll%2BTypes%26sort_order%3Dasc%26show_all%3Dfalse%26start_no%3D1%26sort_by%3DDate%26search_by%3Dmastering%2Bgrails%26topic_by%3DAll%2Btopics%2Band%2Brelated%2Bproducts%26search_flag%3Dtrue%26show_abstract%3Dtrue%26S_TACT%3D105AGX02%26S_CMP%3DEDU&ei=bE35SZjXHoK6Np_T8YIP&sig2=C4EzkhjL4McuxhL6lvTyvg&ct=b](http://www.google.com/bookmarks/url?url=http://www.ibm.com/developerworks/views/java/libraryview.jsp%3Fend_no%3D100%26lcl_sort_order%3Ddesc%26type_by%3DAll%2BTypes%26sort_order%3Dasc%26show_all%3Dfalse%26start_no%3D1%26sort_by%3DDate%26search_by%3Dmastering%2Bgrails%26topic_by%3DAll%2Btopics%2Band%2Brelated%2Bproducts%26search_flag%3Dtrue%26show_abstract%3Dtrue%26S_TACT%3D105AGX02%26S_CMP%3DEDU&ei=bE35SZjXHoK6Np_T8YIP&sig2=C4EzkhjL4McuxhL6lvTyvg&ct=b)

---

