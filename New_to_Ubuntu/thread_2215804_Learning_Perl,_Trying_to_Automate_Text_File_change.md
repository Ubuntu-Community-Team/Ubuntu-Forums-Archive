---
title: "Learning Perl, Trying to Automate Text File changes"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Magnezone150 on 2014-04-08
Hi,

I've been trying to learn Perl and I like it.
But I'm now having trouble automating Text files.

I have scripts now that just call Vi For Example: (system ("vi /etc/file.conf");) and that creates or edits but I still have to manually edit it and then :wq! to save and exit Vi.
Is there a way I can have this process automated, I was told I should learn awk/sed for this but I don't know where to start or what to do.

Suggestions would be awesome, Thanks.

---

### Post by TheFu on 2014-04-08
For quick changes to text files, sed is the right tool if the setting you want is already inside.

All of these tools are based on "regular expressions" - a specialized pattern matching language. "RegEx" is what grep uses too.

[http://www.grymoire.com/unix/sed.html](http://www.grymoire.com/unix/sed.html) - sed tutorial.

You can use perl for this too, but I wouldn't (speaking as a Perl programmer myself). Lots of overhead that just isn't necessary for normal conf files.

If you want to manage servers, then look for a server management tool like Ansible, chef, puppet, rexify, salt.  Rexify is written in Perl. I prefer Ansible - takes about 30 minutes to start managing servers.  If ssh is already working ... you are over 50% done.

I wouldn't bother with awk that this point, but learning enough to slap a tiny 1 liner isn't hard.  sed and cut are plenty, then use perl if something more complex is needed.

---

### Post by Magnezone150 on 2014-04-08
Alright Awesome, Thank you For the suggestions and tips! :)

What I do is I create a lot of Linux VMs and they require set-up and changes to certain config files.
So what I've been doing is automating the set-up with a simple perl script that runs the needed commands to set it up instead of manually typing commands for everything. but when it comes to the config files then I have to use Vi to edit them.

---

### Post by TheFu on 2014-04-08
vagrant and ansible. There are other ways too - probably 500 of them. Vagrant is more for developers. I've never used it.
[http://docs.vagrantup.com/v2/provisioning/ansible.html](http://docs.vagrantup.com/v2/provisioning/ansible.html)

virt-install is another way.

I use ansible to manage about 30 VMs.  We don't create new VMs very often, so using virt-manager is fine to get the machine up with ssh.  Then I .... [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

---

### Post by Vaphell on 2014-04-08
I can't agree learning awk is a waste of time. I've solved many non-trivial problems with it and i still don't know perl.
AWK offers excellent ROI - after just few hours of learning you can solve like 95% of common problems sed fails at.

---

### Post by TheFu on 2014-04-08
> **Vaphell said:**
> I can't agree learning awk is a waste of time. I've solved many non-trivial problems with it and i still don't know perl.
AWK offers excellent ROI - after just few hours of learning you can solve like 95% of common problems.

Agreed, but that same comment could be made for perl, ruby, python, bash  or ... 

If you have 5+ servers to manage, check out ansible. I think you'll thank me.  Ensuring a config option exists inside a config file is trivial with Ansible.  If it exists, it will be left alone. If the line exists, but isn't what you want, it will be changed. If the setting is not in the conf file, it will be added.  All with just 1 trivial ansible input.  If you are managing 50 conf files, all the pre-written, pre-validated ansible code really speeds things up.
My ansible file to have logwatch use my email address:
 common_logwatch_settings.yml 
```
---
- name: Make logwatch mail {{ logwatch_email }} daily
  action: lineinfile dest=/etc/cron.daily/00logwatch 
          regexp="^/usr/sbin/logwatch" line="/usr/sbin/logwatch --output mail --mailto $logwatch_email --detail high" 
          state=present create=yes

```
and that is a complex version.
for sshd_config settings:
```
---
- name: Update ssh parameters  - no root login
  action: lineinfile dest=/etc/ssh/sshd_config
    regexp="PermitRootLogin" line="PermitRootLogin without-password"
    state=present create=yes
  action: lineinfile dest=/etc/ssh/sshd_config
    regexp="X11Forwarding" line="X11Forwarding yes"
    state=present create=yes
  notify:
    - restart ssh

```

---

### Post by Magnezone150 on 2014-04-08
Interesting, I'm going to look into that. Thank you!

But Yeah I create and delete a lot of VMs off my Non-Profit business CentOS Hosted KVM Server.
And where I work I create lots of VMs using VMware Vsphere Client for customers and some customers require Ubuntu for Development and testing. So my Scripts help me complete my Deployments more efficiently.

---

### Post by Vaphell on 2014-04-08
> Agreed, but that same comment could be made for perl, ruby, python, bash or ...

Well, no. Bash has tons of caveats because of the legacy cruft in the whole shell business, python as a general purpose language requires much more boilerplate code to even read the damn file and extract relevant stuff (i suspect ruby is in the same category), perl... well, terse syntax makes it a write only language. The time investment to get any utility from them in text file mangling is considerable.

Sed is a black magic once you go beyond s/// and sucks hard at multiline stuff which is not a problem for awk (configurable RS) and the awk code is mostly what, a bunch of clean *condition { do/print something }* applied on a record-by-record basis?

for me it's bash, sed -> awk -> python and i pull python once for every 20 5minute awk hacks, mostly for things like xml, where text layout != doc structure or when having multilayered arrays/dictionaries is beneficial.

---

