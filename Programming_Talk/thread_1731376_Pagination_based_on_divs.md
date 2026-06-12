---
title: "Pagination based on divs?"
date: 2011-04-17
forum: Programming Talk
---

### Post by armageddon08 on 2011-04-17
I have a JSP page which loads comments posted to an article dynamically and displays them; each with its separate div. I want to paginate the comments based on the number of comments(hence, the number of generated divs). For example, if I have 10 comments/divs, I should get 2 pages and so forth.

Any pointers?

Here is the page if it be of any help:


[HTML]<%@page import="java.util.Vector"%>
<%@page import="java.util.Hashtable"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<style type="text/css">
.comment{
	margin: 2% 1.5% 2% 1.5%;
	padding: 2% 1.5%;
	background-color: #F0B2E0;
	-moz-border-radius:4px;
	-webkit-border-radius:4px;
	border: 1px solid #F0B2E0;
}
.comment_info{
	padding: 1% 1%;
	background-color: #E680CC;
	-moz-border-radius:4px;
	-webkit-border-radius:4px;
	border: 1px solid #E680CC;
}
.comment_poster{
	font-weight: bold;
}
.comment_date{
	margin-left: 3%;
}
.delete_comment:HOVER{
	cursor: pointer;
}
</style>
<script type="text/javascript" src="scripts/script.js"></script>
<script type="text/javascript" src="scripts/jquery-1.4.4.min.js"></script>
</head>
<body>
<% 
String userid = (String)session.getAttribute("uid");
Vector v;
Hashtable comments_data = (Hashtable)session.getAttribute("comments");
int size = comments_data.size();
%>
<h3>Comments</h3>
<%
for(int i=0;i<size;i++) {
	v = (Vector)comments_data.get(i);
%>
<div class="comment" id="comment_<% out.print(v.elementAt(0)); %>">
<div class="comment_info" id="comment_info_<% out.print(v.elementAt(0)); %>">
Posted By: <span class="comment_poster" id="comment_poster_<% out.print(v.elementAt(0)); %>"><% out.print(v.elementAt(2)); %></span>
<span class="comment_date" id="comment_date_<% out.print(v.elementAt(0)); %>">Posted On: <% out.print(v.elementAt(4)); %></span>
<%
	if(userid.equals((String)v.elementAt(1))) {
%>
<span class="delete_comment" id="delete_<% out.print(v.elementAt(0)); %>"><img title="Delete Comment" align="right" height="15px" width="15px" src="images/Error-icon.png"></span>
<script type="text/javascript">
$(document).ready(function(){
	$("#delete_<% out.print(v.elementAt(0)); %>").click(function(){
		alert('<% out.print(v.elementAt(0)); %>');
		deletecomment('<% out.print(v.elementAt(0)); %>');
	});
});

function deletecomment(comment_id) {
	$.post( "DeleteCommentServ", { commentid: comment_id }, 
			function() {
				alert("deleting......");
				loadcomments();
	});
}
</script>

<%
	}
%>
</div>
<p><% out.print(v.elementAt(3)); %></p>
</div>
<%
}
%>
</body>
</html>[/HTML]

---

### Post by armageddon08 on 2011-04-20
Anybody ? I'm really stuck at this moment....

---

### Post by smartbei on 2011-04-22
I am not quite sure what the problem is... What exactly is not working? Do you have a running version somewhere we can play with?

If the problem is **how** to do it, think about this code:
```

for(int i=0;i<size;i++) {
	v = (Vector)comments_data.get(i);

```
And how you might change it so that only *some* of the comments are printed.

---

