---
title: "[SOLVED] compile or something to a .tar after extraction"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-11
ok  I have done everything up to the point of these instructions.  Presently, the extracted package is in it's own folder (named "App") in my home folder. here's the directions:

\par
To perform a system-wide installation, we recommend that you copy the entire
Framework directory into a globally accessible location (/usr/local/msf) and
then create symbolic links from the msf* applications to a directory in the
system path (/usr/local/bin). User-specific modules can be placed into
\texttt{HOME/.msf3/modules} directory.  The structure of this directory should
mirror that of the global modules directory found in the framework
distribution.

---

### Post by Inxsible on 2008-07-11
> **adamogardner said:**
> ok  I have done everything up to the point of these instructions.  Presently, the extracted package is in it's own folder (named "App") in my home folder. here's the directions:

\par
To perform a system-wide installation, we recommend that you copy the entire
Framework directory into a globally accessible location (/usr/local/msf) and
then create symbolic links from the msf* applications to a directory in the
system path (/usr/local/bin). User-specific modules can be placed into
\texttt{HOME/.msf3/modules} directory.  The structure of this directory should
mirror that of the global modules directory found in the framework
distribution.What is the app that you are trying to install?

Maybe there is an easier way. If not, when we know what app it is, ppl may be able to help you better.

But in short what the instructions mean is - if there are multiple users on your machine and you want that app to be available to all users then you have to install it under a global location else it would only be installed in your home directory and only you will have access to it.

---

### Post by adamogardner on 2008-07-11
wrong instructions,  here they are  but I still need help with metasploit  I just downloaded all these apt-gets below including the two for a GUI.  So now I'm stuck with a folder and 10 ruby compilers (hidden in my system) and instructions to choose my console msfconsole or msfweb, etc.  what is a console and why can't i find one?


# apt-get install ruby libruby rdoc
# apt-get install libyaml-ruby
# apt-get install libzlib-ruby
# apt-get install libopenssl-ruby
# apt-get install libdl-ruby
# apt-get install libreadline-ruby
# apt-get install libiconv-ruby
# apt-get install rubygems *

*The RubyGems package may need to be manually downloaded and installed.

If you would like to use the experimental GUI, you will need to install the following packages:

# apt-get install libgtk2-ruby libglade2-ruby

If you would like to use the online update feature, you will need to install the "subversion" package as well. Once the pre-requisites have been installed, download the Unix tarball from Framework Website and extract it to the directory of your choice. If everything was installed correctly, execute the interface of your choice to get started (msfconsole, msfweb, etc).

---

### Post by Inxsible on 2008-07-11
> **adamogardner said:**
> wrong instructions,  here they are  but I still need help with metasploit  I just downloaded all these apt-gets below including the two for a GUI.  So now I'm stuck with a folder and 10 ruby compilers (hidden in my system) and instructions to choose my console msfconsole or msfweb, etc.  what is a console and why can't i find one?


# apt-get install ruby libruby rdoc
# apt-get install libyaml-ruby
# apt-get install libzlib-ruby
# apt-get install libopenssl-ruby
# apt-get install libdl-ruby
# apt-get install libreadline-ruby
# apt-get install libiconv-ruby
# apt-get install rubygems *

*The RubyGems package may need to be manually downloaded and installed.

If you would like to use the experimental GUI, you will need to install the following packages:

# apt-get install libgtk2-ruby libglade2-ruby

If you would like to use the online update feature, you will need to install the "subversion" package as well. Once the pre-requisites have been installed, download the Unix tarball from Framework Website and extract it to the directory of your choice. If everything was installed correctly, execute the interface of your choice to get started (msfconsole, msfweb, etc).Seems like you want to install ruby. I am not sure about Ubuntu but the debian package for rubygems is corrupted. so they advise not to use that.

if you just did ```
apt-get install ruby irb rdoc
``` you would get all the dependencies for ruby1.8

As for metasploit, its a tar.gz...so you would have to compile it and install. Normal procedure for installing from source is, 1)Extract the folder 2)cd to the extracted folder and ```
sudo make install
./configure
```But sometimes the instructions are in the source folder itself.

I have never used metasploit, but there seems to be a install.rb file in the download which means you can simply call ```
ruby /path/to/install.rb
``` and it should do it. (I think)

---

### Post by adamogardner on 2008-07-11
yeah i need ruby for metasploit.  The instructions came off the website.  so whats wrong with ruby?, and what is that command for you gave me?

---

### Post by Inxsible on 2008-07-11
> **adamogardner said:**
> yeah i need ruby for metasploit.  The instructions came off the website.  so whats wrong with ruby?, and what is that command for you gave me?
The command I gave you installs ruby1.8 irb1.8 and rdoc1.8 from the standard repos.

---

### Post by adamogardner on 2008-07-11
what does this mean?

adamogardner@CRONUS:~/Apps/framework-3.1$ sudo make install
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
make: *** No rule to make target `install'.  Stop.
adamogardner@CRONUS:~/Apps/framework-3.1$

---

### Post by Bachstelze on 2008-07-11
Most likely, you're not supposed to *make install*. Read the doc for your program.

---

### Post by Inxsible on 2008-07-11
> **adamogardner said:**
> what does this mean?

adamogardner@CRONUS:~/Apps/framework-3.1$ sudo make install
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
make: *** No rule to make target `install'.  Stop.
adamogardner@CRONUS:~/Apps/framework-3.1$

> **HymnToLife said:**
> Most likely, you're not supposed to *make install*. Read the doc for your program.Yes. the make install methods are just a general way on installing from source. But like I mentioned before, some packagers do it differently.

And especially since this is a ruby program..they are not bound to do it the linux way. There are readme files in the metasploit tar...have a look at those. to see what the installation procedure is.

Mostly likely its calling the install.rb which i also mentioned in my previous post -- but check it just to be sure.

---

### Post by adamogardner on 2008-07-11
the doc said for instasll instructions refer to the website.  Which I copied and pasted previously.  I have tried the install.rb first, but that failed as shown below here:

adamogardner@CRONUS:~$ ruby /path/to/install.rb
ruby: No such file or directory -- /path/to/install.rb (LoadError)

---

### Post by Inxsible on 2008-07-11
> **adamogardner said:**
> the doc said for instasll instructions refer to the website.  Which I copied and pasted previously.  I have tried the install.rb first, but that failed as shown below here:

adamogardner@CRONUS:~$ ruby /path/to/install.rb
ruby: No such file or directory -- /path/to/install.rb (LoadError)When I said /path/to/install.rb -- you had to replace it with the actual path.

What are you installing that app for? That app is for penetration testing and hacking.

---

### Post by adamogardner on 2008-07-11
well let's veer off the subject for a moment:   Downloading mystery packages isn't really my style. I know what it is; I like to play with ****.

---

