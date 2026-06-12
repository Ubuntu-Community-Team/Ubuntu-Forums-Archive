---
title: "Writing a shell script"
date: 2006-03-29
forum: Programming Talk
---

### Post by rado_london on 2006-03-29
Hello
I have few headaches with Dapper and the Internet connection. However I found a solution: I have to ifdown and the up on each login. I want to make a script to do that for me on boot up. Can you please help me with it?

Thanks in advance

---

### Post by xaphan on 2006-03-29
Hello,
give this a shot

#!/bin/bash
sudo su
ifdown eth0
ifup eth0
exit

*assuming your network device is eth0

save the script and put it in /etc/init.d
run the following command: 
update-rc.d <name-of-your-script> defaults
chmod +x  <name-of-your-script>

that should do the trick

---

### Post by rado_london on 2006-03-29
HEy thanks a lot it works. So everytime i switch on the machine it will execute automatically. If so its great.

ANd welcome to our community. This is your first post and you save my life.

Cheers

---

### Post by rado_london on 2006-03-29
Hi again. On the second reboot it didnt work. Now I have other problems. The cpu is running 100% all the time, as well as the machine hangs the switching off.
Any ideas why?

---

### Post by xaphan on 2006-03-29
eek! sorry about that..
next time ill test before i post...
run this command:
update-rc.d -f <name-of-your-script> remove
then make the script:

#!/bin/bash
sudo ifdown eth0
sudo ifup eth0

run these commands:
update-rc.d <name-of-your-script> defaults
chmod +x <name-of-your-script>

still new to shell scripts...


try that.  I just tested with success.

---

### Post by rado_london on 2006-03-29
Everything works now. Thanks again.

---

