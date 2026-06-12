---
title: "Creating red5 applications"
date: 2010-07-29
forum: Programming Talk
---

### Post by tapas_mishra on 2010-07-29
Hi,
I am trying to create an application which will run on a Streaming Server.
The Streaming Server is Red5.

My application is a simple HTML page which should be able serve an flv file from Red5.

Before asking this question I have Googled checked some tutorials but it seems this thing is not documented properly and Red5 community is not so active.So I am asking here.

I created a folder named test in my red5 installation on Ubuntu 10.04 

I installed Red5 the latest from subversion.
In side 
/opt/red5/dist/webapps
I created a folder named test
 
which has 

    test

    WEB-INF
     streams

now in 

/opt/red5/dist/webapps/test/streams 
I kept my flv which I want to stream.

Also in 
/opt/red5/dist/webapps/test/WEB-INF
I created three files 
red5-web.properties  red5-web.xml  web.xml
the contents of whose are 

/opt/red5/dist/webapps/test/WEB-INF/red5-web.properties has

webapp.contextPath=/test
webapp.virtualHosts=*

/opt/red5/dist/webapps/test/WEB-INF/red5-web.xml has
[http://pastebin.com/Njf0Dwmr](http://pastebin.com/Njf0Dwmr)

and 

/opt/red5/dist/webapps/test/WEB-INF/web.xml
has
[http://pastebin.com/tddbRY9Y](http://pastebin.com/tddbRY9Y)

Now I tried to access my application on LAN as 
[http://192.168.1.5:5080/test](http://192.168.1.5:5080/test)
it failed what else do I need to do ?

---

### Post by freedevelopment_net on 2011-04-20
The detailed description how to create red5 application:
[http://www.freedevelopment.net/articles/red5-first-application-example.html](http://www.freedevelopment.net/articles/red5-first-application-example.html)

---

### Post by tapas_mishra on 2011-04-20
Thanks for your message you replied after approximately 9 months later to the date when the question was asked I am now out  of that job also.

---

