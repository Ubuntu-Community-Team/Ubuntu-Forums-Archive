---
title: "Help running JSP"
date: 2007-02-13
forum: Programming Talk
---

### Post by Terryj1974 on 2007-02-13
Good afternoon everybody:

I have been trying my best to run JSP pages using Tomcat 5.5. For whatever reason, the pages will not run.

I am pretty sure that I need to change some configurations to get it to work right, but I have no idea where to start. Here is all of the information that I have (error it gave and my code)- if you need anything additional let me know.

Thank you in advance for your generousity!

Terry

//Error Message

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

org.apache.jasper.JasperException
	org.apache.jasper.servlet.JspServletWrapper.handleJspException(JspServletWrapper.java:510)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:375)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	java.lang.reflect.Method.invoke(Unknown Source)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Unknown Source)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

javax.servlet.ServletException
	org.apache.jasper.runtime.PageContextImpl.doHandlePageException(PageContextImpl.java:858)
	org.apache.jasper.runtime.PageContextImpl.access$11(PageContextImpl.java:796)
	org.apache.jasper.runtime.PageContextImpl$12.run(PageContextImpl.java:778)
	java.security.AccessController.doPrivileged(Native Method)
	org.apache.jasper.runtime.PageContextImpl.handlePageException(PageContextImpl.java:776)
	org.apache.jsp.mysql_jsp._jspService(mysql_jsp.java:109)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	java.lang.reflect.Method.invoke(Unknown Source)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Unknown Source)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

java.lang.NoClassDefFoundError
	com.mysql.jdbc.Connection.this(Connection.java:1174)
	com.mysql.jdbc.Connection.<init>(Connection.java:1404)
	com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)
	java.sql.DriverManager.getConnection(Unknown Source)
	java.sql.DriverManager.getConnection(Unknown Source)
	org.apache.jsp.mysql_jsp._jspService(mysql_jsp.java:66)
	org.apache.jasper.runtime.HttpJspBase.service(HttpJspBase.java:97)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:332)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:314)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:264)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	java.lang.reflect.Method.invoke(Unknown Source)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Unknown Source)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:275)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

note The full stack trace of the root cause is available in the Apache Tomcat/5.5 logs.

//Code

  1 <%@ page import="java.net.*" %>
  2 <%@ page import="java.util.*" %>
  3 <%@ page import="java.io.*" %>
  4 <%@ page import="java.sql.*" %>
  5 <%
  6
  7
  8   try{
  9   Class.forName("com.mysql.jdbc.Driver").newInstance();
 10   }
 11   catch (Exception E) {
 12   out.println("Unable to load driver.");
 13   E.printStackTrace();
 14   }
 15   try{
 16     out.println("Getting Connection ...");
 17  
 21       Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/dbname","<user>", "password");
 22 //    Connection conn = DriverManager.getConnection (url, userName, password);
 23       System.out.println ("Database connection established");
 24
 25       Statement S = conn.createStatement();
 26
 27       ResultSet rs = S.executeQuery("SELECT * FROM opponent");
 28       ResultSetMetaData rsStruc = rs.getMetaData();
 29       out.println("Table:  " + rsStruc.getTableName(1) + "<br>");
 30       out.println("<table bgcolor=c8c8c8 cellpadding=5 cellspacing=1>");
 31       out.println("<tr bgcolor=000000>");
 32       int colCount = rsStruc.getColumnCount();
 33       String colName = "";
 34       for(int i=1;i <= colCount; i++){
 35       colName = rsStruc.getColumnName(i) ;
 36       out.println("<td><B><font color=white>" + colName + "</font></b></td>\n");
 37       }
 38       out.println("</tr>");
 39       while (rs.next()) {
 40       out.println("<tr bgcolor=ffffff>");
 41       for(int i=1;i <= colCount; i++){
 42       colName = rsStruc.getColumnName(i) ;
 43
 44       String fld = rs.getString(colName);
 45         out.println("<td>" + fld + "</td>");
 46       }
 47       out.println("</tr>");
 48       }
 49       out.println("</table>");
 50       rs.close();
 51       conn.close();
 52   }
 53      catch (Exception E) {
 54    out.println("SQLException: " + E.getMessage());
 55      }
 56
 57 %>

---

### Post by LordHunter317 on 2007-02-13
It failed to load some Java class it wants.  Look in the Tomcat logs.

And, if you're going to insist on writing J2EE code that way, just use a damn servlet.  BUt you should probably look at a library to help you, like Wicket or similar.

---

### Post by lloyd mcclendon on 2007-02-13
ugh you really don't want to write webapps this way

jsp is such a steaming pile of dog crap it shouldn't be used to do anything besides present a view on already prepared data.  if you want to do java web development, you should look into using some frameworks to do the data access & logic, and then keep the jsps simple.  better yet you can ditch jsp altogether and use a nice templating language like freemarker.


