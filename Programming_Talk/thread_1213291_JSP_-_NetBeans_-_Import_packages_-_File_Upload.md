---
title: "JSP - NetBeans - Import packages - File Upload"
date: 2009-07-14
forum: Programming Talk
---

### Post by PaulM1985 on 2009-07-14
```

<%-- 
    Document   : index
    Created on : 27-Jun-2009, 19:18:56
    Author     : paul
--%>
<%@page contentType="text/html" pageEncoding="UTF-8"%>
<%@ page import="java.io.*" %>
<%@ page import="java.util.*" %>
<%@ page import="org.apache.commons.fileupload.*" %>
<%@ page import="org.apache.commons.fileupload.servlet.*" %>

 <%! void upload()
               {
                if (ServletFileUpload.isMultipartContent(request)){
          // Parse the HTTP request...
        ServletFileUpload servletFileUpload = new ServletFileUpload(new DiskFileItemFactory());
        List fileItemsList = servletFileUpload.parseRequest(request);
                }
        }
       %>

```

I have copied the file commons-fileupload-1.2.1.jar, which contains the fileupload and servlet packages but the upload statements fail saying that they do not exist.  Where abouts in a Netbeans project does my jar file need to be?

Thanks

Paul

---

### Post by PaulM1985 on 2009-07-19
Bump.

Essentially, this question is not about how to import and use that specific library, it is about where do I position my packages that I wish to import when using JSP and Netbeans.

Has anyone used Netbeans and JSP and imported packages that they have written, or .jar files from a different project?  If so, where in your path did you put your package for import?  Somewhere in Netbeans? Somewhere specific to the Apache Tomcat folder?

Any help would be much appreciated.

Paul

---

### Post by froggyswamp on 2009-07-19
Basically there are 2 steps
1. Create a folder in your project where you're about to put your libs.
2. Let Netbeans know about them.

1. Right-click the project name (in the "Projects" window) -> New -> Folder, call it (say) "lib". Now open your file browser, navigate to that folder and drop all the custom libraries that you have.
2.Right-click the project -> Properties -> Libraries -> Compile (tab) -> Add JAR/Folder and add the jar files, see attached image.

PS: any time you move to another computer you're likely to have to re-specify that path in NetBeans, for some reason, not a big problem though.

---

