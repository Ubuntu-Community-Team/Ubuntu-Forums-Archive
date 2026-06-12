---
title: "fail at importing key using gksudo"
date: 2009-10-08
forum: Programming Talk
---

### Post by valaprgrmr on 2009-10-08
This is my command:
gksudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY

And the output is:
gksudo: unrecognized option '--keyserver'

What should I do?
I need the graphic window.

Thanks.

---

### Post by mikewhatever on 2009-10-08
The graphical way of importing keys is under System->Admin->Software Sources, Authentication tab.

---

### Post by valaprgrmr on 2009-10-08
I'm writing a program and I want the user to type the password in the graphical window.

---

### Post by valaprgrmr on 2009-10-08
success with:
gksudo **"**apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEY**"**

I have one more problem executing this:
echo 'deb [http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/jaunty-ppa/ubuntu) jaunty main' | gksudo tee -a /etc/apt/sources.list

it works fine with sudo but not with gksudo.

Thanks.:)

---

