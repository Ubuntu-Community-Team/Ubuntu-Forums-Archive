---
title: "AJAX Problem"
date: 2010-08-15
forum: Programming Talk
---

### Post by VH-BIL on 2010-08-15
How do you set up AJAX in in monodevelop I am getting the error

```
Warning: Parser failed with error The tag type 'asp:UpdatePanel' has not been registered.. CodeBehind members for this file will not be added.
```

I don't want to have to move the project to VisualStudio

---

### Post by VH-BIL on 2010-08-15
I have managed to get the UpdatePanel registered with
```
<%@ Register assembly="System.Web.Extensions" namespace="System.Web.UI" tagprefix="asp" %>
```

But I am now getting a parse error:
```
System.Web.Compilation.ParseException: Property table not found in type System.Web.UI.UpdatePanel
```

---

### Post by VH-BIL on 2010-08-15
*bump*

---

