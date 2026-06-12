---
title: "how to fix bash shell in ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by ash123 on 2008-05-01
Dear all,

I'm new to linux as well as to ubuntu and i have also installed kubuntu. I was trying to make an installation workable but somehow i just made the shell unaccessible. 
When i open the kconsole its like that

bash: export: `/home/ash/omnetpp-3.3/lib': not a valid identifier
bash: lesspipe: No such file or directory
bash: dircolors: No such file or directory
bash: uname: No such file or directory
bash: uname: No such file or directory
bash: [: !=: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: =: unary operator expected
bash: [: too many arguments
bash: [: =: unary operator expected
bash: sed: No such file or directory
ash@ash-laptop:~$     


I need help to fix this.

Thanks alot
ash

---

### Post by Monicker on 2008-05-01
What did you do when you tried to make it "workable" ???

Did you modify the bash profile?

---

### Post by ash123 on 2008-05-01
i was trying to install a simulator and then i was setting the environment variable in the bash.bashrc file. But now i'm unable to use the sudo and therefore i can't change or modify it. 
cheers

---

### Post by Monicker on 2008-05-01
> **ash123 said:**
> i was trying to install a simulator and then i was setting the environment variable in the bash.bashrc file. But now i'm unable to use the sudo and therefore i can't change or modify it. 
cheers

You changed /etc/bash.bashrc or /home/username/.bashrc ?  If you changed the latter you can copy /etc/skel/.bashrc to your local user account.   I am not seeing anything else which looks like an exact copy of /etc/bash.bashrc when I hunt around on my system.

---

### Post by ash123 on 2008-05-01
Hi, i changed /etc/bash.bashrc.

I can't edit it anymore.
Is there any way i can change this now and remove the changes which i have done it.

cheers

---

### Post by Monicker on 2008-05-01
> **ash123 said:**
> Hi, i changed /etc/bash.bashrc.

I can't edit it anymore.
Is there any way i can change this now and remove the changes which i have done it.

cheers

Did you happen to make a backup copy of the file before you started editing it?  If not, I would boot from the live cd, and copy the file from the live cd to the local hard drive.

---

### Post by Dr Small on 2008-05-01
Reboot into single mode (recovery mode) from the GRUB boot menu, and when it logs you in, you will be root@host:~#

From there, edit the file.

Dr Small

---

### Post by ash123 on 2008-05-01
Hi dear, 

Can u tell me how i can copy the file from live CD. and how i will access the live cd after booting. As live CD gives certain options. So which option should i take. I know i 'm quite messy asking stupid questions but i'm quite new to the environment.

cheers

---

### Post by ash123 on 2008-05-01
Hi dear

can u explain it a bit more. As i tried this but i dont know how to edit the file at the root. As vi editor , gedit and other text editor i know dont work. Can u tell me i should i do that. Thanks for being patient.

cheers

---

### Post by ash123 on 2008-05-01
I booted from liveCD ubuntu. But know i can't see my actual install environment but now i 'm in the environment created by liveCD. I dont know how to access the actual install ubuntu. can u guide me.

cheers

---

### Post by ash123 on 2008-05-02
Dear Moniker and Dr Small 
I'm able to fix the shell problem by utilizing the live cd and managed to fix bash.bashrc shell. I'm really thankful to both of you guy.

cheers

---

