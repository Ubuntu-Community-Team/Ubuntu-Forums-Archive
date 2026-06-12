---
title: "Make search results appear on a page"
date: 2009-01-22
forum: Programming Talk
---

### Post by Kinetic_lord on 2009-01-22
I have this javascript code, for a search function to put on my site. Everything works fine, except that i don't know how to make the search results appear in the same page with the form. Once i press enter, another windows opens with the search results, and white background.


This is the code:

```

var item = new Array();

c=0; item[c]=new Array("index.html","","DemoSite","index,main,start,home,front","Demonstration search engine data about an imagined but probable internet site.");

c++; item[c]=new Array("linux.html","","About Me","about,author,contact,email,who","Contact details and general information about the creator of the site and what the site is about.");

c++; item[c]=new Array("windows.html","","Links page","links,more,where,similar,friends","Links to my favourite sites which I find interesting. Other friends sites which have similar interests to my own.");

c++; item[c]=new Array("mac.html","main/","Main Page","content,main,focus","The main part of my site which contains what you have come to see. Lots of stuff like that and more great things. All in a sub directory.");

c++; item[c]=new Array("software.html","main/images/","Link Logo","link,image,logo,graphic","The logo.jpg is just a small image which you can place on your site as a link to me. It's in a second level subdirectory.");


page="<html><head><title>Search Results</title></head><body bgcolor='white'><center><table border=0 cellspacing=10 width=80%>";


function search(frm) {
win = window.open("","","scrollbars");
win.document.write(page);
txt = frm.srchval.value.split(" ");
fnd = new Array(); total=0;
for (i = 0; i < item.length; i++) {
fnd[i] = 0; order = new Array(0, 4, 2, 3);
for (j = 0; j < order.length; j++)
for (k = 0; k < txt.length; k++)
if (item[i][order[j]].toLowerCase().indexOf(txt[k]) > -1 && txt[k] != "")
fnd[i] += (j+1);
}
for (i = 0; i < fnd.length; i++) {
n = 0; w = -1;
for (j = 0;j < fnd.length; j++)
if (fnd[j] > n) { n = fnd[j]; w = j; };
if (w > -1) total += show(w, win, n);
fnd[w] = 0;
}
win.document.write("</table><br>Rezultatele cautarii: "+total+"<br></body></html>");
win.document.close();
}
function show(which,wind,num) {
link = item[which][1] + item[which][0]; 
line = "<tr><td><a href='"+link+"'>"+item[which][2]+"</a> Score: "+num+"<br>";
line += item[which][4] + "<br>"+link+"</td></tr>";
wind.document.write(line);
return 1;
}
//  End -->

```

The result can appear on another div in the page, i just don't know how to make that :D. I'm not really good...

Thanks.

---

