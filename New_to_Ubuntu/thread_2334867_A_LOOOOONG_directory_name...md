---
title: "A LOOOOONG directory name.."
date: 2016-08-23
forum: New to Ubuntu
---

### Post by jacko777 on 2016-08-23
Hello all,  I hope I am in the correct area to ask a question.  I am an  absolute beginner, having finally got to the end of my tether with  Windows and all its problems.  I have a working?? knowledge of getting  around but I have made some sort of error.  
"rod@rod-System-Product-Name-Invalid-entry-length-16-Fixed-up-to-11:~$"     This is the start page of my Terminal program, it has driven me silly  trying to get rid of it or change it to just ( rod~$ )  Hope someone is  able to help with this.  At 73 years young, and facing a new learning  curve I am stuck.!:confused:

Regards,
Rod

---

### Post by slickymaster on 2016-08-23
Hi jacko777, welcome to the forums.

You’ll need to edit your **/etc/hostname** and **/etc/hosts** files. Just follow [this simple tutorial]("http://www.howtogeek.com/197934/how-to-change-your-hostname-computer-name-on-ubuntu-linux/") on how to do it.

---

### Post by howefield on 2016-08-23
Typing

```
PS1=rod~$
```

should change the prompt temporarily until you end the terminal session. To make the change permanent, edit the hidden file ~/.bashrc, changing.. (line to change marked in red)

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    [COLOR="#FF0000"]PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '[/COLOR]
fi
```

to look like

```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    [COLOR="#FF0000"]PS1='${debian_chroot:+($debian_chroot)}rod\w\$ '[/COLOR]
fi
```

I'd backup the file before changing it with,

```
cp ~/.bashrc ~/.bashrc.old
```

---

### Post by grahammechanical on 2016-08-23
May I explain where things went wrong so that you avoid this happening again? And it is not necessarily your fault.

When we install Ubuntu we need to set some information such as our name; a user name & password. We also need to set a name for the machine/installation so that it can be identified when we connect to a network. This is where things went wrong for you.

The panel where we set a name for the machine already has the words: "System-Product-Name." We need to delete what is written in that panel and replace it with something of our own choosing. It is very easy, perhaps too easy, to add to what is already written there instead of replacing what is written there.

You are not the first person to trip up over this. I did when I first installed Ubuntu. You can follow the advice given above or do what I did when I fell into this trap. Ubuntu was the only OS on the machine and I did not have any personal data on the machine. So, I reinstalled. And during the installation process I replaced "System-Product-Name" with a name of my choosing.

The system does need a rod@something: -$ You choose what the something should be.

If you are dual booting with Windows then re-installation becomes a bit more complicated than simply choosing "Erase disk & install Ubuntu."

We learn more when we get the answer wrong, then we do when we get the answer right. We do not get it wrong a second time.

Regards.

---

### Post by jacko777 on 2016-09-08
Thank you all for the answer.  I have had success changing the name, also I have learned where to edit the problem.
I will now try to mark the thread as answered, then ask yet another question.
Thanks again to you all who helped.
Jacko777

---

