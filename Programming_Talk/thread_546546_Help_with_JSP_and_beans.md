---
title: "Help with JSP and beans"
date: 2007-09-09
forum: Programming Talk
---

### Post by pmdkh on 2007-09-09
I need some help to figure out why my JSP is not working.

I am using Edgy Eft with Tomcat 5.5 from the repositories, along with the sun-java6-jdk.

I have a form in an HTML document (assignment3.3.html) that sends information to a JSP (auto_parts_process.jsp) that displays the data back to the user. Everything worked fine with it when I simply displayed the data to the back to the user. Now I'm trying to add a bean, and I'm having trouble.

Here is the relevant code in the JSP document:

```

<jsp:useBean id="ShippingMethod" scope="application" class="ShippingMethod"/>
<jsp:setProperty name="ShippingMethod" property="shippingMethod" value="<%= request.getParameter("shipping") %>"/>
<jsp:getProperty name="ShippingMethod" property="shippingMethod"/>

```

Here is the code from ShippingMethod.java

```

public class ShippingMethod {
  private String shippingMethod;

  public ShippingMethod() {
  }

  public void setShippingMethod(String x) {
    shippingMethod = x;
  }

  public String getShippingMethod() {
    return shippingMethod;
  }
}

```

This is the error that I get after I submit the information on the form:

```

An error occured at line: 73 in the jsp file: /auto_parts_process.jsp
Generated servlet error:
ShippingMethod cannot be resolved to a type

```

The same errors occurs for line 75. Line 73 is "useBean" line, and line 75 is the "getProperty" line.

The file "assignment3.3.html" and "auto_parts_process.jsp" are located in /var/lib/tomcat5.5/webapps/ROOT/

The file ShippingMethod.class is located in /var/lib/tomcat5.5/webapps/ROOT/WEB-INF/classes/

I think that the problem is probably something very simple, since I'm a beginner at this. If I need to post some more information, let me know.

Thanks for the help.

---

### Post by pmdkh on 2007-09-09
By reading through the Sun Java forums, I was able to fix whatever was wrong. I'll post this information in case someone else comes across it and might find it useful.

Here are the things that I changed. Note, I am not exactly sure what fixed the problem, because I might have had more than one error in my files.

I put the ShippingMethod.class file into the directory:

/var/lib/tomcat5.5/webapps/ROOT/WEB-INF/classes/test/

I also added this line to the beginning of ShippingMethod.java (and recompiled, of course)

```
package test;
```

Since I added a package name, I changed the useBean element to this:

```
<jsp:useBean id="shipping" scope="application" class="test.ShippingMethod"/>
```

I also changed the value of the id attribute because I wasn't sure if it needed to be different than the name of the bean. I saw other people doing it like that, so that's why I changed it. Because I changed the id attribute, I also changed the value of the name attribute for the setProperty and getProperty elements. Here is the code:

```
<jsp:setProperty name="shipping" property="shippingMethod" value="<%= request.getParameter("shipping") %>"/>
<jsp:getPropety name="shipping" property="shippingMethod"/>
```

So, in summary, these are the things that I changed:

1) Put the .class file in the package test
2) Changed the directory of the .class file
3) Changed the value of the class attribute of the useBean element
4) Changed the value of the id element of the useBean element, and subsequently, the value of the name attribute for the getProperty and setProperty elements

That's all. I hope I did a good job explaining and that this can come in useful for someone else.

---

### Post by pmdkh on 2007-09-09
One thing that I forgot to add is that I changed the web.xml file found in the CATALINA_HOME/conf directory. ( For me that file is ultimately located at /etc/tomcat5.5/web.xml ) I came across this information [at this page on the Sun Java forums]("http://forum.java.sun.com/thread.jspa?threadID=708154&messageID=4111577").

I changed it from this:

```

<init-param>
  <param-name>fork</param-name>
  <param-value>false</param-value>
</init-param>

```

to this:

```

<init-param>
  <param-name>fork</param-name>
  <param-value>true</param-value>
</init-param>

```

That's all.

---

