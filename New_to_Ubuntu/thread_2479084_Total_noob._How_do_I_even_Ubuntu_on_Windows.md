---
title: "Total noob. How do I even Ubuntu on Windows?"
date: 2022-09-14
forum: New to Ubuntu
---

### Post by seanthorp on 2022-09-14
So I'm using Ubuntu from the Windows store because I want to use samtools to index and sort my genome BAM file.

I downloaded the latest tar file for samtools but I don't know how to go about installing it.

I know I should be following the instructions here [http://www.sthda.com/english/wiki/install-samtools-on-unix-system](http://www.sthda.com/english/wiki/install-samtools-on-unix-system)

But I'm stuck as to how I can run the tar command on a file that's on my windows C: drive

Do I need to mount that drive somehow or what commands am I lacking?

Thanks

---

### Post by ActionParsnip on 2022-09-14
You will need to be in the Ubuntu OS. None of this is to do with your Windows OS

---

### Post by seanthorp on 2022-09-14
Thanks but you misunderstand me I think. I'm using the Windows Subsystem for Linux and got Ubuntu from the Windows App store. It's literally running inside the Windows OS as some kind of Virtual System.

---

### Post by tea for one on 2022-09-14
I have never used Ubuntu via Windows Subsystem For Linux but I assume you have access to software repositories?
samtools is in the Universe repository.

More info here (including tutorials) [https://ubuntu.com/wsl](https://ubuntu.com/wsl)

---

### Post by seanthorp on 2022-09-14
Thanks for that, I got samtools installed from your advice but it's a slightly older release, no worries, I bet if I read the tutorials you pointed out I can figure out how to do what I was trying to do and find where the windows file system is at. Thanks

---

### Post by col48 on 2022-09-15
If you want to know where the windows file system is (as seen from Linux), try one of the Ubuntu file managers
Nautilus (the default one) : look under Other Locations
Nemo: look under devices

That still does not guarantee you will have read permission but that is fixable.

I have never had Windows and Ubuntu on the same machine, but these are the places I find the other Ubuntu partition on my dual-boot set-up.  If somehow Ubuntu is buried within the Windows file system this would still be the place to start.

---

### Post by TheFu on 2022-09-15
> **col48 said:**
> If you want to know where the windows file system is (as seen from Linux), try one of the Ubuntu file managers
Nautilus (the default one) : look under Other Locations
Nemo: look under devices
 

WSL doesn't have a GUI. It is CLI/shell by default. WSL doesn't have X/Windows by default.  The GUI can be added [https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://docs.microsoft.com/en-us/windows/wsl/tutorials/gui-apps) according to that link.  

WSL questions definitely need to include that in the thread title, so people with the skill will see it and people without it will not be tempted to provide incorrect information.

If you want the full Linux experience, installing a virtual machine and a full distro install into a VM of any Linux you like will result in a much more standard setup. Properly setup, a VM will provide 90+% of the performance that a native, on-hardware, install provides for everything except GUI intensive stuff like gaming.  For typical office productivity programs, the GUI stuff works fairly well these days. No impact to performance for productivity programs.

In MS-Windows, the GUI is an extension of the OS.  That isn't how it works in any Unix system. The GUI is just another program, with specific hardware requirements.

---

