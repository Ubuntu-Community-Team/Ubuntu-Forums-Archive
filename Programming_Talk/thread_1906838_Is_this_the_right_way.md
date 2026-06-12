---
title: "Is this the right way?"
date: 2012-01-10
forum: Programming Talk
---

### Post by Scarlet Sphere on 2012-01-10
I created an environment variable by adding the following line to ~/.bashrc file
```
export EJBCA_HOME=/home/user/ejbca
```
I also tried
```
export EJBCA_HOME="/home/user/ejbca"
```

When I type 
```
printenv
```
or 
```
echo $EJBCA_HOME
```
I see that it has been set. However, when I use the ```
System.getenv("EJBCA_HOME")
```
it returns a null value. 

I replaced it with 
```
System.getenv("PATH")
```
and it does not give a null value. So I think I may not have set the environment variable properly? I have logged out and logged in, restarted and also shutdown and turn it back on but nothing seems to work. 

Can someone help please:confused:

---

### Post by shakabra on 2012-01-10
Proper method is 
```
PATH=/path/to/new/file;$PATH
```
appended to you ~/.bashrc
You could do this in one step using this shell command
```
echo export PATH=\$\{PATH\}:\path/to/new/file >> ~/.bashrc
```

Also make sure you back up your bashrc. It's a pain when you accidently wipe out that file

---

### Post by Scarlet Sphere on 2012-01-10
> **shakabra said:**
> Proper method is 
```
PATH=/path/to/new/file;$PATH
```
appended to you ~/.bashrc


I added this line to ~/.bashrc
```
export EJBCA=/home/user/ejbca;$EJBCA
```

but it still does not work. What am I doing wrong?:confused:

---

### Post by jim_deadlock on 2012-01-10
You failed to follow shakabra's instructions correctly.

---

### Post by Scarlet Sphere on 2012-01-10
> **jim_deadlock said:**
> You failed to follow shakabra's instructions correctly.
Then how should it be?

I tried ```
echo export EJBCA=\$\{EJBCA\}:\/home/user/ejbca >> ~/.bashrc
```
but it still does not appear when I used System.getenv().
and when I "echo $EJBCA" , the result is ```
EJBCA=:/home/user/ejbca
```

System.getenv()still returns a null.:confused:

---

### Post by robsoles on 2012-01-10
> **jim_deadlock said:**
> You failed to follow shakabra's instructions correctly.

Why does it seem like everybody has assumed that Scarlet Sphere is trying to set the path in their system?


Hey Scarlet, been a while since I made new system variables that **weren't** already there (nor so intrinsic as the $PATH :roll:) but your method seems reasonable to me so I just wonder one thing:

Did you get the system to reload your environment by logging out and logging back in (or at least opening a new GUI terminal after modifying the file)?


I am probably wrong as to why you are not seeing **your** environment variable but I am positive those other guys are wrong what they think you are trying to do - please confirm any of this :)

---

### Post by shakabra on 2012-01-10
> **robsoles said:**
> Why does it seem like everybody has assumed that Scarlet Sphere is trying to set the path in their system?


Hey Scarlet, been a while since I made new system variables that **weren't** already there (nor so intrinsic as the $PATH :roll:) but your method seems reasonable to me so I just wonder one thing:

Did you get the system to reload your environment by logging out and logging back in (or at least opening a new GUI terminal after modifying the file)?


I am probably wrong as to why you are not seeing **your** environment variable but I am positive those other guys are wrong what they think you are trying to do - please confirm any of this :)
Yup I misread that. Jumped to conclusions. Whoops.

Environmental variable are stored in /etc/environment. Look there you should be able to figure it out.

---

### Post by Scarlet Sphere on 2012-01-11
This is for a web application which will use a file located in directory "/home/user/ejbca". Since I do not know of any way to get that location other than setting it as an environment variable, that is what I am trying to do. 

I am using java ```
System.getenv("EJBCA");
``` to get the environment variable but it always seems to return a null even though the environment variable seems to be set as ```
echo $EJBCA
```would return "/home/user/ejbca"

If I replace it(EJBCA) with some other random variable I chose from the "printenv" command, it will return that environment variable value. 

I have also tried it with windows environment variables(which I set) and it works. So the only explanation I can think of is that I must have set the environment variable wrong way?

---

### Post by robsoles on 2012-01-11
> **shakabra said:**
> Yup I misread that. Jumped to conclusions. Whoops.Best response I've ever seen to anyone saying something like I said :popcorn:

> **shakabra said:**
> Environmental variable are stored in /etc/environment. Look there you should be able to figure it out.Ahh, of course, but Scarlet Sphere may not realise why this is extremely likely to be the actual answer to the problem they have...


@[COLOR=Red](Imagine-this-as-some-large-spherical-shape)[/COLOR]

Pop this into terminal, you big red ball you!```
gksudo gedit /etc/environment
```After you type your password in I am expecting gedit to be open on your desktop with something like```
PATH="/usr/local/sbin:/usr/local/bin:....
```but of course the list of locations in your path is longer and there may have been other environment variables written there.

