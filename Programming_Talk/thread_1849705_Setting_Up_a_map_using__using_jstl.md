---
title: "Setting Up a map using  using jstl"
date: 2011-09-25
forum: Programming Talk
---

### Post by kunal00731 on 2011-09-25
Hi,
I am facing a problem that i am sure many have faced before , but i  myself could not arrive at a solution, hence need your support and  advice, friends.

I have a query which is retreiving two things for me, one is groupcode  and other is product name. Now i have to put them in a map as key -  value pairs and display the value for a particular key using check boxes  in jsp. I have used jstl here, But i am not realising how to go forward with the map and checkbox issue.
Kindly help, here is my code :
[HTML]
<%@ taglib uri="http://java.sun.com/jstl/core_rt" prefix="c" %>
<%@ taglib uri="http://java.sun.com/jstl/sql_rt" prefix="sql" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/functions" prefix="fn"%>
<%@taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<%@taglib prefix="x" uri="http://java.sun.com/jsp/jstl/xml" %> 
<sql:setDataSource driver="com.microsoft.sqlserver.jdbc.SQLServerDriver" url="jdbc:sqlserver://10.232.6.26:1433;databasename=uisample" user="iwdbuser" password="iwdbuser"/>
<html>
<body>
<sql:query var = "test1" >
select  frk_fundGroupCode , frk_productName from document_detail group by frk_fundGroupCode,frk_productName;
</sql:query>
<table border="0">
<c:forEach var="row" items="${test1.rows}">
<tr>
<td><input type="checkbox" name="id" value="">
<c:forEach var = "key" items ="${row.frk_fundGroupCode}" >
<c:out value="${key}"/>
<tr><td><input type="checkbox" name="id" value=""><c:out value = "${row.frk_productName}"/></td></tr>
</c:forEach>
</td>
<c:set var="count" value="${count + 1 }"></c:set>
</tr>
</c:forEach>
<input type="checkbox" name="id" value="number"><strong> Showing <c:out value = "${count}"/> Funds</strong>  for KIID Documents. 
</table>
</body>
</html>
[/HTML]currently i am getting the result as (consider []--->checkbox)
Showing 4 Funds for KIID Documents.
[]FTF
[]Franklin Templeton Strategic Dynamic Fund
[]FTF
[]Templeton UK Equity Fund
[]FTSAF
[]Franklin Mutual Shares Fund
[]FTSAF
[]Templeton Global Emerging Markets Fund

However, considering FTF as groupcode and key it has two values  -->Franklin Templeton Strategic Dynamic Fund,Templeton UK Equity  Fund.
So what i want is like :
[]FTF
      []Franklin Templeton Strategic Dynamic Fund
      []Templeton UK Equity Fund
[]FTSAF
      []Franklin Mutual Shares Fund
      []Templeton Global Emerging Markets Fund

Kindly tell me how to achieve this.                 :sad::sad::sad:

---

