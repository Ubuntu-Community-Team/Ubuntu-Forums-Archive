---
title: "[SOLVED] Can anyone tell me?"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by burnetbj on 2008-10-06
First off let me just say I have really enjoyed using Linux for awhile now I dont see my self ever stopping using it ......but the only thing I can think of that isnt up to par with its competition is the remote or net shares. So my question is Can anyone tell me why we cant just \\devicename or mstsc or = ip or devicename. I just cant for the life of me see why we need to install software and go through some crazy setup procedures to get into another PC on the network ....just seems goofy ....Am I missing something or is it really this way, if it is really this way are there Programmers working on a replacement software that we can just remote into another device on the network or?  

Thanks for any help

---

### Post by jerome1232 on 2008-10-06
The reason you have to install software is because it's not a good security model to have a default install listening on the network for connections, especially file shareing (then it would be like on windows where we'd be forced to resort to firewalls to prevent access to your computer)

There are many options when it comes to file sharing in ubuntu, the easiest is probably ssh.

for ssh you just install openssh-server, then you can connect from the other computer, places->connect to server->ssh, fill in login name and ip, then it's mounted with an icon on your desktop. You can even bookmark it and access it directly from your places menu afterwards

---

### Post by Zzl1xndd on 2008-10-06
Its also worth noting that you might be sharing with a Windows machine or another Posix operating system so having a pre-installed format wouldn't make too much sense as you might be using NFS or SMB.

---

### Post by burnetbj on 2008-10-07
Thank you for the response, I guess I can understand what your saying. I guess I would do a back flip if I could just \\into my other boxes.....i will try the ssh and see how it goes. I wish we could just just lock down our main machines and \\into another box then authenticate as root when it prompts for permission .....SSH it is i guess

---

### Post by jerome1232 on 2008-10-07
You maaay need to install sshfs as well on the client computer (sudo apt-get install sshfs) not sure so, if you can try it before you install it and let me know :)

---

### Post by burnetbj on 2008-10-07
I am gonna crash for tonight but will give it a shot after work tomorrow thanks for the help

---

### Post by hyper_ch on 2008-10-07
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

Just imagine what these forums would look like if everybody would just post "Help" or "Noob here". What do you think how many people will still look at such threads?

Furthermore, for unrelated questions it's also adviced to open a seperate thread for each one, so that each problem can be addressed (and eventually marked as solved) individually.

---

