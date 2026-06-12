---
title: "Ubuntu 11.10 and Netbeans 7.1: SVN problem"
date: 2012-03-01
forum: Programming Talk
---

### Post by erotavlas on 2012-03-01
Hi, 

 I have a problem with Ubuntu 11.10 and NetBeans 7.1. The problem is with the SVN. I have recently updated to the latest Ubuntu 11.10 from 11.04 and now I can't reach the SVN. Before the update process all worked well. 
 I get this error: 

```


 org.tigris.subversion.javahl.ClientException: Commit failed (details follow): 
 Malformed reply from SOCKS server 
 OPTIONS request failed on '/svn/project' 

```

 I'm behind a proxy but NetBeans can update itself and download the available plugins. 

 What could be the problem? 

 Thank you

---

### Post by dazman19 on 2012-03-09
I program on a machine that was upgraded from 11.04 to 11.10 and all the while i have used netbeans 7 (maybe 7.1) im not sure it auto updates itself.

I never use netbeans to do commit's. I use it to display the blue/red/green/black names of the files, but i dont use it for committing its a bit much.

I use rapid SVN and meld to do my compare work.

This generally tends to give useful error messages which i can generally google to find why its not commiting/checking out.

Sorry i didnt answer your question, i dont know how to fix the problem, but I have avoided it period by using rapidsvn.

---

