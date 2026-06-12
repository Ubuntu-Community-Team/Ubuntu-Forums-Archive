---
title: "java and google maps"
date: 2011-07-12
forum: Programming Talk
---

### Post by RobikShrestha on 2011-07-12
I am building a java web application which uses java classes to find out longitudes and latitudes of different places.

 Now I need to plot those points on the map. The data is stored in a linked list. How would I transport that linked list to javascript, so that I can plot each of the points? 

If there is a better way to do it like using only java please help me.

---

### Post by raja.genupula on 2011-07-12
[http://blog.jcoglan.com/2007/07/23/writing-a-linked-list-in-javascript/](http://blog.jcoglan.com/2007/07/23/writing-a-linked-list-in-javascript/)


i am not a good programmer to understand but i hope it will be useful to you . dont mind if not ,

---

### Post by RobikShrestha on 2011-07-12
thanks, but I was looking for using a java linked list inside javascript linked list.

---

### Post by Zugzwang on 2011-07-12
Use your Java linked list to build a Javascript source code that builds a linked list. Then execute the code in your Javascript interpreter.

---

### Post by RobikShrestha on 2011-07-12
Ok this is a snippet of sample code that succesfully ran:

file.jsp:


<%!int i=0;%>
<%!int zoomLevel[]={1,2,3,4,5};%>

var array=new Array();
<%for (i = 0; i < zoomLevel.length; i++) {%>
                    array[<%=i%>]=<%=zoomLevel[i]%>;
            <%}%>

//do sth with the array[]

---

