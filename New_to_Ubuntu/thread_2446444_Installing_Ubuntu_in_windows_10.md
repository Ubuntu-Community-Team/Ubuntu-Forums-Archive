---
title: "Installing Ubuntu in windows 10"
date: 2020-06-30
forum: New to Ubuntu
---

### Post by paoola1950 on 2020-06-30
Hello, I have installed Ubuntu in windows 10 as I have read in the instructions. I went to the store and I looked for the app.
After doing all , I have restarted my pc . Then I looked for Ubuntu, I have clicked on it . And the message is the following
 paoola@DESKTOP-JLM3MPQ:~$

what I need to do know?
Thank you:confused::confused::confused::confused::confused:

---

### Post by wildmanne39 on 2020-06-30
> I have installed Ubuntu in windows 10 as I have read in the instructions.
Please clarify what you mean by installed ubuntu in widnows 10 ? Please post the link to the instructions you followed and someone should be able to advise you.

---

### Post by aljames2 on 2020-06-30
I think the topic is about the Ubuntu environment app that can run on Windows subsystem. 

[https://ubuntu.com/wsl](https://ubuntu.com/wsl)

To your question about “what next”...I think what you are seeing is the command line.  This is where all the magic happens in linux.  You could use this app to learn the CLI and perhaps some scripting.

---

### Post by wildmanne39 on 2020-06-30
> **aljames2 said:**
> I think the topic is about the Ubuntu environment app that can run on Windows subsystem. 

[https://ubuntu.com/wsl](https://ubuntu.com/wsl)

To your question about “what next”...I think what you are seeing is the command line.  This is where all the magic happens in linux.  You could use this app to learn the CLI and perhaps some scripting.

I think so too but we need clarification because just a few days ago we had a couple of users installing using wubi which is dead and was only meant for temporary installation.

---

### Post by Topsiho on 2020-07-01
First thing to ask is: why did the topic starter install Ubuntu in Windows 10?
Second thing to note: in the link that wildmanne39 gives it says that the Ubuntu **terminal** is installed, 
That means that you get a terminal, that is a text screen, in which you can execute Linux commands.
If you don't know Linux commands this is an excellent way to learn these commands.
On the internet you can find a number of .pdf files in which these commands are very well explained.
I would have jumped up and down in the years I myself was learning Linux, but I am afraid the topic starter did not expect this.
Knowledge of these commands is a "lifelong" investment ...

Topsiho

---

### Post by Topsiho on 2020-07-01
As a starter you can look here:

[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)

Topsiho

---

### Post by SeijiSensei on 2020-07-01
I see no strong arguments in favor of WSL over a [VirtualBox]("https://www.virtualbox.org") virtual machine. Plus with the latter, you're not limited to running just the distribution images in the Microsoft Store.

---

### Post by Topsiho on 2020-07-01
Hello SeijiSensei,

There is (in this particular case): the topic starter has the terminal right before his nose. No need to install virtual boxes (does he know how to do this?).
For the rest: of course you are right. :)
Topsiho

---

### Post by SeijiSensei on 2020-07-01
Without denigrating the original poster, it doesn't sound like he's ready for a terminal-only version of Linux.

Is that really what you get if you install Ubuntu using WSL?  No GUI?  I tried using WSL on a Win10 Pro machine and could never get it to install WSL version 2.  

Installing VirtualBox on Windows consists of downloading the executable from the VB web site and running it.  Then you open the app, click on New, and follow the steps to create a virtual machine.

---

### Post by ActionParsnip on 2020-07-01
+1 vote for virtualbox

You can also boot to the Ubuntu ISO on a USB stick (Transfer the file using Rufus) and try the OS there.

Is this what is needed, please? Just to try Ubuntu?

---

