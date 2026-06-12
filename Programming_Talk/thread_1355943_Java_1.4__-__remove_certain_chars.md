---
title: "Java 1.4  -  remove certain chars"
date: 2009-12-15
forum: Programming Talk
---

### Post by andrew222 on 2009-12-15
I have a Java 1.4 application that submits an XML document to a Siebel CRMS system.  

The business flow is that a user will enter data in a text field.  this data entered is then marshalled into nodes in an XML document using JAXB.  the XML document is encoded as UTF-16 as well.

I am having issues with users copying characters like the single qoute and double qoute characters from a .doc file and then pasting them into the text fields.  This in turn will cause processing errors on the Siebel side.

I would like to know if there is a way which we can look for these characters and replace them with a version of that character from a .txt file, particularly with JDK 1.4?

---

### Post by Physical Hook on 2009-12-15
[http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replace%28char,%20char%29](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replace%28char,%20char%29) ?

---

