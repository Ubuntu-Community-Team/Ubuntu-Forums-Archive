---
title: "[SOLVED] need permission at root/usr to load software ????"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Bartee on 2008-07-12
I am trying to install ruby gems.

I have ruby installed from the package manager. ( Now that's easy !!!)

But I need to load gems.  I downloaded the latest gems and trying to execute setup.rb.

I am getting this in the terminal command:

[FONT="Courier New"]
bartee@bartee-linux:~/MyDownloads/RubyGems120/rubygems-1.2.0$ ruby setup.rb
mkdir -p /usr/local/lib/site_ruby/1.8
mkdir -p /usr/bin
[COLOR="Red"]mkdir -p /usr/local/lib/site_ruby/1.8/rbconfig
/usr/lib/ruby/1.8/fileutils.rb:243:in `mkdir': Permission denied - /usr/local/lib/site_ruby/1.8/rbconfig (Errno::EACCES)[/COLOR][/FONT]

I tried to log in as root and give full permissions to root/usr but that did not work.

This is just a lack of understanding on my part so any info would be appreciated.

---

### Post by hyper_ch on 2008-07-12
use "sudo" instead of login in as root.

---

### Post by Methuselah on 2008-07-12
Yup, as hyper_ch said:

```

sudo ruby setup.rb

```

---

### Post by Bartee on 2008-07-12
COOL !!!!

I get it !!!

I just had to screw my head 180 degrees and look at it from the other direction.

Thanks....

---

### Post by WRDN on 2008-07-12
You can also use the "su" command. For completeness and for the unaware, "sudo" means 'super user do' while "su" only means 'super user'.
The difference is that, sudo is generally used to run a single command with root privileges, while if "su" is entered, you are given root privileges until you close the Terminal window, or type "exit". Consequently, if there is a series of commands, each needing root privileges, "su" may be a better option, although some would argue "sudo" is safer because, you lose the root privileges after the command has finished. In comparison, if you use "su" and forget to lose the root privileges, it could be easy to damage your system.

---

### Post by hyper_ch on 2008-07-13
wrdn: you can't as su is deactivated by default on ubuntu.

---

