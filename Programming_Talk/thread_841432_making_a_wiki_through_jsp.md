---
title: "making a wiki through jsp"
date: 2008-06-26
forum: Programming Talk
---

### Post by dexter.deepak on 2008-06-26
i am trying to make a simple wiki (yesss ..with lot of flaws too :)) through jsp on the apache-tomcat architecture, 
the purpose is described : (i am using file-handling here)
1. there's a folder named wiki, in which all the user created pgs reside.
2. the user gives a name "wname" for the new page he wants to create and saves it in the directory. 
3. the jsp then looks for the word "wname" in all the pages in the wiki directory , and replaces all these entries :
wname   ----> <a href=wname.jsp>wname</a>

till now i was planning to call a shell script from the jsp:
```
sed -i "s/$2/$3$2$4/g" $1
```
in the script should do the task...here's a part of jsp :
```
<%   String bash=("sh "+"path_to_script "+"path_to_wiki_dir "+wname+" <a href="+wname+".jsp "+"<\\/a>"); 
     try
     {    
     Process proc = Runtime.getRuntime().exec(bash);
```

but the script doesnt seem to work :(
i later on think read about the StringBuffer class and thought it was a foolish idea to call a shell script from jsp.
what i need ..
some messiah who can either help me run the script ...which is not even running properly on a standalone basis OR help me write a java code equivalent to sed in that script.

---

### Post by xlinuks on 2008-06-26
Even if you manage to resolve this issue, I think you won't go far this way, you need database(s), they do out-of-the-box filtering and other stuff besides storing data, and in many cases will also be much faster..

---

### Post by dexter.deepak on 2008-06-26
i know..even the database (mysql 5)i am using for other parts of my project has got these capabilities. but i still prefer a traditional style...wanted to explore a bit more !!:)

---

### Post by pmasiar on 2008-06-26
If you follow Turbogears tutorial, you can create simple wiki in about hour, including installation. I know I did.

If you insist on painful experience of Java, at least do yourself a favor and use Model-View-Controller design pattern.

---

### Post by xlinuks on 2008-06-26
This is a good start, and there's also video (pay attention to the ability to visually edit web-gui stuff):
[http://www.netbeans.org/features/web/web-app.html](http://www.netbeans.org/features/web/web-app.html)

---

