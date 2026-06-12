---
title: "Ubuntu 7.10 Installation of Ruby, Rails, Mongrel, SQLite3, Sun-Java-Jdk &amp; Netbeans"
date: 2008-03-12
forum: Programming Talk
---

### Post by Stagiros on 2008-03-12
[SIZE=4][B]This is for helping those of you who want to install a  software framework, for web development, on Ubuntu 7.10.

It uses Ruby, Rails, Mongrel, Sqlite3, Sun-Java-Jdk & Netbeans.[/B][/SIZE]


[SIZE=3]_**Install Ruby, Rails, Mongrel & Sqlite3**_[/SIZE]
[I]
**Update package repository.**
[/I]sudo apt-get update[I]

**Upgrade distribution.**
[/I]apt-get dist-upgrade[I]

[B]Install "ruby1.8" & stuff.
[/B][/I]sudo apt-get install ruby ri irb ruby1.8-dev libruby1.8-dbg libdbm-ruby1.8 libgdbm-ruby1.8 libopenssl-ruby1.8

***Download "rubygems-1.0.1.tgz" from*** "http://rubyforge.org/".

***Extract "rubygems-1.0.1.tgz".***

***Install "rubygems-1.0.1"***
cd rubygems-1.0.1
sudo ruby setup.rb all
[I]
**Update gems.**[/I]
sudo gem update --system
[B]
*Install gem "rails-2.0.2".*[/B]
sudo gem install rails --include-dependencies

***Install "mongrel" gem.***
sudo apt-get install build-essential
sudo gem install mongrel --include-dependencies

***Install Sqlite3 & stuff.***
sudo apt-get install swig sqlite3 libsqlite3-dev libsqlite3-ruby

***Install "sqlite3" gem.***
sudo gem install sqlite3-ruby


[SIZE=3][U][B]Install Sun's java-jdk & Netbeans

[/B][/U][SIZE=2]***Add Hardy repository.***

[/SIZE][/SIZE][I]**Update package repository.**
[/I]sudo apt-get update[SIZE=3][SIZE=2]
***Install Sun's java***
sudo apt-get install sun-java6-jdk

***Remove Hardy repository, so that you revert back to your stable Gutsy one, and update package repository again.***
apt-get update

***Download netbeans-6.0.1-ml-ruby-linux.sh from the Netbeans site if not in the repository***

***Install Netbeans***
chmod +x netbeans-6.0.1-ml-ruby-linux.sh
sudo sh netbeans-6.0.1-ml-ruby-linux.sh

***If during installation you see any gtk errors, ignore them and continue.***

***If at the end of the installation you do not see an icon of Netbeans sitting on your desktop, do the following:***
     1.    Launch "System --> Preferences --> Main Menu"
     2.    Click on "Applications".
     3.    Click on "Programming".
     4.    Click on button "+ New Item".
     5.    Specify "Type:" as "Application"
     6.    Specify "Name:" as "NetBeans IDE 6.0.1"
     7.    Specify "Command:" as "/usr/local/netbeans-6.0.1/bin/netbeans"
     8.    Click on the button with the spring icon (Top left of the window).
     9.    Browse to folder /usr/local/netbeans-6.0.1/nb6.0 and press the button  "Open".
10.    Select "netbeans.png" and press the button "OK".
   11.    You should be able to see the netbeans icon now instead of the spring.  Click on button "OK".
   12.    Go to menu "Applications --> Programming" and drag the "NetBeans IDE 6.0.1" icon on your desktop.
[B]
That is all.  You can now develop using Ruby On Rails, SQLite3 and NetBeans.

[COLOR=Red]*** If you find anything that does not work as stated or have something to add, please post a reply.[/COLOR]
[/B] [/SIZE][/SIZE]

---