Add yours in exactly the same format - if it requires any kind of restart action to become active then just logging out and logging back in (GUI or TTY) won't be enough, an actual reboot will be required.

Has that cut that mustard for you sweetie?

---

### Post by Scarlet Sphere on 2012-01-11
Before reading previous post, I tested all the variables printed out when I run the command "printenv"

From this I found out that my variable was not the only one that returned a null value. 
> Variables that did not return null
PATH
HOME
COLORTERM
XAUTHORITY
LANG
DISPLAY
LANGUAGE
LOGNAME
USERNAME
PWD
LS_COLORS
USER
SHELL
TERM

Variables that did return null
GTK_MODULES
SSH_AGENT_PID
XDG_SESSION_COOKIE
ORBIT_SOCKETDIR
WINDOWID
GNOME_KEYRING_CONTROL
EJBCA
MANDATORY_PATH
LESSCLOSE
GDM_LANG
UBUNTU_MENUPROXY
COMPIZ_CONFIG_PROFILE
GDMSESSION
SHLVL
GNOME_DESKTOP_SESSION_ID
XDG_DATA_DIRS
DBUSS_SESSION_BUS_ADDRESS
LESSOPEN
WINDOWPATH
_
DESKTOP_SESSION
DEFAULTS_PATH
XDG_CONFIG_DIRS
GDM_KEYBOARD_LAYOUT
GNOME_KEYRING_PID
SESSION_MANAGER
SSH_AUTH_SOCK

All of these have values set. The only variable I created is EJBCA. Is there a reason why some of these will return a value and why some do not? I am confused :confused: 

After reading:
I couldn't find /etc/environment before so I had no idea. Now, I am looking at the file and there is only PATH and no others. Is this right?

---

### Post by robsoles on 2012-01-11
> **Scarlet Sphere said:**
> ...

I am looking at the file and there is only PATH and no others. Is this right?
Yup, that's right. Just append it with a line awfully similar this one:```
EJBCA_HOME="/home/user/ejbca"
```

---

### Post by Scarlet Sphere on 2012-01-11
> **robsoles said:**
> Yup, that's right. Just append it with a line awfully similar this one:```
EJBCA_HOME="/home/user/ejbca"
```
I have added the line, saved and also done a reboot. 
"echo $EJBCA_HOME" shows that it has been set but it still returns a null value for System.getenv(). :sad:

What else can I do?](*,)

---

### Post by robsoles on 2012-01-11
Can you try to dig up information on where your Java compiler is getting its copy of environment variables from?

I had a lash in Google and for someone with very little interest in java it was way too much noise to bother with, sorry.


Have I assumed correctly that you are using a JDK and not just a JRE? Um, oh, yeah: What version of Java are you trying this with? Is your compiler (or the JDK/JRE) starting its own environment with select system environment variables (under Ubuntu), or something really weird like that???

---

### Post by Scarlet Sphere on 2012-01-11
I have never used environment variables before this.
The version I am using is```
OpenJDK Runtime Environment (IcedTea6 1.10.4) (6b22-1.10.4-0ubuntu1~11.04.1)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
```

---

### Post by robsoles on 2012-01-11
OK, so I googled a bit more and found: [http://numberformat.wordpress.com/2010/01/24/setting-environment-variables-in-ubuntu/](http://numberformat.wordpress.com/2010/01/24/setting-environment-variables-in-ubuntu/)

Ridiculous as this may seem, I reckon you can try making the file (I assume it doesn't exist(?)) in your home directory, in terminal:```
gedit ~/pam_environment
```Is a nice quick way to be writing the correct file. Apparently the syntax is same as for /etc/environment so you don't need to use export in it.

When that fails my only remaining suggestion is to do your best to find out how the JDK gets any of the system's environment variables at all. Does it (java) list env variables it cannot show the contents of? (Pretty sure something I read said that invoked with no parameter the command returns a list of them - system.getenv() ?)

I think you should ask the moderators to move this thread to programming where it will quite possibly get noticed by somebody who likes java more than I do ;)

---

### Post by Scarlet Sphere on 2012-01-11
Thanks, I have tried that but it still gives null. 

How do I ask the moderators to move this thread to programming. Where is the programming thread?:confused:

---

### Post by howefield on 2012-01-11
> **Scarlet Sphere said:**
> How do I ask the moderators to move this thread to programming.

Done.

---

### Post by Zugzwang on 2012-01-11
@OP: Here is a guess: your .bashrc file is actually never read. This might for example happen if you start a program from the menu in Ubuntu. This might also happen if you, for example, start eclipse from the menu and then execute your program or open a shell from there. 

If my guess is the right one, the solution is to start your programs from a terminal.

Also, only bash will read the .bashrc file. Is probably your default shell set to something different? Try running "bash" explicitly and check if your environment variable has been set.

---

### Post by Stovey on 2012-01-11
Hi.  I am just a beginner, but I will throw in 2 cents anyhow.

I wonder if defining environment variables in .profile rather than .bashrc would make a difference?  Although I don't really see how , since I think .profile usually just runs .bashrc.

So in .profile you would enter:

EJBCA_HOME="/home/user/ejbca"
export EJBCA

Also, the reason printenv returned many environment variable that are null, is because many of them are null by default.

 Someone please feel free to correct me if I'm wrong.

---

### Post by ofnuts on 2012-01-11
> **Stovey said:**
> Hi.  I am just a beginner, but I will throw in 2 cents anyhow.

I wonder if defining environment variables in .profile rather than .bashrc would make a difference?  Although I don't really see how , since I think .profile usually just runs .bashrc.

So in .profile you would enter:

EJBCA_HOME="/home/user/ejbca"
export EJBCA

Also, the reason printenv returned many environment variable that are null, is because many of them are null by default.

 Someone please feel free to correct me if I'm wrong.
It seems that .profile is only run when you logon. All your processes inherit its environment, but that environment remains as it was when you logged on (this includes Eclipse/Netbeans, if started from your desktop).

To test System.getenv(), you have to either edit .profile and logoff/logon (then you can test everywhere, including in your IDE), or edit .bashrc, start a terminal, and either directly use Java there or start your IDE from there.

---

### Post by Scarlet Sphere on 2012-01-11
](*,)I'm still unsure of what to do but what I am actually trying to do is this. 

I have a web application which will make use of EJBCA_HOME to get to a file in that directory. I use ant build to get the .ear file which is then transferred to a jboss application server. 

To test if I can get the environment variable that has been set, I created a button which will display the value of the environment variable. When I press the button, a message dialogue will show the value. The code is below
```
String ejbcaDir = System.getenv("EJBCA_HOME");
    if (ejbcaDir == null) {
        ejbcaDir = "is null";
       JOptionPane.showMessageDialog(null,ejbcaDir.toString());
    } 
    else{
        JOptionPane.showMessageDialog(null,"home: "+ejbcaDir.toString());
    }
