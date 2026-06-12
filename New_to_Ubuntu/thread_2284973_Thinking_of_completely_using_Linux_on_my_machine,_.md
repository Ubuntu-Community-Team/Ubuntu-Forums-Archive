---
title: "Thinking of completely using Linux on my machine, how to do that?"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by jeff131 on 2015-07-02
Hi all,

I have been thinking of using Ubuntu as my default operating system, because I really like Ubuntu, and I do not have anything necessary on my original Windows Operating System. How can I erase all of my Windows data and make my computer all Linux? I may do this quite soon, because I should give myself some time to learn the Linux command line, or I will be stuck on a operating system I do not know how to use. Although, I have heard that Linux command line isn't harder than Mac or Windows command line.


Thank you,

Jeff

EDIT- I have Ubuntu already installed, but in Windows Dual Boot, is there anyway my can make my whole hard drive Linux? (Apologies for not being specific)

---

### Post by stalkingwolf on 2015-07-02
when you install ubuntu the first option you have is to use the entire hard drive.  That wipes everything on the drive.  I would suggest that you dual boot with windows for a time . Just to give yourself time to
get used to ubuntu and to find alternatives to programs that you use that dont have linux alternatives.

---

### Post by cariboo on 2015-07-02
When installing Ubuntu, you are given several choices

[[img]http://i.imgur.com/joI47Yfm.png[/img]](http://imgur.com/joI47Yf)

For the most part, you can do everything graphically, but sometimes it is easier to use the command line, there is a wealth of information on this Forum, so if you run into problems help is just a Google search away

---

### Post by grahammechanical on 2015-07-02
We can use Ubuntu without needing to use Linux commands. By being a regular visitor to this forum you can learn from the answers that people give various useful Linux commands. Some of them produce information about our computer and the operating system. These commands are safe to run and by comparing the results you get on your machine you can learn about Linux.

Be careful about running Linux commands that change things. Be ready to re-install. Or dual boot between 2 installations of Ubuntu - 1 for normal work and 1 for experiments.

Regards.

---

### Post by jeff131 on 2015-07-02
I have actually already done a dual boot with Windows and Linux, with a USB. Concerning about alternatives, just to say, that will not be a concern. The only programs I really need are for school, which I can use Google Drive or LibreOffice. 

Thank you for taking time to answer my question

---

### Post by Jatin_kaushal on 2015-07-03
Can you open up gparted and show us your partitioning scheme? If we can know also know what version of windows you have, we will be able to help you better, because win 7 or lower uses the BIOS settings ( basic input/output system ) but the newer win 8/8.1 uses UEFI ( Unified Extensible Firmware Interface ) or usually just called EFI.

to install gparted, open up terminal and type:
```
 sudo apt-get install gparted 
```

If you want to know what this does, here is the breakdown:

sudo = Super User DO. A command which is used whenever you need to open up or execute a command as the admin of the system. ( a very simple definition of sudo )
apt-get = The package manager of Ubuntu which is a Debian based distribution. Here is a picture showing what branches off of what: [http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png](http://futurist.se/gldt/wp-content/uploads/12.10/gldt1210.png) 
install =  a parameter which we need to give to apt-get to tell it to install the package
gparted = after the install parameter, you need to give the package name. In this case, it is gparted. Some other examples are: gnome-do, compizconfig-settings-manager ( for the fun effects!), vlc, chromium-browser. If you noticed, there is never a space between package names. This is because while using apt-get install  we use spaces to tell it hey, this package name has ended, move over to the next name and install that.

and as for the part about learning the command line, You don't really need to if you are just going to do stuff like surfing the web, google docs, libre office and playing videos. What you do need to learn is the PPA system instead of the .exe files in windows. Here are a few pages where you can read up on ppa:

1) [http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)
2) [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

and here is the main page where almost all PPAs are stored:

1) [https://launchpad.net/](https://launchpad.net/)

As for the rest, if you installed ubuntu AFTER ( after in terms of 'after the partition of windows ) installation of Windows open up gparted and delete the windows partition, then re-size the home partition to cover the unallocated space. If you do not have a /home ( data ) partition, then you should make one by following this article:
[http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/](http://www.howtogeek.com/116742/how-to-create-a-separate-home-partition-after-installing-ubuntu/) 

After you give us your partitioning scheme, we can tell you exactly what to do, but until then, read it up, understand it, but I recommend not doing this as it can delete data.

Thank you for choosing Linux!

---

### Post by jeff131 on 2015-07-03
Hi, 

Okay, because I am ver busy now, and I only have time to answer this quickly, I will follow these instructions. What do you mean by where all PPAs are stored? Do you mean you can find the PPA for an application there? I'm sorry if this question may nag you, but what do you mean if you don't have a home partition?

Thank you for your reply,

Jeff

---

### Post by jeff131 on 2015-07-03
Sorry to bother you, but I do not know how to use gparted. How would you delete the Windows partition? I do not know where it is. And what is the /dev/sda and the /dev/sdb? And sorry to bother you again, but what is the partitioning scheme? Can you please answer these, and I will follow your instructions.

Thank you

---

### Post by monkeybrain20122 on 2015-07-03
If you start gparted it will show you the layout of your hard drive. I suppose that is what you mean by partition scheme. The attached image shows mine.

---

### Post by yancek on 2015-07-03
A pretty detailed tutorial on using GParted is at the link below.  There is a Table of Contents so you can select the section that interests you.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by GrouchyGaijin on 2015-07-04
> **jeff131 said:**
>  The only programs I really need are for school, which I can use Google Drive or LibreOffice. 


Is your school accepting of LibreOffice?  The reason I ask is that at my university my thesis **_had_** to be written in Word.  I suppose I could have written it in LO and then saved as a Word document, but with something as large and involved as a thesis I did not want to risk any formatting issues due to saving in another format.

Furthermore I wanted to use EndNote to manage the references and works cited list.  Yeah, I could have used Zotoro, but in my experience EndNote just does a much better job.

I was able to get a copy of Office 2007 to work under Crossover, but I couldn't get EndNote to communicate with Office via Crossover.  In the end I bought an OEM version of Windows 7 and set up a virtual machine.  The only programs I installed in the VM were Office 2007 and EndNote.

The bottom line is that it would have been much easier if I had had a working dual boot system already set up.

---

