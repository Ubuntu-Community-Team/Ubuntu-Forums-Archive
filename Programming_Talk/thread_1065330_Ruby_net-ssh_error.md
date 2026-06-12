---
title: "Ruby net-ssh error"
date: 2009-02-09
forum: Programming Talk
---

### Post by puelly on 2009-02-09
Hi Guys I am looking for some help to get a simple ruby script working.  I installed ruby from the repositories and rubygems 1.3.1 manually.  I also used gems to install net-ssh.  Things went fine getting these first things installed.  I then wrote a simple script to log into a server via ssh and list the files in the home dir but I am getting the following error when i try to execute the script.  can someone please help.

```
richard@linbox:~/Desktop$ ruby ssh.rb 
ssh.rb:2:in `require': no such file to load -- net-ssh (LoadError)
	from ssh.rb:2

```

Script below

```
require 'net/ssh'

Net::SSH.start('localhost','bumble','********') do |ssh|
    ssh.exec('ls -l')
end
```

---

### Post by rob999 on 2009-03-02
Put this at the top:

```
require 'rubygems'
```

---

### Post by rob999 on 2009-03-02
Also, if using the latest net/ssh, you'll need to pass password as part of the options hash.

```
Net::SSH.start('localhost','bumble',:password=>'********') do |ssh|
```

---

