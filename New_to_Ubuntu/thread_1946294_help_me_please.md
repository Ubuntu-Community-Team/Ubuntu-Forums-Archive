---
title: "help me please"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by profi on 2012-03-24
Ok first of all have a nice day
I need some help with so many things on this system you called perfect....i lost 4 days just to download ubuntu and start using it.
i have one dell inspiron 620 with windows 7.now i want to use backtrack and as i saw i cant cause i must have ubuntu.from this point my problem begins.i try to download and install it...failed for some reason stop downloading.i try to download .iso and burn it....failed when reboot the pc and start the proceed i have a problem 174 sometimes 167 who killed by someone 9
so i decide to use virtual machine and run it from windows environment.i download VMware player and thats it...finally i made it,at least that i thought.
now i have to see all the available wifi....none.i have internet via cable....interesting cause i dont have cable.so my brain start working and i understand that i am taking internet via windows but the problem is i dont want to take internet via windows cause i want to have my wifi card monitored.second problem:my brand new wifi card wna3100 netgear is not supporting ubundu(in 2012 there are company who dont support all OS?)now what?
problem 3.....i decide at least to see who backtrack working.....failed i cant cause when i am moving the file to ubuntu via usb dosnt have any file that you cant just push it and start running(i have to be professor to use ubuntu?15 years with windows i thought is enough)so i decide to burn it(10 dvd is off)failed for one more time.and now the crucial question:if i spend 4 days to youtube in frond one pc for simple programs how many centuries i have to spend for programming and hacking?
how and what can i do for all that?
p.s 1i am sorry for my tone and especially for my grammar in English but i am not English

---

### Post by kazztan0325 on 2012-03-25
@profi:

Sorry, I don't know how and what can I help you...

Would you please explain your problem more briefly?
Thank you.

---

### Post by profi on 2012-03-26
i thought i speak too much in my first post and that's the reason no one answer,but i was wrong...they just didn't understand  :p
ok here is how the things are untill now.i download VMware player to run ubuntu from windows cause i couldn't do with no other way.
i am trying to use my wifi wna 3100 netgear usb and i cant.i have internet from windows(i am running Ubuntu from virtual machine)via virtual lan but i want to use my wifi card in Ubuntu cause i want backtrack.
that is my problem...nothing is work with Ubuntu and i get angry with that cause i am beginner with ubuntu and i cant resolve the problem by myself.

---

### Post by grahammechanical on 2012-03-26
First, lets us clear up some misunderstandings.

Backtrack is nothing to do with Ubuntu. It is built on Ubuntu but it is independent from Ubuntu. You do not need Ubuntu to install Backtrack. 

So, if you have problems installing Backtrack then you must ask for help at the Backtrack web site. Backtrack is an operating system and not a program you can run in Ubuntu.

Second point. All of us here are volunteers. Do not expect instant help.

Third. If you are burning the ISO image to disk in Windows 7 then error 174, error 167, and message 9 are Microsoft Windows 7 Messages. They are not a problem with Ubuntu.

We do not have to be a professor to use Ubuntu. Your failures are all in Windows 7 and in VMware.

We do not say that Ubuntu is perfect. Actually it is under continual development.

If you are running an operating system in VMware then the access that the operating system has to the hardware (including the modem/router) is through VMware and Windows 7. So, again the problem you have is not with Ubuntu.

---

### Post by profi on 2012-03-26
> **grahammechanical said:**
> First, lets us clear up some misunderstandings.

Backtrack is nothing to do with Ubuntu. It is built on Ubuntu but it is independent from Ubuntu. You do not need Ubuntu to install Backtrack. 

So, if you have problems installing Backtrack then you must ask for help at the Backtrack web site. Backtrack is an operating system and not a program you can run in Ubuntu.

Second point. All of us here are volunteers. Do not expect instant help.

Third. If you are burning the ISO image to disk in Windows 7 then error 174, error 167, and message 9 are Microsoft Windows 7 Messages. They are not a problem with Ubuntu.

We do not have to be a professor to use Ubuntu. Your failures are all in Windows 7 and in VMware.

