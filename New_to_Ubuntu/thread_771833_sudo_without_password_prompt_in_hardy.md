---
title: "sudo without password prompt in hardy"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Frank Golden on 2008-04-28
Hi folks, First off I know enabling sudo without a password prompt is potentially unsafe but I am the only user and the only person with access to my machine. Here's my problem.
I just tried to edit the sudoers file in hardy using the following command.

```
EDITOR=gedit sudo visudo 
```

I have used this command to open the sudoers file in earlier versions of Ubuntu so that I could enable using sudo without password prompt.
Again I know this is potentially unsafe but it is my computer.
In hardy the above command opens the file in the terminal and not gedit like it is supposed to do.
Uncommenting the line ```
%sudo ALL=NOPASSWD: ALL
``` won't save nor can I add the line ```
frank ALL=(ALL) NOPASSWD: ALL
``` the terminal won't let me add the above line.
In earlier versions of Ubuntu the EDITOR=gedit... command opened the sudoers file in gedit and allowed saving changes.
What gives with hardy?
Is there a way to change the sudoers file in hardy to allow me to sudo
without the password prompt?

---

### Post by sam_delta on 2008-04-28
sudo security its not only for unauthorized users, but also to malicious software or hackers, i woulnt recommend doing that.

sam

---

### Post by cm.squared on 2008-04-28
From the man page it sounds like visudo isn't set up to accept other editors.  Short of recompiling visudo with that option set, it sounds like the easiest (if unsatisfactory) workaround would be to learn enough vi/m to edit the sudoers file...

There's a good tutorial at [this website]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html").  It's really not as hideously unusable as people claim.  I found that I actually like it.

---

### Post by Frank Golden on 2008-04-28
> **sam_delta said:**
> sudo security its not only for unauthorized users, but also to malicious software or hackers, i woulnt recommend doing that.

sam
I know that but it is my computer and I can do what I want with it.
I know the risks. So having said that is there any way to do what I want in hardy or have the Linux gods with hardy decided to protect me from myself like M$ does.
If you won't post a solution on this public forum at least PM me with one.

---

### Post by sam_delta on 2008-04-28
have you considered making a root account?

```
sudo passwd root
```

ull be able to log in as , user name "root", and the password you just entered

to disable root acc

```
 sudo passwd -l root 
```

sam

---

### Post by cm.squared on 2008-04-28
Another solution would be to edit the sudoers file like this:
```
gksudo gedit /etc/sudoers
```
Make the changes you want and choose "Save as..." something like sudoers.edited.  Then you could sudo copy the edited file to the real sudoers:
```
sudo cp /etc/sudoers.edited /etc/sudoers
```
That should be the last password you need to enter for sudo...

---

### Post by Frank Golden on 2008-04-28
> **cm.squared said:**
> From the man page it sounds like visudo isn't set up to accept other editors.  Short of recompiling visudo with that option set, it sounds like the easiest (if unsatisfactory) workaround would be to learn enough vi/m to edit the sudoers file...

There's a good tutorial at [this website]("http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html").  It's really not as hideously unusable as people claim.  I found that I actually like it.
Ok that answers my question. I guess the devs don't trust me or any other user to know what is good for them.
I use some custom launchers I created that use the gksu prefix in the command and it is annoying to have to type in my password on occasions when I use them.

---

### Post by Frank Golden on 2008-04-28
> **cm.squared said:**
> Another solution would be to edit the sudoers file like this:
```
gksudo gedit /etc/sudoers
```
Make the changes you want and choose "Save as..." something like sudoers.edited.  Then you could sudo copy the edited file to the real sudoers:
```
sudo cp /etc/sudoers.edited /etc/sudoers
```
That should be the last password you need to enter for sudo...
Thanks cm worked great.

---