### Post by AnotherDave on 2008-03-27
Thanks for the guide. Unfortunately, it is not complete and will not work as written (or maybe I'm missing something???)

Under **Upgrade distribution** I needed to **sudo** apt-get dist-upgrade. No biggie, I can figure that one out. 

But I don't understand why under **Install "rubygems-1.0.1** that sudo ruby setup.rb all doesn't work. There is no /usr/bin/ruby.

**Shouldn't we have installed ruby before this point???**

---

### Post by mssever on 2008-03-27
> **AnotherDave said:**
> Thanks for the guide. Unfortunately, it is not complete and will not work as written (or maybe I'm missing something???)

Under **Upgrade distribution** I needed to **sudo** apt-get dist-upgrade. No biggie, I can figure that one out. 

But I don't understand why under **Install "rubygems-1.0.1** that sudo ruby setup.rb all doesn't work. There is no /usr/bin/ruby.

**Shouldn't we have installed ruby before this point???**

I'm pretty sure that Ruby is part on a default Ubuntu install. But regardless, Ruby is a dependency for many of the installed packages (ri, irb, etc.). So if you don't have Ruby, your system is broken, not this HOWTO. (Though I don't necessarily endorse the HOWTO.)

Of course, you can install rubygems (and the gems listed in the guide) from the repos if you want.

---

### Post by sullivan.t on 2008-03-28
Thanks so much for this!  It's a great list of "must have" apps!

---

### Post by Stagiros on 2008-03-31
Dear AnotherDave, I have checked thoroughly this guide guide before posting it. It works. It is what I did on my system, which I am using for production development.

If you perform the step "***Install "ruby1.8" & stuff."  ***exactly as stated and then the steps "***Download "rubygems-1.0.1.tgz" from*** "http://rubyforge.org/"." & "***Extract "rubygems-1.0.1.tgz"." & "******Install "rubygems-1.0.1""  ***in that exact order, everything will work as expected.  Try it again and let us know how it goes.

Thanks for taking the time to read it anyway.

---

### Post by kup3rt1n0 on 2008-04-01
Actually, I had the same issue as AnotherDave.

 It seems the packages listed don't install the ruby command line interpreter. Also, it was not installed by default on my system (7.10 desktop). The only thing I did different than the HOWTO was I installed rubygems from the repos and I somehow doubt the rubygems tarball installs the ruby CLI.

However, a quick *apt-get install ruby* took care of the problem...

---

### Post by mssever on 2008-04-01
> **kup3rt1n0 said:**
> Actually, I had the same issue as AnotherDave.
<snip>
However, a quick *apt-get install ruby* took care of the problem...

I looked into this further, and discovered that ri, irb, and friends install ruby1.8 by dependency, not ruby. I've reported a [bug about this]("https://bugs.launchpad.net/ubuntu/+source/ruby-defaults/+bug/210631"), where I also explained the situation in greater detail. The workaround is, as you said, to explicitly install ruby, or to use ruby1.8; e.g., ```
ruby1.8 foo.rb
```


[quote=stagiros]sudo apt-get install ri
sudo apt-get install irb
sudo apt-get install ri1.8
sudo apt-get install ruby1.8-dev
sudo apt-get install libruby1.8-dbg
sudo apt-get install libdbm-ruby1.8
sudo apt-get install libgdbm-ruby1.8
sudo apt-get install libopenssl-ruby1.8[/quote]
@OP: I suggest you update this section of your original post to reflect this bug in Ruby's packaging: ```
sudo aptitude install ruby ri irb ruby1.8-dev linruby1.8-dbg libdbm-ruby1.8 libgdbm-ruby1.8 libopenssl-ruby1.8
```Note that I put it all in one command. Installing each package separately wastes a huge amount of time. Also, some of the packages you listed, such as libruby1.8-dbg and libopenssl-ruby1.8 are only useful in certain situations.

---

### Post by Stagiros on 2008-04-02
What goes on in your case is what user "mssever" suggests.  The executable "ruby1.8" is installed as a depedency for the packages ir, irb but it is not linked to "ruby".

To end this once and for all, so everybody can install everything as stated, I did what user "mssever" suggested. To the portion entitled "[I]
**Install "ruby1.8" & stuff.", **[/I]I added the command "sudo apt-get install ruby". That will fix the problem.

So thank you all for the feedback and those of you that had problems, thank "mssever" for the quick fix.

Enjoy your development!

---

### Post by mssever on 2008-04-02
> **Stagiros said:**
> To end this once and for all, so everybody can install everything as stated, I did what user "mssever" suggested. To the portion entitled "[I]
**Install "ruby1.8" & stuff.", **[/I]I added the command "sudo apt-get install ruby". That will fix the problem.
A couple more suggestions: First, if you list the install command as one command, people can copy and paste if they want, instead of having to manually type each command. See the example in my post above. Obviously, no one other than a newbie would run the commands as given; there's a significant time penalty (often measured in minutes) every time you run apt-get or aptitude. If tou combine all the installs into one command, you only pay that penalty once, instead of once per package.

My second suggestion is that you simply list ri. Since ri depends on ri1.8, there's no reason to explicitly name ri1.8.

---

### Post by Stagiros on 2008-04-02
The reason I listed installs as a series of separate commands was for the newbies to have a clearer understanding of what is going on.

As far as performance is concerned, I can only say I am sorry if that has proven a resource hog for people with weak Pcs.  I have a fairly powerful machine and tend to forget about performance issues.  Sorry again.

Anyway, I have made the changes you suggest to keep things efficient and clear.

Thanks for the suggestions.

---

