---
title: "how to install mapserver on ubuntu"
date: 2015-01-23
forum: New to Ubuntu
---

### Post by Liden75 on 2015-01-23
am new to the world ubuntu,
 I'm finding it very difficult to understand how it handled the file system of the program ubuntu, with these permits to turn on and off.

 then,
 I have the need to install the programs for webgis.

 I installed without problems apache:

 sudo apt-get install apache2

 I try to write in the browser localhost and I get a page that tells me that apache runs.

 I create a folder (webgis) in my home and I start installing mapserver:

 cd / home / vittorio / webgis

 and then give the command

 sudo apt-get install mapserver cgi-mapserver-bin

 to this I am going to see if everything went well, by clicking on the link:

 http: // localhost / cgi-bin / mapserv

 but I get this error:

 not Found
 The requested URL / cgi-bin / mapserv was not found on this server.

 I have to change any file system folders?
 install the program as an administrator and not as a member?
 (I have not given the command sudo ??? and then from terminal how do you switch to administrator ???)

 Thank You

 Vittorio
 Naples, Italy

---

### Post by Holger_Gehrke on 2015-01-23
Since I don't have it installed, I can't tell you much. But from a quick look in synaptic I can tell you that there's a package named mapserver-doc. This should at least give you some pointers. After installation you can ask the package manager where the files have been installed by giving this command:
```

dpkg-query -L mapserver.doc

```

---

