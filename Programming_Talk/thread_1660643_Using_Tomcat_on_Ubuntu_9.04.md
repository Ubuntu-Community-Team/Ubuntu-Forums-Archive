---
title: "Using Tomcat on Ubuntu 9.04"
date: 2011-01-05
forum: Programming Talk
---

### Post by RSASKA on 2011-01-05
Hello,

I am studying for J2EE certification for my job. Interesting topic, but I am totally novice.

Right now, I am following directions to run Tomcat

[http://www.ubuntugeek.com/how-to-install-tomcat-6-on-ubuntu-9-04-jaunty.html](http://www.ubuntugeek.com/how-to-install-tomcat-6-on-ubuntu-9-04-jaunty.html)

It runs, but when I attempt to access /etc/tomcat6/tomcat-user.xml, it says I do not have permission. 

I am the person who installed Ubuntu on my home Dell Laptop.

Please guide.

---

### Post by RSASKA on 2011-01-05
OK, I was able to edit the file, but I still have problems. Below is the updated file:

GNU nano 2.0.9       File: /etc/tomcat6/tomcat-users.xml                      

<?xml version='1.0' encoding='utf-8'?>
<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at

      [http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->
<tomcat-users>
<!--
  <role rolename="tomcat"/>
  <role rolename="role1"/>
  <user username="tomcat" password="tomcat" roles="tomcat"/>
  <user username="both" password="tomcat" roles="tomcat,role1"/>
  <user username="role1" password="tomcat" roles="role1"/>

  <role rolename="manager"/>
  <role rolename="admin"/>
  <user name="admin" password="admin" roles="manager,admin"/>
-->
</tomcat-users>


When I restart Tomcat, and then go to [http://localhost:8080/manager/html](http://localhost:8080/manager/html), I keep entering admin admin as username and password, but I get error 401 Unauthorized.

Please help!

---

### Post by Some Penguin on 2011-01-05
"<!--" and "-->" denote comment blocks in XML...

---

### Post by RSASKA on 2011-01-05
> **Some Penguin said:**
> "<!--" and "-->" denote comment blocks in XML...


You are awesome!!!!!

---

