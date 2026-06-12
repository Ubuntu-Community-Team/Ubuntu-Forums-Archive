---
title: "Problem with nvidia driver on 19.10"
date: 2019-11-22
forum: New to Ubuntu
---

### Post by townhill on 2019-11-22
[I]I've installed 19.10 and the drivers for my nvidia 1050Ti graphics card seem to have installed OK from the iso.  When I check "additional drivers"  I see that I am using  nvdia driver 440 which should be the latest one for my graphics card,  there are several other nvidia drivers listed as well as the nouveau driver.

However when I run nvidia-smi  from the terminal i get the error "[/I]NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running."
I use Blender and when I try to choose my nvidia card for rendering, Blender says no gpu found.    

I tried removing and reinstalling the nvidia drivers but still the driver does not seem to be running.  

The Xserver is set to the nvidia card.  When I run lspci | grep NVIDIA  I get "01:00.0 3D controller: NVIDIA Corporation GP107M [GeForce GTX 1050 Ti Mobile] (rev a1)" so I think the card is seen.  I ran nvidia-settings from the terminal to be sure it is set to my card.  i disabled secure boot and reinstalled drivers again. but still get the same error when running nvidia-smi.

I just left Windows 10 to switch to Ubuntu and could really use some guidance to get my graphics card working.  Any help will be greatly appreciated.

Thanks,

Bob

---

### Post by Autodave on 2019-11-23
Is this a laptop or desktop?  If a laptop, they sometimes have 2 graphics cards in them and will normally run on the lower power Intel card.  Check in your BIOS and see if you can disable that card so that you will only use the Nvidia card.

---

### Post by mörgæs on 2019-11-23
Good point. 

The output from ```
sudo lshw -C video
``` will show if there are one or two cards and the drivers in use.

---

### Post by townhill on 2019-11-23
i am running on a laptop.  The output I get from sudo lshw -C video is pasted below.  I notice that the nvidia card says "unclaimed" with "physical id=0"  

  *-display UNCLAIMED       
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Ti Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128) memory:a4000000-a407ffff
  *-display
       description: VGA compatible controller
       product: UHD Graphics 630 (Mobile)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:136 memory:a2000000-a2ffffff memory:80000000-8fffffff ioport:5000(size=64) memory:c0000-dffff

---

### Post by gnusci on 2019-11-23
[https://docs.blender.org/manual/en/latest/render/cycles/gpu_rendering.html?highlight=gpu](https://docs.blender.org/manual/en/latest/render/cycles/gpu_rendering.html?highlight=gpu)

apt-get install nvidia-cuda-toolkit

---

### Post by townhill on 2019-11-24
Thanks for the tip, Gnusci,  my nvidia card is on the supported list of the blender manual.  i am using Blender 2.81 and it still says no GPU found.

I  installed the nvidia cuda toolkit but I still get the error.  Is there something I need to configure in the toolkit?  If so, I don;t see a way to do that.

sudo bvidia settings returns:

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system


(nvidia-settings:4379): GLib-GObject-CRITICAL **: 12:58:17.846: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 12:58:17.848: PRIME: Requires offloading
** Message: 12:58:17.848: PRIME: is it supported? yes

and nvidia-smi still says that that  the driver isn't running


I beginning to think I might have to reinstall 19.10 again and start over.

---

### Post by townhill on 2019-11-24
The step I was missing was to enroll MOK on reboot.  When I rebooted and rentered my password the nvidia 440 driver was recognized.  Thanks to Gnusci and  [mörgæs]("https://ubuntuforums.org/member.php?u=939075")[COLOR=#000000]  for the suggestions.[/COLOR]

---

