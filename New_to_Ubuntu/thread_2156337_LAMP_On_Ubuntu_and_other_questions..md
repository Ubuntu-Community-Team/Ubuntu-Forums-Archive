---
title: "LAMP On Ubuntu and other questions."
date: 2013-06-21
forum: New to Ubuntu
---

### Post by pmu on 2013-06-21
Hi,


I am looking for a stable linux which I can use for play + work. I want to configure and deploy LAMP(P would be Perl) on my laptop to test and play. Anyone here has tried a small LAMP setp on Ubuntu Desktop?  Say if you want to further test out stuff with running VMWare/Virtualbox instances inside it, use one of them as a web server and try out LAMP and similar things (Perl Dancer is something I have on the list), is that possible with Ubuntu?


Previous linux experience wise, I have basic familiarity with CentOS and Fedora and am comfortable with command line, yum update, rpm, installing repositories, a bit of sed and awk, configuring apache etc. Also want to get into Intermediate/advanced Bash scripting, get really comfortable with network configuration as well. From what I know as of now, apt-get is Ubuntu's equivalent of RHEL/CenOS yum, so hoping that it will be quite as pleasure to use it. Can I take some, if not all the stuff that I learn from Ubuntu and apply that to other Linux Flavours in general? 


Installing Perl Modules from CPAN was an issue with CentOS as it kept throwing YAML errors. Google helped me, but hoping if there is an easier way to do it on Ubuntu. Is there a sort of a package manager for Ubuntu that takes care of Perl Module installations as well? 
 
Many apologies in advance if this sounds condescending, but anyone here who uses Ubuntu for production grade work or software development? Please, dont get me wrong here. I am not trying to run Ubuntu down. Generally, production grade Linux DE have nothing much to write home about but this one, is real awesome. I checked it by running it off a Live DVD and frankly am blown away with the polished and slick user interface. This Unity DE thing is really nice. Took some time to figure it out, but what I love is the polished awesome look and the fact that I dont need to use the mouse much. So if there are fellow users here who are already using it for all the stuff mentioned above (basically a linux system for production grade work), please do let me know.


I really want to settle down on a stable linux version. Something that I will use for atleast next 3 years or so.

---

### Post by Lars Noodén on 2013-06-21
Welcome.

Perl is built in to Linux and BSD so you don't need to install it.  The perl modules are another matter.  You can find most of them in the repositories and they can be installed with the package manaer.  In other words, install them either graphically using Synaptic or in the terminal with APT. 

The other tools, Apache and MySQL or Postgresql can also be installed from the repositories.   MariaDB does not seem to be available yet.  These can be installed anywhere, on a server or on your desktop.  If you want to be careful, you can do your tests first in a VM like Qemu or VirtualBox first before moving them to the desktop.  

If you want stable (as in unchanging and predictable), go with either Ubuntu 12.04 server LTS or with Debian 7 (wheezy).  

