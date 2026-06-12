---
title: "Cannot SUDO with USER"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by dummyapple on 2008-05-21
Hi. I've created a root user for admin purposes on my server and another user using this command:
useradd -m abc


However, this user cannot do simple things such as install flash, or really do anything which requires SUDO.

How can I make this user more powerful? or even give it root control if there's not other way. Thanks!

If I do SUDO it says
"sudo password for abc" = i enter the password then
"sorry, user abc is not allowed to execute [command] as root on [computer IP/name]"


I'd prefer a command which I can do to make abc powerful enough to install things or just use sudo. 
Thanks!

---

### Post by dark_harmonics on 2008-05-21
[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

Check that to find out how to add the user to the "administrators" group. I know how to do it through the gui but never did it from a command.

---

### Post by dummyapple on 2008-05-21
> **dark_harmonics said:**
> [http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

Check that to find out how to add the user to the "administrators" group. I know how to do it through the gui but never did it from a command.

Thanks. I just need to know what the default 'root' group is named? The group which is admin. I can add my user to that.

---

### Post by dark_harmonics on 2008-05-22
Well there is technically a "root" group but i think the group name you want is "admin".

---

### Post by Joeb454 on 2008-05-22
I'm thinking you'll want admin as well. You could look at the other user on the PC to see what groups they are in, and base the new user from that :)

---

