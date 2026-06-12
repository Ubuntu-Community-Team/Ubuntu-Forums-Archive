---
title: "Problems with Wine 'hic'"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Gael33 on 2008-08-01
My OS is Ubuntu Hardy 8.04 LTS. 
I installed the latest version of 'Wine' as there are a couple of Windows programs I really need. I know that 'Wine' creates a C:\ drive to install on (it says so in the instructions) but when I try to install a Windows program it tells me the C:\ drive doesn't exist. I have tried removing Wine and reinstalling it using Synaptic Package Manager but that hasn't solved the problem.
Any help would be appreciated.
Thanks,
Gael.

---

### Post by Het Irv on 2008-08-01
How are you trying to install programs?  ```
sudo wine install.exe
```
Something like that?

---

### Post by Gael33 on 2008-08-01
> **Het Irv said:**
> How are you trying to install programs?  ```
sudo wine install.exe
```
Something like that?

I used the Synaptic Package Manager.

Gael.

---

### Post by NovaAesa on 2008-08-01
Okay, you used the synaptic package manager to install wine itself, but how are you installing the Windows prgrommes that you want to use?

You should use the termital for this. Change the working directory to where the setup file is (probably setup.exe or install.exe) and then run the termital code:
```
sudo wine filename.exe
```
This should start the installer for the programme you are trynig to install.

---

### Post by Gael33 on 2008-08-01
> **NovaAesa said:**
> Okay, you used the synaptic package manager to install wine itself, but how are you installing the Windows prgrommes that you want to use?

You should use the termital for this. Change the working directory to where the setup file is (probably setup.exe or install.exe) and then run the termital code:
```
sudo wine filename.exe
```
This should start the installer for the programme you are trynig to install.

I've had a look at WineHQ and it says that Wine 1.0 is the stable program. The program after that is a development and does not receive a key certificate (yet). If I download the stable program (Wine 1.0) on to the desktop, how do I install it from there using the Terminal?
Please remember I am only a novice with Ubuntu although I am familiar with Windows.
Thanks,
Gael.

---

### Post by Het Irv on 2008-08-04
On the Wine install page, there is a section describing how to add the Wine Repository into your sources list and then install it.  This is the best way to install Wine because it will allow the Package Updater to automatically update Wine.

---

