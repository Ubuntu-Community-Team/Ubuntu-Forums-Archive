---
title: "How to connect JSP with mySQL"
date: 2009-12-16
forum: Programming Talk
---

### Post by hendra40 on 2009-12-16
Hello everyone,
I have a problem about connection with mySQL.

I have written these code :

connection.jsp
```

<%


		
Connection con = null;
Statement st = null;

		Class.forName("com.mysql.jdbc.Driver").newInstance();
	//	out.print("success");
                con = DriverManager.getConnection( "jdbc:mysql://localhost:3306/education","username","password");

	        st = con.createStatement();

%>


```

index.jsp
```

<%@ page import="java.sql.*" %>

<%@ include file="connection.jsp" %>



<head>


<title>Home</title>


</head>



<body>


  

      <%

	  ResultSet rs = st.executeQuery("Select * from test");

	

	  while(rs.next())

	  {

	  	  

		 out.println(rs.getString("a")+"<br>"); 

	  

      	   }
		rs.close();

 	   %>      

  



</body>

</html>

```

Structure :
Database : education
Table    : test
column   : a

And I have error :
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

I have store mysql-connector-java-5.1.6.jar on /var/lib/tomcat6/webapps/ROOT/test/WEB-INF/lib

My link : [http://localhost:8081/test/index.jsp](http://localhost:8081/test/index.jsp)

Thanks for replying this thread.

---

