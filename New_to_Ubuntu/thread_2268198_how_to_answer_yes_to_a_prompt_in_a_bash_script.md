---
title: "how to answer yes to a prompt in a bash script?"
date: 2015-03-06
forum: New to Ubuntu
---

### Post by Delco on 2015-03-06
I am using ubuntu 14.04 in a virtualbox guest.

I run the following command on my terminal to install guest additions:

```
sudo apt-get -y install virtualbox-guest-dkms
```

I thought that the -y was supposed to answer yes to any prompts, but it does not answer yes to this question:

```
Configuration file '/etc/X11/Xsession.d/98vboxadd-xclient'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** 98vboxadd-xclient (Y/I/N/O/D/Z) [default=N] ?
```

I already have vbox guest additions installed but they are an older version, so I am getting prompted with this. How would I run the original command so it automatically answers Y to this prompt?

---

### Post by ian-weisser on 2015-03-06
Generally, you don't want to auto-answer config questions like that.
The system is telling you that it really doesn't know what to do and needs human input.

If you really want to delete your custom file, then delete it *before* running the command. No more conflict. No more question.

---

