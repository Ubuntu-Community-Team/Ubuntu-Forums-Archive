---
title: "[HOWTO] Search and install PPAs from the command line."
date: 2010-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Wrinkliez on 2010-07-08
Soo, I got bummed that there was no way to search and install PPAs from the command line.  So I created my own program to do it!  It works pretty well, just don't stray off the path i.e. don't put in a letter when it asks you for a number.  But, let's get started.

[SIZE="5"]Installation.[/SIZE]

_Step One_ - Install my PPA.  **Warning:** This program is written in Ruby.  All it is is a Ruby script.  If you don't want to install the Ruby language or its dependencies, I don't know what to tell you.

```
sudo add-apt-repository ppa:wrinkliez/ppasearch
```

_Step  Two_ - Update your repositories!

```
sudo aptitude update
```

_Step Three_ - Install ppasearch! Make sure you agree to install the dependencies when it asks you.

```
sudo aptitude install ppasearch
```

[SIZE="5"]An example of how to use ppasearch.[/SIZE]

_Step One_ - Run ppasearch.  It will ask you what you want to install.

```
ppasearch
```

[[IMG]http://img696.imageshack.us/img696/5046/daviddavidlaptop003.png[/IMG]](http://img696.imageshack.us/i/daviddavidlaptop003.png/)

_Step Two_ - Type whatever you want to install.  I'm going to search for the PPA of my favorite twitter client, [Pino]("http://pino-app.appspot.com/").  CHANGE IT TO WHATEVER YOU WANT.

```
pino
```

[[IMG]http://img695.imageshack.us/img695/9007/daviddavidlaptop004.png[/IMG]](http://img695.imageshack.us/i/daviddavidlaptop004.png/)

_Step Three_ - Press the number to the corresponding PPA.  Your answer shouldn't have brackets.

```
1
```

[[IMG]http://img31.imageshack.us/img31/852/daviddavidlaptop005.png[/IMG]](http://img31.imageshack.us/i/daviddavidlaptop005.png/)

_Step Four_ - Are you sure you want to install this PPA?

```
y
```

_Step Five_ - Put in your password and your done.  Just remember to update your sources via

```
sudo aptitude update
```

and there, you've installed the PPA.  :)

---

### Post by nilarimogard on 2010-07-11
Amazing idea! Thank you very much!

Btw, we've featured PPASearch of WebUpd8 (which I see you have in your sig - so thanks for that too :D ).

---

### Post by Kruptein on 2010-07-11
How to install ruby on ubuntu?

I only find how to install ror,

if I do sudo apt-get install ruby (or with aptitude), I get a packet does not exist...

---

### Post by nilarimogard on 2010-07-11
@Kruptein: just install ppasearch, Ruby comes as a dependency.

@Wrinkliez: any chance PPA Search could list the searched application version for each PPA? That would be really useful...

---

### Post by Kruptein on 2010-07-11
ow yeah, I already know why it failed, nevermind :)

---

### Post by sammyboy405 on 2010-07-11
No Matter what I search for I Get this error.

```
/usr/bin/ppasearch:19:in `gets': No such file or directory - gm-notify (Errno::ENOENT)
	from /usr/bin/ppasearch:19
```

Any Ideas on what im Missing?

---

### Post by sammyboy405 on 2010-07-11
> **sammyboy405 said:**
> No Matter what I search for I Get this error.

```
/usr/bin/ppasearch:19:in `gets': No such file or directory - gm-notify (Errno::ENOENT)
	from /usr/bin/ppasearch:19
```

Any Ideas on what im Missing?

Figured it out..

I Need to Learn to read....

I was using ppasearch like a full CLI..   I was typing ppasearch gm-notify rather than just ppasearch by itself. 

So My own fault there.

---

### Post by koushik.ms on 2010-07-12
This is an amazing idea and thanks for sharing this.

I am facing an issue when I try to run this from behind a proxy at work. I have setup the proxy using System -> Preferences -> Network Proxy and, as it happens, I have same proxy for "all protocols". So whenever I open a terminal, the following three environment variables are always defined.

ftp_proxy=ftp://squid.mycompany.com:3128/
http_proxy=http://squid.mycompany.com:3128/
https_proxy=https://squid.mycompany.com:3128/

This happens even if I only specify http proxy and tick "Use same proxy for all protocols".

When I run ppasearch and specify a search string, I get an error "in `open_http': Non-HTTP proxy URI: [https://squid.mycompany.com:3128/](https://squid.mycompany.com:3128/) (RuntimeError)"

Any tips for fixing this ?

"unset"-ting the https_proxy env variable solves the problem, but I guess that is not a "clean" fix.

Full transcript of the session below.
ing02741@TREUBG:~$ ppasearch

What would you like to search for?
pino
/usr/lib/ruby/1.8/open-uri.rb:203:in `open_http': Non-HTTP proxy URI: [https://squid.mycompany.com:3128/](https://squid.mycompany.com:3128/) (RuntimeError)
	from /usr/lib/ruby/1.8/open-uri.rb:616:in `buffer_open'
	from /usr/lib/ruby/1.8/open-uri.rb:164:in `open_loop'
	from /usr/lib/ruby/1.8/open-uri.rb:162:in `catch'
	from /usr/lib/ruby/1.8/open-uri.rb:162:in `open_loop'
	from /usr/lib/ruby/1.8/open-uri.rb:132:in `open_uri'
	from /usr/lib/ruby/1.8/open-uri.rb:518:in `open'
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/bin/ppasearch:27
ing02741@TREUBG:~$

---

### Post by sanderj on 2010-07-18
> **sammyboy405 said:**
> Figured it out..

I Need to Learn to read....

I was using ppasearch like a full CLI..   I was typing ppasearch gm-notify rather than just ppasearch by itself. 

So My own fault there.


The same happened to me. So maybe handy (@wrinkliez) to detect and warn for this kind of mistakes, and print a usage ...

---

### Post by sanderj on 2010-07-18
I try install google chrome / chromium like below, but  I still have to type sudo apt-get install chromium-browser" afterwards.

Does ppasearch only add the repository, do I still have to invoke the "sudo apt-get install" myself? If so, how do I find out the package name (in this case chromium-browser)?




```
ubuntu@ubuntu:~$ ppasearch

What would you like to search for?
chrome

Good news! Found 6 results!

[1] PPA for Ubuntu Chromium - Beta Channel
[2] PPA for Ubuntu Chromium - Dev Channel
[3] PPA for Ubuntu Chromium - Stable Channel
[4] Better management of background windows
[5] widget
[6] PPA for shane fagan

Which one would you like to install?
3
Are you SURE you want to add ppa:chromium-daily/stable to your Software Sources? [Y/N]
y
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv FBEF0D696DE1C72BA5A835FE5A9BF3BB4E5E17B5
gpg: requesting key 4E5E17B5 from hkp server keyserver.ubuntu.com
gpg: key 4E5E17B5: "Launchpad PPA for chromium-daily" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ubuntu@ubuntu:~$ sudo aptitude update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US    
Hit http://archive.ubuntu.com lucid Release.gpg                                                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/chromium-daily/beta/ubuntu/ lucid/main Translation-en_US
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]              
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://ppa.launchpad.net/chromium-daily/stable/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/troorl/pino/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg 
Ign http://ppa.launchpad.net/wrinkliez/ppasearch/ubuntu/ lucid/main Translation-en_US
Hit http://archive.ubuntu.com lucid Release                          
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US          
Hit http://security.ubuntu.com lucid-security Release                                     
Hit http://ppa.launchpad.net lucid Release                           
Hit http://archive.ubuntu.com lucid-updates Release                                       
Hit http://security.ubuntu.com lucid-security/main Packages          
Get:2 http://ppa.launchpad.net lucid Release [57.3kB]                
Hit http://archive.ubuntu.com lucid/main Packages                        
Hit http://archive.ubuntu.com lucid/restricted Packages                    
Hit http://archive.ubuntu.com lucid/multiverse Packages                    
Hit http://archive.ubuntu.com lucid/universe Packages                      
Hit http://archive.ubuntu.com lucid/main Sources                           
Hit http://security.ubuntu.com lucid-security/restricted Packages          
Hit http://security.ubuntu.com lucid-security/multiverse Packages          
Hit http://security.ubuntu.com lucid-security/universe Packages            
Hit http://security.ubuntu.com lucid-security/main Sources                 
Hit http://security.ubuntu.com lucid-security/restricted Sources           
Hit http://archive.ubuntu.com lucid/restricted Sources                     
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://ppa.launchpad.net lucid Release            
Hit http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid/main Packages
Get:3 http://ppa.launchpad.net lucid/main Packages [3,017B]
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Fetched 60.6kB in 1s (40.3kB/s)
Reading package lists... Done

ubuntu@ubuntu:~$ google-chrome
google-chrome: command not found
ubuntu@ubuntu:~$ google-chromium
google-chromium: command not found
ubuntu@ubuntu:~$ 

```

---

### Post by v1ad on 2010-07-18
```


vlad@vlad-Main:~$ ppasearch
/usr/bin/ppasearch:3:in `require': no such file to load -- rubygems (LoadError)
	from /usr/bin/ppasearch:3

```

error, any idea of what it could be?

---

### Post by v1ad on 2010-07-18
sudo apt-get install rubygems .............

that took care of it.

maybe on that error ask them if they want to install rubygems to make it work and have it install it for them.

i didn't realize what was going on till i looked at your script.

---

### Post by Wrinkliez on 2010-07-23
> **v1ad said:**
> sudo apt-get install rubygems .............

that took care of it.

maybe on that error ask them if they want to install rubygems to make it work and have it install it for them.

i didn't realize what was going on till i looked at your script.

You seem to be the unfortunate soul who decided to update the program when I hadn't had that marked as a dependency.  It's fixed now :)

