---
title: "Migrated Webapp CSS Not Loading"
date: 2013-03-27
forum: Programming Talk
---

### Post by proksy on 2013-03-27
OK, this isn't my first rodeo so-to-speak but I have run into a wall trying to get CSS to work on a new 12.04 LAMP + tomcat build.  I had an old web developer work station i needed to "recycle" and so I copied the web app project directly over to the new computer.  We use eclipse the make java jsp webapps.  The old workstation is still up and working perfectly fine but the new workstation will not load CSS no matter what I do.  When I use firebug to debug it shows CSS pointing to localhost:8080/css/ and recognizes the css file, styles.css with a checkmark next to the file name.  When I try to navigate to localhost:8080/css/styles.css I recieve _The requested resource (/css/styles.css) is not available._ So firebug finds and sees the styles.css but tomcat doesn't.  My code for the html is the following:

```

 <!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" 
"http://www.w3.org/TR/html4/loose.dtd"> 
<html> 
    <head> 
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> 
        <title>Login Page</title> 
        <link href="../css/styles.css" rel="stylesheet" type="text/css" media="all" />
    </head> 
<body>
Work damn you'z!!!
<div id="head">
 <div id="head_cen">
  <div id="head_sup" class="head_pad">
   <p class="search">
   </p>
    <h1 class="logo"><a href="index.html"></a></h1>
    <ul>
    </ul>
  </div>
 </div>
</div>
<div id="content">
 <div id="content_cen">
  <div id="content_sup" class="head_pad">
   <div id="welcom_pan">
    <h2><span>Work!!! </span>Login</h2>
    <br><br>
   </div>
  </div>
 </div>
</div>
<div id="foot">
 <div id="foot_cen">
 <p>created by: A Huge Pain-in-the-neck<a href="" target="_blank"></a></p>
 </div>
</div>
</body> 
</html>

```

The styles.css code is absolutely not the issue here because I have the working webserver right in front of me and have simply copied the files over to the new server.  I have googled this and have followed the steps provided here:

[http://stackoverflow.com/questions/7636360/why-doesnt-tomcat-6-find-my-styles-css](http://stackoverflow.com/questions/7636360/why-doesnt-tomcat-6-find-my-styles-css)

I have tried referencing styles.css from the project folder of eclipse and the ROOT/css/ directory in tomcat with no success.  A nice cold beer to anyone willing to help out ;)  Thanks everyone in advance.

---

### Post by proksy on 2013-04-05
quick update:  I still have not figured out what the issue is on this machine but I have built a separate computer using ubuntu 10.04 and all seems to be working quite well at the moment.  I have decided to make this a weekend project for me so I will keep this thread posted with what I find.

---

### Post by r-senior on 2013-04-05
This arrangement works for me on Tomcat 7: (It's not a repository install, it's just the tomcat zip file unpacked in my home directory).

```

$ cd ~/Software/apache-tomcat-7.0.25/webapps/
$ ls -R test css
css:
test.css

test:
index.html
$ cat css/test.css
h1 {
    color: red;
}
$ cat test/index.html 
<html>
<head>
<title>Test</title>
<link rel="stylesheet" href="../css/test.css" type="text/css"/>
</head>
<body><h1>Test</h1></body>
</html>
```

So basically that is a test and css directory under webapps; the test directory contains index.html which refers to the test.css file in the css directory using "../css/test.css". My heading is shown in red according to the stylesheet and I can see the content of that stylesheet with [http://localhost:8080/css/test.css](http://localhost:8080/css/test.css).

So it's either a typo somewhere, or your Tomcat is configured differently. Perhaps you could try unpacking the Tomcat zip file under your home and replicating the test above? To start the server, make sure nothing else is on 8080 and run startup.sh from the bin directory.

Then try it with your project. If it doesn't work, it's probably the project. If it does work, it's probably the settings in the repository install of Tomcat.

Having said all that, I usually put the css directory inside the context root of the web application and refer to that in the JSP with:

```
<link rel="stylesheet"	href="${pageContext.servletContext.contextPath}/css/tickets.css" ...
```

Obviously in that case you package the whole lot into a war file, including the css (which must be outside WEB-INF), and it gets exploded within its own directory under webapps.

---

