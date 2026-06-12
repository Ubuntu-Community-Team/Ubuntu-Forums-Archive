---
title: "Best Web Server with GUI for Ubuntu"
date: 2023-04-27
forum: New to Ubuntu
---

### Post by dodgy geezer on 2023-04-27
I don't know if you would call me a beginner - I've been running Ubuntu as a desktop service for some years - but I come from a Windows background and so am heavily reliant on a GUI interface. I have difficulty, for instance, understanding the file structure in Linux, which makes any CLI manipulation very dodgy...

A long time ago I set up a web site supporting a hobby. Nothing fancy, mainly static pages and downloads. It gets anything from 0=100 page reads a day.  It was set up on an XP machine using a simple and easy-to use free application - just download, run, fill in the URLs you want to service on the GUI and away it goes.  It runs behind a Smoothwall hardware firewall, and provides for multiple vhost sites.

It is now well out of date, no longer supported, and doesn't support HTTPS. Still runs well, but I should really update to a more modern system. And since I don't want to buy any more Windows, that means running on Linux - ideally Ubuntu.

But I simply cannot find an equivalent open source free application which matches it. All Linux web servers seem to have similar admin to Apache - a bewildering array of configuration files and additional services which need to be installed in a way I can't understand.  I recently tried to load Cherokee, which looked as if it had a GUI, and got: 

