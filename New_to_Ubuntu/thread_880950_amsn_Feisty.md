---
title: "amsn Feisty"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Carl_Barks on 2008-08-05
Hello there community.

I am using Ubuntu Feisty and lately amsn won't connect at all. I've been hiting my head on the wall doing all the crazy stuff and searching the whole internet to find a solution.

I am using an older version of amsn(0.96). It seems the problem is that because microsoft changed some protocols i have to get the 0.97.2 version of amsn, BUT, i can't get it to install it. Manually , i get an error 
-----------------------------------------------
Checking for required C library versions ... OK
Error: Unable to prepare package AMSN MSN client.
-------------------------------------------------

if i try  sudo apt-get install amsn it says that i already have the latest version!!!

So, my guess is that, feisty are too old to support the new version of amsn (i get the same thing with firefox3 and i am still using the 2version). 

Is this right? Do i really have to go upper into Gutsy or Hardy? Thnx in advance.

---

### Post by Ryadt on 2008-08-05
Its nothing to do with fiesty..Lots of people have been having this problem running hardy (including myself).
Solved it by downloading amsn from its website using the Tcl/Tk84 installer.

---

### Post by Carl_Barks on 2008-08-05
> **Ryadt said:**
> Its nothing to do with fiesty..Lots of people have been having this problem running hardy (including myself).
Solved it by downloading amsn from its website using the Tcl/Tk84 installer.

did that but i can't install it. that's the problem. I get the Error i mentioned above, and i think it has to do with feisty. That i cannot install the new version on feisty. (i have been using 0.96 till today)

---

### Post by Carl_Barks on 2008-08-06
bump

---

### Post by Adri2000 on 2008-08-06
Hi,
I am going to upload a fixed package to feisty-proposed. I will need you to test it so that it can then be moved to feisty-updates. Please watch the bug report: [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)
Thanks.

---

### Post by Carl_Barks on 2008-08-09
> **Adri2000 said:**
> Hi,
I am going to upload a fixed package to feisty-proposed. I will need you to test it so that it can then be moved to feisty-updates. Please watch the bug report: [https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722](https://bugs.launchpad.net/ubuntu/+source/amsn/+bug/243722)
Thanks.

thnx for you work but being a completely noob in complicated things on Linux , what the heck i do with this? [http://launchpadlibrarian.net/16595922/amsn_0.96%2Bdfsg1-0ubuntu2.1.debdiff](http://launchpadlibrarian.net/16595922/amsn_0.96%2Bdfsg1-0ubuntu2.1.debdiff)

As you can see someone posted accepted at feisty-proposed so i think this might really work, but i don't know what exactly to do in order to fix it. Thnx in advance

---

### Post by Adri2000 on 2008-08-10
You should enable feisty-proposed, update amsn, and disable feisty-proposed. If you don't know how to do that, you can also directly download the .deb and install it manually (double-click on it).

It's [http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.96+dfsg1-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.96+dfsg1-0ubuntu2.1_i386.deb) if you're using a 32 bits PC.

---

### Post by Carl_Barks on 2008-08-12
> **adri2000 said:**
> you should enable feisty-proposed, update amsn, and disable feisty-proposed. If you don't know how to do that, you can also directly download the .deb and install it manually (double-click on it).

It's [http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.96+dfsg1-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/a/amsn/amsn_0.96+dfsg1-0ubuntu2.1_i386.deb) if you're using a 32 bits pc.

[solved]

---

### Post by Adri2000 on 2008-08-12
> **Carl_Barks said:**
> [solved]

Can you please add a comment to the bug I mentioned earlier saying that it works for you on feisty? It's needed so that the fixed package can then be distributed through the normal updates.

---

