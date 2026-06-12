---
title: "Wine -&gt; Predictwind Offshore app"
date: 2024-06-12
forum: New to Ubuntu
---

### Post by cmckesson on 2024-06-12
Hello Ubuntu community.  I am a complete newbie to Linux.  I am an end-user, not a developer.  My familiarity is CP/M &#8594; MS-DOS &#8594; Windows.  But I now have a new Ubuntu 24 machine and I really like it.

 There is one piece of Windows software that is forcing me to maintain a dual-boot option, and I am here to ask your help it getting the app to run under Wine.

The windows app in question is the Predictwind Offshore App.  Predictwind’s download page is here: [https://www.predictwind.com/apps/offshore-app#downloads](https://www.predictwind.com/apps/offshore-app#downloads) 

As you will see, that page takes you to the Windows Store website, here:[https://apps.microsoft.com/detail/9nblggh2nn9h?hl=en-us&gl=US](https://apps.microsoft.com/detail/9nblggh2nn9h?hl=en-us&gl=US).  The Windows Store website tells me that I can only download the Offshore App after I sign in.  I have signed in to my Microsoft account, but this has no apparent effect on the Windows Store website.

 I now understand that I can only download Offshore by using the Windows Store _App_, not the Windows Store _website_.

Help?

 
 What I have tried:
> Installed Wine, all OK.
> Following instructions I found here ([https://askubuntu.com/questions/1111881/how-to-run-windows-store-apps-on-linux](https://askubuntu.com/questions/1111881/how-to-run-windows-store-apps-on-linux)) I downloaded the "appxBundle"
> I extracted the APPX file.  This resulted in an Offshore.exe file.   
> I ran "wine Offshore.exe" and got error “Unhandled ID query type 0x5”

 Note that I think the resulting Offshore.exe file is the actual app, and is not an installer.  So by trying to run it (under Wine) it immediately goes looking for components that are not installed, hence the fail.

 I would appreciate any help the community can provide.

Given my neophyte status, in my dreams one of you will simply install Offshore on one of your machines, and then tell me the steps that worked.  Of course, I appreciate that this is a big request so I’ll be happy with whatever smaller aid you may provide.

 
 Respectfully,

 Chris McKesson

---

### Post by TheFu on 2024-06-13
[https://www.winehq.org/search?q=Offshore](https://www.winehq.org/search?q=Offshore) doesn't find anything for that application, so I suspect the application has a tiny user-base and nobody has even attempted to get it working with WINE.  

WINE works with less than 20% of general applications and that's if someone struggles to hunt down all the little issues, OCX and DLL files that are required AND those files don't try to use parts of the WIN4 API that WINE hasn't begun to implement.  For someone to go to all that effort, it requires someone who is being paid to do it OR someone (like a teenage boy) who really wants to play a specific game.  Otherwise, most application just won't get the required attention and a community effort to specifically add the missing parts of the WINE API for a specific part of a specific program will never happen.

Now, if you have lots and lots of time on your hands and really don't want to run the program in a dual-boot or inside a virtual machine, then perhaps you are stubborn enough to do all that effort.  If this is _your itch_, and it might be, then I'll wish you luck. You'll need to become a bit of a developer to understand how to read error messages, review stack traces and learn about **winetricks** to get around missing DLLs and calls in your WINE efforts.  

I really wanted Quicken 2010-2013 to work under WINE.  Even got it working about 80% .... meaning the tax planning things never worked, but the registers, and stock data downloads did.  Then Quicken released a new version and everything broke again. They were just beginning to push for their "annual subscription" support model, so I stopped upgrading versions and stayed on the 2013 version.  Eventually, some of the data became corrupted, so I had to use MS-Windows and the extra tools to validate the quicken data files available there.  I've been running that program under a virtual machine since and don't have any plans to upgrade until absolutely forced for some other reason.  Of course, the entire OS it runs under isn't supported, so I keep it offline - no network connections at all. This isn't too bad.  Weekly, I manually enter stock price data and I've been entering all transactional data across every account for longer than I've been using Linux (over 30 yrs), so that isn't an issue to me.  I find entering the data helps me to know where our money is going and how our investments are doing.  Sort like how changing the oil in our cars helps me notices major issues BEFORE anyone gets stranded in the middle of nowhere.

Anyway to get help, you'll need to learn to post the full stack trace inside _forum code tags_ to get any help.  1 error means nothing. WINE throws all sorts of crap output and learning to find the actual error and where it is happening is really necessary.

---

### Post by currentshaft on 2024-06-13
You never said why you need to use Predictwind specifically. There is likely other, better software to do what you want.

What problem are you trying to solve?

---

### Post by cmckesson on 2024-06-13
Thank you for that very helpful reply TheFu.  I didn't realize all of those issues with using WINE.  It sounds like sticking with a dual boot is a better plan for me.
Your mentioned the option of a Virtual Windows Machine.  Can you point me in the direction of an Ubuntu app to that end?  Indeed, that's what I was looking for when I found Wine....despite it being " not an emulator" lol!

Thanks again, very much.

---

### Post by cmckesson on 2024-06-13
My problem is to download weather routing via satellite.
I use PredictWind to obtain weather forecasts in the form of GRIB files, and the Offshore app handles both the display of these files, and also the request, via SatPhone, from the PredictWind servers located in New Zealand.

I live part of year on a boat in the Pacific Ocean, very far off-grid.

---

### Post by grahammechanical on 2024-06-13
Wine developers have to write new code to mimic Microsoft libraries. This takes a lot of time. We should not expect Wine to be compatible with recent Windows versions, such as 10 & 11.

Is it possible to download a useable version of the application you that worked on Windows 7 or 8?

Just a suggestion.

I run a Windows Library type app in Wine. I download from the application's web site. The download is a small exe file. What I get when I run it is the bear application without any data. I then use the application's update options to bring in the data which is about 3.5 GB.

Perhaps your application works in the same way. 

There is more than one way to install Windows apps in Wine. We can install winetricks (it is in Ubuntu Software) and use that. We can run

```
wine explorer.exe 
```

that will load a Windows type file manager and we can use that ti find the exe file and double click. 

Regards

---

### Post by grahammechanical on 2024-06-13
This might be a Linux alternative to the Windows product

[https://zygrib.org/](https://zygrib.org/)

Regards

---

### Post by cmckesson on 2024-06-13
Thank you Graham!

---

### Post by TheFu on 2024-06-13
> **cmckesson said:**
> Thank you for that very helpful reply TheFu.  I didn't realize all of those issues with using WINE.  It sounds like sticking with a dual boot is a better plan for me.
Your mentioned the option of a Virtual Windows Machine.  Can you point me in the direction of an Ubuntu app to that end?  Indeed, that's what I was looking for when I found Wine....despite it being " not an emulator" lol!

Thanks again, very much.

Virtual Machines are a technology, not any specific program.  I've used most of them over the last 25+ yrs. Each has pros and cons.  Sometimes "hypervisor" is the term to search to find the different lineups.  What I use is meant for experienced people, so it probably isn't the best answer for your needs.  Also, if direct access to hardware is needed by the VM, then there are challenges, since VMs usually provide fake hardware for the OS running inside the VM, not access to any direct hardware.  Of course, if the hardware you need to access is on a network, then that works the same as any physical machine would, but if you need to access any adapters via a PCIe slot or USB, there can be challenges.  You'll need to do lots of research before deciding if this method will work for you or not.  

I've been using virtual machines for almost everything for a long time, but I don't need direct access to hardware 99.9999999999% of the time.  For example, if you have a fancy GPU, then you can forget about a VM having access to it.  The hypervisor will provide a "fake" GPU for the guest OS to access.  For normal productivity applications, this is fine.  Some people find it sufficient for CAD software, but almost nobody finds it acceptable for most games that aren't cards or 15+ yrs old.

A few Linux hypervisors that you can research:
[LIST]
[*]Gnome Boxes
[*]VMware Player
[*]VMware Workstation
[*]Oracle VirtualBox
[*]Citrix Xen (or whatever they call it today)
[*]KVM/QEMU with libvirt+ virt-manager
[/LIST]

And there must be 20 others.  I use the last one in that list. It is what most commercial VPS companies use - like Amazon - to let people rent part of a physical server for their own needs.  I've used all of those in the list, except Gnome Boxes.  I found it too dumbed down to be useful.  Also, unless you are an expert, only 1 hypervisor can be installed on a physical system at a time.

Be careful with the licenses.  Oracle's VirtualBox has a F/LOSS license, but the "guest additions", which make it useful for needs like yours are NOT F/LOSS and have some nasty clauses.  Be certain you understand what you are agreeing to. You may become trapped in a license and terms you don't like.

[https://ubuntu.com/blog/kvm-hyphervisor](https://ubuntu.com/blog/kvm-hyphervisor) is an overview. Don't take this as a recommendation for what you should or shouldn't choose.

---

### Post by cmckesson on 2024-06-14
Another awesomely useful response, thank you very much.
I'll do some research and see if any of these options look to be worth the effort for my simple case.  I did look at one option (LXD) which seems straightforward.  I am stopped at the moment because I don't have the bandwidth to download a Windows ISO image.  I also have the question of whether I will need to pay for Windows in order to use it within the VM.  
But I'll take your list and have a look at those options as well.  In a few weeks I may return with more questions.

Thank you again for taking the time to craft such helpful replies.  

Chris McKesson

---

### Post by TheFu on 2024-06-14
I use LXD for managing LXC containers which cannot run MS-Windows.  I've read that LXD could be used for managing VMs too, but since it is a CLI-only interface, I suspect you would rather use one of the GUI hypervisor controllers instead.  I would not use LXD for managing KVM VMs.  It just feels wrong, but perhaps I'm just comfortable doing it the way I've been doing it since 2010 with virt-manager.

Only you can decide.

---

