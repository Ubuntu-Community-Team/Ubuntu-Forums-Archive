---
title: "urgent:problem with jsp's"
date: 2008-07-23
forum: Programming Talk
---

### Post by phanther on 2008-07-23
i have been working on compression and decompression of files using html interface, let me be more clear, it goes like this..

1)i have a html page where i have included a form "file" through frontpage which includes a text field and a browse button.thn i included a submit buttong.

my basic idea was to browse for a zipped file using browse button.once i have selected the file, the path will be shown in the text field.now when i click on the submit button, it will invoke the decompression code in the jsp i have created.the whole code is in java.

**my problem is tht when i am clicking the submit button, after the apache tomcat server iniates it is showing null pointer exception, i.e it is unable to read the path from the text field.

funny thing is a similar type of code is workin fr compression page but not for decompression.

i'll put up all the code i have used below.

if anyone can find the fault with the programming, pls help me solve it, i have to actually submit it to my dept. lecturer by friday, so i'm in a hurry, hope u understand.

*PS:i've done the whole thing using netbeans IDE 5.5

the html code fr the user interface is this:


//////////////////////////////////////////////////////////
<html>

<head>
<meta http-equiv="Content-Language" content="en-us">
<meta name="GENERATOR" content="Microsoft FrontPage 5.0">
<meta name="ProgId" content="FrontPage.Editor.Document">
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
<title>Compress</title>
<meta name="Microsoft Theme" content="slate 011">
</head>

<body bgcolor="#131313" background="background_slate.gif" text="#FFFFFF" link="#B6B04D" vlink="#707849" alink="#E6E18E">

<!--mstheme--><font face="Verdana,Arial,Helvetica,sans-serif">

<form method="POST" action="decompress2.jsp" enctype="multipart/form-data">
  <!--webbot bot="FileUpload" u-file="D:\GRIET\VMTS\web\_private\form_results.csv" s-format="TEXT/CSV" s-label-fields="TRUE" --><p align="center">
  <span lang="en-gb"><u><font size="6"><b>Decompress</b></font></u></span></p>
  <p>&nbsp;</p>
    <p><font size="5">&nbsp;
            </font>
  <p><span lang="en-gb">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  </span><input type="file" name="file" size="20"></p>
  <p>&nbsp;&nbsp;&nbsp; <span lang="en-gb">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  </span><button name="B1"><span lang="en-gb">submit</span></button></p>
  <p></p>
</form>

<!--mstheme--></font>

</body>

</html>
////////////////////////////////////////////////////////////


* in the form action i've used "decompress2.jsp".....the code is:

////////////////////////////////////////////////////////////


<%@ page import="java.util.zip.*,java.io.*" %>
<html>
<body>
<%@ page import="java.util.zip.*,java.io.*" %>
<html>
<body>
<%! int Buffer=2048;%>
<%
   BufferedOutputStream dest=null;
   byte data[]=new byte[Buffer];
   String a=request.getParameter("file");
   FileInputStream fi=new FileInputStream(a);
   ZipInputStream in1=new ZipInputStream(new BufferedInputStream(fi));
   ZipEntry entry;
   while((entry=in1.getNextEntry())!=null)
   {
    int count;
    FileOutputStream fo = new FileOutputStream(entry.getName());
    dest = new BufferedOutputStream(fo,Buffer);
    while((count=in1.read(data,0,Buffer))!=-1)
    {
     dest.write(data,0,count);
    }
    dest.flush();
    dest.close();
   }
   in1.close();
    %>

</body>
</html>
*here the name of the text field included in the form "file" is also "file".so i'm basically using a variable string "a" to copy the path in the text field and using to decompress it back again.

/////////////////////////////////////////////////////////////

after running and browsing for this path "C:\Users\phanther\abc.zip" and submitting it, this is the exception i'm getting

/////////////////////////////////////////////////////////////


HTTP Status 500 -

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

