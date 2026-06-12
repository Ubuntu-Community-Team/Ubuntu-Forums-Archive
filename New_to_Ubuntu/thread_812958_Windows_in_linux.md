---
title: "Windows in linux"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
Can anyone indicate me the perfect tutorial on how to run windows applications on linux?

---

### Post by ukripper on 2008-05-30
> **cristo-father said:**
> Can anyone indicate me the perfect tutorial on how to run windows applications on linux?

you will need wine to do that, but all win applications won't run even under wine.

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by Therion on 2008-05-30
That's a complicated question.  

You can either use Wine and see if the application runs well or you could install Windows in a Virtual Machine.  Or you could look for another application that is native to Linux that you could use instead.  If there are LOT of Windows applications you simply MUST use, a virtual machine is probably going to be your best option.  That, or continuing to use Windows.

If you could tell us which Windows applications it is you need to run in Ubuntu we might be better able to help you.

---

### Post by Duck2006 on 2008-05-30
Or you can use crossover, but all win applications won't run in that to. You can run a virtualbox. You can get it from synaptic package manager.

---

### Post by cristo-father on 2008-05-30
> **Duck2006 said:**
> Or you can use crossover, but all win applications won't run in that to. You can run a virtualbox. You can get it from synaptic package manager.

Is it very resource heavy?

---

### Post by Duck2006 on 2008-05-30
> **cristo-father said:**
> Is it very resource heavy?

It may be, but it run's ok on my system.

---

### Post by cristo-father on 2008-05-30
> **Duck2006 said:**
> It may be, but it run's ok on my system.
Is it able to run all windows applications?

---

### Post by ukripper on 2008-05-30
> **cristo-father said:**
> Is it able to run all windows applications?

No depends what you looking to use.

---

### Post by Oldsoldier2003 on 2008-05-30
> **cristo-father said:**
> Is it able to run all windows applications?

not even Windows can do that :)

For the most part VirtualBox or VMWare will run just about any windows program inside a virtual Windows session. 

You will have problems with Games and programs that rely on 3d since its not fully supported in a virtual machine yet.

---

### Post by george9233 on 2008-05-30
> 
You will have problems with Games and programs that rely on 3d since its not fully supported in a virtual machine yet.


I agree with that.

I once tried to install Office 2003 in the Windows guest in virtual box by using CD, but the installer just failed to start properly. 

And one other time I tried to install an online pool game client, the installation was successful,the program was able to start, but when I tried to start a new game it crashed. However, VirtualBox do run more software than wine.

---

### Post by Duck2006 on 2008-05-30
> **oldsoldier2003 said:**
> not Even Windows Can Do That :)

For The Most Part Virtualbox Or Vmware Will Run Just About Any Windows Program Inside A Virtual Windows Session. 

You Will Have Problems With Games And Programs That Rely On 3d Since Its Not Fully Supported In A Virtual Machine Yet.

 +1

---

### Post by jimv on 2008-05-30
Running Windows Apps in Linux

Step 1.  Install WINE with this command: sudo apt-get install wine
Step 2.  Cross fingers
Step 3.  Double click Windows executable file
Step 4.  Experience great joy if program works, or great frustration if program fails.

---

### Post by cristo-father on 2008-05-30
> **Oldsoldier2003 said:**
> not even Windows can do that :)

For the most part VirtualBox or VMWare will run just about any windows program inside a virtual Windows session. 

You will have problems with Games and programs that rely on 3d since its not fully supported in a virtual machine yet.
Is VirtualBox better than VMWare?

---

### Post by Duck2006 on 2008-05-30
> **cristo-father said:**
> Is VirtualBox better than VMWare?

Depends on what your system is, some run better on some systems than others do.

---

### Post by cristo-father on 2008-05-30
> **Duck2006 said:**
> Depends on what your system is, some run better on some systems than others do.
I have a :
Pentium 4 3.0 
1G Ram
Nvidia 6600

---

### Post by Duck2006 on 2008-05-30
I have a Pentium 4, 2.6Gb CPU and 512Mb of ram and it runs ok for me.

---

### Post by cristo-father on 2008-05-30
> **Duck2006 said:**
> I have a Pentium 4, 2.6Gb CPU and 512Mb of ram and it runs ok for me.

VMWare or virtualbox ?

---

### Post by Duck2006 on 2008-05-30
> **cristo-father said:**
> VMWare or virtualbox ?

I have run both at one time or another, but i like virtaul box better and run that now.

---

### Post by saratchandra on 2008-05-31
> **cristo-father said:**
> VMWare or virtualbox ?

I'm using virtualbox to run windows. Download the latest version from their website if you want USB support. My webcam doesn;t run on Linux, so I'm using virtual windows just for that.:guitar:

---

