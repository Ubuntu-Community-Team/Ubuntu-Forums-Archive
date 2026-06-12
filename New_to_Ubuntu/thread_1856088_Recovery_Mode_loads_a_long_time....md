---
title: "Recovery Mode loads a long time..."
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Phillie on 2011-10-07
Hi there :)

I'm trying to get into the recovery mode but it stops at:

```

Loading, please wait
[      4.576313]<30>udev[65]:starting version 167
```

and then there's a blinking underline....
Does starting the recovery mode takes more than one hour?

I just want to get into a root shell for running one command (unfortunately theres no other way to fix my problem...) 
Booting normally works fine.

I'm using: Kubuntu 11.04 installed with wubi beside Windows7

LG
Phillie

PS: Please excuse my English...

---

### Post by Frogs Hair on 2011-10-07
Hello and Welcome

You could boot normally and try Crtl + Alt F1 or F2 .

---

### Post by Phillie on 2011-10-07
Hi

ctrl+alt+f1 gives me a blinking underline samething with f2... should it open a rootshell ?

Is there any way to get into a root shell without the recovery mode or sudo?
(because sudo is the problem... I did something very stupid...)

lg
Phillie

---

### Post by wildmanne39 on 2011-10-07
Hi, you can do it with ctrl+alt+f1 at the blank screen type your user name and then your password, and no the terminal does not open the blank screen is the terminal in layman terms.
Thank you

---

### Post by Phillie on 2011-10-07
Thank you...

But I cant type anything on the black screen... there's just this blinking line... shall I wait longer?

lg
Phillie

---

### Post by wildmanne39 on 2011-10-07
Hi, you should be able to enter your user name right away, the password will not show on the screen, it should just allow you to type the commands if you entered your login and password correctly, but if you are having a sudo issue that could be the problem.
Thank you

---

### Post by Phillie on 2011-10-07
Yeah I think its really the sudo thing... I acidentally made the sudoers.d folder my own... and now 
```
chown -r root /etc/sudoers.d
```wont work... and

```
chmod 0440 /etc/sudoers.d
```just changes the rights... the folder still belongs to me... 

I see a newinstallation coming...  :-(

lg
Phillie

---

### Post by wildmanne39 on 2011-10-07
Hi, here is a link to fix the sudoer file.
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)
There are 4 ways of repairing sudo in this link, and it depends on what you have done to break sudo.
Thank you

---

### Post by jtarin on 2011-10-07
> **Phillie said:**
> Hi there :)

I'm trying to get into the recovery mode but it stops at:

```

Loading, please wait
[      4.576313]<30>udev[65]:starting version 167
```

and then there's a blinking underline....
Does starting the recovery mode takes more than one hour?

I just want to get into a root shell for running one command (unfortunately theres no other way to fix my problem...) 
Booting normally works fine.

I'm using: Kubuntu 11.04 installed with wubi beside Windows7

LG
Phillie

PS: Please excuse my English...

This command is the equivalent of su for Ubuntu, it asks for your password and switches to the root user:

    sudo -s 

And don’t forget to type exit to switch back to your normal user when you are done.

---

### Post by jtarin on 2011-10-07
> **Phillie said:**
> Hi there :)

I'm trying to get into the recovery mode but it stops at:

```

Loading, please wait
[      4.576313]<30>udev[65]:starting version 167
```

and then there's a blinking underline....
Does starting the recovery mode takes more than one hour?

I just want to get into a root shell for running one command (unfortunately theres no other way to fix my problem...) 
Booting normally works fine.

I'm using: Kubuntu 11.04 installed with wubi beside Windows7

LG
Phillie

PS: Please excuse my English...

What command are you wanting to run before boot?

---

