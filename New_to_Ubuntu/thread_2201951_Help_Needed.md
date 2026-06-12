---
title: "Help Needed"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by john148 on 2014-01-26
Hi everyone,  I am absoloutly new to Ubuntu and have never worked with it.  That being said I am having an issue.  I am trying to set up a static router and I am using vmware.  This is an assignment for a class.  I have successfully added another network interface,  eth0 and eth1 are both pingable.  I went into the /etc/sysctl.conf**[FONT=&quot]    [/FONT]** and removed the “#” from the following line net.ipv4.ip_forward=1.  Next I am trying to go to /etc/rc.local .   I am able to get there but when I enter the command /sbin/iptables -P FORWARD ACCEPT
I get an **E486 Pattern not found : sbin**  I have not been able to figure this out and I have about givin up any help would be greatly appreciated.  I have attached a screenshot.  Thank you again.

John

---

### Post by Mark Phelps on 2014-01-26
We are not a homework service. Please see code of conduct which you agreed to.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued

---

### Post by john148 on 2014-01-26
I am not asking you to give me the answer,  I am trying to learn ubuntu and I would appreciate some help.  The last thing I want is someone to answer the question that would defeat the purpose of doing the assignment.  The reason I stated it was homework was because I did not want the answer and wanted to let everyone know this was an assignment. Also, no where in the post do I ask for someone to answer it so excuse me if I was not clear and thank you for your concern.

John

---

### Post by steeldriver on 2014-01-26
I don't think your issue has much to do with the assignment - you appear to be trying to edit the file with vi (or possibly vim) without understanding the 'modal' behaviour of the editor. 

Until you press i (to enter *insert mode*) the editor is in *command mode* - and it is interpreting your keyboard input '/sbin' to mean 'search the file for the string sbin'. Since the file doesn't contain the string, you get the response 'E486: Pattern not found: sbin'

FWIW I suggest you use the 'nano' editor instead - it is a bit more intuitive

---

### Post by The Cog on 2014-01-26
You are using vi to edit the file. You forgot to press the I key to enter insert mode before typing the line you want to enter. A / when you are not in insert mode is the start of a search string, hence the response Pattern not found.

You may find nano easier to use for now, although I think it is probably worth learning basic vi commands in the long term.

Oh pooh. Steeldriver beat me to it by 7 minutes. Did it really take me that long to type? Distracted by the telly.

---

### Post by john148 on 2014-01-26
Thank you so much guys,  can you guys reccomend any online sources for beginners to learn how to navigate through Linux

John

---

