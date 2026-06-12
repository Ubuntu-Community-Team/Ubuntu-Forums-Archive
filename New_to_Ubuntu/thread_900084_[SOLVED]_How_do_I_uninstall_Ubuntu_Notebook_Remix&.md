---
title: "[SOLVED] How do I uninstall Ubuntu Notebook Remix&amp;gt;"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by cnico88 on 2008-08-25
I downloaded the EEE Ubuntu 8.04 developed by some guy specifaclly for the EEE PC and I installed it on my EEE 1000H. Everything works fine except I want to run the full desktop mode instead of the Remix mode. So how do I go about uninstalling it>? I am doing this because I want to learn linux.

---

### Post by cnico88 on 2008-08-25
anybody?

---

### Post by pyromanic123boom on 2008-08-25
I don't understand...is it like a different version of ubuntu, and you want the regular distro? [www.ubuntu.com](www.ubuntu.com) for an iso file.

---

### Post by valdrini on 2008-08-25
Go to System, Administration, Synaptic Package Manager and search the keyword "NETBOOK" and then select the first one, click with the right button and click mark all for removal or smth similiar. After that is removed, go to the terminal (applications > accessories > termina) and execute sudo apt-get remove ume-launcher. Restart and you will be ok :)

---

### Post by Lirisimah on 2008-12-19
Ok, I want to get rid of the Notebook Remix as well...
I tried what you instructed and it doesn't work in the terminal. I get this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable.)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I really need to get rid of the Notebook Remix, it's driving me crazy. Any help would be appreciated.

I've been perusing the depths of Google trying to find somewhere that'll give me instructions that work but this one keeps popping up the most. I know the thread is a few months old, but I really would like this to get fixed.

---

### Post by w4ett on 2008-12-20
follow the wiki here: [http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Ubuntu_Eee_8.04.1%27s_Regular_Desktop_mode_instead_of_the_Netbook_Remix_interface](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to_use_Ubuntu_Eee_8.04.1%27s_Regular_Desktop_mode_instead_of_the_Netbook_Remix_interface)

Might just help.

---

### Post by slkuhn on 2008-12-26
> **Lirisimah said:**
> 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable.)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Someone can correct me if I am wrong, but I believe that this error just means that you have Synaptic Package Manager open at the same time that you were trying to run the 'apt' command. Simply repeat your procedures but close out Synaptic before you issue your terminal command.

EDIT: I just noticed that this was marked as solved. Would you mind replying with the instructions that solved your problem? I assume that is was the link that w4ett provided for you.

---

