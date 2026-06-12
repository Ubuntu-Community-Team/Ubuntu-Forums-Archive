---
title: "Firestarter when running blocks printing and internet access"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Jim Rimedio on 2008-10-30
I installed Firestarter 1.0.3.  Now, I have to stop Firewall to print and to access the internet.  As a newbie, I am sure there is a way to configure the Firewall to keep it running while printing and accessing the firewall.

     I am using Ubuntu 8.4 connected to a Microsoft Network on a Microsoft XP box.  The host is named BLACKCOMPUTER, the printer is a HP Laser Jet 1018.

    Can anyone tell me what to do in Firestarter to solve this problem?

---

### Post by meindian523 on 2008-10-30
You probably need to open the ports you are using.I don't know the exact port numbers,but I think editing outbound policy to be permissive by default and blacklist traffic may be a solution to your problem.

---

### Post by eolson on 2008-10-30
As Meindian said the outbound traffic policy probably needs to be reset.

Click on the firestarter icon
seclect policy

You should see inbound traffic policy maybe outbound
If it says inbound click on it the select outbound
click on permission
then click the apply policy

you should be good from there.

as a sidenote, you really don't need a firewall at all, but being as how you've already  got it  you might as well have it.

---

### Post by Thelasko on 2008-10-30
I had the same problem.  It turns out there is a bug in Firestarter.  Development for Firestarter is dead upstream.  I recommend Gufw instead.  It has been added to the repositories for Intrepid Ibex, but you can get a version for Hardy [from here.]("http://gufw.tuxfamily.org/index.html")

---

