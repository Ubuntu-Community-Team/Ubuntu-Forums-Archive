---
title: "Importing classes in JSP"
date: 2009-09-23
forum: Programming Talk
---

### Post by cph05a on 2009-09-23
How can I import a simple java class in JSP using Tomcat?

Currently I have this class:
```

package SimpleTest;

public class SimpleClassTest 
{
	private int param;
	
	public SimpleClassTest(int param)
	{
		this.param = param;
	}

	public int getParam() 
	{
		return param;
	}

	public void setParam(int param) 
	{
		this.param = param;
	}
}

```

I've compiled it into a class file and put it in Tomcat 6.0/webapps/ROOT/WEB-INF/classes/SimpleTest. I have the following JSP file:
```

<%@ page import="SimpleTest.*" %>
<%
	SimpleClassTest simp = new SimpleClassTest(5);
%>

```

This keeps giving me an error.

---

### Post by myrtle1908 on 2009-09-23
What's the error?

Normally you wouldn't use ROOT as the folder for your application.  From memory this is where the Tomcat welcome page etc. runs from.  You should instead create a separate folder under 'webapps' which should have the following structure as a minimum:-
```

webapps
  /myApp
    JSPs, HTML etc
    /WEB-INF
      web.xml (yes you need one of these)
      /lib
        JARs
      /classes
        /SimpleTest
          SimpleClassTest.class
```

You would then access the app like: [http://localhost:8080/myApp/myFile.jsp](http://localhost:8080/myApp/myFile.jsp)

Ultimately, you should consider using an IDE like Eclipse or something that can automate the build/deploy process.

---

### Post by froggyswamp on 2009-09-24
Since he's a newbie I'd rather recommend NetBeans since it's (much) more user friendly than Eclipse and also works better out of the box, no offence to Eclipse though.

---

### Post by cph05a on 2009-09-25
Thanks for the input, guys. I never did figure out why this wasn't working. My directory structure was the same as myrtle1908 mentioned. 

I ended up getting around it by using Eclipse (for Java EE version) to create .war files since they are easier to deploy (I hate netbeans).

---

