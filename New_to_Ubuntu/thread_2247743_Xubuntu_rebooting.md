---
title: "Xubuntu rebooting"
date: 2014-10-10
forum: New to Ubuntu
---

### Post by Ashima_Loomba on 2014-10-10
Hi All,

   
          I am facing a strange problem of rebooting. Here is the detail of my configuration :
  MotherBoard : Digilite DL-AD2550BG-ITX,
Processor   : Quad thread,
RAM         : 2 X 2 GB SODIMM RAM,
OS          : Xubuntu 14.04 32 bit.
  I am using this machine to run Web Based Application on google chrome.  I also use firefox (for my firewall settings). Some times I need to use both the browsers together. I also rdp to my windows server. 

  The system randomly reboots. I have 5 such machines. Earlier I  thought it could be RAM problem (as I am using firefox) so I increased  the RAM from 2GB to 4 GB and increased SWAP to 4GB. Any kind of help  will be greatly appreciated. I really need to solve this issue.

      

Thank You,
Regards
Ashima

---

### Post by ajgreeny on 2014-10-10
Overheating?  Is it a laptop or desktop?

Do all five machines act the same or just one?

What graphic card and driver?

Check your memory with memtest from the grub menu as that may be faulty.  Let it run as long as you can, preferably overnight and check for any errors it shows at the bottom of the screen.

---

### Post by Ashima_Loomba on 2014-10-14
Hi,
  Thanks for the response. it. 
  They are all Desktops. All of them reboot randomly. Is it  because of heavy web applications it is going out of memory. 
I earlier had 2 GB Ram. Recently upgraded to 4 GB. After that reboots have reduced significantly. Should I consider upgrading the system to 8 GB RAM with 64 bit Xubuntu ? 

It has Built-in Intel® PowerVR SGX545, DirectX 9.0, Pixel Shader 3.0 ( I guess this is the Graphics Card). I have also performed memory test. All clear. No issue with it.
Thanks,
Regards,
Ashima

---

### Post by ian-weisser on 2014-10-15
I have never seen Ubuntu magically reboot because it ran out of memory.

Instead, I have seen performance noticeably degrade as the system consumes more and more swap memory after all the RAM is consumed.
Finally, the application that pushes memory over RAM + Swap will crash.

To the user, it looks like the system gets slower, and slower, then their favorite application hangs, and hangs, and finally crashes.
Then the system is happy and fast again.

Ubuntu does not shut down or reboot without leaving a message in /var/log/syslog. This helps you determine where the halt or reboot command originated. Also, the shutdown is clean.

If the message isn't there, and the shutdown isn't clean, then it's not Ubuntu - it's a hardware fault.

---