About shell scripting and such, that is nearly identical from distro to distro.  The main thing that might be different between distros would be the package manager and the default programs and settings that are present.  There are some shell scripting resources listed in this thread: [http://ubuntuforums.org/showthread.php?t=2155675](http://ubuntuforums.org/showthread.php?t=2155675)

---

### Post by pmu on 2013-06-21
Hi Lars,

Thank you for replying. I am looking more for a desktop version rather than a Server version to be physically installed on my laptop. I could try out the Server Version(s) you mentioned in the VMs, but I am basically planning to use Ubuntu 12.04 as a one single OS for all my needs mentioned above.

Thank you once again for replying.

---

### Post by Lars Noodén on 2013-06-21
You can start with the server distro and then install on top of it the few desktop components that you need.  Or you can start with one of the LTS desktops and install the server components to meet your needs.  Either way it is the same foundation and same packages.

---

### Post by TheFu on 2013-06-21
Good news. I've been using Ubuntu Server for production Perl Dancer apps the last 2 yrs. I've been using Ubuntu Servers in production since 2008. Extremely solid and stable.

I can't possibly explain everything I think you need to know in this forum. Don't have time.

#1. When it comes to perl programming, do not use packages provided by the distro. Using something like PerlBrew instead. 
[http://blog.jdpfu.com/2011/08/24/perlbrew-for-self-contained-perl-installations](http://blog.jdpfu.com/2011/08/24/perlbrew-for-self-contained-perl-installations)  There are too many reasons to list them all why this is a good idea.  You'll still use CPAN, just inside the PerlBrew local container for each Perl instance you install.

#2.  Don't use Apache to run Dancer Apps.  Would you drive an 18-wheeler to the local corner store to pick up soda?  Read the docs on PSGI compatible servers - I use an nginx - plackup - starman setup myself.

#3. Definitely read up on Modern Perl [http://modernperlbooks.com/mt/index.html](http://modernperlbooks.com/mt/index.html) , Perl Tidy, and Perl Critic. Know them.  use them. Love them.

#4. Find and join your local Perl Monger group. My local group meets monthly and keeps me upto date with the current perl efforts and new techniques.  YAPC-NA [http://www.yapcna.org/yn2013/](http://www.yapcna.org/yn2013/) just finished, so there should be lots of interesting discussions.

Be certain to read all the help files for Dancer. There must be 50 of them on specific items - deployment, testing, etc... These are in CPAN and very clearly documented, IMHO.

Anyway, that should get you started.

---

### Post by pmu on 2013-06-21
Hi TheFu,

Thank you sir. That was quite well explained. To be frank, Perl Dancer was just one of the things in my list, but heck, after your write up, I feel like I really should give it a try.

So is it possible, that I can use Ubuntu 12.04 Desktop Version first to try out the stuff on my laptop, and then take things ahead from there?

You sound like a Perl Guru/Expert, and its nice to get help from experts like yourselves. Do you use Ubuntu 12.04 on your laptop for production work?

---

### Post by TheFu on 2013-06-21
> **pmu said:**
> Hi TheFu,

Thank you sir. That was quite well explained. To be frank, Perl Dancer was just one of the things in my list, but heck, after your write up, I feel like I really should give it a try.

Dancer is really amazing. I've written about 5 lines of code and had a working application with it. Usefully only on a trusted network with highly trusted users, but still, it provided complete access to CRUD data in a single DB table. I was impressed it took so little code.

> **pmu said:**
> So is it possible, that I can use Ubuntu 12.04 Desktop Version first to try out the stuff on my laptop, and then take things ahead from there?

Sure. Just learn how to do things without the GUI. Linux servers don't have a GUI.

> **pmu said:**
> You sound like a Perl Guru/Expert, and its nice to get help from experts like yourselves. Do you use Ubuntu 12.04 on your laptop for production work?

I am not a Perl expert by any stretch of anyone's imagination.  I've written a few apps and those apps work.  I've been hacking perl off and on since 1996. It has never been a full-time job for me.  I think it takes 10 yrs of full-time work to become an expert in any field. I'm very short on that with perl.  I have perhaps 2 yrs of perl dev experience over all that time. I'm a noob.

My laptop doesn't run Linux. It is mainly a remote desktop access device.

My netbook does run Linux, but only as a remote desktop device.

My primary "desktop" runs inside a private cloud under a KVM virtual machine.  Nothing on it is "production" - that term only applies to servers running the specific software stack necessary - definitely NO GUI.  To me "production" means 100% stable, not for development, not for testing, uptimes measured in years. That is my telco background talking.

You started by asking about LAMP. Not certain you got this from me, but I don't use LAMP. I'm running:
* Linux
* Nginx
* Postgres/PostgreSQL
* Perl
LNPP?  Whatever.  MySQL (from Oracle) is a poor DB choice, IMHO.  If you must use something like that, go with MariaDB. It is a drop in replacement for MySQL - without the Oracle baggage.  I try to avoid using anything from Oracle. I've been burned too many times to trust them anymore. Hopefully, you'll avoid being burned by making good choices now.

Nginx is a light-weight web server and reverse proxy with a small footprint and enterprise capabilities. Configuration is much easier than Apache with mod_x, mod_y, mod_z and mods_a-thru-w, plus the kitchen sink. No thanks.  I stopped using apache in any serious way about 5 yrs ago.  Too many features and addons means much less security. Apache's mod_security sorta points out the issue to me.

PostgreSQL - A database that can loss data or corrupt data isn't worth anything to me. PostgreSQL has been ACID compliant for over a decade. Sometimes it performs better that MySQL and sometimes it performs worse.  PostgreSQL feels the most like Oracle to me, plus it has native Perl for DB triggers. Seems like a win-win for someone using Perl.  More and more frameworks are using PostgreSQL - including the RoR service provider Heroku. There must be a reason for that, right?

Perl - I learned perl well enough to get things done in the mid-1990s. Never found anything compelling enough to switch away completely, though I do like Ruby and Python.  RoR is too heavy for most web deployments. Deploying a RoR app will usually cost 2-3x more per month in VPS due to the increased memory and CPU required.  Python is the language that I recommend to people interested in learning to program today.  MIT CS101 classes are based on Python and the _Hard Way_ python teaching tools seem really great for new programmers.  [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program) has more information and background, if anyone gets bored. I would change my comments about javascript - I'd be more specific to javascript as used in browsers today. Live and learn

Anyway, you will choose whatever you need - just be certain you make the choices with a good reason. Sometimes "*everyone else does it this way*" **is** a good reason. Often, it is not.

I hope others respond with interesting insights.

---

### Post by pmu on 2013-06-21
Hi TheFu,

I am blown. I dont know what to say. Your reply is an eye opener. No kidding. Complete, full fledged eye opener. 

I now know why a friend of mine kept telling me to try Ubuntu. When I asked him why, he said the community and forums are awesome.

Once again, sincere thanks to you. I will surely try PostGreSQL. I did browse about it a bit, and the stuff seems dense. More dense than MySQL to my un initiated newbie eyes and brain. :)

About Ubuntu 12.04, I am truly blown away. 

I used unetbootin to copy the iso on USB pen drive, and booted off of it. From the moment I hit "Install" to the time the "Reboot now" menu, it took 5 minutes. Yes, 5 minutes by the wall clock. I hope nothing is missed out. Its quite unusual for a linux distro, or any distro to install so fast. Just hoping that nothing is skipped/broken...Well, if it were broken, it would error out, but it didnt.

In the process of running "apt-get update". 

You indeed are an Expert and I dont have words to thank you.

Regards,

pmu

---

