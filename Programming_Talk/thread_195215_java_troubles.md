---
title: "java troubles"
date: 2006-06-12
forum: Programming Talk
---

### Post by henrikwidth on 2006-06-12
Hi all

I have a dapper server-install with Tomcat5/jdk. The tomcat examples are working fine, but when i try to deploy an app that is developed on a windows machine I get this error:
```
HTTP Status 500 -

type Exception report

message

description The server encountered an internal error () that prevented it from fulfilling this request.

exception

javax.servlet.ServletException: Servlet.init() for servlet jsp threw exception
	java.security.AccessController.doPrivileged(Native Method)
	com.hotel.servlets.IndexS.service(IndexS.java:51)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

root cause

java.security.AccessControlException: access denied (java.lang.RuntimePermission accessClassInPackage.org.apache.jasper)
	java.security.AccessControlContext.checkPermission(AccessControlContext.java:264)
	java.security.AccessController.checkPermission(AccessController.java:427)
	java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
	java.lang.SecurityManager.checkPackageAccess(SecurityManager.java:1512)
	sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:265)
	java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1255)
	org.apache.catalina.loader.WebappClassLoader.loadClass(WebappClassLoader.java:1189)
	java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	org.apache.jasper.servlet.JspServlet.init(JspServlet.java:97)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:114)
	java.security.AccessController.doPrivileged(Native Method)
	com.hotel.servlets.IndexS.service(IndexS.java:51)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:802)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:585)
	org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:243)
	java.security.AccessController.doPrivileged(Native Method)
	javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
	org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:272)
	org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:161)

note The full stack trace of the root cause is available in the Apache Tomcat/5.0 logs.
```

I read somwhere that it could be the security policy that messes things up, but I don't know how to change it.

I'll truly appreciate some help here :)

Best regards

Henrik

---

### Post by henrikwidth on 2006-06-12
as mentioned here: [http://www.ubuntuforums.org/showthread.php?t=180029](http://www.ubuntuforums.org/showthread.php?t=180029)
I don't have CLASSPATH defined either.. how should I proceed?

Henrik

---

### Post by jvictor on 2006-06-13
CLASSPATH and JAVA_HOME needs to be set in ~/.bashrc of the person whos gng to run tomcat

my bashrc carries somethign like this
```

JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun
export JAVA_HOME

CLASSPATH=/home/juby/java/lib/mysql-connector-java-3.1.7-bin.jar:.
export CLASSPATH
```

can u post the code thats there in the class IndexS.java in and around line # 51

---

### Post by henrikwidth on 2006-06-13
Hi

Here is all of IndexS.java

```
package com.hotel.servlets;
import com.hotel.beans.HotelBean;
import com.hotel.values.*;
import java.util.StringTokenizer;
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.PrintWriter;
import java.io.IOException;

public class IndexS extends HttpServlet
{

  public void init(ServletConfig config) throws
ServletException
  {
    super.init(config);
  }

  public void service(HttpServletRequest request,
HttpServletResponse 
response) throws ServletException, IOException
  {
System.out.println("entrando al servlet");
String encabezado = request.getParameter("encabezado");
String textoUp = request.getParameter("textoUp");
String textoDown = request.getParameter("textoDown");
String campo1= request.getParameter("campoUno");
String campo2= request.getParameter("campoDos");
String campo3= request.getParameter("campoTres");
String campo4= request.getParameter("campoCuatro");
String codigo= request.getParameter("codigo");
CategoriaValue value = new CategoriaValue();
//String mensaje = "";

    try
    {
      HotelBean bean = new HotelBean();
     value = bean.getDetallePagina(codigo);

	request.setAttribute("detalleValue",value);
  
    System.out.println("el texto es---> " + encabezado );
    }
    catch (Exception e)
    {
      e.printStackTrace();
    }

    RequestDispatcher rdisp = 
    request.getRequestDispatcher("index.jsp");
    rdisp.forward(request, response);
   }
}
```

Henrik

---

### Post by jvictor on 2006-06-13
Hi 

In the corresponding class that has lines

```
CategoriaValue value = new CategoriaValue();
```

or

```
value = bean.getDetallePagina(codigo);
```

or

```
 HotelBean bean = new HotelBean();
```

By any chance are u using a System.exit(0); or something of that sort ? 
Usually you get this kind of errors when u try to do somethign of that sort.

Yes u r running into trouble due to the security manager, which doesnt allow unauthorized use of system properties , disk write / read etc.

You can find the security policy file at $TOMCAT_HOME/conf/catalina.policy

But editing it is not recommended in usual circumstances in other words for 'normal webapps'

Edit :-

In addition to it , I've some suggestions on your code . 

Since you are extending HttpServlet I suggest you must write the 'logic' in the doGet() or doPost() methods , as this is the 'recommended' way.

Are u able to install and run tomcat in your home directory ?

---

### Post by LordHunter317 on 2006-06-13
[QUOTE=jvictor]Since you are extending HttpServlet I suggest you must write the 'logic' in the doGet() or doPost() methods , as this is the 'recommended' way.[/quote]It umm, never got that far.  It blew up in the init() method for the servlet.

---

### Post by jvictor on 2006-06-13
```
com.hotel.servlets.IndexS.service(IndexS.java:51)
```

Hasnt it hit the service()  ??

The init of the JSP has failed, the underlying cause is that service's() line #51 has blew.

EDIT--
Maybe is he trying to do some stuff in the JSP like calling System props in a method within the JSP?

---

### Post by mlind on 2006-06-13
Do as jvictor said, override only doGet and doPost. You don't need to
implement lifecycle methods like init() if you don't plan to modify their current
behaviour.

I tried with Tomcat 5.5.xx and this worked out fine.


```

import java.io.IOException;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;


public class IndexS extends HttpServlet {
	private static final long serialVersionUID = 1L;
	
	@Override
	protected void doGet(HttpServletRequest request,
			HttpServletResponse response) throws ServletException, IOException {
		
		System.out.println("entrando al servlet");
		String encabezado = request.getParameter("encabezado");
		String textoUp = request.getParameter("textoUp");
		String textoDown = request.getParameter("textoDown");
		String campo1 = request.getParameter("campoUno");
		String campo2 = request.getParameter("campoDos");
		String campo3 = request.getParameter("campoTres");
		String campo4 = request.getParameter("campoCuatro");
		String codigo = request.getParameter("codigo");
		
		CategoriaValue value = new CategoriaValue();
		// String mensaje = "";
		try {
			HotelBean bean = new HotelBean();
			value = bean.getDetallePagina(/*codigo*/);
			request.setAttribute("detalleValue", value);
			System.out.println("el texto es---> " + encabezado);
		} catch (Exception e) {
			e.printStackTrace();
		}
		
		RequestDispatcher rdisp = request.getRequestDispatcher("index.jsp");
		rdisp.forward(request, response);
	}
	
	@Override
	protected void doPost(HttpServletRequest request,
			HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}
	
}

```

---

