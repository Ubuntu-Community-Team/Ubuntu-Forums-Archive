---
title: "gaining root powers"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by issae002 on 2012-03-26
It's been many years since I used unix, but here goes.

My machine is new, and I am the only user.  At first login, I created my account.  While the machine claims I am the administrator, it only allows me to login as a "guest user" and seems to grant no powers, e.g., to install software.  su root or sudo do nothing.  Any advice is appreciated.

---

### Post by oldfred on 2012-03-26
Welcome to the forums.

You should not be logging in as guest but as the user & password you created when you installed. That user is an admin and then sudo or su should work.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by issae002 on 2012-03-26
I thought I was, but now realize that the default "guest" has the "name" of my computer.  This name is similar to my admin name, so I was fooled.  Glad that, by accident, I chose different names!  Thanks much!

---

### Post by NaN010101 on 2012-03-26
I hope I'm not hyjacking the thread here but issae002 seems happy with the answer he got to a question very similar to mine...
 
This is about my 10th time "trying to get started" with Linux so I setup Ubuntu 10.11 on a VMWare server VM (with an admin name and password) the other day .. 
 
I open Terminal and it says I'm logged in as User and if I want to execute a command as root, I should use "sudo command".. so I clearly am not root now.. I type su and I am prompted for a password... I assume it wants root's password.. What to heck is root's password?.. In the whole install process I was never asked to enter one.. (I've just re-installed the whole VM again just to make sure). I've tried blank, "root", user's password.. I don't get it.. what to heck is root's password?
 
Any help appreciated.
 
 
update.. 
doh.. should have read [[COLOR=#444444]https://wiki.ubuntu.com/RootSudo[/COLOR]]("https://wiki.ubuntu.com/RootSudo") mentioned above first.. Thanks

---

### Post by aysiu on 2012-03-26
NaN010101, if you want a semi-permanent root login, then ```
sudo -i
``` is your friend.

---

### Post by NaN010101 on 2012-03-26
thanks aysiu

I should actually have read that _whole_ post about sudo vs root before I updated my post. I've edited my update so I don't sound like I'm looking to change everything before I've bothered to understand it.. I HATE THAT : -) )

---

### Post by oldfred on 2012-03-26
We all have to learn and I am stilling learning a lot by reviewing others who post some good info in areas that I am not so familiar.

I hope you did see the important post. The only issue with this it that is just does not work in my house. :)

[http://xkcd.com/149/](http://xkcd.com/149/)

---

