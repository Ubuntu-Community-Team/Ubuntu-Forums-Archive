---
title: "Usage of ElementFactory.createXMLName"
date: 2012-01-18
forum: Programming Talk
---

### Post by caja0710 on 2012-01-18
Hi, I am hitting an issue when compiling the java program.  When using javac to compile the java file, it is returning 'cannot find symbol' and it is complaining I don't declare a varialbe of 'com'.  However, com is the path to another class file.  Does anyone know if it is the right way to call another class file within ElementFactory.createXMLName?


CreateUpdateWKRPCasesCodec.java:130: cannot find symbol
symbol  : variable com
location: class com.abc.CreateUpdateWKRPCasesCodec
        new PropertyInfo(ElementFactory.createXMLName("http://abc.com/", "caseRequestEntries", null), **[COLOR=Red]ElementFactory.createXMLName[/COLOR]**("http://abc.com/", "CaseRequestEntries", null), "caseRequestEntries", **[COLOR=Red]com/abc/CaseRequestEntries[/COLOR]**, false, true), new PropertyInfo(ElementFactory.createXMLName("http://abc.com/", "UserId", null), ElementFactory.createXMLName("http://www.w3.org/2001/XMLSchema", "string", null), "userId", java/lang/String, false, true), new PropertyInfo(ElementFactory.createXMLName("http://abc.com/", "Password", null), ElementFactory.createXMLName("http://www.w3.org/2001/XMLSchema", "string", null), "password", java/lang/String, false, true)
                                                                                                                                                                                                               ^

---

