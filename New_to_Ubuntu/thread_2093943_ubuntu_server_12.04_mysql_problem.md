---
title: "ubuntu server 12.04 mysql problem"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by mihajlo92 on 2012-12-12
So I've setup my server with ubuntu server and came across some problems. First I bought a domain name from a hosting provider for my website and then ive setup my server like i said, so now i want my webpage to use mysql datase from my server at home. I tryed enabling remote control and according to some suggestions I did enable it, bit I still cant connect. I tried to connect to mysql database from my friends pc which i assume ot's the same using heidisql alltho no luck. I allowed all privileges to the user I created and commented out bind ip my.cnf file..Still no luck and I also did alot of other stuff and I cant get it to work. Can someone help me? Suggest somethig? Thank you in advance.

---

### Post by SeijiSensei on 2012-12-12
Let me see if I understand this.  You have a website on some remote server and a MySQL database at home that you want the remote site to use?  Do you have control over the remote server, or are you just buying hosting space?  If you purchased a hosting package, doesn't it come with MySQL?  If so, just use mysqldump to create a text file image of your database and install it on the web server.

If you want to connect from the web host to your local server, you'll need to open a port on your router and forward it back to port 3306 on your MySQL machine.  Then you should be able to connect to your home server using its IP address and the port you selected.  Note that this will only work reliably if your home computer has a static IP address.  Most residential connections do not come with one, so if your Internet provider changes your address one night, your website will no longer see the server.  I've had my address change if my router is offline for just a few minutes.

If this is just for fun, that's an acceptable solution.  But if this is a site that needs to be up 24/7, then you need a solution where the MySQL server and the web server are on the same machine or within the provider's network.

---

### Post by mihajlo92 on 2012-12-12
That's exactly I want to do. I think that I will upgrade my package from my provider to get a static IP so that I can use their mysql server instead of mine, think that is a better and easier solution. But you opened my eyes now, I just didnt want to pay them more for static IP since i got a cheap package where mysql server is locked and i can only use it using through phpmyadmin. Thank you for your help, with your reply i will be able to solve my problem.:guitar:

---

