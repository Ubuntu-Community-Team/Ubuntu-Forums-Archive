---
title: "How to use JSTL tags without using jsp UseBean ?"
date: 2013-05-17
forum: Programming Talk
---

### Post by kunal00731 on 2013-05-17
[COLOR=#000000][FONT=Arial]I have a problem where i am supposed to stop XSS vulnerabilities . A typical example here is invulnerable.jsp :
[/FONT][/COLOR]
```
<h2><%= myObj.getElf() %></h2>
``` [COLOR=#000000][FONT=Arial]The myObj is an object of the kObj class , which i have created in the jsp file :[/FONT][/COLOR]

```
<% kObj myObj = [COLOR=#2B91AF]KSession[/COLOR].getPostInfo(session); %>
```[COLOR=#000000][FONT=Arial]The problem here is there is no use of use bean here in this framework. As a result usage of core JSTl becomes troubling and it does not work. For e.g when i try to do :[/FONT][/COLOR]

```
<h2><c: out value={$( myObj.elf)} /></h2>
``` [COLOR=#000000][FONT=Arial]It does not work and tells me that there is no value for the object elf with the . operator.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The kObj class is not strictly a POJO as well. Can some one suggest what i can do here ?[/FONT][/COLOR]

---

### Post by r-senior on 2013-05-17
Scriptlet expressions and declarations within simple scriptlets just operate on local variables inside the _jspService method. JSTL expressions use scoped (page, request, session and application scope) variables. You can make something scoped using JSP: useBean or JSTL's set tag, eg. <c:set ...> but you can't otherwise mix scriptlet variables and JSTL.

If you are creating variables in _jspService using scriptlets, the easiest way to access them is using scriptlets. JSTL becomes strong when servlets (or framework controllers) are stuffing data into request, session and application scope in an MVC architecture. In that scenario, the getPostInfo call would be in a servlet that puts the data into request scope and uses a request dispatcher to forward to the JSP which retrieves the data using JSTL.

---

### Post by kunal00731 on 2013-05-20
@r-senior : Thanks . I have tried out something with the page context, such as now i am setting the variable first in page context as :

> <%setPageContext("desiredObj",myObj.getElf());%>

Then i am feeding them inside c: out, the problem is while setting the attribute , i am still using scrip-let coding , which i don't want to do . 

That's why i was wondering, whether there isn't any way that i can retrieve the data using jstl right away and not use scrip-let coding any where ?

---