---

### Post by gnimsh on 2010-07-25
sanderj, to search for a package use this command: apt-cache search <program name>.  So after you add the chrome pository, for example, type apt-cache search chrome and hit enter and it will return all results.  Then use sudo apt-get install and type out the package name.  I think you can use tab for autocomplete at this point.

---

### Post by gnimsh on 2010-07-25
I'd like to see if sudo apt-get update could be added to ppasearch so after the PPA is added it could also automatically update the sources list?  That would be fantastic in cutting down steps when adding a ppa.  Then I can go right ahead and install the program when I'm done.

Thanks!

---

### Post by sanderj on 2010-07-25
> **gnimsh said:**
> sanderj, to search for a package use this command: apt-cache search <program name>.  So after you add the chrome pository, for example, type apt-cache search chrome and hit enter and it will return all results.  Then use sudo apt-get install and type out the package name.  I think you can use tab for autocomplete at this point.

That works! Thank you.

---

### Post by gnimsh on 2010-08-13
I just ran ppasearch again and it asked if I wanted to update apt. Thanks!

---

### Post by nutznboltz on 2010-11-05
Any chance you could upgrade from [Y/N] prompts to [Y/N/Q] ones?

It's hard to exit ppasearch now.  Ctrl-D is not working right.

---

### Post by lkjoel on 2010-11-05
> **nutznboltz said:**
> Any chance you could upgrade from [Y/N] prompts to [Y/N/Q] ones?

It's hard to exit ppasearch now.  Ctrl-D is not working right.
CTRL-C or CTRL-Z should work.

---

### Post by lkjoel on 2010-11-05
Could you make a version for Maverick?

---