org.apache.jasper.JasperException: Exception in JSP: /decompress2.jsp:9

6:    BufferedOutputStream dest=null;
7:    byte data[]=new byte[Buffer];
8:    String a=request.getParameter("file");
9:    FileInputStream fi=new FileInputStream(a);
10:    ZipInputStream in1=new ZipInputStream(new BufferedInputStream(fi));
11:    ZipEntry entry;
12:    while((entry=in1.getNextEntry())!=null)


Stacktrace:
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:504)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:393)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:368)

root cause

java.lang.NullPointerException
	java.io.FileInputStream.<init>(FileInputStream.java:103)
	java.io.FileInputStream.<init>(FileInputStream.java:66)
	org.apache.jsp.decompress2_jsp._jspService(decompress2_jsp.java:53)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.netbeans.modules.web.monitor.server.MonitorFilter.doFilter(MonitorFilter.java:368)

note The full stack trace of the root cause is available in the Apache Tomcat/5.5.17 logs.
Apache Tomcat/5.5.17


pls tell me where lies the mistake and how to solve it, thanks in advance

---

### Post by tinny on 2008-07-23
Quick question...

Does tomcat have permission to read the file?

Also I notice that you buffer is only 2048 bytes, correct? How big is the file? 

Can you debug your JSP?

---

### Post by phanther on 2008-07-23
i think it does, the reason is i have used a similar jsp for compression which is working, it has the same html page too xcept tht the form action is for compression jsp, the code fr it is like this....


<%@ page import="java.util.zip.*,java.io.*" %>
<html>
<body bgcolor="#131313" background="background_slate.gif" text="#FFFFFF" link="#B6B04D" vlink="#707849" alink="#E6E18E">

<!--mstheme--><font face="Verdana,Arial,Helvetica,sans-serif">

<%! int Buffer=2048;%>
<%
BufferedInputStream origin=null;
FileOutputStream dest = new FileOutputStream("C:\\Users\\phanther\\abc.zip");
ZipOutputStream out1 = new ZipOutputStream(new BufferedOutputStream(dest));
byte data[]=new byte[Buffer];
String a=request.getParameter("file");
FileInputStream fi=new FileInputStream(a);
origin=new BufferedInputStream(fi,Buffer);
    ZipEntry entry=new ZipEntry(a);
    out1.putNextEntry(entry);
    int count;
while((count=origin.read(data,0,Buffer))!=-1)
    {
    out1.write(data,0,count);
    }
    origin.close();
   out1.close();%>
    <p align=center>Compressed</p>
<!--mstheme--></font>
</body>
</html>



this has worked perfectly, so i think when tomcat is allowing to read a normal file for compression thn it has to allow it fr decompressing a zipped file, still correct me if i'm wrong

---

### Post by phanther on 2008-07-23
as far as the buffer size is concerned, well i overlooked it, the compressed file is 1.04MB but i have given only 2048 bytes.does this cause the problem.i have debugged it and it says its fine

---

### Post by tinny on 2008-07-23
Opps...

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by phanther on 2008-07-23
Oh i understand tht it against the rules, but i'm quiet fed up of it, i've been trying it on my own for a month now, asked some of faculty from my college and even outside, discussed it with my friends and on.......but its still troubling me and the deadline is just a few days.as my last attempt to solve this, i've posted it here expecting some professional help.

so if u think its answerable pls do.

---

### Post by Kadrus on 2008-07-23
Use the CODE or PHP tags to post your code and to make it more readable for others.

---

### Post by datajelly on 2008-08-12
phanther,

I believe the problem is that you are using an enctype of mutlipart/form-data (which is correct for uploading files), but you cannot access this data using request.getParameter(). So request.getParameter("file") will return null, which is resulting in the NullPointerException. J2EE does not really have built-in support for handling file uploads.

You will need to look into using something like [Apache Commons FileUpload]("http://commons.apache.org/fileupload/index.html") to help you parse the file upload and provide you with a File.

---