We do not say that Ubuntu is perfect. Actually it is under continual development.

If you are running an operating system in VMware then the access that the operating system has to the hardware (including the modem/router) is through VMware and Windows 7. So, again the problem you have is not with Ubuntu.

ok we clear half of them....i already install backtrack with Vmware again so i can understand that i don't need Ubuntu
second i didnt said something about the time i understand after the reply of kazztan0325
that i wasn't be clear to what i need.
third...yes i burn it in windows 7 the .iso but i dint run it from windows.i reboot and run the dvd.never mind i didn't know that i have to burn the disc in Ubuntu
and now for the last one..i run ubuntu from vmware and i change the usb from windows to ubuntu.but there is no drivers for wna 3100 so the problem is from ubuntu(actually is netgear as i said and not ubuntu problem)and i have to figure out.
btw thanks for your time

---

### Post by Mark Phelps on 2012-03-26
> **profi said:**
> second problem:my brand new wifi card wna3100 netgear is not supporting ubundu(in 2012 there are company who dont support all OS?)now what?

In fact, very FEW companies produce drivers for OSs other than MS Windows.  So, it's fairly common to find hardware NOT supported in Linux that is supported in MS Windows.

To check on the WiFi card, you should do a search both in the Hardware forum and in the Networking forum -- for thread with "wna3100".  You may find that someone else has already reported the problem and the solution has been found.

---

### Post by mörgæs on 2012-03-26
> **profi said:**
> i thought i speak too much in my first post and that's the reason no one answer,but i was wrong...they just didn't understand

A more informative thread title would also help you getting people's attention.

---

### Post by haqking on 2012-03-26
Backtrack is a specialist security auditing distro with a built in collection of tools built for purpose.

Its wifi chipset support is specific for purpose and limited to certain chipsets out of the box.

see here [http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers](http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers)

and if you are having the issues you say i suspect Backtrack is not a tool you need or should be using, learn more linux first.

Cheers

---

### Post by donkyhotay on 2012-03-27
I'm a little confused about this, my understanding is that you're trying to run backtrack in a virtual machine in windows and to use the WiFi card from ubuntu. In this setup Ubuntu is going to be incapable of directly using the WiFi card because windows has physical control of the system, not ubuntu. You will need to set up the WiFi on windows first and then configure your VM software to allow ubuntu to have network access.

---

### Post by haqking on 2012-03-27
> **donkyhotay said:**
> I'm a little confused about this, my understanding is that you're trying to run backtrack in a virtual machine in windows and to use the WiFi card from ubuntu. In this setup Ubuntu is going to be incapable of directly using the WiFi card because windows has physical control of the system, not ubuntu. You will need to set up the WiFi on windows first and then configure your VM software to allow ubuntu to have network access.

the wifi device he wants to use is a USB device which can be used in a VM, but obviously not at the same time as the host.

---

### Post by donkyhotay on 2012-03-27
> **haqking said:**
> the wifi device he wants to use is a USB device which can be used in a VM, but obviously not at the same time as the host.

When I've used VM's before the network adapter was controlled by the host not the VM. The VM was able to access the internet through the host and didn't control things directly. I've never had the VM directly control any type of NIC that the host couldn't also access. I could be wrong but I didn't think it was possible to have a VM control a NIC without the host also seeing it.

---

### Post by haqking on 2012-03-28
> **donkyhotay said:**
> When I've used VM's before the network adapter was controlled by the host not the VM. The VM was able to access the internet through the host and didn't control things directly. I've never had the VM directly control any type of NIC that the host couldn't also access. I could be wrong but I didn't think it was possible to have a VM control a NIC without the host also seeing it.

I use USB network devices all the time in VM's, a USB device is a USB device regardless of its function.

Specifically Backtrack which alot of people use in a VM and require its own network device, if the USB device is being used by the host then no.

For example right now my laptop is using it internal wireless NIC for internet connectivity, but the BT 5 VM running on it has its own wireless connection using a wireless alfa aw036NH USB device.

Cheers

---

