---
title: "Can't run JSF book examples on tomcat6"
date: 2009-07-26
forum: Programming Talk
---

### Post by andrew222 on 2009-07-26
I am having problem getting downloaded JSF examples for the O'Reilly text 'Java Server Faces (H.Bergsten)'.

I downloaded the source code in a zip file titled jsfexamples.zip from the author's website at this URL:


*[http://www.hansbergsten.com/downloadjsf.jsp](http://www.hansbergsten.com/downloadjsf.jsp)*


I extracted the files contents and then as directed, put the 'jsfbook' folder into the tomcat directory's 'webapps' folder on my system at: 


*/usr/share/tomcat6/webapps*


using this script,  *cp -R jsfbook $CATALINA_HOME/webapps*

I checked and the file was copied successfully.

I defined the usernames in the tomcat-users.xml file as directed at the author's website.  

Then I restarted the server and put this URL in the browser to get to the 'jsfbook' application:

[I]
[http://localhost:8080/jsfbook/](http://localhost:8080/jsfbook/)[/I]


This is where the trouble began;  I got a 404 status code error telling me:


* "The requested resource (/jsfbook/) is not available."*


I think that there must be some issues with file permissions/access.  Since I downloaded it, I may have to do something to change permissions?  

I right clicked on the folder and then right clicked 'properties', then 'permissions'  and then saw a message at the bottom saying, 

[I]
"you are not the owner, so you cannot change these permissions"[/I].



_What can I do to get Tomcat to let me run these examples?  Is it a file permissions issue? _

---

