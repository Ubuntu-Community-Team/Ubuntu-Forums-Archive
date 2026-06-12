---
title: "Gambas3"
date: 2018-10-08
forum: Packaging and Compiling Programs
---

### Post by neelabh.dutt on 2018-10-08
Public Procedure Connect()
  Dim $Con As New Connection
  '$Con.close()
  $Con.type = "mysql"
  $Con.Host = "localhost"
  $Con.Login = "root"
  $Con.Port = "3306"
  $Con.Name = "sys"
  $Con.Password = "xyzd"
  $Con.name = "mysql"
  $Con.open()
End
 

This code generates error on my machine. It says "Cannot Connect with the server. Please help.

---

### Post by neelabh.dutt on 2018-10-10
Hello! Please tell me how to install Gambas on Ubuntu Bionic Beaver. Database cannot be connected. There is some trouble.

---

