---
title: "Understanding the sh command"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by adj3 on 2014-10-30
Hello people,

I was trying to add the Skype ppa to my system when I came across this command:

sudo sh -c "echo 'deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner' >> /etc/apt/sources.list.d/canonical_partner.list"

I don't understand what this command does and had a few questions about it.

Firstly I don't understand what is sh's functionality reading the man page.
Secondly I am having trouble understanding what sh really dose mainly because if bash is basically Bourne Shell... why do we need to use sh in the first place?
Thirdly how is the code above comparable to add-apt-repository ppa:.../ppa

Thank you for your time :)

---

### Post by JazzPotato on 2014-10-30
The code does that same thing as the add-apt-repository command, but sometimes people dont' have it installed on their *buntu systems so I assume whoever wrote that command was anticipating that.
Also, the "sudo sh" at the beginning of that command is perfectly superfluous, at least on *buntu systems. everything before the "echo" could be dropped. I think, *maybe * that the person who wrote the command was anticipating that some users wouldn't have bash installed, and they just wanted to make sure that you ran it in a shell? :-k

---

### Post by Lars Noodén on 2014-10-30
The shell is a user interface for the whole operating system.  There are several varieties of shell, some are closer to the universal standard, like dash, others, like zsh and bash, are more tricked out.  The bash shell is less portable and not as fast, but can do a lot more.  In a situation where you need to run many shell scripts back to back, it can make a difference in speed to use sh and not bash.  The regular shell is also more portable, so if you write your script on Gnu/Linux, it is more likely to run unmodified on BSD or Solaris etc. if you run sh (dash) instead of bash or zsh.

You can think of the line like this pseudo-code:
```

sudo { 
     sh -c "{
        echo 'deb http://archive.canonical.com/ubuntu/ trusty partner' >> /etc/apt/sources.list.d/canonical_partner.list
     " }
}

```

The "sh -c" is needed to run "echo >>" under its own shell in order to do all that as root using "sudo" since without it the redirect >> will fall outside the effects of sudo.  The -c just means run the following commands.  So the result is that it appends the line 'deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) trusty partner' to the file /etc/apt/sources.list.d/canonical_partner.list

Like with anything, complexity also brings risk.  And we saw last month some shell problems bite us as a result of the complexity.  Here is one:

[http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-6271](http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2014-6271)

These problems were not present in the more standard, simpler shells.

---

### Post by adj3 on 2014-10-31
Thank you for your responses. I had two more unrelated questions the first one is: can I name the canonical_partner.list whatever I want or should it be specifically named "canonical_partner.list"? My second question is what are these names: trusty partner, saucy partner, raring partner ,quantal partner .........?

---

### Post by deadflowr on 2014-10-31
Each version of Ubuntu has it's own repository, so 14.04(trusty) has one, as do 12.04(precise), and 12.10(quantal).
If that helps.

It should also be noted that the canonical partners repos already has an entry in the main repository sources list.
located at /etc/apt/sources.list.
It is also already entered in the available listing of repositories in the program called Software and Updates.
Look in the section marked Other Software.
It is always disable by default, but opening that above mentioned program will allow you to easily enable it.

Of course this is completely off-topic to the thread conversation, but I felt it was worth a mention...

---

### Post by Lars Noodén on 2014-10-31
The filenames in that directory need to end in .list, as far as I know, for APT to read them but other than that you can call it what you want.  

```

deb http://archive.canonical.com/ubuntu/ trusty partner

```

The first name in the list, "trusty", is that of the version.  The different [versions of Ubuntu have different names](https://wiki.ubuntu.com/Releases).  So "trusty" tells APT to get the files for 14.04 LTS and not any others.  The second name, and any subesquent names, in the list is the repository.  "partner" is for material contributed by Canonical's partners.  It is one source of third-party packages.  The usual options are ["main" and "universe"](https://help.ubuntu.com/community/Repositories/Ubuntu), though some people might also enable "restricted" and "multiverse".

---