[http://stripes.m4cj.org](http://stripes.m4cj.org)
[http://www.springframework.org](http://www.springframework.org)  -- both of these together is very nice, but might be a little over your head right now.
[http://www.hibernate.org](http://www.hibernate.org) - abstracts the database and just lets you just call save(someObject) - generates all the crazy sql

also checkout the display tag library, <display:table name="someList" /> is a lot easier than all those <td> tags


anyway,

java.lang.NoClassDefFoundError
com.mysql.jdbc.Connection.this(Connection.java:117 4)

looks like you didn't place the mysql jar file in tomcat_directory/common/lib ?

---

### Post by LordHunter317 on 2007-02-13
> **lloyd mcclendon said:**
> better yet you can ditch jsp altogether and use a nice templating language like freemarker.I'm not sure why you would want to replace a templating language with another templating language, unless you need outputs JSP cannot provide.  Either way, it's a terrible suggestion unless you need Freemarker.


> [http://stripes.m4cj.org](http://stripes.m4cj.org)
[http://www.springframework.org](http://www.springframework.org)  -- both of these together is very nice, but might be a little over your head right now.I'm not sure why one would want to combine Spring and Stripes, except to make life harder.  Spring doesn't gain you anything over Stripes, unless you're already using Spring.  And the combination of the two requires you to violate JavaBean naming conventions to be 100% secure because of boneheaded decisions made by both parties.  GG.

Better idea is something like Wicket, which really gets webapps right.  You don't need all this scaffolding, just the view<->code seperation.  Stripes is alright, but they tend to encourage too much logic in JSPs for my taste.  But if you like Stripes, that's fine.  Stripes + Spring is just begging for trouble.

> [http://www.hibernate.org](http://www.hibernate.org) - abstracts the database and just lets you just call save(someObject) - generates all the crazy sqlAssuming you can detail with all the constraints it imposes, sure.  And assuming you don't end up having to learn it's poor SQL replacement in the end anyway, sure.

> looks like you didn't place the mysql jar file in tomcat_directory/common/lib ?Couldn't possibly.  Actually read the backtrace.

---

### Post by lloyd mcclendon on 2007-02-13
> **LordHunter317 said:**
>   Either way, it's a terrible suggestion unless you need Freemarker.

No, it's not.  Freemarker templates are as readable as it gets, they do everything jsp does and more - except scriplets.  OP may have a problem with that one :)  .. I went from jsp to freemarker and i will never go back, jstl and el were bullshit ways of squeezing some power out of the xmlness of jsp.  freemarker is so readable it's a pleasure to work with.

> I'm not sure why one would want to combine Spring and Stripes, except to make life harder.  Spring doesn't gain you anything over Stripes, unless you're already using Spring.

you obviously have not seen my data access layer.  spring is an amazing framework, i'm not sure where you're getting the idea that it doesn't add anything.  AOP?  hibernate infrastructure?  setter injection?  Spring & stripes integrate very well with the @SpringBean annotation in the action bean.  adding spring in the middle layer was a piece of cake and has shrunk my code base by probably 30%! "don't repeat the DAO",  

> And the combination of the two requires you to violate JavaBean naming conventions to be 100% secure because of boneheaded decisions made by both parties.  GG.

what?  can you elaborate on this one?  i follow the javabean contract to the letter (ha) and all is well... 

> Better idea is something like Wicket, which really gets webapps right.  You don't need all this scaffolding, just the view<->code seperation.  Stripes is alright, but they tend to encourage too much logic in JSPs for my taste.  But if you like Stripes, that's fine.  Stripes + Spring is just begging for trouble.

never used wicket, won't comment.  the most logic we have in our jsps (freemarker) is a [#list] or [#if] ... and those are scarce.  90% pure html, css & js.  i'm guessing you saw the stripes examples with logic in the jsp and thought that it's the only way to do it - it's not.  user clicks a button, fires an event in the action bean, bean delegates all the business logic out to spring, and takes the user to another page.   again stripes + spring is actually a very pleasant mix... perhaps your thinking of spring web flow or spring mvc, just the container and some aop stuff is a great fit.

> Assuming you can detail with all the constraints it imposes, sure.  And assuming you don't end up having to learn it's poor SQL replacement in the end anyway, sure.

absolutely, hibernate is a bitch to figure out.  fortunately spring does help a ton with managing everything.  and hql isn't bad but it's confusing for people to pick up.

someone released an extension to stripes called stripernate, i hacked it around a good bit to work with spring - it is amazing how powerful this is.  we are working on some reflection based code to generate a full freemarker web interface to any domain model.  write your pojos w/ hib annotations, and manage them from the web w/ a sql backend.  cool stuff indeed.

---

### Post by LordHunter317 on 2007-02-13
> **lloyd mcclendon said:**
> No, it's not.  Freemarker templates are as readable as it gets, they do everything jsp does and more - except scriplets.They're not any better.

> you obviously have not seen my data access layer.I'm not sure I want to.

>  spring is an amazing framework, i'm not sure where you're getting the idea that it doesn't add anything.  AOP?  hibernate infrastructure?  setter injection?Why do I want those things?  Spring is just another Java -> XML conversion.  Most of the time, it actually fails to save me writing text, it just shifts what I'm writing.  This is why people abandoned Struts.  If you really need all those features integrated, then Spring can be a help.  Most projects do not, however, need all those features integrated.

> what?  can you elaborate on this one?  i follow the javabean contract to the letter (ha) and all is well... See the cautions here:[http://stripes.mc4j.org/confluence/display/stripes/Spring+with+Stripes](http://stripes.mc4j.org/confluence/display/stripes/Spring+with+Stripes)
That is to be read as: "Oops, we're retarded" and no other way. 

> guessing you saw the stripes examples with logic in the jsp and thought that it's the only way to do it - it's not.  user clicks a button, fires an event in the action bean, bean delegates all the business logic out to spring, and takes the user to another page.No, I know it's not.  But it's encouraged.  This is in constrast to say, the ASP.NET examples where it is encouraged to a lesser degree.

> again stripes + spring is actually a very pleasant mix... perhaps your thinking of spring web flow or spring mvc, just the container and some aop stuff is a great fitI'm thinking most applications don't need a View -> Action -> Business -> Data layer.

If you buy fully into the multi-tier koolaid, then I suppose you've at least listed the best-of-breed for what they do.  But I'm not sure that the approach is valid for most projects.

---

### Post by lloyd mcclendon on 2007-02-13
> **LordHunter317 said:**
> They're not any better.

I'm not sure I want to.

hahah.  scared?  it is pretty slick really, based on this with a few extra features [http://www-128.ibm.com/developerworks/java/library/j-genericdao.html](http://www-128.ibm.com/developerworks/java/library/j-genericdao.html) ..  cool stuff, spring AOP has piqued my interest a lot in the past few months

> Why do I want those things?  Spring is just another Java -> XML conversion.  Most of the time, it actually fails to save me writing text, it just shifts what I'm writing.  This is why people abandoned Struts.  If you really need all those features integrated, then Spring can be a help.  Most projects do not, however, need all those features integrated.

why i do i use them?  that's acutally a great question, and i'm having a hard time coming up with a clear answer other than "it's cool".  the xml files look bad but they're really not, especially if you turn autowiring on.  the main reason i intially made the move to spring was for the proven transaction demarcation & hibernate infrastrucure.  along the road i've discovered some unrelated cool stuff, and i expect to find lots more in the future.  it's a very general purpose framework, you are free to use as much or as little as you like.  my boss is a real sucker for the beandoc utility.

> See the cautions here:[http://stripes.mc4j.org/confluence/display/stripes/Spring+with+Stripes](http://stripes.mc4j.org/confluence/display/stripes/Spring+with+Stripes)
That is to be read as: "Oops, we're retarded" and no other way. 

not a problem at all, i read that a long time ago but completely dismissed it.  i don't need accessors for stateless business logic objects, so it's just  
@SpringBean
private UserManager userManager; 

you're saying this is a total deal breaker and it's not even a problem at all.  maybe i'm missing something?

> I'm thinking most applications don't need a View -> Action -> Business -> Data layer.

If you buy fully into the multi-tier koolaid, then I suppose you've at least listed the best-of-breed for what they do.  But I'm not sure that the approach is valid for most projects.

agreed it's not totally necessary for a lot of projects, but even for simple ones it is nice - once you've worked up to it.  I've progressed from pure jsp like what we have here, to jsp + stripes (sql statements in action beans), to jsp + stripes + hibernate DAO, to jsp + stripes + spring + hibernate.  

Even for small projects this archetecture has been a pleasure to work with.  throw in an ant project generator, a few python scripts for passive code generation and managing all the requried artifacts to support this are not a hassle.  if it wasn't for this damn html crap we could get large webapps out the door pretty quickly.  we've put so much effort into the back / middle tiers that they are by all means trivial and transparent.  the main problem we are trying to solve now is the stupid *** UI that takes forever to do a good job on.

---

### Post by LordHunter317 on 2007-02-13
> **lloyd mcclendon said:**
>  maybe i'm missing something?The fact that it's even a possibility, no matter how remote, means boneheaded design.  Attackers shouldn't be able to attack me just because I made something public.

---

### Post by lloyd mcclendon on 2007-02-13
> **LordHunter317 said:**
> The fact that it's even a possibility, no matter how remote, means boneheaded design.  Attackers shouldn't be able to attack me just because I made something public.

right, i've always wondered why those idiots are always telling us to use that private word all the time.  

that boneheaded design is actually what makes stripes so great: binding request parameters by name to a web of objects via accessor methods.  this vunerability does not only apply to @SpringBeans, but anything that has an get or set method in the bean is transparently bound to / from a http param.  there is actually an extension in the works (it might be out), to provide something like @DontBind or @DenyBinding / @AllowBinding to make this safer.   there's been a lot of debate about this on the mailing list, but everyone agrees it is absolutely necessary to prevent a jackass from binding something bad to something they shouldn't even see.

it is pretty scary, our database essentially has a full web frontend.  by viewing the source of the page & changing some text box or button names you could do some damage.  fortunately it's a secure site with trusted users so we haven't really cared to much about it.  the stripes validator can catch a lot of this stuff but not everything.

---

