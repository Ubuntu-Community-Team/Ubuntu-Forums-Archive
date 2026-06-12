---
title: "How do you tell an /etc/init.d/ script to execute as an alternate user ( not root ) ?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by jocko_johnson on 2008-08-26
Hello, I have a script (/etc/init.d/tomcat) that starts my Tomcat 6 at boot. Everything is working fine, but I figured it would be a good idea to have Tomcat run by a user "tomcat" with low privileges as opposed to running as root, the way it currently does

I can't figure out how to do this.

my current code looks like:
#!/bin/sh
#Tomcat auto-start service
#processname: tomcat

TOMCAT_HOME=/path..to..tomcat
export JAVA_HOME=/path..to..java

case $1 in
start)
sh $TOMCAT_HOME/bin/startup.sh
;;
stop)
sh $TOMCAT_HOME/bin/shutdown.sh
;;
....more....

I have a feeling that what I am trying to do can be accomplished by changing:

"sh $TOMCAT_HOME/bin/startup.sh"

to something like:

"sudo tomcat sh $TOMCAT_HOME/bin/startup.sh"

but I am not very experienced and have been unable to stumble upon the correct way.

Any help is greatly appreciated.

---

### Post by eightmillion on 2008-08-26
Maybe you could try:
> su - tomcat -c sh $TOMCAT_HOME/bin/startup.sh
If you don't run it as root, it will ask for tomcat's password. Hope this helps.

---

### Post by phidia on 2008-08-26
I think if you chmod and chgrp the script it will not run with root privledge.
See man chgrp & chmod.

---

### Post by caljohnsmith on 2008-08-26
Here's a recent thread that I think will solve your problem:
[http://ubuntuforums.org/showthread.php?p=5662769](http://ubuntuforums.org/showthread.php?p=5662769)

---

### Post by jocko_johnson on 2008-08-27
got the answer....

new script...

#!/bin/bash
#Tomcat auto-start at boot


CATALINA_HOME=path-to-tomcat-home
export JAVA_HOME=path-to-java-home

case $1 in
start)
	/bin/su <username> $CATALINA_HOME/bin/startup.sh
	;;
stop)
	/bin/su <username> $CATALINA_HOME/bin/shutdown.sh
	;;
restart)
	/bin/su <username> $CATALINA_HOME/bin/shutdown.sh
	/bin/su <username> $CATALINA_HOME/bin/startup.sh
	;;
force-reload)
	/bin/su <username> $TOMCAT_HOME/bin/shutdown.sh
	/bin/su <username> $TOMCAT_HOME/bin/startup.sh
	;;
esac
exit 0


thanks for your suggestions - a fellow geek at work helped me out with this and it works now.

so for anyone who wants to use this to configure tomcat 6 to startup ( using a user with lower privileges than root ) when the machine first boots:
1)create script in /etc/init.d/ called "tomcat"
2)copy the contents of the script I displayed above ( replace "<username>" with the name of the user with low privileges ) and save as "/etc/init.d/tomcat"
3)make script executable:  in the terminal type:
    sudo chmod 755 /etc/init.d/tomcat
4)create symbolic links:
  a)sudo ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
  b)sudo ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat
4)restart and tomcat should be running when your machine boots

thanks also to [howtogeek.com]("www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/") for creating the symbolic links to get the command "tomcat start" to be run at boot and command "tomcat stop" at shutdown.

edit:  one more note - be sure that the user you are going to run tomcat with is the owner of your tomcat install directory.
if this is not working ( to see the response for why it isn't working ) type "sudo sh /etc/init.d/tomcat start" and you should get a decent clue as to why it isn't working.

---