.......
Ign:6 [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu) jammy InRelease
Err:7 [https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu](https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Err:8 [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu) jammy Release
  404  Not Found [IP: 185.125.190.52 443]
.......
E: The repository 'https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
........
Package cherokee is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'cherokee' has no installation candidate
E: U nable to locate package cherokee-admin




which, of course, I don't understand.

So I have three questions:

1 - does anyone know of a small, simple, gui-based web server that does https and vhosts?
2 - what have I been doing wrong when trying to install Cherokee?
3 - Is what I am trying to do impossible, and should I be trying to do something different?

If you have read this far, thanks.  And even more thanks if you have any answers...

---

### Post by chris0nlinux on 2023-04-27
You can try building Cherokee from source using the instructions in the downloads page:[https://cherokee-project.com/downloads.html](https://cherokee-project.com/downloads.html) Don't forget to install python2 as this is a dependency of Cherokee! Just do a simple ```
sudo apt install python2
```
Let me know if this helps.

---

### Post by dodgy geezer on 2023-04-27
Thanks for the response!

I tried to follow the instructions on the download site, and succeeded in downloading a file called 'web-master' - but I don't know where it went.  Then the instructions tell me to follow the "/configure, make, make install dance:" - which I know nothing about at all.  I would guess that compiling from source involves finding compiler software, feeding a source file into it and getting an excecutable out. but I would be completely lost if I tried to do that.

It looks as if Cherokee is not going to be the simple gui application I hoped it would be...

---

### Post by ActionParsnip on 2023-04-27
[https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/dists/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/dists/)
[https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/dists/](https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/dists/)

the PPAs don't support Jammy and should be removed

---

### Post by dodgy geezer on 2023-04-27
Ah. What are the PPAs, and how do I remove them? 

Is it the case that Cherokee will not work in Ubuntu? If so, there seems little point in continuing...

---

### Post by ActionParsnip on 2023-04-27
They are PPAs that you have added. It's a conscious action. You can disable sources in the Software Centre

---

### Post by dodgy geezer on 2023-04-27
AP, I'm afraid that I do not understand what you have said. I don't know what a 'PPA' is, I didn't add anything beyond following the Cherokee Install instructions, and I don't know where the Software Centre is, nor how to 'disable sources' if I were ever to find it. As I said, I am used to a Windows GUI inteface, and have no knowledge of the underlying structure of Linux.

---

### Post by ActionParsnip on 2023-04-27
> **dodgy geezer said:**
> AP, I'm afraid that I do not understand what you have said. I don't know what a 'PPA' is, I didn't add anything beyond following the Cherokee Install instructions, and I don't know where the Software Centre is, nor how to 'disable sources' if I were ever to find it. As I said, I am used to a Windows GUI inteface, and have no knowledge of the underlying structure of Linux.

What is the output
```

cat /etc/apt/sources.list.d/*

```

---

### Post by dodgy geezer on 2023-04-27
The result of running that command is as follows. What did it do?

$ cat /etc/apt/sources.list.d/*
deb [https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/](https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/) jammy main
# deb-src [https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/](https://ppa.launchpadcontent.net/alex-p/qcad/ubuntu/) jammy main
deb [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main
# deb-src [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main
# deb [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) jammy main # disabled on upgrade to jammy
# deb-src [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) focal main
deb [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) focal main
# deb-src [http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu](http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu) focal main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable main # disabled on upgrade to jammy
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable main

---

### Post by grahammechanical on 2023-04-27
PPA = Personal Package Archive. It is a way of getting software that is not officially supported by the Ubuntu developers. A developer produces some software. He packages it and stores it in a personal archive or repository. To install a PPA as a repository in Ubuntu we run some commands that put the internet address of the repository/archive in a certain system text file.

To see what software sources/repositories you have (both official or PPA) open Software & Updates utility, The Ubuntu Software tab will list official Ubuntu repositories. The Other Software tab will list PPAs. Each PPA will have a check box that is ticked. Unticked the relevant PPAs

Regards

---

### Post by dodgy geezer on 2023-04-28
Ah - I have never come across this idea. When you download an excecutable in Windows you can execute it!

I found the Software/Updates utility, and found the Cherokee PPA lines ticked. I unticked them as suggested, and tried to download the install again, but got the same error. It looks as if teh required files just aren't there...

---

### Post by ActionParsnip on 2023-04-28
OK If you run
```

sudo apt update

```
Is it smooth?

---

### Post by ActionParsnip on 2023-04-28
Why does a web server need a GUI? You are editing config files to setup the service as needed.....

---

### Post by dodgy geezer on 2023-04-28
> **ActionParsnip said:**
> OK If you run
```

sudo apt update

```
Is it smooth?

Not sure what 'smooth' means - if I apply the command there is a set of 'jammu-updates' followed by this:

Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 c-n-f Metadata [14.2 kB]
Reading package lists... Done                                      
E: The repository 'https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by ActionParsnip on 2023-04-28
OK run:
```

grep chero /etc/apt/sources.list.d/*

```
This will show the file referencing the PPA. You can then remove it

---

### Post by dodgy geezer on 2023-04-28
> **ActionParsnip said:**
> Why does a web server need a GUI? You are editing config files to setup the service as needed.....

If you read the initial comment I made, you will see that I am a Windows GUI user trying to see if I can move over to Ubuntu. I do not understand enough about the Ubuntu O/S to configure a Web Server via the commad line - as you can see, I cannot even understand what is going on with the Download/Install process. 

It may be that there is no simple Ubuntu web server which can meet my needs, in which case I will have to reluctantly return to Windows...

---

### Post by ActionParsnip on 2023-04-28
> **dodgy geezer said:**
> If you read the initial comment I made, you will see that I am a Windows GUI user trying to see if I can move over to Ubuntu. I do not understand enough about the Ubuntu O/S to configure a Web Server via the commad line - as you can see, I cannot even understand what is going on with the Download/Install process. 

It may be that there is no simple Ubuntu web server which can meet my needs, in which case I will have to reluctantly return to Windows...

All config of a web server is done in command line. Instead of simply saying I don't understand.... learn something new. Apache is in the default repositories. You have followed some random guide online and caused issues. The repositories named in the guide only support older versions of Ubuntu.

---

### Post by dodgy geezer on 2023-04-28
> **ActionParsnip said:**
> OK run:
```

grep chero /etc/apt/sources.list.d/*

```
This will show the file referencing the PPA. You can then remove it


Output is:

grep chero /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/cherokee-webserver-ubuntu-ppa-jammy.list:deb [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main
/etc/apt/sources.list.d/cherokee-webserver-ubuntu-ppa-jammy.list:# deb-src [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main
/etc/apt/sources.list.d/cherokee-webserver-ubuntu-ppa-jammy.list.save:# deb [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main
/etc/apt/sources.list.d/cherokee-webserver-ubuntu-ppa-jammy.list.save:# deb-src [https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/](https://ppa.launchpadcontent.net/cherokee-webserver/ppa/ubuntu/) jammy main

However, when I look in the 'Files' window under Home I can't see any directory called 'etc'.  This makes me think that, although you are very kind to help me, I'm rather out of my depth, and unlikely to be able to run Cherokee successfully, even if we do get it working...

---

### Post by tea for one on 2023-04-28
> **dodgy geezer said:**
> However, when I look in the 'Files' window under Home I can't see any directory called 'etc'.  This makes me think that, although you are very kind to help me, I'm rather out of my depth, and unlikely to be able to run Cherokee successfully, even if we do get it working...
Files > Other Locations > Computer.
However, you will need sudo (elevated privileges) to edit System Files.

---

### Post by ActionParsnip on 2023-04-28
OK, run:
```

sudo rm /etc/apt/sources.list.d/cherokee-webserver*
sudo apt update 

```
Should now be smooth

---

### Post by tea for one on 2023-04-28
> **dodgy geezer said:**
> If you read the initial comment I made, you will see that I am a Windows GUI user trying to see if I can move over to Ubuntu. I do not understand enough about the Ubuntu O/S to configure a Web Server via the commad line - as you can see, I cannot even understand what is going on with the Download/Install process. 
It may be that there is no simple Ubuntu web server which can meet my needs, in which case I will have to reluctantly return to Windows...
Just offering information about GUI for Linux servers [https://cockpit-project.org/](https://cockpit-project.org/)
I'm sure that there are other alternatives via [https://alternativeto.net/](https://alternativeto.net/)

---

### Post by dodgy geezer on 2023-04-28
Brilliant!  This is the output:
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]                           
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]                            
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease [108 kB]                         
Get:5 [https://dl.cloudsmith.io/public/caddy/stable/deb/debian](https://dl.cloudsmith.io/public/caddy/stable/deb/debian) any-version InRelease [7,505 B]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [1,069 kB]               
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [912 kB]             
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [800 kB]                  
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main Translation-en [156 kB]                  
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 Packages [729 kB]             
Fetched 4,010 kB in 22s (178 kB/s)                                                                   
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.

What did you do? I'm guessing that this means that the Cherokee Web Server software is loaded on my machine, and all I have to do now is find out how to raise teh GUI to talk to it...

Thanks a lot!

---

### Post by dodgy geezer on 2023-04-28
> **tea for one said:**
> Just offering information about GUI for Linux servers [https://cockpit-project.org/](https://cockpit-project.org/)
I'm sure that there are other alternatives via [https://alternativeto.net/](https://alternativeto.net/)

Ah, now those are straight GUIs for servers. I'm looking to run a web server on a single Ubuntu box behind a hardware firewall, and wanted one that had a simple GUI setup and run...

---

### Post by TheFu on 2023-04-28
> **dodgy geezer said:**
> Ah - I have never come across this idea. When you download an excecutable in Windows you can execute it! 

Linux isn't Windows.  You'll need to get over that thought or you will be frustrated.
Linux speaks a completely different language and requires learning how to speak that language to do non-trivial things, like risk the entire security of your system, which is what a web server does.  

In Linux, running a web server is a big deal (and it should be), since it opens the entire system to being hacked.  The fact that WinXP allowed you to run a web server without understanding the risks is really a major issues.

I can't help with a GUI-based web server.  If I caught one running on my network, I'd immediately block that user from all computer access and talk with their manager about the risks so they could decide what retraining/punishment was needed.

Saying you don't know what something is is fine.  Using a web search to fill in knowledge gaps and asking questions for clarification is expected.  A web search for "ubuntu ppa" would easily have provided the answer. [https://help.ubuntu.com/community/PPA](https://help.ubuntu.com/community/PPA) is the first link returned.

Web servers need 20+ configuration settings, perhaps more if you care about security or want TLS support.  That doesn't really lend to being a GUI program.

If you have all your webfiles in a single directory and just want to share them locally, there are lots of 1 command web servers which will do exactly that, and nothing else. No TLS support.  Some examples:
```
Python 2.x
  $ python -m SimpleHTTPServer 8000

Python 3.x
  $ python -m http.server 8000

Twisted (Python)
  $ twistd -n web -p 8000 --path .


Ruby
   $ ruby -rwebrick -e'WEBrick::HTTPServer.new(:Port => 8000,
                        :DocumentRoot => Dir.pwd).start'

Ruby 1.9.2+
   $ ruby -run -ehttpd . -p8000

Perl
   $ cpan HTTP::Server::Brick   # install dependency
   $ perl -MHTTP::Server::Brick -e
           '$s=HTTP::Server::Brick->new(port=>8000);
            $s->mount("/"=>{path=>"."});
            $s->start'

Plack (Perl)
   $ cpan Plack   # install dependency
   $ plackup -MPlack::App::Directory -e
               'Plack::App::Directory->new(root=>".");' -p 8000

Mojolicious (Perl)
   $ cpan Mojolicious::Lite   # install dependency
   $ perl -MMojolicious::Lite -MCwd -e 'app->static->paths->[0]=getcwd;
                                    app->start' daemon -l http://*:8000

http-server (Node.js)
   $ npm install -g http-server   # install dependency
   $ http-server -p 8000

node-static (Node.js)
   $ npm install -g node-static   # install dependency
   $ static -p 8000

PHP (>= 5.4)
   $ php -S 127.0.0.1:8000

busybox httpd
   $ busybox httpd -f -p 8000

```
These all assume the CWD/PWD is the same as where the files are. If you don't know what CWD is, that's basic knowledge for every computer, including MS-Windows.  Any beginning tutorial/book should cover it for any OS. [https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)  is covered in that link on pg 3.  Basic knowledge.

---

### Post by dodgy geezer on 2023-04-28
I agree that Linux is not Windows. But I disagree with the statement that "a Web Server doesn't really lend to being a GUI program", if that means that it cannot be controlled entirely through a GUI front end.  The engine of the server is obviously hidden, but there is no reason why quite a complex web server should not be controlled entirely through a GUI.   I have been running one with no problems under Windows for over 10 years, without needing to know the innards of XP.

There may well not be an existing GUI-driven open source web server which is Linux-compatible. But such things, supporting multiple services and HTTPS, are surely perfectly possible. And that is all I am looking for...

---

### Post by TheFu on 2023-04-28
> **dodgy geezer said:**
> I agree that Linux is not Windows. But I disagree with the statement that "a Web Server doesn't really lend to being a GUI program", if that means that it cannot be controlled entirely through a GUI front end.  The engine of the server is obviously hidden, but there is no reason why quite a complex web server should not be controlled entirely through a GUI.   I have been running one with no problems under Windows for over 10 years, without needing to know the innards of XP.

There may well not be an existing GUI-driven open source web server which is Linux-compatible. But such things, supporting multiple services and HTTPS, are surely perfectly possible. And that is all I am looking for...

I never said it couldn't be done.  I said that it doesn't lend to being done that way.  However, since Linux servers are where web servers typically run and Linux server do not have any GUI, then what's the point?
For sharing files between desktops, there are other solutions, though many of those do require admin-level knowledge to setup.

You completely ignored the statements about poor security by allowing users to run a web server on a desktop. I suppose we'll agree to disagree on that.  That's fine.

There are web-apps that can control web servers.  Unfortunately, those usually require complex installs, configuration and added layers to make them secure enough to even be considered.  Something like webmin or cockpit come to my mind.  Those are not end-user tools.

I provided some simple 1-line web servers.  No need for a GUI at all. You only need 1 for a static website to work.  I don't understand why those aren't sufficient for your needs. After all, I suspect that pretty GUI you though was so amazing on WindowsXP did run just one of those behind the scenes.  Current, supported, releases of Ubuntu all have Python3 installed.  Is it really so hard to 

```
cd /path/to/the/files
python3 -m http.server 8000
```
That's the Unix way.  Try it.  It's easy.  Nothing extra to install. It will "just work".  Heck, I bet this would work on MS-Windows too, if python3 were installed.

If you want TLS (HTTPS), then there are some steps.  I'd use the Perl version with HTTP::Server::Brick myself, since the example to make it work is simple (for me) and here: [https://metacpan.org/pod/HTTP%3a%3aServer%3a%3aBrick](https://metacpan.org/pod/HTTP%3a%3aServer%3a%3aBrick)  Managing the certs are outside all web servers, so this isn't unexpected.  I use acme.sh to use free Let's Encrypt certs.

---

### Post by dodgy geezer on 2023-04-28
I wasn't sure what you were actually saying, which is why I questioned your comment. My original requirement is specified in my first post, which was a web server with a GUI front end to control it, able to host multiple web sites (at least 4), running on Ubuntu and supporting HTTPS. The point would be that I could understand a GUI presentation much more easily than I could a CLI. I know such things are possible, since I have been running one on a Windows system for over 10 years with no security problems, but I would like to move over to Ubuntu.  If I can.   The machine I run on is an XP desktop, though single purpose, and getting quite tired after running continuously all this time.  Ubuntu would allow me to run a more modern OS....

---

### Post by Holger_Gehrke on 2023-04-28
The cherokee-webserver is a project that can charitably be described as being in maintenance-mode. It had it's last release in 2013; the last changes in the github repository were bugfixes made two or three month ago. AFAIK there are no ready to install packages for current versions of Ubuntu. If you really want to run this, compiling and installing from source is the only option. I tried doing that today and it went relatively smoothly if we overlook all the warnings from the compiler about deprecated functions being used in the code. The 'GUI' for managíng the server is actually a local webserver on a different port which serves pages that allow you to configure the server. So basically something like one of those webmin-things but built into the server.

Holger

---

### Post by dodgy geezer on 2023-04-28
Ah - that IS useful news!  I was only going by the description, which suggested that it would be useful - that would also explain the difficulty in loading it.

I have noticed that there are some GUI front-ends for Apache - maybe I can get what I want with a LAMP load and one of these?

---

### Post by stevermann on 2023-04-28
Why not just use Apache2?  The only difference I can see is that Cherokee has a GUI for setup.  The thing is, I have never needed to configure my Apache setup as it works just fine right out of the box.  And the number of Apache users here probably outnumber the Cherokee users 100:1, so forum support is much more likely.

---

### Post by TheFu on 2023-04-28
> **dodgy geezer said:**
> I wasn't sure what you were actually saying, which is why I questioned your comment. My original requirement is specified in my first post, which was a web server with a GUI front end to control it, able to host multiple web sites (at least 4), running on Ubuntu and supporting HTTPS. The point would be that I could understand a GUI presentation much more easily than I could a CLI. I know such things are possible, since I have been running one on a Windows system for over 10 years with no security problems, but I would like to move over to Ubuntu.  If I can.   The machine I run on is an XP desktop, though single purpose, and getting quite tired after running continuously all this time.  Ubuntu would allow me to run a more modern OS....

No security problems that you know.  Unsupported and unpatched software on a LAN is a risk to the entire LAN.

Running a supported OS is the first step.

There is a fancy GUI for all web servers, it is called "an editor". Using the editor, we ask the webserver to do things for us.
To run 4 virtual hosts is pretty easy, but it is impossible if you are more interested in seeking things that don't really exist on Linux.

Step 1: 
  Setup directories to hold your 4 different websites. Typically, these would be in /var/www/{domainname}/.  Create a directory for each virtual website there and place the static files into each directory.  Multiple subdirectories are allowed.

Step 2:
  Install a web server. Apache or nginx are very commonly used and both generally work, from a high level, about the same. They both support running 1 or 50,000 websites using virtual hosts.

Step 3:
  For each virtualhost (website), create a file in /etc/{web-server-name}/sites-available/ ... the web-server-name would already exist based on which web server you installed using normal Ubuntu package managers.  the sites-available/ directory is where configurations are placed for sites that may or may not be currently active. By default, none are active ... er ... except the default one, which is setup as an example template.
While not mandated, placing each virtual website into a separate file allows for cleaner management, easier troubleshooting, and lots of copy/paste solutions.  
I think only about 8 lines are needed to get a working virtual website that responds to [www.domain.com](www.domain.com).
Further, you can add TLS support for each virtual website separately this way, so only 1 site is down while you learn to get that more complex solution working.  I have 6 lines in my virtual websites for TLS support.  For greater performance and some security, I add about 50-100 more lines, but those are optional.  For example, I use gzip and a micro-cache to ensure that any identical pages requested within 10 seconds by different users are already rendered and compressed, ready to be transferred to the client.  When there are 20+ concurrent users, this technique vastly improves performance.  Of course, it only works for static files. For files/links that are customized per client system, the dynamic parts really can't be cached, but all the static content can.

Step 4:
  Move into the sites-enabled/ directory and create symbolic links to any website config files in the sites-available/ directory that you want live.  This can be manually accomplished or there's usually a tool that will create the symbolic link too.  I just never bother, so I don't know the name.

Step 5: 
  Test the configuration(s) for parsing.  With nginx, the -t option will do that.
```
$ sudo nginx -t
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```

Step 6: 
  Restart/start the webserver and go visit the website(s) to ensure they are working.
  ```
sudo systemctl restart nginx.service
```

Easy-peasy.  Anytime the system is rebooted, nginx will automatically start and work, even if you don't login.  With real web servers, when they are installed onto the system, they are setup to run, at boot, by default.

Almost everything that I show with **nginx** works either the same or very similar for **apache**.

Obviously, registration for domain names, setting up DNS, opening ports on your router and any SSL/TLS certs needed are handled outside this.  If you have those things working already, then really just handling the router port-forward is probably all that remains.  You'll probably want to setup firewall rules on the Ubuntu system to ensure only the webserver ports are available to the world.  

Usually, hosting these things at home is a really bad security choice, so perhaps someone else can talk you into using either a free hosting service (like github) or a very cheap one like NearlyFreeSpeech ($0.50/month) or if you want one based on Ubuntu, you can use BlueHost or run your own VPS at a cloud provider for less than $5/month.  None of those have any GUI, but the stuff I outlines will work - or at least help you to understand what is needed.

---

### Post by mIk3_08 on 2023-04-29
> **dodgy geezer said:**
> If you read the initial comment I made, you  will see that I am a Windows GUI user trying to see if I can move over  to Ubuntu. I do not understand enough about the Ubuntu O/S to configure a  Web Server via the commad line - as you can see, I cannot even  understand what is going on with the Download/Install process. 
It may be that there is no simple Ubuntu web server which can meet my  needs, in which case I will have to reluctantly return to  Windows...
> **dodgy geezer said:**
> 
I do not understand enough about the Ubuntu O/S to configure a  Web Server via the commad line - as you can see, I cannot even  understand what is going on with the Download/Install process.
If you really want to migrate your MS Windows skills to Linux then better have the full understanding of CLI because its very far different from your GUI skills.
> **ActionParsnip said:**
> All config of a web server is done in  command line. Instead of simply saying I don't understand.... learn  something new. Apache is in the default repositories. You have followed  some random guide online and caused issues. The repositories named in  the guide only support older versions of Ubuntu.
I strongly agree with you ActionParsnip. Regards and cheers.

---

### Post by SeijiSensei on 2023-04-29
Have you considered using a Windows-based web server? This link covers IIS, the native Windows server. I'm pretty sure it has a GUI.

[https://www.comparitech.com/net-admin/iis-windows-web-server/](https://www.comparitech.com/net-admin/iis-windows-web-server/)

There also a version of Apache for Windows, but you'd still need to deal with text-based configuration files. For that, I'd stick to Linux.

[https://httpd.apache.org/docs/2.4/platform/windows.html](https://httpd.apache.org/docs/2.4/platform/windows.html)

---

### Post by Holger_Gehrke on 2023-04-30
One large advantage manually written configuration files have over a GUI are comments. You can put not just the configuration but also the reason for doing it this way into the file, either for others or as a reminder for yourself. Even better, if you start from a default configuration and change it you can mark your changes (optimally the same way in all configurations) and find your changes quickly. For example I always put my initials and the date in a comment at the beginning of any changes I make. This way I can simply 'grep' for any configurations I have changed from the defaults. A well commented configuration can be almost self-documenting.

Holger

---

### Post by dodgy geezer on 2023-05-02
Yes, this appears to be the standard response. It seems that there IS no practical GUI front-end for Apache, and, as far as I can see, no demand for such a thing. There appears to have been interest in his topic about 10 years ago, but I have found no obvious candidate for the sort of thing I want to do.

My problem is that I do NOT want to learn Linux - I want to USE it - in a similar way to the way Windos and Mac users use their systems. GUIs provide an interface to complex software that lets a user operate it without worrying about correct paths, required services and spelling errors.  

I was looking for a Web Server which could be run on a stand-alone system behind a firewall, supporting vhosts and https, with a static IP address and a simple, intuitive config/control interface. I have spent many hours over the last three days trying to get Apache to work on a Ubuntu 20.4 server build, and have given up before I even got to trying to load a GUI, let alone handling certificates.  Having to load a screen display capabiliy had me stumped for a long time...

I am sure that everyone on this site is easily capable of setting up and running such a service. My problem is that I am not, and I don't want to run a web server where, if anything goes wrong, I cannot immediately see, using a simple interface, how to put it right...

---

### Post by dodgy geezer on 2023-05-02
> **TheFu said:**
> 

No security problems that you know.  Unsupported and unpatched software on a LAN is a risk to the entire LAN.



This is not a commercial site. It is a home site. The web server runs on its own dedicated machine in its own VLan, behind a hardware firewall. The firewall logs show no particular problems, beyond a period about 14 years ago when I was running FTP services rather than FTPS for a short time and had increased attacks - though nothing successful.

All of this was set up using Windows GUI interactions, which meant that I could easily understand what I was doing. I am sure that you could create a short script which would load and run any particular service that you or I could specify. But I do not want to use something where I have insufficient understanding to maintain it unless I become a Linux CLI expert. I believe that you are correct when you imply that the sort of environment that I am seeking does not exist on Linux - though there seem to be many web pages that suggest that it does....

---

### Post by dodgy geezer on 2023-05-02
> **Holger_Gehrke said:**
> One large advantage manually written configuration files have over a GUI are comments. You can put not just the configuration but also the reason for doing it this way into the file, either for others or as a reminder for yourself. Even better, if you start from a default configuration and change it you can mark your changes (optimally the same way in all configurations) and find your changes quickly. For example I always put my initials and the date in a comment at the beginning of any changes I make. This way I can simply 'grep' for any configurations I have changed from the defaults. A well commented configuration can be almost self-documenting.

Holger

A GUI (of the kind that Windows typically uses) IS self-documenting. You can see on a dashboard what is running and how it is configured, at a high level. There is no need for any comment.

---

### Post by dodgy geezer on 2023-05-02
> **SeijiSensei said:**
> Have you considered using a Windows-based web server? This link covers IIS, the native Windows server. I'm pretty sure it has a GUI.

[https://www.comparitech.com/net-admin/iis-windows-web-server/](https://www.comparitech.com/net-admin/iis-windows-web-server/)

There also a version of Apache for Windows, but you'd still need to deal with text-based configuration files. For that, I'd stick to Linux.

[https://httpd.apache.org/docs/2.4/platform/windows.html](https://httpd.apache.org/docs/2.4/platform/windows.html)


Thank you for that data!  I do already use a Windows web server, with a full GUI, but it is running on XP. I expect Windows to move to a rental model, and want to avoid having to pay continually to use an O/S - particularly since I expect web services will cost a lot!  I already use Ubuntu desktops and have been wanting to move to a Linux-based Web service, but as you can see. what I am looking for does not seem to exist. Yet...?

---

### Post by Holger_Gehrke on 2023-05-02
> **dodgy geezer said:**
> A GUI (of the kind that Windows typically uses) IS self-documenting. You can see on a dashboard what is running and how it is configured, at a high level. There is no need for any comment.

Oh, so there's no need to explain to somebody else - or yourself a few month after you configured something - **why** you did it that way ? That's what I meant, you can have arbitrary text in a configuration to remind yourself of the reasoning behind your configuration; for example: in Apache there are multiple worker modules. Why did I chose to use the multi-process mpm_prefork_module and not the multi-thread mpm_worker_module ? 

Because the PHP module isn't threadsafe and creates problems with the multithread worker (at least at the time when I set up a web server the last time)  and the workaround is to use PHP as a FastCGI, which is something I haven't done before. In a configuration file I can put in a comment to myself to remind me of the reason, in a GUI I can't.

Of course, the author of a really good GUI would know about the problem and wouldn't allow you to use the wrong mpm with php or would set up FastCGI for you and would probably have other nifty goodies like a tool that helps in creating rules for URL rewriting ...; I don't know any GUI for Apache which is that good ... 

Comments are not optional in any configuration that is complex enough; the amount of possibilities in a configuration for Apache is so large that not commenting it is an act of negligence. The same goes for any program of comparable complexity. 

Holger

---

### Post by TheFu on 2023-05-02
I don't recall seeing the OP ask for help with Apache.  Much of post #31 has the overview of the steps involved.  Usually people only have issues with 1 step.  The specific site config file.  For a simple static website, that's about 8 lines and there are literally millions of examples on the internet.

But it is his choice at this point.  Either do things the Linux way or don't.

---

### Post by dodgy geezer on 2023-05-03
> **Holger_Gehrke said:**
> 


Of course, the author of a really good GUI would know about the problem and wouldn't allow you to use the wrong mpm with php or would set up FastCGI for you and would probably have other nifty goodies like a tool that helps in creating rules for URL rewriting ...; I don't know any GUI for Apache which is that good ...


Holger


Correct. That would be normal for a practical GUI on other O/S.



> **TheFu said:**
> 

But it is his choice at this point.  Either do things the Linux way or don't.




And that point, I think, concludes this thread. It seems clear that the 'Linux way' does not and is not going to include GUI configuration and operation in the same style as Windows or Mac. I was obviously misled by web advertisements which suggested that such things existed...

---

### Post by ActionParsnip on 2023-05-04
What web server in Windows has a GUI?

---

### Post by cainesaj on 2023-05-04
> **dodgy geezer said:**
> 
So I have three questions:

1 - does anyone know of a small, simple, gui-based web server that does https and vhosts?
2 - what have I been doing wrong when trying to install Cherokee?
3 - Is what I am trying to do impossible, and should I be trying to do something different?



[LIST=1]
[*]Yes, they probably do, though it is likely that the "GUI" is a web based interface and not specific to the web server. See e.g. [Cockpit]("https://cockpit-project.org/").
[*]While subjective, the most wrong part is likely the attempt to persue the wrong approach to hosting a web service in 2023, combined with unnecessary platform requirements.
[*]No (since possibility is rarely a limiting factor) and yes.
[/LIST]

From your description of "Nothing fancy, mainly static pages and downloads." it sounds like some static content which you want to make available via HTTPS to a general audience on the Internet. This remains a great project for someone who wants to learn about a range of technologies, but you do not sound like someone whose idea of fun includes
[LIST]
[*]testing multiple ACME clients,
[*]using DNS-01 challenge properly authenticated with your name service provider's API to renew your certificate from your choice of provider,
[*]scheduling the renewal with a systemd timer on the Linux platform which you have properly secured and keep updated,
[/LIST]
and that's just one option in part of the S in the HTTPS aspect, all of which involves a lot of commands and text and logs.
It sounds like you want a hosting provider which provides a web service which you can use to serve your files and take care of everything except the content for you. In this case you have many options, but you might start with your domain registrar since many offer free basic web and mail redirect services with the domain.

---

