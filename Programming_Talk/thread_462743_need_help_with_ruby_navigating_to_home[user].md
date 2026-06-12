---
title: "need help with ruby: navigating to /home/[user]"
date: 2007-06-03
forum: Programming Talk
---

### Post by maniacmusician on 2007-06-03
Hi,

I'm learning ruby, and writing my first "usable" program in it. I'm trying to figure out how to get ruby to navigate to/create a directory inside the /home/[user] dir of the user running the app. This is so that I can get it to create a .[config] folder for the app like most common apps do.

Also, how would I simply get it to recognize which user(s) is currently logged in? 

Just some general instructions would be nice. I'm browsing the rdoc documentation ( [http://www.ruby-doc.org/core/](http://www.ruby-doc.org/core/) ) right now to see if there's any classes that cover this, but it's a long search, so if anyone knows the answer, please help me out.

---

### Post by bobbocanfly on 2007-06-03
In bash scripting/terminal "~/" is the home directory, so typing

 ```
cd ~/
```

takes you straight into the currently logged in users home directory.

---

### Post by winch on 2007-06-03
You could use environment variables.
HOME is the users home directory
USER is the username.

Environment variables can be access through the ENV variable.

```
ENV['HOME']
=> "/home/some_user"
ENV['USER']
=> "some_user"
```

I believe ruby also uses the contents of HOME to expand ~ when used in file and directory names.

---

### Post by maniacmusician on 2007-06-03
> **winch said:**
> You could use environment variables.
HOME is the users home directory
USER is the username.

Environment variables can be access through the ENV variable.

```
ENV['HOME']
=> "/home/some_user"
ENV['USER']
=> "some_user"
```
Awesome, thank you. This is exactly what I was looking for!
> **winch said:**
> I believe ruby also uses the contents of HOME to expand ~ when used in file and directory names.
What do you mean by this comment?

---

### Post by JT673 on 2007-06-03
~ (tilde) is the variable for the user's home.  For example if you type:

```
echo ~
```

into the terminal, it will give you what you want.

On the interesting side, when you use sudo, the ~ variable doesn't change:

```

#!/usr/bin/ruby

user=`whoami`
home=`echo ~`
if user == "root\n"
    if home == "/root\n"
        puts "Hi, root!"
    else
        puts "Naughty sudoer!"
    end
else
    puts "You can't use this script because you're not root!"
end

```

---

### Post by maniacmusician on 2007-06-03
> **JT673 said:**
> ~ (tilde) is the variable for the user's home.  For example if you type:

```
echo ~
```

into the terminal, it will give you what you want.

On the interesting side, when you use sudo, the ~ variable doesn't change:

```

#!/usr/bin/ruby

user=`whoami`
home=`echo ~`
if user == "root\n"
    if home == "/root\n"
        puts "Hi, root!"
    else
        puts "Naughty sudoer!"
    end
else
    puts "You can't use this script because you're not root!"
end

```
Thanks, I guess that would work too, although the ENV variable does the job as well.

---

### Post by JT673 on 2007-06-03
Yea, I suppose that will make it easier to read...

---

### Post by qneill on 2008-11-06
Note that the "~" mechanism you are using above is not ruby itself performing the expansion, it is the bash shell invoked by the back ticks ``.  To get ruby to do it (and to avoid some of the security problems with launching an external shell) try File.expand_path() instead

```

# using ~ with no expansion produces no output
p = "~/*"
Dir.glob(p) => []

# using ENV["HOME"] works
p = ENV["HOME"] + "/*"
Dir.glob(p) => [ ... lots of output snipped ... ]

# using Ruby's File.expand_path works too
p = File.expand_path("~")
Dir.glob(p) => [ ... lots of output snipped ... ]

```

---

