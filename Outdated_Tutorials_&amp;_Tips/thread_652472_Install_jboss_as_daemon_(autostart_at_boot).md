---
title: "Install jboss as daemon (autostart at boot)"
date: 2007-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by CuBone on 2007-12-28
** Alterative **

Here is an alternative solution, since this guide is quite outdated (though it should still work). Thank you Monti

> **monti said:**
> I've created a fairly robust init script for JBoss here: [https://jira.jboss.org/jira/browse/JBPAPP-3194](https://jira.jboss.org/jira/browse/JBPAPP-3194)

The /etc/init.d/jboss script doesn't need editing, all configuration is done in /etc/default/jboss

All feedback is welcome.


The actual guide

**Introduction**

This guide will let you run jboss as a daemon, that means you'll have a jboss instance that starts a computer boot. When you download jboss you get some example init scripts for different distributions but none for ubuntu. I did however get it to work with minor changes to the red hat init script. This is how I did it, there might be some better way and if you find better solutions than the ones in this guide please let me now and I'll post them here. 

At the end of this tutorial you will have (if everything goes as planned) a jboss instance running that starts at computer boot with the help of a daemon script in /etc/init.d/. To keep things tidy jboss will have a separate user called jboss as process owner.

**Ubuntu versions tested**

Ubuntu 7.10 32 bit Server Version
Ubuntu 7.10 32 bit Desktop Version

**Step 1: Install suns jdk**

There have been problems reported with jboss and java 6 in the past. I don't know if there still is compatibility issues but to be safe I use java 5.

```

sudo apt-get install sun-java5-jdk


```

**Step 2: create the jboss user**

The reason to use a separate user account for jboss is to control the permissions of the jboss instance. You don't want jboss running as root with unlimited access to the whole system.  There is no password created for the jboss user, and you probably don't need one either (unless you actually want to login as the jboss user). 

```

sudo mkdir /home/jboss
sudo useradd -s /bin/bash -d /home/jboss jboss
sudo chown jboss:jboss /home/jboss/ 

```

**Step 3: Download jboss**

