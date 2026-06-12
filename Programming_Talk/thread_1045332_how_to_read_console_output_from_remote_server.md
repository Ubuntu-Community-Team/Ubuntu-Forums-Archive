---
title: "how to read console output from remote server"
date: 2009-01-20
forum: Programming Talk
---

### Post by Grace.zhang on 2009-01-20
I use tomcat as my server platform in Ubuntu.

when the user clicks a button (assume war application) and the action
'system.out.println' a message, how can I *remotly* read this message (read the message from a different computer instead of the server)?

when I use the eclipse, I can read it from the console but if I'm in a
different location, how can I see this message remotely?

I'm thinking about remote debugging (JPDA), however, it's very difficult to configure in order to make JPDA run. I tried based on tutorial of google search, bug failed.

I wonder if remote debugging can actually solve my problem. If not, is there any other to solve? Thank you!

---

### Post by linezfanatix on 2009-01-20
Connecting your app using eclipse remote debugger would not allow you to view the console logs. What you can do is use the "nohup" utility when you start your app server and redirect the output to some file. I use jboss server and the command looks like $ nohup ./run.sh -c <server_instance_name> > ../server/<server_intance_name>/log/nohup.out (assuming you are in the bin directory of your jboss installation). Usually the <server_instance_name> = "default"

Post this it would be pretty much up to you how you can view this file, I guess a putty connection and do tail -f on the file.

This is pretty much what I do to see the logs on remote machines. 

Hope this helps.

~ Amit

---

### Post by Grace.zhang on 2009-01-20
Thank you, Amit. But I'm using tomcat instead of JBoss. Do you have any idea how to do on tomcat? BTW, is the nohup.out the same idea with log4j except nohup.out can only contain the console output? 

Thanks again.

---

