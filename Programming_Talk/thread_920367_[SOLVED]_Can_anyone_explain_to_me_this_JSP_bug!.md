---
title: "[SOLVED] Can anyone explain to me this JSP bug!"
date: 2008-09-15
forum: Programming Talk
---

### Post by balagosa on 2008-09-15
```

 <%
      String strGender = rs.getString("gender");

      if(strGender.equals("male"))
      {
      	out.println("1");
      }

      if(rs.getString("gender").equals("male"))
		{
			out.println("2");
		}
      %>

```

In theory, the output should be "12". But guess what, only "2" was printed. I spent hours of debugging because I was supposed to use **strGender.equals** but the results only ended up in frustrations. So I made experiments, and the direct comparison of **rs.getString** was the result that worked.

Can anyone explain to me why?

---

### Post by NoReflex on 2008-09-15
I think the output is :
```
1
2
``` and you only get the last line ("2").
Could you try the same code using print instead of println?

Best wishes,
NoReflex

---

### Post by balagosa on 2008-09-15
You know what is weird...

the **strGender** already worked without me changing anything. All i did was eat my dinner, returned after 30mins, then it worked.

Not the first time I encountered this problem.

---