Go to [http://labs.jboss.com/jbossas/downloads/](http://labs.jboss.com/jbossas/downloads/) and get the latest stable version of jboss (4.2.2.GA when this guide was written). Download it to your home directory.
 Now you have a file in ~/jboss-4.2.2.GA.zip

I used unzip to extract the archive, to install it run
```
sudo apt-get install unzip
```
but feel free to extract it with what ever program you feel fit. 

sidenote:
When I installed jboss on my server I installed it in the /opt/folder instead of /home/jboss/. Where ever  you decide to put jboss make sure the jboss user has read and write permission to the jboss folder and it's subfiles/-folders. 

Move it to jboss home and extract it. To make a future upgrade of jboss a little easier a symlinc to jboss home is created. When you decide to upgrade jboss you'll just have to edit the symlinc to point to the new version. 

```

cd ~
sudo mv jboss-4.2.2.GA.zip /home/jboss/jboss-4.2.2.GA.zip
sudo chown jboss:jboss /home/jboss/jboss-4.2.2.GA.zip
sudo su jboss
cd ~
unzip jboss-4.2.2.GA.zip
ln -s jboss-4.2.2.GA jboss
exit

```

**Step 5:Get the init scriptt**

All the changes to the red hat init script is in the setup section in the beginning of the script. If you followed my guide to the letter you can download my version of the script thats attached to this post. If you installed java or jboss in other directories it's probably easier to edit the script your self. 

[COLOR="Navy"]**Option 1:** download my script

Download the scriptattached to this post to your home folder then run this to move it to the correct folder. 

```

sudo mv ~/jboss/jboss_init.sh /etc/init.d/jboss

```

**End option 1**[/COLOR]

[COLOR="DarkGreen"]**Option 2:** edit the original red hat script yourself.

Copy the red hat init script to the init.d directory and rename it. 

```

sudo cp /home/jboss/jboss/bin/jboss_init_redhat.sh /etc/init.d/jboss

```

This is all the changes I made to the scipt, nothing fancy, just som variables for jboss that needs to be set correct.

```

#define where jboss is - this is the directory containing directories log, bin, conf etc

JBOSS_HOME=${JBOSS_HOME:-"/home/jboss/jboss"}

#define the user under which jboss will run, or use 'RUNASIS' to run as the current user

JBOSS_USER=${JBOSS_USER:-"jboss"}

#make sure java is in your path

JAVAPTH=${JAVAPTH:-"/usr/lib/jvm/java-1.5.0-sun"}

#configuration to use, usually one of 'minimal', 'default', 'all'

JBOSS_CONF=${JBOSS_CONF:-"default"}

#the host where jboss should answer. o.o.o.o means answer all calls. set this to yourhost.com

JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}

# Uncomment this line to store the console output, otherwise it's sent to /dev/null
 (good for debugging)
# JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/server/$JBOSS_CONF/log/console.log"}


```

**End option 2**[/COLOR]

**Step 6: Install the init script **

Make your script owned by root and executable. 
Create run level shortcuts for the script.

```

sudo chown root:root /etc/init.d/jboss
sudo chmod ug+x /etc/init.d/jboss
sudo update-rc.d jboss defaults

```

To start jboss you type

```

sudo /etc/init.d/jboss start

```

If everything has gone as planned you should now have a functional installation of jboss that will start itself on computer boot. 

**Step 7: Redirecting traffic from port 80 to jboss port 8080 (Optional)**

The default port for jboss is 8080 but the standard port for http traffic is 80. Port 80 is however a restricted port and can only be bound by root. To get around this little pickle you can redirect the incoming traffic on port 80 to 8080, the same goes for the https traffic on port 443 to jboss 8443. Here's a way to do that. 

```

iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 8080 
iptables -t nat -A PREROUTING -p udp -m udp --dport 80 -j REDIRECT --to-ports 8080 
iptables -t nat -A PREROUTING -p tcp -m tcp --dport 443 -j REDIRECT --to-ports 8443 
iptables -t nat -A PREROUTING -p udp -m udp --dport 443 -j REDIRECT --to-ports 8443 

```

This forward script was originally found here, [http://www.2nrds.com/port-forwarding-in-linux](http://www.2nrds.com/port-forwarding-in-linux)

**Remove**
If you found a better way to do this or if you just don't want this installed anymore here's what you do.

Warning! All files will be removed from your sytem.

Remove the init daemon script
```

sudo /etc/init.d/jboss stop
sudo update-rc.d jboss remove
sudo rm /etc/init.d/jboss

```

Remove jboss files and user
```

sudo userdel jboss
sudo rm -r /home/jboss

```

Remove java
```

sudo apt-get remove sun-java5-jdk


```

Remove unzip
```

sudo apt-get remove unzip

```


**End**

That's all for me. This is my first ubuntu guide and my knowledge about linux is a bit limited. So if you think I made some bad decisions in this setup please let me know and we can make this guide better together.

---

### Post by codelion on 2008-01-02
Has to be plural instead of singular:

sudo update-rc.d jboss defaults

---

### Post by codelion on 2008-01-02
Also, for desired results I'm using a minus sign in

JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}

---

### Post by codelion on 2008-01-02
And for creating the user in order for it to work I had to create a group first, and I used these two lines instead of the three lines

sudo groupadd jboss
sudo useradd -s /bin/bash -d /home/jboss -m -g jboss jboss

No need for mkdir or chown.  The chown needed the group to exist, but here the -m option takes care of the mkdir and chown.

---

### Post by CuBone on 2008-01-03
> **codelion said:**
> And for creating the user in order for it to work I had to create a group first, and I used these two lines instead of the three lines

sudo groupadd jboss
sudo useradd -s /bin/bash -d /home/jboss -m -g jboss jboss

No need for mkdir or chown.  The chown needed the group to exist, but here the -m option takes care of the mkdir and chown.

Here my lack of linux experience shows. I'll look in too this and to your other posts to. Thank you for your input

---

### Post by mark_k on 2008-01-04
(1) Word to the wise, I created the 'jboss' user via the ubuntu gui widget (before I found this post) and set the default shell to '/bin/false'. Don't do that. Use the 'useradd' command above that specifies a login shell, or set it with the gui widget to a real shell, otherwise the user can't run java. Rookie mistake, but it threw me for a bit of a loop.

(2) I had to make the same +/- change for JBOSS_CONSOLE. It now looks like this

# Uncomment this line to store the console output, otherwise it's sent to /dev/null
# JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/server/$JBOSS_CONF/log/console.log"}

Thanks to everybody involved in putting this script together.


- Mark

---

### Post by drapsag on 2008-03-14
there is an error in your start/stop script

it must be:
JBOSS_BIND_ADDR=${JBOSS_BIND_ADDR:-"-b $JBOSS_HOST"}

---

### Post by medined on 2008-07-19
Thanks for the post.

---

### Post by AdagioParaCuerdas on 2008-07-25
i got an error with the sh script

# sudo /etc/init.d/jboss start
JBOSS_CMD_START = cd /home/jboss/jboss/bin; /home/jboss/jboss/bin/run.sh -c default
/etc/init.d/jboss: 71: Syntax error: "(" unexpected

it refers to:

> 
function procrunning() {
   procid=0
   JBOSSSCRIPT=$(echo $JBOSSSH | awk '{print $1}' | sed 's/\//\\\//g')
   for procid in `/sbin/pidof -x "$JBOSSSCRIPT"`; do
       ps -fp $procid | grep "${JBOSSSH% *}" > /dev/null && pid=$procid
   done
}


stop() {
    pid=0
    procrunning


---

### Post by johog on 2008-08-06
[FONT="Arial"]Tanks.
I'm running Ubuntu 8.04
Installed java-6 and jboss-5.0.0.CR1 
Editing of /etc/init.d/jboss become little different for me. 
[/FONT]
[FONT="Century Gothic"]#define where jboss is - this is the directory containing directories log, bin, conf etc
#JBOSS_HOME=${JBOSS_HOME:-"/usr/local/jboss"}	JOHOG
JBOSS_HOME=${JBOSS_HOME:-"/home/jboss/jboss"}

#define the user under which jboss will run, or use 'RUNASIS' to run as the current user
JBOSS_USER=${JBOSS_USER:-"jboss"}

#make sure java is in your path
#JAVAPTH=${JAVAPTH:-"/usr/local/jdk/bin"}	JOHOG
JAVAPTH=${JAVAPTH:-"/usr/lib/jvm/java-6-sun-1.6.0.06"}

#configuration to use, usually one of 'minimal', 'default', 'all'
JBOSS_CONF=${JBOSS_CONF:-"default"}

#the host where jboss should answer. o.o.o.o means answer all calls.	JOHOG
JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}
[/FONT]

---

### Post by alekeri on 2008-08-30
Thanks for this guide. It's for me is the only way to start JBoss as daemon on Ubuntu. 
I tried to use JS Wrapper as alternative way, but unfortunately my attempts was unsuccessful due to "wrapper: cannot execute binary file" error. May be somebody has experience with mentioned tool?

---

### Post by brightonmike on 2008-09-09
> **AdagioParaCuerdas said:**
> i got an error with the sh script

# sudo /etc/init.d/jboss start
JBOSS_CMD_START = cd /home/jboss/jboss/bin; /home/jboss/jboss/bin/run.sh -c default
/etc/init.d/jboss: 71: Syntax error: "(" unexpected

it refers to:
I came unstuck with this problem in the redhat script, something to do with the 'function' keyword? - Not enough shell skills!

I found an alternative script on the forum at:
[http://ubuntuforums.org/archive/index.php/t-492697.html](http://ubuntuforums.org/archive/index.php/t-492697.html)

which seems to work...

Thanks for the post and replies by the way..

---

### Post by octavio@javafact.com on 2008-09-14
> **AdagioParaCuerdas said:**
> i got an error with the sh script

# sudo /etc/init.d/jboss start
JBOSS_CMD_START = cd /home/jboss/jboss/bin; /home/jboss/jboss/bin/run.sh -c default
/etc/init.d/jboss: 71: Syntax error: "(" unexpected

it refers to:

According to "Portable Shell Programming" by Bruce Blinn, a function is not delcared with a "function" keyword.  A function is declared with only the function name.  Delete the mistaken keyword from the script and it will execute.

---

### Post by cristian.vulpe on 2008-09-19
Great information!
If I'd have knew that I wouldn't have spent the time to dig it for myself. However, if somebody is interested in my experience, I have installed JBoss 4.2.3.GA on my Ubuntu (8.04) machine and when trying to run it as a service I had some problems with the already-available scripts (e.g. for RedHat, SuSE, HPUX). Therefore I have derived the RedHat script and here are the steps that made my installation work:

   1. Create in **/etc/init.d** folder a file for the JBoss service (e.g. **jboss.sh**). Note that you need the right to create files there...
   2. Using your preferred editor (e.g. **gedit**), fill in the file with the following content (note that changes for your local installation are needed):
```

      #!/bin/sh
      #
      # This script has been derived from the following one:
      # $Id: jboss_init_redhat.sh 71252 2008-03-25 17:52:00Z dbhole $
      #
      # JBoss Control Script
      #
      # To use this script run it as root - it will switch to the specified user
      #
      # Here is a little (and extremely primitive) startup/shutdown script
      # for Ubuntu systems. It assumes that JBoss lives in /usr/local/jboss,
      # it's run by user 'jboss' and JDK binaries are in /usr/local/jdk.
      # All this can be changed in the script itself. 
      #
      # Either modify this script for your requirements or just ensure that
      # the following variables are set correctly before calling the script.
      #
      # Major changes from the original one:
      # * usage of the shutdown.sh script instead of killing the jboss' JVM process. This simplifies the structure of the script.
      # * added support for bind address change (see the JBOSS_HOST variable).

      #define the JAVA_HOME
      JAVA_HOME=${JAVA_HOME:-"/usr/local/jdk"}

      #define where jboss is - this is the directory containing directories log, bin, conf etc
      JBOSS_HOME=${JBOSS_HOME:-"/usr/local/jboss"}

      #define the user under which jboss will run, or use 'RUNASIS' to run as the current user
      JBOSS_USER=${JBOSS_USER:-"jboss"}

      #configuration to use, usually one of 'minimal', 'default', 'all'
      JBOSS_CONF=${JBOSS_CONF:-"default"}

      #bind address
      JBOSS_HOST=${JBOSS_HOST:-"127.0.0.1"}

      #define the script used to start jboss
      JBOSSSH=${JBOSSSH:-"$JBOSS_HOME/bin/run.sh -c $JBOSS_CONF -b $JBOSS_HOST"}

      #define the script used to stop jboss
      JBOSSST=${JBOSSST:-"$JBOSS_HOME/bin/shutdown.sh -S -s jnp://$JBOSS_HOST:1099"}

      if [ "$JBOSS_USER" = "RUNASIS" ]; then
      SUBIT=""
      else
      SUBIT="su - $JBOSS_USER -c "
      fi

      if [ -n "$JBOSS_CONSOLE" -a ! -d "$JBOSS_CONSOLE" ]; then
      # ensure the file exists
      touch $JBOSS_CONSOLE
      if [ ! -z "$SUBIT" ]; then
        chown $JBOSS_USER $JBOSS_CONSOLE
      fi 
      fi

      if [ -n "$JBOSS_CONSOLE" -a ! -f "$JBOSS_CONSOLE" ]; then
      echo "WARNING: location for saving console log invalid: $JBOSS_CONSOLE"
      echo "WARNING: ignoring it and using /dev/null"
      JBOSS_CONSOLE="/dev/null"
      fi

      #define what will be done with the console log
      JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}

      JBOSS_CMD_START="cd $JBOSS_HOME/bin; $JBOSSSH"
      JBOSS_CMD_STOP="cd $JBOSS_HOME/bin; $JBOSSST"

      if [ ! -d "$JBOSS_HOME" ]; then
      echo JBOSS_HOME does not exist as a valid directory : $JBOSS_HOME
      exit 1
      fi

      case "$1" in
      start)
        cd $JBOSS_HOME/bin
        echo JBOSS_CMD_START = $JBOSS_CMD_START
        if [ -z "$SUBIT" ]; then
            eval $JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &
        else
            $SUBIT "$JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &" 
        fi
        ;;
      stop)
        cd $JBOSS_HOME/bin
        echo JBOSS_CMD_STOP = $JBOSS_CMD_STOP
        if [ -z "$SUBIT" ]; then
            eval $JBOSS_CMD_STOP >${JBOSS_CONSOLE} 2>&1 &
        else
            $SUBIT "$JBOSS_CMD_STOP >${JBOSS_CONSOLE} 2>&1 &" 
        fi
        ;;
      restart)
        $0 stop
        # there must be a time between the "stop" and the "start" because the mentioned two are asynchronous operations.
        # this depends on how fast your machine is.
        sleep 3
        $0 start
        ;;
      *)
        echo "usage: $0 (start|stop|restart)"
      esac

```
   3. Configure the script to start for your preferred runlevels (e.g. 3 and 5). To do this you can use the **sysvconfig** utility.

The same information is available at [http://cristivulpe.blogspot.com/2008/09/jboss-on-ubuntu-as-system-v-service.html]("http://cristivulpe.blogspot.com/2008/09/jboss-on-ubuntu-as-system-v-service.html").

Regards,
  cristi

---

### Post by sPyTe on 2008-11-24
Thank you very much!! It seems works for me!! 

Just in case, thank you very much ^^!!!

---

### Post by csaxena on 2008-11-25
Hello All,

I am trying to RUN JBOSS As Daemon on Ubuntu Command Line Server. 
I have jboss-4.2.1.GA Server. 
After doing all the necessary set for running jboss as Daemon. I am getting an error saying "Command Not Found". "sudo /etc/init.d/jboss start"

& when i tried this command "sudo /etc/init.d/jboss.sh start" it says "sudo: unable to execute /etc/init.d/jboss.sh: No such file or directory"

Please help me out with this. 

-Chetan.

---

### Post by ringzhz on 2009-02-05
CuBone,

Thanks for all the effort of sharing this info. This guide is awesome and still works perfectly on server edition 8.10. The only problem I had was with this line in your init script:
> 
```
JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}
```

This needed to be changed to 
```
JBOSS_HOST=${JBOSS_HOST:-"-b 0.0.0.0"}
```
In order to work for me. 

Thanks again for the outstanding job!

---

### Post by JeppeM on 2009-02-25
Thanks for the guide. I'm just posting to clear up some of the confusing there seems to be with the JBOSS_HOST. If you've copied the init script for the downloaded jboss 4.2.2 codes, then you'll end up with a script that does not define JBOSS_HOST, however, it does define JBOSS_BIND_ADDR. The corect way to make this work like it should is to add JBOSS_HOST before the JBOSS_BIND_ADDR:

```

#define JBOSS_HOST so that it listens to all availible ips
JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}

#if JBOSS_HOST specified, use -b to bind jboss services to that address
JBOSS_BIND_ADDR=${JBOSS_BIND_ADDR:-"-b $JBOSS_HOST"}

```

Note that both the JBOSS_BIND_ADDR and JBOSS_HOST lines have been changed.

Other than that, thanks a lot for a great guide!

---

### Post by m2000 on 2009-05-09
Hello,

I have problems trying to autoboot JBoss 4.2.3 + Portal 2.7.2 on Ubuntu server 9.0.4 (on VirtualBox).

I have done the steps explained in this thread. 

Jboss booting halts: "Runtime shutdown hook called, forceHalt: true" and then it shuts down.

The script starts ok from console: sudo /etc/init.d/jboss start

My hosts file and permissions to jboss directories seem to be ok. 

Any idea what is wrong?


Console log:

Here we go
 Setup the JVM
 Setup the JVM classpath
 Set stuff
 Set native path
=========================================================================

  JBoss Bootstrap Environment

  JBOSS_HOME: /home/jboss/jboss-portal-2.7.2

  JAVA: /usr/lib/jvm/java-1.5.0-sun-1.5.0.18/bin/java

  JAVA_OPTS: -Dprogram.name=run.sh -server -Xms128m -Xmx512m -XX:MaxPermSize=256m -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -Djava.net.preferIPv4Stack=true

  CLASSPATH: /home/jboss/jboss-portal-2.7.2/bin/run.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.18/lib/tools.jar

=========================================================================

18:34:34,773 INFO  [Server] Starting JBoss (MX MicroKernel)...
18:34:34,780 INFO  [Server] Release ID: JBoss [Trinity] 4.2.3.GA (build: SVNTag=JBoss_4_2_3_GA date=200807181417)
18:34:34,781 INFO  [Server] Home Dir: /home/jboss/jboss-portal-2.7.2
18:34:34,781 INFO  [Server] Home URL: file:/home/jboss/jboss-portal-2.7.2/
18:34:34,781 INFO  [Server] Patch URL: null
18:34:34,782 INFO  [Server] Server Name: default
18:34:34,782 INFO  [Server] Server Home Dir: /home/jboss/jboss-portal-2.7.2/server/default
18:34:34,782 INFO  [Server] Server Home URL: file:/home/jboss/jboss-portal-2.7.2/server/default/
18:34:34,782 INFO  [Server] Server Log Dir: /home/jboss/jboss-portal-2.7.2/server/default/log
18:34:34,782 INFO  [Server] Server Temp Dir: /home/jboss/jboss-portal-2.7.2/server/default/tmp
18:34:34,802 INFO  [Server] Root Deployment Filename: jboss-service.xml
18:34:35,483 INFO  [ServerInfo] Java version: 1.5.0_18,Sun Microsystems Inc.
18:34:35,483 INFO  [ServerInfo] Java VM: Java HotSpot(TM) Server VM 1.5.0_18-b02,Sun Microsystems Inc.
18:34:35,483 INFO  [ServerInfo] OS-System: Linux 2.6.28-11-generic,i386
18:34:36,777 INFO  [Server] Core system initialized
18:34:44,067 INFO  [WebService] Using RMI server codebase: [http://127.0.0.1:8083/](http://127.0.0.1:8083/)
18:34:44,069 INFO  [Log4jService$URLWatchTimerTask] Configuring from URL: resource:jboss-log4j.xml
18:34:44,090 INFO  [Server] Runtime shutdown hook called, forceHalt: true
18:34:44,090 INFO  [Server] JBoss SHUTDOWN: Undeploying all packages
...

Thanks!

---

### Post by m2000 on 2009-05-09
double post (because of refresh, sorry)

---

### Post by CuBone on 2009-05-11
m2000

Try to move jboss to start later in the boot sequence. Since the script works when you start it manually later. Maybe something that jboss is dependent on hasn't been started yet (the network maybe?).

---

### Post by m2000 on 2009-05-11
> **CuBone said:**
> m2000

Try to move jboss to start later in the boot sequence. Since the script works when you start it manually later. Maybe something that jboss is dependent on hasn't been started yet (the network maybe?).


Ok, this seems to be the root of the problem. 

I defined the jboss to start in run level 3. The system stayed in run level 2 although I log in and network and gui works ok (I have Ubuntu server with Gnome installed). 

If I force level 3 (sudo init 3) jboss starts normally.

I'm new to Linux and now confused again. Why didn't the system reach run level 3?

Thanks,
m2000

---

### Post by CuBone on 2009-05-13
You shouldn't change the runlevel for it. Just make sure it starts later in the boot sequence

---

### Post by needhelpplease on 2009-07-17
See also: [Installing JBoss Server on Ubuntu](http://chiralsoftware.com/linux-system-administration/jboss-server-deployment.seam).  It covers more recent versions of Ubuntu (8.10) and also JDK 6.

---

### Post by xcxdark on 2009-08-03
Hi all,
I am a linux newbie and i couldn't get the jboss run.
I did everything described here also read some other post on internet. The problem is that jboss don't run even if i type: 
```
/etc/init.d/jboss start
```
this doesnt give any error but jboss doesn't start either. when i say:
```
/etc/init.d/jboss stop
```
it says there is no jbossas currently running so system recognizes the file..
Can someone help me?

Thanks

---

### Post by avjazelur on 2009-09-16
Hi all - 

I also am having trouble getting JBoss (4.2.3) started via an init script on Ubuntu 9.04. 

I presume this is because the tutorial above is targeted at Ubuntu 8.10. Does anyone know if a revised version of the init script has been produced?

Thanks -

---

### Post by MikeZ83 on 2009-09-27
Hi all

Seems like I've encountered a similar problem. I've tried to adapt the instructions to my environment but in the end there's never any reaction on port 80 or 8080.

Trying to start the daemon by hand results in the following line:
```
user@ubuntu904desktop:/opt/jboss$ sudo /etc/init.d/jboss start
JBOSS_CMD_START = cd /opt/jboss/bin; /opt/jboss/bin/run.sh -c default -b 0.0.0.0
```I'm trying to install Jboss (and later on Jboss Seam) in a virtual machine running a current Ubuntu 9.04 with the java-6-sun-1.6.0.16 installed from the repository.

The archive has been unpacked to /opt and given a symbolic link for easier maintenance.
```
user@ubuntu904desktop:/opt$ ls -lach
total 16K
drwxr-xr-x  4 user  user  4.0K 2009-09-27 03:50 .
drwxr-xr-x 21 root  root  4.0K 2009-09-27 04:14 ..
lrwxrwxrwx  1 root  root    14 2009-09-27 03:48 jboss -> jboss-5.1.0.GA
drwxr-xr-x  9 jboss jboss 4.0K 2009-09-27 05:50 jboss-5.1.0.GA
lrwxrwxrwx  1 root  root    19 2009-09-27 03:48 jboss-seam -> jboss-seam-2.2.0.GA
drwxr-xr-x 11 jboss jboss 4.0K 2009-09-27 05:09 jboss-seam-2.2.0.GA

```My only changes to the start script are the following lines:
```
JBOSS_HOME=${JBOSS_HOME:-"/opt/jboss"}
JBOSS_USER=${JBOSS_USER:-"jboss"}
JAVAPTH=${JAVAPTH:-"/usr/bin"}
JBOSS_BIND_ADDR=${JBOSS_HOST:-"-b 0.0.0.0"}
```Here's an excerpt from the current /etc/init.d/jboss file:
```
#define where jboss is - this is the directory containing directories log, bin, conf etc
JBOSS_HOME=${JBOSS_HOME:-"/opt/jboss"}

#define the user under which jboss will run, or use 'RUNASIS' to run as the current user
JBOSS_USER=${JBOSS_USER:-"jboss"}

#make sure java is in your path
JAVAPTH=${JAVAPTH:-"/usr/bin"}

#configuration to use, usually one of 'minimal', 'default', 'all'
JBOSS_CONF=${JBOSS_CONF:-"default"}

#if JBOSS_HOST specified, use -b to bind jboss services to that address
JBOSS_BIND_ADDR=${JBOSS_HOST:-"-b 0.0.0.0"}

#define the classpath for the shutdown class
JBOSSCP=${JBOSSCP:-"$JBOSS_HOME/bin/shutdown.jar:$JBOSS_HOME/client/jnet.jar"}

#define the script to use to start jboss
JBOSSSH=${JBOSSSH:-"$JBOSS_HOME/bin/run.sh -c $JBOSS_CONF $JBOSS_BIND_ADDR"}

if [ "$JBOSS_USER" = "RUNASIS" ]; then
SUBIT=""
else
SUBIT="su - $JBOSS_USER -c "
fi

if [ -n "$JBOSS_CONSOLE" -a ! -d "$JBOSS_CONSOLE" ]; then
# ensure the file exists
touch $JBOSS_CONSOLE
if [ ! -z "$SUBIT" ]; then
chown $JBOSS_USER $JBOSS_CONSOLE
fi
fi

if [ -n "$JBOSS_CONSOLE" -a ! -f "$JBOSS_CONSOLE" ]; then
echo "WARNING: location for saving console log invalid: $JBOSS_CONSOLE"
echo "WARNING: ignoring it and using /dev/null"
JBOSS_CONSOLE="/dev/null"
fi

#define what will be done with the console log
#JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}
JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/log/console.log"}

JBOSS_CMD_START="cd $JBOSS_HOME/bin; $JBOSSSH"
JBOSS_CMD_STOP=${JBOSS_CMD_STOP:-"$JAVAPTH/java -classpath $JBOSSCP org.jboss.Shutdown --shutdown"}

if [ -z "`echo $PATH | grep $JAVAPTH`" ]; then
export PATH=$PATH:$JAVAPTH
fi

if [ ! -d "$JBOSS_HOME" ]; then
echo JBOSS_HOME does not exist as a valid directory : $JBOSS_HOME
exit 1
fi

echo JBOSS_CMD_START = $JBOSS_CMD_START

case "$1" in
start)
cd $JBOSS_HOME/bin
if [ -z "$SUBIT" ]; then
eval $JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &
else
$SUBIT "$JBOSS_CMD_START >${JBOSS_CONSOLE} 2>&1 &"
fi
;;
stop)
if [ -z "$SUBIT" ]; then
$JBOSS_CMD_STOP
else
$SUBIT "$JBOSS_CMD_STOP"
fi
;;
restart)
$0 stop
$0 start
;;
*)
echo "usage: $0 (start|stop|restart|help)"
esac
```As you can imagine, any help in the right direction would be greatly appreciated.
Thanks in advance for your opinion.


[CENTER] **------------------------------------****-------------****---------------------****-------**
[LEFT]


[/LEFT]
[/CENTER]
** Addendum:**

Managed to find the source of one of my problems but there's still a catch.

Out of curiosity I started it directly using the run.sh file and found out that some of the Java during the init was complaining about a port being in use.

A quick Google search turned up the following result: [http://www.lamscommunity.org/dotlrn/clubs/technicalcommunity/forums/message-view?message_id=508530](http://www.lamscommunity.org/dotlrn/clubs/technicalcommunity/forums/message-view?message_id=508530)
And the 5th entry in that thread contains the solution:> If you are using linux, see if another instance is running (ps -ef|grep java). If it is JBoss, stop it by running /path-to-jboss/bin/shutdown.sh -S Once you are sure that Jboss or tomcat is running, then restart JBoss and you start up properly.
  Thanks,
  Ernie A quick lookup using **ps -ef|grep java** showed that VMware Server 2 (the one with that annoying web interface) and Apache were still running.
Told them to annoy someone else (read: stopped the services using **sudo /etc.init.d/vmware stop** and so on) and JBoss didn't complain anymore (or so I thought).

Starting it using the **run.sh** works just fine (JBoss AS page shows up on *localhost:8080*) but using the modified Red Hat script only results in some serious CPU load without any reply from port 8080.


[CENTER] **------------------------------------****-------------****---------------------****-------**
[LEFT]


[/LEFT]
[/CENTER]
[B] Addendum 2:
[/B]I'm not sure why but after making the following change the init script starts up the server and I get a sign of life from port 8080:
```
#define what will be done with the console log
#JBOSS_CONSOLE=${JBOSS_CONSOLE:-"/dev/null"}
JBOSS_CONSOLE=${JBOSS_CONSOLE:-"$JBOSS_HOME/log/console.log"}
```I've also attached an example of the log output since there are still errors but at least it seems to react again.

---

### Post by abhishek.ransingh on 2009-11-18
abhishek@abhishek-laptop:~$ sudo /etc/init.d/jboss start
[sudo] password for abhishek: 
JBOSS_CMD_START = cd /home/jboss/jboss-5.1.0.GA/bin; /home/jboss/jboss-5.1.0.GA/bin/run.sh -c default -b 0.0.0.0

I got the message like above.
Even in eclipse, its not working....
I'm even unable to change the port number..
Plzzzz do help me....

---

### Post by monti on 2009-12-01
I've created a fairly robust init script for JBoss here: [https://jira.jboss.org/jira/browse/JBPAPP-3194](https://jira.jboss.org/jira/browse/JBPAPP-3194)

The /etc/init.d/jboss script doesn't need editing, all configuration is done in /etc/default/jboss

All feedback is welcome.

---

### Post by adrianodfo on 2009-12-16
Refering to the post #16

I have the same problem. Did you get a solution?

---

### Post by monti on 2009-12-16
> **adrianodfo said:**
> Refering to the post #16

I have the same problem. Did you get a solution?

Just use the script in   #29 instead, problem solved.

---

### Post by brahim.abdesslam on 2010-02-17
> **codelion said:**
> Also, for desired results I'm using a minus sign in

JBOSS_HOST=${JBOSS_HOST:-"0.0.0.0"}

To use it on all IPs available on the server i needed to add the -b option even if no IP is specified to the start option.

JBOSS_HOST=${JBOSS_HOST:-"-b 0.0.0.0"}

Thanks for the post.

---

### Post by arm4n on 2010-04-20
> **csaxena said:**
> Hello All,

I am trying to RUN JBOSS As Daemon on Ubuntu Command Line Server. 
I have jboss-4.2.1.GA Server. 
After doing all the necessary set for running jboss as Daemon. I am getting an error saying "Command Not Found". "sudo /etc/init.d/jboss start"

& when i tried this command "sudo /etc/init.d/jboss.sh start" it says "sudo: unable to execute /etc/init.d/jboss.sh: No such file or directory"

Please help me out with this. 

-Chetan.

I have the same Error before, but only if I tried to run "jboss start" or "sudo jboss start" from etc/init.d folder. If I run "sudo /etc/init.d/jboss start", then it worked.

---

### Post by zerozone on 2010-05-19
Thanks. this tutorial it's OK for ubuntu 10.04 and jboss 5.1

---

### Post by LinuxLars on 2011-02-10
Thanks for the great post.

I'm running Ubuntu server 10.10 and JBoss AS 6.0. Followed the guidelines but am getting an error when I'm trying to start JBoss:

[FONT="Courier New"]# sudo /etc/init.d/jboss start
-su: -c: line 0: syntax error near unexpected token `2&#8242;
-su: -c: line 0: `cd /usr/local/jboss-6.0.0.Final/bin; /usr/local/jboss-6.0.0.Final/bin/run.sh -c default -b 0.0.0.0 > 2>&1 &’[/FONT]

If I change to the jboss bin directory and start it manually, it starts up fine. 

Anyone know what’s going on here?
Thanks!

---

### Post by CuBone on 2011-02-10
You are redirecting your output but there is no file specified for the output

...run.sh -c default -b 0.0.0.0 > 2>&1 &

should be 

...run.sh -c default -b 0.0.0.0 > /path/to/a/logfile 2>&1 &

or if you have enough logging setup within the logging framework in jboss you can 
just remove the outputredirect

...run.sh -c default -b 0.0.0.0 &

---

### Post by LinuxLars on 2011-02-10
Aha! Thanks!

---

### Post by mariejones on 2011-06-07
had the same problem as LinuxLars, but now it is solved

---

