---
title: "I can't open NVIDIA Driver"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by shico90 on 2011-10-14
Hello,
I downloaded a driver from Nvidia site and I can't install it, It writes
Could not open the file /home/shico/Downloads/NV…A-Linux-x86-285.05.09.run.
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.
I posted a screen in the attachment.

---

### Post by Filby1 on 2011-10-14
I get this with an ATI driver also

---

### Post by Filby1 on 2011-10-14
I think you may need to download Synaptic, and download the files that are listed as needed on the website, the readme file on the graphics card website will say you need packages you need them first before you can use the Drivers package you downloaded.

or i might be wrong, im stuck with this myself

---

### Post by TeoBigusGeekus on 2011-10-14
You need to make it executable first.
Open a terminal, navigate to its path
```
cd /home/shico/Downloads/
```
and give
```
chmod +x Nvidia-etc-etc.run
```
Then run it with
```
./Nvidia-etc-etc.run
```
If it complains that it needs root access, use sudo with the last command.
If it further complains that it cannot run the file because the x server is in use, boot up in recovery mode from grub and repeat the procedure from terminal (without sudo this time; you'll be in a root shell).

---

### Post by 3rdalbum on 2011-10-14
Whoa, whoa, wait a minute.

Your graphics card is an Nvidia 8200, according to your earlier post.

I'd recommend NOT to manually install the Nvidia driver from the Nvidia website; it'll be more work for you in the short-term and long-term.

Instead, install it from the Additional Drivers program in Ubuntu. Assuming you have an internet connection, you just need to update your package list (if you don't know how to do this graphically, just run 'sudo apt-get update' in the terminal) and then the Additional Drivers program will offer to download and install a driver for you.

It'll be much easier. Manually installing the Nvidia driver requires installing some additional packages, temporarily turning off the GUI and running the installer on the command-line. The Additional Drivers program is much easier because it doesn't require that stuff.

---

### Post by sadaruwan12 on 2011-10-14
Friends first of all these are executable script files you cant just open them up like in windows by double clicking it the OS don't know how to open the extension.

So why do you want to install proprietary drivers any way Ubuntu do have drivers you need for in the "Additional Drivers" program normally it detects any needed third party drivers and downloads them with out any issue.

If you still want do it using the package from NVIDIA then it's pretty complicated task. You've to know your way around terminal session the old school linux. Also you need to remove the free drivers as well as the third party drivers for NVIDIA if you've installed them

Even after this you want to do it then I'll make it easier for you use this PPA and get your current drivers upgraded. Also remember to remove the old NVIDIA drivers if you have installed them.

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

```
sudo apt-get update
```

```
sudo apt-get install nvidia-current
```

If theres anything come back we'll help you.

---

### Post by shico90 on 2011-10-14
Thank you all so much for your help, I didn't do it manually and let it update itself and it worked. Thanks :)

---

### Post by shico90 on 2011-10-14
> **3rdalbum said:**
> Whoa, whoa, wait a minute.

Your graphics card is an Nvidia 8200, according to your earlier post.

I'd recommend NOT to manually install the Nvidia driver from the Nvidia website; it'll be more work for you in the short-term and long-term.

Instead, install it from the Additional Drivers program in Ubuntu. Assuming you have an internet connection, you just need to update your package list (if you don't know how to do this graphically, just run 'sudo apt-get update' in the terminal) and then the Additional Drivers program will offer to download and install a driver for you.

It'll be much easier. Manually installing the Nvidia driver requires installing some additional packages, temporarily turning off the GUI and running the installer on the command-line. The Additional Drivers program is much easier because it doesn't require that stuff.
Thank you very much :)

---