```
> Also, the reason printenv returned many environment variable that are null, is because many of them are null by default.
printenv shows that all the environment variables have been set, however, when I tested replaced "EJBCA_HOME" with the other variables which should not be null, some still returned null. I don't understand why this is so:confused:

So far, I have tried the following:

~/.bashrc
export EJBCA_HOME=/home/user/ejbca

gksudo gedit /etc/environment
EJBCA_HOME="/home/user/ejbca"

~/.pam_environment
EJBCA_HOME=/home/user/ejbca

/etc/profile.d/ejbca.sh
export EJBCA_HOME=/home/user/ejbca

~/.profile
EJBCA_HOME="/home/user/ejbca"
export EJBCA_HOME

/etc/profile
export EJBCA_HOME="/home/user/ejbca"

/etc/bash.bashrc
export EJBCA_HOME="/home/user/ejbca"

all of which will give a value when "echo $EJBCA_HOME" is used but gives a null for System.getenv()

Can anyone help?

---

### Post by fct on 2012-01-12
> **Scarlet Sphere said:**
> ]I have a web application which will make use of EJBCA_HOME to get to a file in that directory. I use ant build to get the .ear file which is then transferred to a jboss application server. 

If you're running applications in JBoss (or other application servers like WebLogic), then you can't rely on system environment variables. App servers usually isolate the applications from the host system, and provide their own environment.

Instead of env variables, setup some JBoss system properties for the application to use:

[https://community.jboss.org/wiki/SystemPropertiesInConfigFiles](https://community.jboss.org/wiki/SystemPropertiesInConfigFiles)
[https://community.jboss.org/wiki/PropertiesService](https://community.jboss.org/wiki/PropertiesService)

---

### Post by Scarlet Sphere on 2012-01-12
> **fct said:**
> If you're running applications in JBoss (or other application servers like WebLogic), then you can't rely on system environment variables. App servers usually isolate the applications from the host system, and provide their own environment.

Instead of env variables, setup some JBoss system properties for the application to use:

[https://community.jboss.org/wiki/SystemPropertiesInConfigFiles](https://community.jboss.org/wiki/SystemPropertiesInConfigFiles)
[https://community.jboss.org/wiki/PropertiesService](https://community.jboss.org/wiki/PropertiesService)

So according to this, I should create a local.properties file in jboss/server/default/conf and copy the whole text found in [https://community.jboss.org/wiki/PropertiesService](https://community.jboss.org/wiki/PropertiesService) and replace the properties like this?
> <server>
    <mbean code="org.jboss.varia.property.SystemPropertiesService"
           name="jboss.util:type=Service,name=SystemProperties">
            
        <!-- Load properties from each of the given comma seperated URLs -->
        <attribute name="URLList">
            [http://somehost/some-location.properties](http://somehost/some-location.properties),
            ./conf/somelocal.properties
        </attribute>
            
        <!-- Set properties using the properties file style. -->
        <attribute name="Properties">
            EJBCA_HOME="/home/user/ejbca"
            property2=This is the value of my other property
        </attribute>
            
    </mbean>
</server>

Is this right?

---

