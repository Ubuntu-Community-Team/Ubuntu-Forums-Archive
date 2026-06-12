---
title: "Help, Installing Ubuntu onto VBox"
date: 2024-09-30
forum: New to Ubuntu
---

### Post by desertvsgaming on 2024-09-30
Hello, I am installing Ubuntu into Virtual Box for a class project and I load it in all fine but after the first update it gets stuck at the Ubuntu 24.04 screen with 4 dots. I am unsure on how to proceed or start with finding what is wrong.

I found a YouTube video detailing to hold escape during startup to see a Command line detailing where the error is but it does not work.

I will try and post a screen shot once I figure out how.

Thank you

---

### Post by ian-weisser on 2024-09-30
Does "after the first update" mean that the first boot of the installed VM works properly?

---

### Post by yancek on 2024-09-30
What is the host OS and versions?  Which version of VirtualBox?  I'm also not sure what you mean by 'first update'.  Did you just boot the Ubuntu iso and run it or did you go through the install process after creating the virtual machine in VBox?  Did you then try to update?  Why and how did you try to update?  Did you use a terminal with the apt or apt-get command or the Ubuntu Software GUI installer?

You can attach files or images using the dropd own arrow to the right of the paperclicp icon above the text input box you use in your post.

---

### Post by desertvsgaming on 2024-09-30
> **yancek said:**
> What is the host OS and versions?  Which version of VirtualBox?  I'm also not sure what you mean by 'first update'.  Did you just boot the Ubuntu iso and run it or did you go through the install process after creating the virtual machine in VBox?  Did you then try to update?  Why and how did you try to update?  Did you use a terminal with the apt or apt-get command or the Ubuntu Software GUI installer?

You can attach files or images using the dropd own arrow to the right of the paperclicp icon above the text input box you use in your post.

I installed it and did an upgrade in terminal. When I tried to close down the machine it refused to power down and then finally got a notice that the machine had aborted.

I also used sudo apt upgrade

Host os is windows. Virtual box 7.0.12

And I cant figure out how to attach photos on mobile

---

### Post by yancek on 2024-10-01
>  I installed it and did an upgrade in terminal. When I tried to close  down the machine it refused to power down and then finally got a notice  that the machine had aborted

Does this mean shutting down Ubuntu within Virtualbox or shutting down VirtualBox?  Had your update on Ubuntu completed?  When you try to boot Ubuntu in VBox now, do you see Advanced Options in the boot menu and have you tried them and if so, with what result?  Have you tried reinstalling Ubuntu in VirtualBox again and made notes of the steps you took?

---

