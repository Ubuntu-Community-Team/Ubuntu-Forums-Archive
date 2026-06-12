---
title: "Nvidia problem"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by ashleyb on 2012-05-10
I need some help. Ubuntu is running in low graphics mode because it failed to load nvidia kernel. I have only had my new card for three weeks. I could use some step by step help. I've tried some other things I've seen but none have worked.

---

### Post by kc1di on 2012-05-10
> **ashleyb said:**
> I need some help. Ubuntu is running in low graphics mode because it failed to load nvidia kernel. I have only had my new card for three weeks. I could use some step by step help. I've tried some other things I've seen but none have worked.
we need a little more information, What Card is it of starters?

Also the out put of the following command issued in a terminal would be helpful
```
lspci
``` l is a lowcase L not the number one.

---

### Post by ashleyb on 2012-05-10
It is an nVidia geforce 8400GS

---

### Post by Frogs Hair on 2012-05-10
The computer I am currently using has the same card and is working well with the Nvidia current driver. Try removing and reinstalling the driver from additional drivers and describe what you have tried so far.

---

### Post by kc1di on 2012-05-10
> **ashleyb said:**
> It is an nVidia geforce 8400GS

That card should work with nvidia-current and that should be available in additional drivers tool.

---

### Post by ashleyb on 2012-05-10
How do I remove and reinstall? I don't know that much. So I need it to be dumbed down and very easy to follow. I've googled the problem and have followed things that other threads on here have suggested to type in the terminal but nothing has worked or more likely I don't know how to work it.

---

### Post by Frogs Hair on 2012-05-10
Open additional drivers from dash , select the line with the installed driver and select remove on the bottom right . Close and reopen additional drivers , select Nividia current and select activate . when the driver is downloaded and installed you will be prompted  to restart.

If you have not previously installed a driver install Nvidia current when you open additional drivers. Since you wrote Nvidia module failed to load I assumed you had attempted a driver installation already.

---

### Post by ashleyb on 2012-05-10
[ATTACH]217686[/ATTACH]

[ATTACH]217687[/ATTACH]


Maybe this will help too?

---

### Post by Frogs Hair on 2012-05-10
With an 8400GS you should be offered the two options seen in my screen-shot . I'm afraid  I don't know what you would have to edit in your X configuration, so you will have to wait wait for someone who does .

There are instructions to restart the X sever at the link, but you will have to edit the configuration first.

[http://askubuntu.com/questions/1220/how-can-i-restart-x-server-from-the-command-line](http://askubuntu.com/questions/1220/how-can-i-restart-x-server-from-the-command-line)

---

### Post by sadaruwan12 on 2012-05-11
Your computer is just like mine same type of a PC with all powerful AMD powering it (Love AMD).

On to your problem now,

First tell me did you used the driver installation file from the NVIDIA web site or from a repository or from the "Additional Drivers" ?

Secondly tell me if you had installed the drivers from the NVIDIA installation file have updated your system after that?

For the above two questions if you answer like this,

For Q1 NVIDIA installation file.

For Q2 Yes I did upgrade the system.

Before we start go to the NVIDIA site and download the proper driver package for your system (For you it have to Linux 64 .run file).

Then what you have to is follow the below steps.

1. Press the below listed key combo and drop in to the terminal.

```
Ctlr + Alt + F1 ... F6
```

You can use F1 t oF6 to get a CLI interface.

2. Log in using your user name and the password.

3. Make sure you don't have the free Nouveau driver is not installed. Use the below command to remove it.

```
$ sudo apt-get --purge remove xserver-xorg-video-nouveau
```

4. Now run this command to stop the desktop manager.

```
$ sudo service lightdm stop
```

5. Now use the cd command to go in to the folder  where you've downloaded the installation file.

Ex. if you have your file in the down load folder
```
$ cd Downloads
```

6. Run this command to execute the NVIDIA driver installer.

```
$ sudo sh ./<Name of the package with the extension>
```

7. The installer will start it work just continue saying "Yes".

8. If every thing goes well and finishers you'll drop back to the CLI

9. To restart your computer use the below command.

```
$ sudo init 6
```

10. When the PC boot up your problem will be solved.

OK thats the steps if your answer are yes if not then lets look at it.

---

### Post by ashleyb on 2012-05-11
I did get the driver off the Nvidia website first, then I did an update and everything is working but is just huge. I've gone back to the website to download the drivers again and this is what it keeps telling me...[ATTACH]217721[/ATTACH]

---

