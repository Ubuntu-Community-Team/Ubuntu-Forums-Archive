---
title: "Anyway to automatically run a .py program whenever you start the terminal?"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by caiocamboim on 2013-06-04
I am a complete beginner at this and new to the forums. Just started using ubuntu and started learning python today, know just the very basics or less than that! ](*,)

   So I'd like to know if there's a way to automatically run a python(.py) program whenever you open the terminal(Like a ***print "Hello sir."*** program), or something else whenever you turn on the computer. 

   Also as I'm using ubuntu side by side with Windows 7 through Grub, I'd like to know if there's a way to quickly switch between them without having to wait for the computer to restart and run Grub, and just then choose the OS.

Thank you all :D

---

### Post by Impavidus on 2013-06-04
You can put the command to run it in your **.bashrc** file. Everything in that file is executed whenever you open a new terminal.

In this case python sound like overkill. You can also put **echo Hello sir.** in your .bashrc.

---

### Post by caiocamboim on 2013-06-04
Ok that sounds useful but how do I do that? ;P Sorry but as I mentioned Im a total beginner...

---

### Post by arpanaut on 2013-06-04
The only way to quickly switch between OS's is to have one OS running with the other OS running in a virtual machine installed on the original OS

See Here: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)
and: [https://help.ubuntu.com/community/Virtualisation](https://help.ubuntu.com/community/Virtualisation)

---

### Post by caiocamboim on 2013-06-04
> **Impavidus said:**
> You can put the command to run it in your **.bashrc** file. Everything in that file is executed whenever you open a new terminal.

In this case python sound like overkill. You can also put **echo Hello sir.** in your .bashrc.

Thanks for the help! :D I could do it using **emacs .bashrc** and then using the **echo **command. He greeted me when I logged in! xD

---

### Post by caiocamboim on 2013-06-04
> **arpanaut said:**
> The only way to quickly switch between OS's is to have one OS running with the other OS running in a virtual machine installed on the original OS

See Here: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)
and: [https://help.ubuntu.com/community/Virtualisation](https://help.ubuntu.com/community/Virtualisation)

I don't think my computer can handle a virtual machine program... Thanks anyways.  But are you sure there isnt some kind of link/program that you can click that will automatically restart the computer and select the other OS? It sucks that we have to wait for it to restart to select the right OS or it will choose the default one(I already changed the default OS from Ubuntu to Windows)

---

